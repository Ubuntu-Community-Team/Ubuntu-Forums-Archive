---
title: "Win 7 cannot access share - using Webmin to administer."
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by houldsworth1 on 2010-07-09
Hi all. 

I'm pretty new here and I want to be able to set up my Linux box as a shared drive (so that I can use it as a backup drive to my win7 machine).

I'm using webmin to administer Samba and I get to the point where it shows:

[COLOR="Blue"]Share Name   	Path   	                Security   
homes	        All Home Directories	Read/write to everyone[/COLOR]

When I go to my win7 machine it I can browse to the machine (called jira2) and see the folder called homes, but when I click on the folder it says [COLOR="blue"]Windows cannot access \\JIRA2\homes[/COLOR]
if I expand the details it says [COLOR="blue"]Error code 0x80070035[/COLOR]

I am running Ubuntu 10.04.

Thanks for the help.

---

### Post by Audiosears on 2010-07-22
Houlds,

With Windows 7, by default it wants to authenticate using only the ntlmv2 handshake - usually tweaking the local security policy will allow it to connect to samba shares:

[http://www.builderau.com.au/blogs/viewblogpost.htm?p=339270746]("http://www.builderau.com.au/blogs/viewblogpost.htm?p=339270746")

Setting the network security on the windows 7 machine to send both LM and NTLM responses may be of help.  You can also set this up as a group policy rule if you're running Active Directory on your network and have multiple Windows 7 terminals...

---

