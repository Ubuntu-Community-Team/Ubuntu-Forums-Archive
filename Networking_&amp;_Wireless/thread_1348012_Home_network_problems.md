---
title: "Home network problems"
date: 2009-12-06
forum: Networking &amp; Wireless
---

### Post by xzing on 2009-12-06
Ok I am at wits end here.  I just installed Ubuntu 9.10 this weekend and I can't get the other computers on my home network to see my shared drives.  The other computers on the network are both Ubuntu and Windows XP machines.   I made sure samba was installed.  I checked the "smb.conf" file and made sure that both the correct "workgroup" and "hostname" were there.  Everything seems to be set up correctly according to all of the info I have seen online looking for a solution.  Connecting to the internet is not a problem either.  But here is the weird part. I can solve the problem if I restart samba and the network in the terminal. by typing ```
sudo /etc/init.d/networking restart
``` and then typing ```
sudo /etc/init.d/samba restart
``` (not necessarily in that order).  What is going on?  Can I just get the computer to show up on the network without having to go through this rigmarole each time I reboot?  

I don't know what info you would like me to share with you about the computer or the network but if you ask me I will be glad to share what I can.  Between this and the 17 other Ubuntu problems I am currently having I am beyond frustrated and I have had nothing but trouble so I really need some help here, please.

Xzing

---

### Post by Iowan on 2009-12-06
Sorry to hear about your problems - hope I don't add to them...
I've seen some threads that suggest installing **smbfs** along with the Samba server.

---

### Post by xzing on 2009-12-06
> **Iowan said:**
> Sorry to hear about your problems - hope I don't add to them...
I've seen some threads that suggest installing **smbfs** along with the Samba server.

First of all I appreciate the quick response.  I will take anything I can get.  Unfortunately I feel like I am floating on an river of Ubuntu without a paddle.  So I will take any suggestions.  However, I tried that too.  I went to package manager and installed [B]smbfs[\B].  That seems to have made the change to working by restarting Samba and the Network.  But still no good.  Any other ideas though?  Two heads are better than one! :D

---

### Post by Kanshu on 2009-12-07
> **xzing said:**
> First of all I appreciate the quick response.  I will take anything I can get.  Unfortunately I feel like I am floating on an river of Ubuntu without a paddle.  So I will take any suggestions.  However, I tried that too.  I went to package manager and installed [B]smbfs[\B].  That seems to have made the change to working by restarting Samba and the Network.  But still no good.  Any other ideas though?  Two heads are better than one! :D
I sympathize with you. I'm also trying to connect two computers with a cable, but I can't seem to get a straight answer. I tried following instructions from an Ubuntu book, but there seems to be a point in the explanation where I get lost. The context seems to be different so there is always that gap in the explanation. Anyway, I hope you don't mind me piggybacking on your thread. I like to see several solutions to the problem.

By the way, I have a dual boot desktop with XP and Ubuntu 9.10. And the notebook has XP, Ubuntu 9.10 and Kubuntu 9.10. I'd like to start with an Ubuntu to Ubuntu connection first.

---

### Post by DGortze380 on 2009-12-07
Are you sure Samba is actually running at boot time?

You can't access shares.
Run /etc/init.d/samba restart
Can Access shares
Reboot
Can't access shares


Sounds like it's not coming up at boot.

---

### Post by bayvista on 2009-12-08
There's a major problem with 9.10 networking so I suggest you go back to 9.04 until they fix it. That's what I did.

---

### Post by davidm84 on 2009-12-08
> **bayvista said:**
> There's a major problem with 9.10 networking so I suggest you go back to 9.04 until they fix it. That's what I did.
I'm using 9.10. All I had to do is write a script (that does the aforementioned restart of samba) then run this with the boot. This also comes in dandy if you wish to add more operations when booting.
Never had a problem with the "networking" at all!

---

