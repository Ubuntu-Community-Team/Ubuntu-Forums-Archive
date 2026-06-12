---
title: "No internet connection in Ubuntu 9.04"
date: 2009-10-12
forum: Networking &amp; Wireless
---

### Post by Radissthor on 2009-10-12
Hello, I've just switched to Ubuntu from Windows and, for my sorprise, the internet connection was recognized at once. I have a Dell Inspiron 1525.

I went to another house, where I had to configure a PPPOE connection besides the wireless connection. It worked fine. 

The problem is that now, back at my house, Wired Nteworks says "disconnected" and wireless Networks (the one I use) says "device not managed"

Maybe I screwed up when setting up the other connection... I would appreciate some help, since I'm new at Ubuntu and don't much about computers in general. 

Thanks!

---

### Post by Iowan on 2009-10-12
It seems like some PPPOE connections store information in */etc/network/interfaces*, and when an interface is defined there, Network Manager doesn't touch it. Check contents of that file - you should be able to comment out everything except the two lines defining "lo", and restart/reboot. Still, it *shouldn't* mess with the wireless connection.

---

### Post by Radissthor on 2009-10-12
Thanks for replying!

I'm afraid I don't understan the instructions. I'm really very new at this. Anyway, I didn't find any folder called network or iterfaces. I typed /etc/network/interfaces in the terminal and it replied:
bash: /etc/network/interfaces: Permission denied

What do I do?

---

### Post by Radissthor on 2009-10-12
Please help. I went to System>Administration>Network Tools and in Network device it says: Loopback Interface (lo). Other options available are eth0, eth1 and Unknown Interface (pan0)...
Please help, I've tried but I'm too unexperienced in Linux

Oh! and another thing:

When I go o system>Administration>Hadwire Drivers, it says that Broadcom STA wireless driver is activated and currently in use

Any help?

---

### Post by Iowan on 2009-10-12
> **Radissthor said:**
> What do I do?:oops: Oops! Sorry I wasn't more specific... Try ```
cat /etc/network/interfaces
```

---

### Post by Radissthor on 2009-10-12
Ok, many thanks for the specification.

It says:

auto lo 
iface lo inet loopback


auto dsl-provider 
iface  dsl-provider inet ppp
pre-up /sbin/ifconfig/eth1 up # line maintained by pppoeconf

auto eth1
iface eth1 inet manual

---

### Post by Iowan on 2009-10-12
Using **gksudo gedit /etc/network/interfaces**, edit the file to be:```
auto lo 
iface lo inet loopback


#auto dsl-provider 
#iface  dsl-provider inet ppp
#pre-up /sbin/ifconfig/eth1 up # line maintained by pppoeconf

#auto eth1
#iface eth1 inet manual
```Save it and reboot/restart. 
Personally I like **nano** - the command would be **sudo nano /etc/network/interfaces**.

---

### Post by Radissthor on 2009-10-12
> **Iowan said:**
>  
Personally I like **nano** - the command would be **sudo nano /etc/network/interfaces**.

Ok I didn't get the last part. I typed te first command and everything looked the same as you said it should, expet that I added the # sign and where it said 

/sbin/ifconfig eth1 up # line mantained by pppoe conf

Ichanged it to 

/sbin/ifconfig/eth1 up # line mantained by pppoe conf

But I don't know if those changes are meaningful. I will post my results Asap!

---

### Post by Radissthor on 2009-10-12
It worked!! Many Many thanks! It-s good to know one can always trust the Ubuntu Community. 
Thank you a lot having so much patience Iowan.

---

### Post by Iowan on 2009-10-12
> **Radissthor said:**
> Ok I didn't get the last part. **nano** is another editor you could have used. I like it because it has the shortcuts at the bottom of the page (my brain is full of useless information like my college bank account number and the square root of 514). Glad you got it working!

---

### Post by lrcaballero on 2009-10-12
You should left click on the Internet bar on your top right corner and see what it shows there?? and you should be able to see your internet connection, click on it and it should be done, you should be connected. If you plug-in directly you should have any problems, Ubuntu 9.04 by default recognizes either wired or wireless connections.

Good Luck (Linux Rocks!!!!!)

Luis:popcorn:

---

