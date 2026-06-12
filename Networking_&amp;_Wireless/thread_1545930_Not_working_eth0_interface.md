---
title: "Not working eth0 interface"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by Harker2010 on 2010-08-04
Hello everyone!,
I'm quite desperate for a problem with my lan connection. (I'm desperate because i've the necessity to do a big upload of data overnight and now i'm without connection from that machine)

I've this ubuntu box from 6 months now (ubuntu 9.10 in the beginning and the upgraded to 10.04) and i'm very proud of it, never had a problem before.
Yesterday after finished working i shut down the pc regularly, today when I turn it on again the LAN connection doesn't connect anymore! (I'ven't done any update yesterday, nothing changed) and this is the network manager I can see from this morning:


[IMG]http://img33.imageshack.us/img33/886/69322324.png[/IMG]

The PC connects to the internet through a router.

The strange thing is that neither the leds of the (integrated) network card blink, so i thought could be an HW probelm.
To be sure about it, I run a live ubunto distro and then during the boot the NIC leds went on and i could connect on internet regurlaly

I want to make clear first that during all the afternoon i've tried to look for a solution on google, forums etc... I've found problem that could be similar to mine (maybe not totally) and i've tried any suggested solution for those problems without results

I give you some elements that could be helpful to find a solution for my problem (I hope):


In the BIOS everything is ok, the LAN is enabled and i've also tried to turno on the WAKE ON LAN (I've found somewhere that this could help even if i was sceptic)

On the PC there's installed ubuntu only (so no Windows 7 or any other 'dangerous' OS)

Driver/modules seems to be installed correctly (I worked fine till yesterday!!) as you can see in the lpsci command here:

```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated 
Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition 
Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 
(rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 
(rev 01)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 
(rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 
(rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller 
#1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI 
Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI 
Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI 
Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI 
Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller 
(rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B 
PCI Express Gigabit Ethernet controller (rev 03)
```this is my /etc/network/interfaces 
```

auto lo
iface lo inet loopback
```ifconfig -a command:
```
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:1094 (1.0 KB)  Byte TX:1094 (1.0 KB)

vboxnet0  Link encap:Ethernet  HWaddr  XX:XX:XX:XX:XX:XX 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)
```ifdown & ifup commands:
```
ifdown eth0
ifdown: interface eth0 not configured


ifup eth0
Ignoring unknown interface eth0=eth0.
```I really don't know what to do... formatting the pc right know would be a disaster for me... i need to be back operative as soon as possible! I'm desperate! Till yesterday it worked wonderful! I haven't done any change on LAN or else, just worked with OpenOffice and GIMP! :(

Thanks for any help you could give me!

Regards

---

### Post by Harker2010 on 2010-08-04
P.S: just noticed now, i've added the tag [lubuntu] in the title... it  is [ubuntu].. how can i change it?

---

### Post by Iowan on 2010-08-04
> **Harker2010 said:**
> P.S: just noticed now, i've added the tag [lubuntu] in the title... it  is [ubuntu].. how can i change it?

I didn't notice the [lubuntu] tag, but I added [ubuntu] for you.

[Here ]("http://ubuntuforums.org/showthread.php?t=1505217") is something to try to see if it helps with NM.

---

### Post by Jonathan A Smith on 2010-08-04
Hi, I had this exact same problem.
I reinstalled drivers, configured it manually, did all sorts of stuff.
I fought with it all night last night and eventually used the nuclear option. (Backup my stuff and reinstall... it didn't work!)

I finally found the answer to the problem here:

[http://www.question-defense.com/2010/06/03/ubuntu-10-4-eth0-not-available-rtl-81398139c8139c-rev-10]("http://www.question-defense.com/2010/06/03/ubuntu-10-4-eth0-not-available-rtl-81398139c8139c-rev-10")

Pretty much, all that you have to do is use mii-tool to set the networking speed.

Hope this helps,

-Jon

---

### Post by Harker2010 on 2010-08-05
Thanks Iwoan and Jonathan.
(Iwoan, for the tag issue I've tried to mess a bit around on command of the board, then i've marked it as solved, and the unmarked again and the [lubuntu] tag disappearead, now thanks to you is corrected)

Last night surfing on the web and help by another user i was able to put back the interface one using the command:

sudo mii-tool --reset

and as i soon as i launched this command the eth0 went back online working greatly, but it wasn't a permanent fix, since the next reboot the lan was down again, and launching again the command was able to go back online.


In any case after i was finally able to upload and download and i left my pc for working all the night the stuff for my job, i shut it down regularly, turned off the main switch that shuts down also the gigabit switch and the router.
When i turned on the pc 10 minutes ago, it started working again like nothing as happened!

Yesterday i did ton of tries rebooting with lan cable plugged and unplugged but it was impossible to make it work... now after having shut down everything, it works regularly... could have been the router or the switch even if my notebook (which i used to to open this thread) worked fine and my xbox too?

I'll keep in mind what you have suggested as solution, Johnatan, in case the episode will repeat again.


The only strange thing is that today the automatic updates of ubuntu suggested me as updated the kernel 2.6.32-24 and using the command:
uname-r
i see as my kernel 2.6.32-24 .. is it normal? should i do the suggested update?



Thanks for the help!

---

### Post by polver on 2010-08-13
Hello to everyone:

I'm having the same [Harker2010]("http://ubuntuforums.org/member.php?u=1124221")'s problem working 10.04 LTS on a Dell latitude 820. Worked OK, lan and wifi until last update.
If tried everything on this page but still not working.
Maybe could be a modules problem?

Thank you all

---

