#!/bin/bash

echo "Password Generator with Encryption & Decryption"
echo "Must be a SUPER USER "
sudo apt-get update -y
sudo apt-get install cut -y
sudo apt-get install gpg -y
echo " Select any Option Password Generator Encryption or Decryption"
echo "Enter the choose"

choice="Password_Generator  Password_Generator_with_Encryption Decryption"


select option in $choice;
do
	if [ $REPLY = 1 ];
	then
		echo "You have Selected Password Generator"
		echo "Enter the Length of the Password which u want :"
		read Pass_length
		echo "Enter the Sequences of Password you need : "
		read Length
		echo "Enter the filename"
		read Name
		touch $Name.txt /home/unkown/Documents/
			for i in $(seq 1 $Length);	
			do
				openssl rand -base64 48 | cut -c1-$Pass_length >> /home/unkown/Documents/$Name.txt
			done
			exit 0
			
			
	elif [ $REPLY = 2 ];
	then
		echo "You have Selected Encryption with Password Genearatiom"
		echo "Enter the Length of the Password which u need: "
		read Pass_length1
		echo "Enter the Seqences of Password you need :"
		read Length1
		echo "Enter the file name : "
		read Name
		
		touch $Name.txt /home/unkown/Documents/
			for i in $(seq 1 $Length1);
			do
				openssl rand -base64 48 | cut -c1-$Pass_length1 >> /home/unkown/Documents/$Name.txt  
		 gpg -c $Name.txt
			done
	
		echo "The File $Name.txt has been Encrypted"
			
				

		elif [ $REPLY = 3 ];
		then
	
			echo "You have Selected Decryption"
			echo "You have Select a File which inside a director which this script is there"
			echo "Enter the file name to Decryptd"
			read File2;
			gpg -d $File2
			echo "The file $File2 has been Decrypted"
			exit 0
		else [ $REPLY -gt 4 ];
			echo "You have selected wrong input"
			exit 0
			

   	fi
done

exit 0
