---
title: "cant access internet"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by unclejack3 on 2009-03-07
I am running ubuntu 8.1 from cd,using a e220 wireless modem which is recognized and can connect to optus 3g network (very slow)but firefox cannot browze anything.I downloaded opera with xp,booted ubuntu to complete  the opera install but once again it could not download the remaining install files needed by opera,so it seems to be a ubuntu issue rather than firefox,I think.All I basically want is a linux system on my pc to browse the web without having virus etc software running,if another linux operating system works  with my dual boot pc then thats fine but i know nothing about linux ,I just want something to work. any suggestions would be appreciated.

---

### Post by jamesr on 2009-03-08
Hi,

Two comments,
how did you determine the spped of access, you said very slow.
If you are running from a CD, how did you change to opera?

You mentioned dual boot  but you also said "running from a CD". More information and/or clarifaction would be helpful

---

### Post by lindsay7 on 2009-03-08
dito that,

I can not really tell what you have going form you discription?,

I all you want is a Linux distro to web surf and email, you should look at Linux Puppy. Put in on a usb drive and you can start it and use it anywhere. It uses very little space, I have it on a 256meg usb drive. You can write to the drive so in you need more space for storage just put it on a bigger usb stick.

---

### Post by unclejack3 on 2009-03-10
ok lets make it clearer...I have xp on c drive running firefox and I.E using a huawei e220 ,optus 3g connections .
If i want ububtu I reboot using the cd drive and the linux cd . I select "use ubuntu without changing anything ",,,it boots ,loads ubuntu ,recognises the modem and connects to optus 3g.
I then open firefox and try to call up a website,,,have tried many even the ones in the drop down list,,and it tries to look for them,,after 1 min it  returns a "address not found".thats it...
I know the speed of the connection is very slow i.e  1 kbs,,sometimes 40 bytes...and sometimes it whizzes to 25kb but thats with xp where i use the modem program to see this info,,although I can see this speed using ubuntus system monitor and its below 1 kb...as for opera I downloaded it using xp but I  install it  useing ubuntu as xp does not recognise  the files and I want to intall it for ubuntu not xp. I hope that clarifies things...I will however try puppy,hope it recognises the modem.

---

### Post by jamesr on 2009-03-10
Hi,

Are you happy using the CLI ie the command line interface, because it would be easier to see what is going on when using CLI.

In a terminal widow type ```
sudo ifconfig -a
```

---

### Post by unclejack3 on 2009-03-12
hi thanks for your reply but before i go with ubuntu lets see if puppy is easier. i am running puppy but it does not seem to recognise mu usb huawei e 220 modem,,now i believe i need the driver but it seeems so complicated to install it..you need to be a linux programmer  .is there a simple package i can download that will just see my modem and work..

I will try he sudo thing but what are you expecting back?

okay here is the result 

ubuntu@ubuntu:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:17:31:12:28:26  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x8400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:648 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:40448 (40.4 KB)  TX bytes:40448 (40.4 KB)

pan0      Link encap:Ethernet  HWaddr b6:d2:21:dd:87:0b  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

ubuntu@ubuntu:~$

---

