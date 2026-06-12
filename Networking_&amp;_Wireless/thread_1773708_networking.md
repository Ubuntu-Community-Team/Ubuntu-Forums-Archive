---
title: "networking"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by msidhard on 2011-06-02
friends i have a desktop and laptop nw i want to connect both through ethernet and want to transfer the files to one another. i dont know how to do, please help

---

### Post by phil13 on 2011-06-02
Hi

I'm not sure about this answer - it's all from a quick google search. Have you tried searching for "transfer files over ethernet" or something similar? There's a lot of content out there already.

Is it an ethernet crossover cable or just a normal ethernet cable? If it's the latter then it's not possible to transfer files directly - you'll need to connect both the computers to the same router/hub first.

---

### Post by pqwoerituytrueiwoq on 2011-06-02
i would use the [FONT=Courier New]scp[/FONT] command 
to receive files you will need [FONT=Courier New]openssh-server[/FONT] installed
with the proper ports forwarded you can use this between 2 computers on the other side of the planet (with Internet connection)
to copy from my laptop to my desktop at home i would do this
[FONT=Courier New]scp ~/Desktop/filesToSend/* me@10.0.0.50:/home/me/Desktop/Files2ReciveFolder[/FONT]


if you have some files you want to sync you can use ubuntuone it is a online backup/file sync

---

### Post by msidhard on 2011-06-02
thanks for ur reply but i tried and got tired and at last am here

---

### Post by msidhard on 2011-06-02
friends first i want to know whether both are connected and futher steps thereafter  step by step

---

### Post by dozycat on 2011-06-02
If you are in the same network why not setup samba.

---

### Post by msidhard on 2011-06-02
friends i am newbie just  i have a ethernet cable, a desktop,and laptop only nothing else help me

---

### Post by Miljet on 2011-06-02
I use NFS (Network File System) for that. This is a link to the best guide I have found.

[http://mostlylinux.wordpress.com/network/nfshowto/](http://mostlylinux.wordpress.com/network/nfshowto/)

---

### Post by dozycat on 2011-06-02
what operational systems do you have?
what is your network? a switch? a crossover cable?

---

### Post by dozycat on 2011-06-02
Try this:

[http://www.unixmen.com/linux-distributions/4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-]("http://www.unixmen.com/linux-distributions/4-ubuntu/1203-how-to-install-and-configure-samba-in-ubuntu-1010-maverick-meerkat-via-gui-")

Usually I don't do it, I use an usb or I have a windows machine and connect from ubuntu to windows to the share is very easy.

---

### Post by uRock on 2011-06-02
Moved to *Networking & Wireless*

---

### Post by spiky001 on 2011-06-02
msidhard I think you better describe what you have tried and succeeded at have you got the 2 machines connected together

---

### Post by msidhard on 2011-06-03
Friends am running ubuntu on both systems 10.04 and natty respectively. I have the cable which is used to connect system and adsl modem. I just connected both systems on the either ends of the cable through Ethernet port.

---

### Post by msidhard on 2011-06-04
friends at last  found something.
1. i connected both systems through ethernet port
2. i used " sudo ifconfig eth0 192.168.1.2" and "sudo ifconfig eth0 192.168.1.3" on system respectively
3. then i used "ping 192.168.1.2" and found both the systems are connected.
4. i can connect to other system by using place->conncet to server option and could see the shared drives but could not open it. it says "unable to mount windows share"
5. and also i saw "server's shared files" icon in the desktop of the client computer and i opened it. when i tried to copy files to the shared files folder the connection disconnected.
6. now i want to move 60GB of files from my laptop to my desktop. i am using desktop as server and laptop as client. both systems are running ubuntu 11.04 and 10.04 respectively.

---

