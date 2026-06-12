---
title: "Guide to Authenticating Against Novell Server"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Augsburg on 2009-04-15
I have a quick and easy procedure for Authenticating (and connecting) to a Novell Server.  Here is how:

> sudo apt-get install ncpfs
> cd /usr/bin
> sudo chmod +s ncp*

create the file novelAuthenticate.sh:
> nano novelAuthenticate.sh

> #! /bin/sh

#Get username
echo "username:"
read input2
#Get first letter of last name (if needed for context)
input3=$(echo $input2|awk '{ print substr( $0, 1, 1 ) }')
#Get password
echo "password:"
stty -echo
read input4
stty echo
#Putting it all together
ncplogin -S ldap.<server.com> -A ldap.<server.com> -U .$input2.$input3.<remaining parents in tree> -P $input4
sleep 2
#Check if it mounted
if [ "$(mount |grep LDAP.<server.com>)" = "" ]
then
	echo "not logged in"
	else
                #unmount server volume
	        ncplogout ncp/LDAP.<server.com>/SYS
                #exit script
		exit 0
	fi
	echo "login failed"
#re-run until correctly authenticated
sh novelAuthenticate.sh

Lastly:

> cp ~/novelAuthentication.sh /usr/bin
> cd /usr/bin
> sudo chown root:student novelAuthenticate.sh
> sudo chmod +s novelAuthenticate.sh


To mount the server (the netware server in my case was just for authentication), i used ftp (if your server doesn't have ftp available, there are other means of doing it.  I find this way to be very effective):

> sudo apt-get install curlftpfs

Then add the following to the script just after the ncplogout line:

  curlftpfs ftp://$input2:$input4@ftp.<server.com> <mount point>

I found it beneficial to create a folder in my home folder to user solely as my mount point.

To run the unmount script at logout, add this line to /etc/gdm/PostSession/Default just before the last line (exit 0):

fusermount -u <mount point>

---

### Post by cjfisrt on 2009-05-21
Hi 

Thanks for the info.....I am lookign for a solution that will help me to recieve the ldap notifications from EDir and also to enable the users to reset there passwords from there ubuntu work stations......

Do you have any idees?

Cheers

---

