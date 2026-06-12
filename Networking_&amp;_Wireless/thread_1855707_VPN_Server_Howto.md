---
title: "VPN Server Howto?"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by Goldendog on 2011-10-06
Hello, 

I have been searching the internet for two days and have posted on three different boards.  I am trying to get a Windows 7 machine to VPN into my Ubuntu 11.04 at home.  I would like to map a drive to use data for a Windows Application.

I am completely new to Linux and have been trying to find a guide to walk me through the process.  So far I have checked out OpenVPN and Untangle.

Any links, descriptions, flames, opinions, or instructions are most welcome.

I have a shared folder and mapped drive that my Windows 7 box can read/write to while in the same network already configured.  Now, how do I take it across the internet...

Thanks fellas.

---

### Post by Iowan on 2011-10-06
[Here]("https://help.ubuntu.com/11.04/serverguide/C/vpn.html") is a link to the 11.04 Server Guide.
The description suggests it's for creating a VPN between two servers - so it may not be what you're looking for.

---

### Post by Goldendog on 2011-10-06
This looks great, thank you.

I will give it a go in the morning.

---

### Post by Goldendog on 2011-10-07
I am getting an Error when trying to copy the ta.key file from the Ubuntu Server to place it on the Windows machine.

The file has an 'X' next to it and when I try to copy:

Error while copying "ta.key".
There was an error copying the file into /Share
Error opening file: Permission Denied

I tried using the 'CP' command and right clicking the file and checking properties.  It says I am not the owner of the file.

How do I get this badboy onto the Windows machine like the instructions tell me to?  I have followed the above tutorial step by step.  Thanks!

EDIT:
I tried doing a users command to get my info and applying it to a CHOWN command.
'changing ownership of 'ta.key': operation not permitted'

---

