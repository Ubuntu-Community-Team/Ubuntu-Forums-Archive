---
title: "Need help installing wireless card!!!"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by jeb800e on 2009-08-10
I am very new to Linux and the Ubuntu system, and I need some major help installing my Belkin Wireless-G Desktop Card F5D7000 (ver. 7000) using MadWifi v0.9.4 . I can't seem to even get past the beginning, earliest step in the installation! Can someone please guide me through it?! I am running Ubuntu 7.10, installed right off of a requested disk from Canonical.

Please help me! Thanks.

---

### Post by The Toxic Mite on 2009-08-10
Hey! Don't worry! :)

Go to Applications > Accessories > Terminal and enter the following commands:

```

sudo lshw -c network
iwconfig
ifconfig

```

Post the outputs of them when you're done

Thanks :D

---

### Post by MadHatter21 on 2009-08-10
For one thing i think you should try to get up and running on a newer version of ubuntu, 9.04 perhaps? [Ubuntu 9.04]("http://www.ubuntu.com/getubuntu/download"). Now maybe you have a really old card, and madwifi works on it, but im pretty sure that you need ath5k or ath9k driver on your distro, Give us the results of the commands above and i will help you further.


MadHatter21

---

### Post by yuvrajsp on 2009-08-10
Do you have the .INF file for the driver of your wireless card? If not google the driver & then try to install it from Application -> Add/Remove Progs -> System Tools -> Check Windows wireless drivers & you are good to go..

---

### Post by jeb800e on 2009-08-10
> **The Toxic Mite said:**
> Hey! Don't worry! :)

Go to Applications > Accessories > Terminal and enter the following commands:

```

sudo lshw -c network
iwconfig
ifconfig

```Post the outputs of them when you're done

Thanks :D

Do I have to have MadWifi installed to do this?? If so, how do I install it? I can't even understand how to install MadWifi! :(

---

### Post by jeb800e on 2009-08-10
> **MadHatter21 said:**
> For one thing i think you should try to get up and running on a newer version of ubuntu, 9.04 perhaps? [Ubuntu 9.04]("http://www.ubuntu.com/getubuntu/download"). Now maybe you have a really old card, and madwifi works on it, but im pretty sure that you need ath5k or ath9k driver on your distro, Give us the results of the commands above and i will help you further.


MadHatter21

Ubuntu 9.04 won't run on my computer. I've tried it numerous times. Once I figure everything out, I will probably upgrade to 8.04 LTS.

---

### Post by The Toxic Mite on 2009-08-10
> **jeb800e said:**
> Do I have to have MadWifi installed to do this?? If so, how do I install it? I can't even understand how to install MadWifi! :(

You don't need to have madwifi on your computer to do those commands.

---

### Post by jeb800e on 2009-08-10
Umm... is this method legal, The Toxic Mite? lol

---

### Post by jeb800e on 2009-08-10
This is what I got in the Terminal:

Code:

>  	 	 [SIZE=2]jeb@Ubuntu-Linux:~$ sudo lshw -c network[/SIZE]
 [SIZE=2][sudo] password for jeb:[/SIZE]
 [SIZE=2]Hardware Lister (lshw) - B.02.10[/SIZE]
 [SIZE=2]usage: lshw [-format] [-options ...][/SIZE]
        [SIZE=2]lshw -version[/SIZE]
 

         [SIZE=2]-version        print program version (B.02.10)[/SIZE]
 

 [SIZE=2]format can be[/SIZE]
         [SIZE=2]-html           output hardware tree as HTML[/SIZE]
         [SIZE=2]-xml            output hardware tree as XML[/SIZE]
         [SIZE=2]-short          output hardware paths[/SIZE]
         [SIZE=2]-businfo        output bus information[/SIZE]
 

 [SIZE=2]options can be[/SIZE]
         [SIZE=2]-class CLASS    only show a certain class of hardware[/SIZE]
         [SIZE=2]-C CLASS        same as '-class CLASS'[/SIZE]
         [SIZE=2]-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )[/SIZE]
         [SIZE=2]-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )[/SIZE]
         [SIZE=2]-quiet          don't display status[/SIZE]
 

 [SIZE=2]jeb@Ubuntu-Linux:~$ iwconfigiwconfig[/SIZE]
 [SIZE=2]bash: iwconfigiwconfig: command not found[/SIZE]
 [SIZE=2]jeb@Ubuntu-Linux:~$ iwconfig[/SIZE]
 [SIZE=2]lo        no wireless extensions.[/SIZE]
 

 [SIZE=2]eth0      no wireless extensions.[/SIZE]
 

 [SIZE=2]jeb@Ubuntu-Linux:~$ ifconfig[/SIZE]
 [SIZE=2]eth0      Link encap:Ethernet  HWaddr 00:01:80:5F:75:50  [/SIZE] 
           [SIZE=2]UP BROADCAST MULTICAST  MTU:1500  Metric:1[/SIZE]
           [SIZE=2]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/SIZE]
           [SIZE=2]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/SIZE]
           [SIZE=2]collisions:0 txqueuelen:1000 [/SIZE] 
           [SIZE=2]RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/SIZE]
           [SIZE=2]Base address:0xb000 Memory:f8100000-f8120000 [/SIZE] 
 

 [SIZE=2]lo        Link encap:Local Loopback  [/SIZE] 
           [SIZE=2]inet addr:127.0.0.1  Mask:255.0.0.0[/SIZE]
           [SIZE=2]UP LOOPBACK RUNNING  MTU:16436  Metric:1[/SIZE]
           [SIZE=2]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/SIZE]
           [SIZE=2]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/SIZE]
           [SIZE=2]collisions:0 txqueuelen:0 [/SIZE] 
           [SIZE=2]RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/SIZE]
 

 [SIZE=2]jeb@Ubuntu-Linux:~$ [/SIZE] 
 

---

### Post by The Toxic Mite on 2009-08-10
> **jeb800e said:**
> This is what I got in the Terminal:

Code:

You seriously need to upgrade Ubuntu.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

