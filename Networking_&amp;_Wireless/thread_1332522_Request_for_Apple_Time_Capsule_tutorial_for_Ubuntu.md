---
title: "Request for Apple Time Capsule tutorial for Ubuntu 9.10"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by vendicate on 2009-11-20
I have followed the tutorials out there on how to connect and they all say this:

> Time capsule is an apple NAS product. You can connect to it using an ubuntu system with the following procedure  
[LIST]
[*]Make sure you have *smbclient* and *smbfs* installed, check by doing a search using synaptic package manager
[*]Create Media folder in root named "capsule"
[/LIST]
 cd /media
sudo mkdir capsule

[LIST]
[*]Create a launcher using the following script
[/LIST]
 sudo mount.cifs //192.168.1.1/"Your Friendly Time Capsule Name"/ /media/capsule -o pass=password

[LIST]
[*]where:
[LIST]
[*]The IP Address is the one that you assign to the Time Capsule using your Apple AirPort Utility on a Mac,
[*]The 'directory' name enclosed in double quotes is the name assigned to your Time Capsule when it it set up on the Mac - see how the volume appears listed on a Mac machine to derive this,
[*]/media/capsule is the name of the mount point that you selected,
[*] password is replaced with whatever password you elected to use during the Airport configuration. Apple give you two options here. You can either use the same password as your Wireless Network password [generally a bad idea] or you can select a different one [obviously much more sensible].
[/LIST]
 
[/LIST]
This does not work for me and many others. Please submit a better tutorial..

This is the error I get:

> [COLOR=DarkGreen]bruno@buddha:~$ sudo mount.cifs //10.0.1.1/"Time Capsule"/ /media/capsule -o pass=password
[sudo] password for bruno: 
retrying with upper case share name
mount error(6): No such device or address
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
bruno@buddha:~$ nmblookup -A 10.0.1.1
Looking up status of 10.0.1.1
    TIME-CAPSULE    <00> -         B <ACTIVE> <PERMANENT> 
    WORKGROUP       <00> - <GROUP> B <ACTIVE> <PERMANENT> 
    TIME-CAPSULE    <20> -         B <ACTIVE> <PERMANENT> 

    MAC Address = 00-26-BB-6C-12-BE

bruno@buddha:~$ smbclient -L //TIME_CAPSULE
Enter bruno's password: 
Connection to TIME_CAPSULE failed (Error NT_STATUS_BAD_NETWORK_NAME)
bruno@buddha:~$ [/COLOR]  


---

