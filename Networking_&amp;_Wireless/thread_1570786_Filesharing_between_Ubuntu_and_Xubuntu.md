---
title: "Filesharing between Ubuntu and Xubuntu"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by m138 on 2010-09-08
Would someone please help me? I am very new to linux but i've jumped in with both feet so to speak.
I want to enable file sharing between two computers in my home, preferably through some graphical file manager. I have one PC running ubuntu latest release and another with lesser resources running xubuntu. Both computers are  wired to this soho watchguard red box, there is also a wireless access point connected to that watchguard, but I don't really care about that right now. Both computers were able to connect to the internet the moment they were installed without changing any thing. honestly i dont know which pc is which (which is eth0,eth1 and lo). I'm guessing someone will ask what ifconfig shows:

stephen@stephen-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:00:e8:e0:1e:54  
          inet6 addr: fe80::200:e8ff:fee0:1e54/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:8
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xe800 

eth1      Link encap:Ethernet  HWaddr 00:16:17:7a:34:d0  
          inet addr:192.168.227.3  Bcast:192.168.227.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe7a:34d0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93837 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119861 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:101592070 (101.5 MB)  TX bytes:14734735 (14.7 MB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:94878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:94878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10696724 (10.6 MB)  TX bytes:10696724 (10.6 MB)

Also please keep in mind that xubuntu is using the thunar file manager, which is  different than ubuntu, I'd like to keep it with the older box running xubuntu, but if installing ubuntu on both machines is the only way to go I'd do it.

---

### Post by elico on 2010-09-08
first you can use this
[https://help.ubuntu.com/10.04/internet/C/index.html](https://help.ubuntu.com/10.04/internet/C/index.html)

all the things that listed in your post are your network interfaces.
lo is loopback (the computer speaks to it self \different software talks with the other)
eth0
and eth1 are representing lan card 
do you have to NIC's in your machine?
there is one interface that is connected to a LAN segnent 
can you get internet on this machine?

you can use FTP or samba or nfs for file sharing between the machines.
Are you using any windows machine in the network?

---

### Post by m138 on 2010-09-08
I have 2 machines, both have nic's and both are connected and able to use the internet without a hitch.
as far as windows goes, the xubuntu machine boots with the option to run either xubuntu or xp pro sp3
the ubuntu machine has only that, i do have a license for xp home sp3 but i'm trying to avoid windows if at all possible. 

so lo is just a loopback..does that mean eth0 and eth1 are different machines?

I should try setting up samba on both devices?

---

