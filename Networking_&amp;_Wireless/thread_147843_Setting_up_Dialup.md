---
title: "Setting up Dialup"
date: 2006-03-20
forum: Networking &amp; Wireless
---

### Post by KuTsuM on 2006-03-20
Hello all, thanks for taking a look at my thread :)

Before I begin, I would like to say I love Ubuntu so much already, and I just got the CD's today :) Second, I have looked through the forums and all links referring to dialup networking including the documentation on it. [DialupModemHowto]("http://wiki.ubuntu.com/DialupModemHowto"). Right now I'm on a seperate system that's windows XP, and I downloaded the file and transfered it on to a floppy disk, hoping it may work. I tried to put it on the linux system, but the disk isn't formatted for linux, so all I get is an error. So  I have two questions, either one can be answered.

 I'm trying to, of course, setup a dialup connection, but I don't know how. Obviously, dialup takes work to set up compared to ethernet. How can I do this?
a) I know about Linmodems and such. However, I need scanModem.gz to be transfered over to my linux system, how can I do this?
b) is there a way I can set up the dialup network without this?

Thanks a lot :)

---

### Post by red_shrike on 2006-03-21
Sure. That program tells you what modem do you have, and whether it is supported on your system or not. Trick is that kernel 2.6 has lower support for some modems than 2.4 It would be easier for us to help if you would tell us what modem do you have.

---

### Post by KuTsuM on 2006-03-21
Yes, but how do I get the program onto my other system when all I have other than that one is a Windows system?

---

### Post by KuTsuM on 2006-03-21
Ok, I used pppconfig and configured the connection, than when I typed 'pon' nothing happens. I took a look at the plog command and this is what I got:
> Mar 20 20:23:40 localhost pppd[6887]: Device ttS0 is locked by pid 6883
Mar 20 20:23:40 localhost pppd[6887]: failed
How can I fix this?

---

### Post by red_shrike on 2006-03-21
In general when you give output, give the whole thing. As far as I can see, it seems that even though you have configured ppp, system doesn't have any drivers to work with and deault ttS0 is taken by some other device. May I suggest you use gnome-ppp. [http://www.icmreza.co.yu/blogs/vladecks/?page_id=7](http://www.icmreza.co.yu/blogs/vladecks/?page_id=7)
scroll down and select 0.3.23 version. Sorry for this not being in english, but hey, its a great software so why not use it. If you get errors like, modem not detected it simply means you gonna have to find drivers for linux for this modem. It doesnt matter if you download it on XP or if modem scanning tool is on the floppy. Extract it on the linux desktop and read the README file. It explains it clearly. I remember using it once, and I didn't have to mess with floppy anyhow. Except that it told me thet I wont be able to run it on 2.6 kernel so now I am in process of porting my system on 2.4.

---

### Post by red_shrike on 2006-03-21
Wait, can you see your ntfs partition from linux?

---

### Post by KuTsuM on 2006-03-23
I'm not sure what you mean...

Anyways, when I try to move scanModem.gz across systems using a CD-R I get an error:
"Unable to mount the selected volume. Error: Given UDI is not a mountable volume" What is causing this error and how can I fix it?

Thanks for all the help so far, red_shrike

---

### Post by red_shrike on 2006-03-28
Sorry for not replying sooner, I had to read some ridiculus english homework stuff (Macbeth, Beowulf, Grendel,...). I hate literature. Anyway, check out [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) tuxfiles are excelent source for newbs. Your thing with cd rom seems to be a bug in Ubuntu. Try $ sudo umount /dev/hdc or $ sudo umount /dev/hdd If that works, than try mounting your drive again ($ sudo mount /dev/hdc (or hdd)) This seemd to work for other people. Iwas worried by the fact you have to use cd-r and floppies to transfer files across platforms. Read the link and than you should be able to see your win part of the disk. It might help if you told me what modem you have.

---

