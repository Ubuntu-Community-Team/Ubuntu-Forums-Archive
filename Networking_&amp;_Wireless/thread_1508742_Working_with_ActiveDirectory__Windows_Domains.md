---
title: "Working with ActiveDirectory / Windows Domains"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by damian_ on 2010-06-13
Using Ubuntu 9.10 ..

I have recently set up a Windows Domain using Windows 2003 SBS, everything seems to work well and how it's meant to. I have managed to link up my Ubuntu laptop into the domain using Likewise and that all works fine, although it took a few setting changes to make it all connect properly.

I am now looking for a method of running login scripts for the domain users, which I can't find documentation ANYWHERE on how to do it, if there even is a way to do it ..

I guess the easiest method would be to set up the client machine to check a remote path for a script to run after login, but I'm trying to steer away from a method that requires me to modify the client machine (just in case I need to change paths on the server, I'd have to update every client using the server).

Even doing it the above mentioned way, I still haven't been able to find documentation on how to 'catch' the system when adding a user so it can modify their .profile to map drive/run script.

If anyone has figured out how to do any of this and can explain or send me in the right direction I'd appreciate it, at the moment it just seems like I'm getting nowhere!

Thanks

---

