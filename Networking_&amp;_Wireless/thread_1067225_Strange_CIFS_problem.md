---
title: "Strange CIFS problem"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by droker on 2009-02-11
Hi Everyone, 

This is my First post. 

I have been using Ubuntu for about a year now and have been singing its praises for to my family and friends, and have managed to convert everyone.

I recently changed pc from a Athalon X2 4200+ to a Shuttle X27D dual core atom board. I copied all the settings over from my old pc to my new one.

This is the first problem I have had that i cant fix, and im really confused. It was not a problem on my old pc.

I have mounted a drive using cifs in /etc/fstab with the following line: 

//192.168.100.3/Downloaded	           /media/downloads cifs	credentials=/home/droker/.smb_pass,nounix,iocharset=utf8,noperm,file_mode=0777,dir_mode=0777 0 0

When i try and copy 1 file from the share to my pc i get about 2MB/sec. If i start a second simultaneous transfer the data rate for both increase to about 3.5-4.5 MB/sec so 7 MB/sec total. If i cancel 1 transfer the other slows back down to 2MB / sec again.

If i go through the Places/Network way of getting to the share I and copy the same file to the pc, I get 7-8 MB/sec

I used wireshark to take a network trace of the 2 scenarios. With the CIFS share It requests 16K blocks if information. With the Places/Network transfer it requests 64K blocks. But this wouldnt explain why running 2 transfers at the same time speeds things up.

To make things even stranger If i copy a file from my pc to the share I get about 10MB/sec.

I hope someone can help because i am at a loss. it seems one other person has had the same problem as me in the past but there was no solution posted.

[http://ubuntuforums.org/showthread.php?t=723333&highlight=cifs+performance+multiple](http://ubuntuforums.org/showthread.php?t=723333&highlight=cifs+performance+multiple)

Thanks in advance for your help

Dean

---

### Post by FishRCynic on 2009-02-11
you may have already done this:

altf2 gksudo gedit /etc/samba/smb.conf

or in termingal
sudo gedit /etc/samba/smb.conf
(or vi or nano or editor of choice)


try adding

socket options = TCP_NODELAY

or

socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192

there are other options but these work for me

restart samba

---

### Post by droker on 2009-02-11
Thanks for the speedy reply.
Unfortunately I have tired every combination of options in the smb.conf file. And nothing works.

I think the problem is more fundamental than that, probably something to do with a network driver combined with samba issue, as i didnt have this problem on my old pc (with same smb.conf settings, and talking to the same freenas box)

I dont understand why adding a second transfer speeds both up?

Any one else got any ideas?

---

### Post by dmizer on 2009-02-11
Does the problem persist if you enable netbios name resolution with winbind?

---

### Post by droker on 2009-02-11
I have managed to fix it :D

After much googling, I narrowed it down to a bug with the RealTek driver that only seems to show up with samba. If you follow the instructions in that link, it compiles r8168 driver from source and blacklists the r8169 driver that Hardy loads as default.

[http://www.jamesonwilliams.com/hardy-r8168](http://www.jamesonwilliams.com/hardy-r8168)

I know get 6.9 MB/sec instead of 1-2. and my write speed to the server has gone up slightly as well :D

Thanks for your help.

How do i go about getting this raised as a bug? Anyone know?

---

### Post by droker on 2009-02-11
Ok I spoke too soon, the performance still goes up if i have 2 transfers happening at the same time, but now i only get a 20% increase in performance compared to an 80% change i was seeing before.

I can live with the change for now, how do i get a bug raised?

Thanks

Dean

---

### Post by dmizer on 2009-02-11
> **droker said:**
> I can live with the change for now, how do i get a bug raised?

Thanks

Dean

Have a look here: [http://ubuntuforums.org/showthread.php?t=1011078](http://ubuntuforums.org/showthread.php?t=1011078) :)

---

### Post by droker on 2009-02-12
Excellent :)

Thank you.

---

