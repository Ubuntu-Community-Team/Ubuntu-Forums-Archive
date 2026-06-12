---
title: "Home Network"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by DoctorVell on 2012-06-26
Hi there,

Here is the current setup:

Wife's Computer: Windows 7
My Computer: Ubuntu 12.04

Both updated to the last updates.

We both connect to the internet via WIFI through Clear Internet...works great for both of us.

I am wondering is there a way we can have it that if we have to chat with each other WITHOUT connecting to the internet and so she can send me files and I can send her files without messing with the internet.

Hope this is clear (no pun intended) to understand, if not ask and I will TRY to clarify it.

---

### Post by sudodus on 2012-06-26
Yes it is possible. I suggest that you install ***ssh server*** in your Ubuntu computer. And she can install ***winscp*** in her Windows computer. And you create a common directory and/or a user account for your wife in your computer.

Then she can transfer files to the common directory (and her user account's home directory).

If she also gets some ***ssh client*** software, she can also log in to her user account and you can chat the 'original' way using [FONT="Courier New"]write[/FONT]. There are of course also more modern softwares to accomplish the chatting. Many of them are using the detour via the internet. I think ***Skype*** is using the internet for finding the other computer, but after that it might establish a direct connection between your computers.

---

### Post by Morbius1 on 2012-06-26
Another option if all you want is to transfer a file from A to B: TransferOnLan : [http://code.google.com/p/transfer-on-lan/](http://code.google.com/p/transfer-on-lan/)

It's java based so you just extract it and run it instead of installing it. And since it's a jar file it can be run on Windows, Linux, and Mac.

---

### Post by DoctorVell on 2012-06-27
Thank-you both!
:) :) :) :) :)

---

### Post by asmoore82 on 2012-06-27
The current linux version of the Pidgin instant messenger (formerly GAIM) supports "ad-hoc" chatting on the local subnet with the Avahi/mDNS/Bonjour system. I would assume the windows version of Pidgin will do the same if Bonjour (comes with iTunes) is installed.

---

