---
title: "Ubuntu can't access Win PC"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by sandman3838 on 2010-05-11
Hello

I have to ask but what am I missing here?

All my other systems in the house can access my Ubuntu 10.04 system (Shared folder).

However my one Ubuntu PC can't access Windows (Shared) in this case Winxp.  Now all my other Winxp & Win_7 system can access each other.

Basically Ubuntu Can't access Winxp Shared folder.  It's listed as an icon  Windows Network but when I select the Winxp computer I get "UNABLE TO MOUNT LOCATION"  

Attached is my SMB file if you see something missing please let me know.

Thank you for your time and help.

---

### Post by sandman3838 on 2010-05-11
Got it!
I thought I had lost this information but I had saved it in a word document.  After each of the solutions here I tried to access the Win systems.  Each time it failed until I did problem 3 part 2!  
I hope this helps....

******************************** 

Problem 1:
Ubuntu is not able to browse shares in workgroups that it is not a member of. By default, Ubuntu is a member of the “WORKGROUP” workgroup, but not all Windows computers use this convention. In order to correct this problem, you’ll need to verify that all your Windows computers belong to the same workgroup. In order to check/change that, please see this Microsoft support document: [http://support.microsoft.com/kb/295017](http://support.microsoft.com/kb/295017)
= = = = = = = = = = = = = = = = = = =

Problem 2: 
There is no easy way to change the workgroup that Ubuntu belongs to. This means that you can either assign all of your Windows computers to the “WORKGROUP” workgroup (as outlined under "Problem 1"), or edit /etc/samba/smb.conf in order to change the workgroup that Ubuntu is a member of.


Problem 2 - part 1
Open this file for editing with the following command:

Code:
gksudo gedit /etc/samba/smb.conf

Scroll down to the section that looks like this:

Code:
 #======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
Change “WORKGROUP” in “workgroup = WORKGROUP” to match your Windows workgroup.

Problem 2 - part 2
It may also help to add netbios name = computer-name just below "workgroup = WORKGROUP".

Your "computer-name" can be anything, but common convention is to use the name you gave it when you installed Ubuntu (everything after the "@" symbol on the CLI prompt).

For example, here's my CLI prompt:

Code:

And here's my smb.conf file:

Code:
#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = WORKGROUP
   netbios name = shinkansen
Now, save the file by clicking on "File" > "save", close gedit, and restart samba with the following command:

Code:
sudo /etc/init.d/samba restart

If, after running the above command, you see this error:

Code:
sudo: /etc/init.d/samba: command not found

Just reboot your machine instead.
= = = = = = = = = = = = = = = = = = =

Problem 3:
Ubuntu is unable to browse Windows host names by default. Enabling this ability will also require a conf file edit.

---CAUTION---
If you are using Firestarter, uninstall it before making this edit. Firestarter may prevent the machine from booting after this change is made. Use GUFW instead.
---CAUTION---

Problem 3 - Part 1
Open /etc/nsswitch.conf for editing with the following command:

Code:
gksudo gedit /etc/nsswitch.conf

Find the line that looks something like:

Code:
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4

For this line, order IS important. You’ll need to add the “wins” option before dns, so the line reads like this:

Code:
 hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Now, save the file by clicking on "File" > "save" and close gedit.

Problem 3 - Part 2
You'll also have to install the winbind daemon in order to resolve hostnames. This is easily done with the following command:

Code:
sudo apt-get install winbind
Then, either restart networking or reboot.

---

