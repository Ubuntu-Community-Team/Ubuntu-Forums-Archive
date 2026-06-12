---
title: "Failure at attempt to directly transfer files from PC to PC over the internet"
date: 2009-01-12
forum: Networking &amp; Wireless
---

### Post by Aralhach on 2009-01-12
I've been looking for a way to directly transfer files from my computer to a friend's computer over the internet (without using email, or file storage servers, or anything like that).  I tried to get an FTP server running on my computer.  I installed the ProFTPd package, and downloaded a File Sharing app that shows up on my System > Preferences menu, and gives a port and everything. My friend has tried to connect (with Filezilla, from a Windows XP SP3 computer) with no avail.

I have a wired network on this side.  What's the command in Linux to know the local IP address and the global one if possible (without going to showmyip.com).  I told my friend to connect to port 21, 10021 (the port that it said on the file sharing thing) and nothing works.

I would really appreciate some help here.

---

### Post by dmizer on 2009-01-14
Does your friend use linux?

Both of you will have to configure your router/firewall for port forwarding. If you're dead set on FTP, you can take a look at the third link in my sig. Otherwise, I suggest something encrypted and secure like [ssh](http://www.debian-administration.org/articles/27).

---

### Post by Aralhach on 2009-01-14
Yes, he uses Ubuntu Hardy (I use Intrepid).  I didn't think that was too important.  I've heard of SSH, and I will look into it.

Thanks a lot! (I don't know what happened to the thanked posts thing :))

---

