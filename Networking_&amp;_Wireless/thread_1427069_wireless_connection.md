---
title: "wireless connection"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by prabir on 2010-03-11
i am new to ubuntu, and recently upgraded to 9.10

when i connected by usb modem and tried to configure, i got the following response:

mm@mm-laptop:~$ wvdialconf
The program 'wvdialconf' is currently not installed.  You can install it by typing:
sudo apt-get install wvdial
wvdialconf: command not found

mm@mm-laptop:~$ sudo apt-get install wvdial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wvdial is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wvdial has no installation candidate

please guide me.

---

### Post by Naggobot on 2010-03-11
Few weeks ago I tried to install some program. I cant remember what it was, probably bluefish. 

For some reason repo in my country did not have that pakage. 

I fixed the issue by changing the repo to main repository. 

You can try this as follows

System -> administration -> synaptic pakage manager

in synaptic select from top menu

settings -> repositories -> download from -> main server

Remember to change back to your local mirror if  you try this. 

Before you try check that wvdial is not installed. I have it installed but I have not used pppeven once. It is probably installed since I have integrated modem. 

Other than this I can not offer any resolutions. I hope that someone else has better and deeper understanding and can help you.

---

