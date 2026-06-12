---
title: "Networking problem with Asus P5LD2"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by bayger on 2006-06-08
Hello, I have very strange problem with networking under my fresh installation of ubuntu 6.06. After some time of working, for example while listening to the internet radio (di.fm), my network connection is somehow broken. I have access only to a few pages and my music stream is not working anymore. Only google works and a few other websites. Moreover, icmp traffic is okay, because pings are working okay. It seems like some (but not all) incoming http packets were ignored by the system. Does anyone have solution to this problem? As I wrote in the title I have Asus P5LD2 motherboard with 1GB of RAM, SATA barracuda 160GB disk and GF7800GTX (nvidia-glx installed). My router is Linksys WRT54G, but it seems that it doesn't  matter, because connection under Windows just works. I know that there are/were some problems with sky2 kernel module, but I don't know how to solve them. Message log doesn't have any entries related to this problem. Does anyone have similar problems with networking?

---

### Post by Ivan Matveich on 2006-06-08
What a strange bug. All I can say is

(a) install another ethernet card
(b) run tcpdump to analyze your traffic
(c) find out what triggers the bug: all large downloads? certain ports? etc

---

### Post by bayger on 2006-06-08
First of all, big thanks for this lightnin-fast answer. :) I will investigate net traffic with tcpdump, maybe I will install i386 version of the ubuntu (instead of amd64 which I already have installed) or just use LiveCD version for some time (it is possible that I made some changes to the system so networking is broken). As I wrote earlier this happens when listening to the di.fm radio, but I think it is rather non-deterministic bug.

And one more thing. Maybe this is only a coincidence but all this started when my ISP changed my public IP to something like 85.x.x.x from 65.x.x.x. It doesn't make sense to me, but maybe it's somehow related to the problem (I doubt).

Anyway, if somebody has any other ideas please reply. :)

---

### Post by bayger on 2006-06-08
I've done some investigation with tcpdump and here is a fragment of a dump:

```

13:04:35.908145 IP 192.168.1.99.36219 > 160.79.128.22.7090: . ack 8630255 win 1204 <nop,nop,timestamp 3116743 1682952837>
13:04:36.032421 IP 160.79.128.22.7090 > 192.168.1.99.36219: . 8630255:8631703(1448) ack 227 win 49232 <nop,nop,timestamp 1682952939 3116743>
13:04:36.032442 IP 192.168.1.99.36219 > 160.79.128.22.7090: . ack 8631703 win 874 <nop,nop,timestamp 3116867 1682952939>
13:04:36.032849 IP 160.79.128.22.7090 > 192.168.1.99.36219: . 8631703:8633151(1448) ack 227 win 49232 <nop,nop,timestamp 1682952939 3116743>
13:04:36.041402 IP 160.79.128.22.7090 > 192.168.1.99.36219: . 8633151:8634599(1448) ack 227 win 49232 <nop,nop,timestamp 1682952939 3116743>
13:04:36.095648 IP 192.168.1.99.36219 > 160.79.128.22.7090: . ack 8634599 win 150 <nop,nop,timestamp 3116930 1682952939>
13:04:36.418096 IP 192.168.1.99.36219 > 160.79.128.22.7090: . ack 8634599 win 1534 <nop,nop,timestamp 3117253 1682952939>
13:04:36.716724 802.1d config 8000.00:12:17:de:34:fa.8001 root 8000.00:12:17:de:34:fa pathcost 0 age 0 max 20 hello 2 fdelay 0 
13:04:37.905050 IP 192.168.1.99.36219 > 160.79.128.22.7090: . ack 8634599 win 3514 <nop,nop,timestamp 3118740 1682952939>
13:04:37.946569 arp who-has 192.168.1.99 tell 192.168.1.1
13:04:37.946582 arp reply 192.168.1.99 is-at 00:13:d4:c3:97:88 (oui Unknown)
13:04:38.716696 802.1d config 8000.00:12:17:de:34:fa.8001 root 8000.00:12:17:de:34:fa pathcost 0 age 0 max 20 hello 2 fdelay 0 
13:04:39.993985 IP 192.168.1.99.36219 > 160.79.128.22.7090: . ack 8634599 win 7144 <nop,nop,timestamp 3120829 1682952939>
13:04:40.716598 802.1d config 8000.00:12:17:de:34:fa.8001 root 8000.00:12:17:de:34:fa pathcost 0 age 0 max 20 hello 2 fdelay 0 
13:04:42.716557 802.1d config 8000.00:12:17:de:34:fa.8001 root 8000.00:12:17:de:34:fa pathcost 0 age 0 max 20 hello 2 fdelay 0 
13:04:44.716459 802.1d config 8000.00:12:17:de:34:fa.8001 root 8000.00:12:17:de:34:fa pathcost 0 age 0 max 20 hello 2 fdelay 0 
13:04:46.716416 802.1d config 8000.00:12:17:de:34:fa.8001 root 8000.00:12:17:de:34:fa pathcost 0 age 0 max 20 hello 2 fdelay 0 

```

This is communication dump with di.fm while streaming. I was listening to the station and suddenly stream stoped incoming. I don't see anything interresting in this dump. Because I am definitely not an expert in linux, could you tell me what tools should I use to get to know what is going on. My connection is again usable when I deactivate and activate eth0, so maybe this info will help somehow.

And some detailed info about my hardware by lspci:
```

0000:00:00.0 Host bridge: Intel Corporation 945G/P Memory Controller Hub (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 945G/P PCI Express Graphics Port (rev 02)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
0000:00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
0000:02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 Gigabit Ethernet Controller (rev 19)
0000:04:00.0 VGA compatible controller: nVidia Corporation GeForce 7800 GTX (rev a1)

```

Unfortunately I don't have other ethernet card to test connection. Okay, that's all from me right now. :-k

---

### Post by bayger on 2006-06-08
Everything is working fine as I'm writing this words. What did I do? I removed the "Network Monitor" applet from gnome panel. It seems that this little monitoring tool sometimes breaks connection. I am not completly sure that it's true, maybe it is another coincidence. Anyway, I just wanted to let you know how I solved the problem.

---

### Post by bayger on 2006-06-09
Arghh! Another network crash, after one day of proper working. How to diagnose this problem? Please help.

---

### Post by dvarsam on 2006-06-09
Dear "bayger",

I happen to own the _same_ Mobo like you (Asus P5LD2)!

Can you please tell me step-by-step what your are doing so that I simulate it on my P5LD2 Mobo to (hopefully) help you?

Thanks.

P.S.1> Please send a step-by-step procedure, cause I have NO clue about what you are doing...

P.S.2> You are lucky you got an ASUS P5LD2 Mobo!!!
(and NOT an ASUS P5LD2-_VM_, cause the later was awful - it did NOT recognize the LAN & it took me 2 weeks to find out a way to make its LAN work in Ubuntu... - if you want to see with your own eyes, visit: [http://ubuntuforums.org/showthread.php?t=154532](http://ubuntuforums.org/showthread.php?t=154532)
In the end, even though I finally managed to make the P5LD2-VM work, I decided to replace it with the P5LD2 - I hated installing LAN drivers every time I had to format... & best of all, the P5LD2 recognized the LAN with no additional driver installs...). Anyway, that was a long story...

---

### Post by bayger on 2006-06-09
Hello dvarsam,

My problem is completly non-deterministic and it seems that only I have such problems with networking. There is no step-by-step procedure to reproduce this network problem. It just sometimes happens without any specific reason. I listen to the di.fm almost all the time, so I know when my connection is broken - no music from my speaker. :( Today I was working under winxp and connection stopped working also (but also google.com didn't respond). However, it repeaired itself after a minute. I'll try ubuntu with another NIC (PCI 3COM) which I've just ordered. Maybe it will help. Anyway, thank you very much for you effort in solving my problem, I really appreciate that. And yes, Asus P5LD2 is really great mobo. It just works with ubuntu "out of the box". Regards.

---

### Post by dvarsam on 2006-06-09
Dear "bayger",

> My problem is completly non-deterministic and it seems that only I have such problems with networking. There is no step-by-step procedure to reproduce this network problem. It just sometimes happens without any specific reason.

Ok, I see!

> I listen to the di.fm almost all the time, so I know when my connection is broken - no music from my speaker. :( Today I was working under winxp & connection stopped working also (but also google.com didn't respond).
However, it repeaired itself after a minute.

Ok, listen to my story:

I have the same problem (in a way) & if I am right, it has nothing to do with what Computer you are Connecting...
When I am surfing on the Net, sometimes (even when I surf at this Forum), i click on a "link" & that link does _NOT_ load!!!
My mouse cursor turns into this "wait" icon (in Ubuntu it is a turning Cd-disk"), but NO web page is actually loaded...
This procedure might last (in my case), for 5-10 seconds!!!
So, I am left with the impression that I am "out of connection"!!!

However, In my opinion, that has to do with the DSL Internet Service Provider (ISP) you are using...

Either their lines seem to "overload" with traffic (which the ISP can't handle), or something else is happening, which I can NOT describe (cause I am NOT a hardware expert NOR a ADSL Technician)...

In my case, this "signal delay" seems to last 5-10 seconds (the most), but it happens many times throughout a day!!!

IF your case seems the same like mine, I assume that your experience is worse compared to mine, cause your delay is longer...!!!

I would suggest that you Call/Talk/Speak to your ISP & complain about this problem. Maybe you are NOT located in a "big" City Center, and in the Countryside this gets worse... (I don't know...)

> I'll try ubuntu with another NIC (PCI 3COM) which I've just ordered. Maybe it will help.

I think it has to do with your ISP connection (either their PCs have problems or their line/connection wires coming from their Center to your home has problem)...

But again, I am NO expert...

> Anyway, thank you very much for you effort in solving my problem, I really appreciate that.

You are welcome!

> And yes, Asus P5LD2 (without an onboard Graphics Card) is really great mobo. It just works with ubuntu "out of the box".

YES, it is _true_, I can _confirm_ too!

However, the _opposite_ occurs with the Mobo ASUS P5LD2-VM (_with_ onboard graphics card)!!!

It _totally_ sucks!!!

Take care!

P.S.> If worse comes to worse, try to change your ISP to a diff one. You never know, maybe things are going to get better for you (make sure they use diff wiring lines to connect from their Center to your Home)!

---

### Post by bayger on 2006-06-10
First of all, thanks for the answer. Probably you are right that my problem is ISP specific. My ISP recently made some infrastructure changes. I hope it will stabilize soon. Interestingly my connection again works perfect, so maybe my problems are gone. We will see. Anyway, I could change my ISP but my current ISP doesn't limit my transfer to something like 20GB/month and alternative one does that. I don't want limits. Besides other machines in my home network work perfect with my ISP (yes, windows machines). 

Take care! :D

---

### Post by kozimodo on 2006-06-11
I have the same problem as well.  I believe it has something to do with the current kernel (linux-image-2.6.15-23-386).  I have exactly the same problem with my new AOpen EZ482 which also has the same ethernet device.  But when I boot up under the linux-image-2.6.15-22-386 the problem disappears.  Try downloading and installing the beta-release.

BTW, I filed a bug report for this ([https://launchpad.net/bugs/45800](https://launchpad.net/bugs/45800)) but so far it seems to have been ignored -- you might want to add your own comment.

---

### Post by bayger on 2006-06-14
Hi Kazimodo,

Do you use network monitoring tools? I think all network hangs are caused by Network Monitor applet or System Monitor (which has network monitoring graph on Resource tab). Do you think it is possible? I have strong feeling that it is somehow related.

---

### Post by hvidgaard on 2006-06-14
I have had (having actually) this problem too. To me it seems as beeing an software bug since changing to an static IP and then back to DHCP will make it come back online.

I know for sure that the internet gateway is working (both of them on 2 seperate lines, one DLS 20/20mbit and DSL 4/0,7mbit) when the internet disapperes (checked from 2 other machines on the LAN).

But come to think of it, I remember to have the exact same problem under windows xp, but here the entire functionallity disapeared (ie. no ping even on LAN) and the only solution was to change the MAC address to something new (or to reboot)

Under ubuntu I'm experiencing the same symtoms as you are, and seems somehow related to the "System Monitor". But it happen "out-of-the-blue" so to say too and I can't say that anything triggered it :(

I am very sure this has nothing to do with your ISP.

---

### Post by hvidgaard on 2006-06-14
Ohh, Iforgot to add my hardware:

Asus P5LD2
PentiumD 920
2x1gb kingston pc4200
Hitachi 160gb sata
running Ubuntu "Dapper Drake"

---

### Post by kozimodo on 2006-06-20
[QUOTE=bayger]Hi Kazimodo,

Do you use network monitoring tools? I think all network hangs are caused by Network Monitor applet or System Monitor (which has network monitoring graph on Resource tab). Do you think it is possible? I have strong feeling that it is somehow related.[/QUOTE]
I do use the network monitor applet but that doesn't seem to have any affect as when I use the older kernel, I have no network problems.  The problem seems to have been fixed (so far so good) with the newest kernel image.  Have you tried it yet?

---

### Post by kozimodo on 2006-06-21
Nope. linux-image-2.6.15-25-k7 doesn't fix the problem either.  Back to linux-image-2.6.15-22-k7.

---

### Post by kozimodo on 2006-06-21
Well, lost ethernet with linux-image-2.6.15-22-k7 also today.  I did some looking around and apparently, the problem is with the Marvell module, sky2.  I have compiled an alternative but supposedly inferior (seems quite large) module called sk98lin which is downloadable from marvell.com.  So far it seems to be working fine and under heavy load.

There is a [HOWTO]("http://ubuntuforums.org/showthread.php?t=176096&highlight=sk98lin") for installing it but it seems more complicated than necessary to me so here is a simplified version of the installation procedure that I used.[LIST=1]
[*]Make sure you have build-essential and the kernel headers installed
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```
[*]Create a simlink to the kernel headers. E.g.,
```
sudo ln -s /usr/src/linux-headers-$(uname -r) /usr/src/linux
```
[*]Download the driver from Marvell's website.  There are currently two versions -- 8.32.2.3 and 8.40.2.3.  The latter says something about "bonding only" but I used it and it seems to work.
[*]Disable your adapter (System/Administration/Networking) and unload the sky2 driver
```
sudo modprobe -r sky2
```
[*]Unpack the driver, cd to the unpacked directory and install the driver:
```
tar xjvf install-8_32.tar.bz2
cd DriverInstall
sudo ./install.sh
```
[*]Make sure sky2 doesn't get loaded in the future
```
sudo gedit /etc/modprobe.d/blacklist
```
and add
```
blacklist sky2
``` to the file. Save and close.
[/LIST]

---

### Post by trasila on 2006-08-25
Hi, I had this same problem when I was installing Ubuntu 6.06 to my friend. I caused even the installer to fail when it tried to configure apt. After I turned MTU of the network interface to 1300 it has been working fine. So in order to do this you can open terminal and type "sudo ifconfig eth0 mtu 1300" assuming your network interface is eth0. in order to keep this setting you have to edit the settings in file: /etc/network/interfaces and add line saying "pre-up /sbin/ifconfig eth0 mtu 1300"

I don't know what the actual problem is and it is not the MTU but anyway, this could be used as a quick fix.

---

### Post by Dr. Dweebis on 2006-09-23
Hi Bayger -
I have assmebled a machine with a P5LD2 and I've had a lot of trouble getting it set up - in fact it is not set up.  Can you tell me you configuration so that I might emmulate it?  My setup is:
P5LD2
Pentium 840D
2GB Kingston PC 5300 DDR2 RAM
eVGA GeForce 7600 GT KO
Firewire 1x PCI
and I've tried:
320gb Western Digital SATA drive
160Gb Seagate Barracuda (Ultra ATA)

The SATA didn't work, and the ultra ATA worked for abit in series with the DVD out of the blue IDE controller.

Any insight?

Thanks -

Dr. Dweebis


> **bayger said:**
> Hello dvarsam,

My problem is completly non-deterministic and it seems that only I have such problems with networking. There is no step-by-step procedure to reproduce this network problem. It just sometimes happens without any specific reason. I listen to the di.fm almost all the time, so I know when my connection is broken - no music from my speaker. :( Today I was working under winxp and connection stopped working also (but also google.com didn't respond). However, it repeaired itself after a minute. I'll try ubuntu with another NIC (PCI 3COM) which I've just ordered. Maybe it will help. Anyway, thank you very much for you effort in solving my problem, I really appreciate that. And yes, Asus P5LD2 is really great mobo. It just works with ubuntu "out of the box". Regards.

---

### Post by Dr. Dweebis on 2006-09-23
Hi Dvarsam - 
I have assmebled a machine with a P5LD2 and I've had a lot of trouble getting it set up - in fact it is not set up.  Can you tell me you configuration so that I might emmulate it?  My setup is:
P5LD2
Pentium 840D
2GB Kingston PC 5300 DDR2 RAM
eVGA GeForce 7600 GT KO
Firewire 1x PCI
and I've tried:
320gb Western Digital SATA drive
160Gb Seagate Barracuda (Ultra ATA)

The SATA didn't work, and the ultra ATA worked for abit in series with the DVD out of the blue IDE controller.

Any insight?

Thanks,

Dr. Dweebis
> **dvarsam said:**
> Dear "bayger",

I happen to own the _same_ Mobo like you (Asus P5LD2)!

Can you please tell me step-by-step what your are doing so that I simulate it on my P5LD2 Mobo to (hopefully) help you?

Thanks.

P.S.1> Please send a step-by-step procedure, cause I have NO clue about what you are doing...

P.S.2> You are lucky you got an ASUS P5LD2 Mobo!!!
(and NOT an ASUS P5LD2-_VM_, cause the later was awful - it did NOT recognize the LAN & it took me 2 weeks to find out a way to make its LAN work in Ubuntu... - if you want to see with your own eyes, visit: [http://ubuntuforums.org/showthread.php?t=154532](http://ubuntuforums.org/showthread.php?t=154532)
In the end, even though I finally managed to make the P5LD2-VM work, I decided to replace it with the P5LD2 - I hated installing LAN drivers every time I had to format... & best of all, the P5LD2 recognized the LAN with no additional driver installs...). Anyway, that was a long story...

---

