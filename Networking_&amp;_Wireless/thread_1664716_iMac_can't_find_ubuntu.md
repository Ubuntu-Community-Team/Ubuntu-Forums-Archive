---
title: "iMac can't find ubuntu"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by proslambano on 2011-01-11
Hi, 
I have ubuntu 10.10 and a new iMac with Snow Leopard 10.6.6

I can find the shares on the mac from ubuntu.  But when I try to find the ubuntu shares from my mac, the imac finder gives me the message "Connection Failed".  It offers me a "connect as" button, but this just simply gives me the message "The server 'ubuntu' may not exist or it is unavailable at this time. Check the server name or IP address...".  Note: the server name should be correct because the ubuntu machine shows up in the sidebar of finder as "ubuntu" the name of my ubuntu machine.

I tried Finder / Go / Connect to Server and entered "smb://192.168.1.91", the local IP.

This seemed like it might work, because it asked me for my username and password.  I typed in my ubuntu username and password and it replied that one or the other didn't match!

What should I do next?  

Many thanks
Brian

---

### Post by PatchesTheCaveman on 2011-01-11
Samba (Windows file sharing) uses a different password store, because Windows uses a different hashing/encryption algorithm for its passwords as opposed to Linux.  To set your password for file sharing, go to Applications > Accessories > Terminal and type the following in the black box that appears and press Enter:
```
sudo smbpasswd *<username>*
```
You will be asked for your normal password.  Type that in and press Enter.  It won't show stars or dots or anything but it will work.  Next you'll be asked for the password for file sharing.  Enter that in (it can be the same as your login password) and hit Enter.  You'll be asked to repeat it.

You should then be able to access it from your Mac with the password you just set (if it's different).

---

