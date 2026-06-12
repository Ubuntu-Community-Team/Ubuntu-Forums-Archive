---
title: "Wifi won't connect"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by movrshakr on 2009-05-04
New install of 8.04 on HP laptop zv5220us...
I entered all the wireless setups (WPA2, AES, passphrase, SSID) but it will not see the network. No clue how to fix that. I am very conversant with networking, but zero knowledge about ubuntu vagaries and tools regarding it. 

I notice the light in the wireless button is not on.  Pressing the button does not turn it on.  Then I found this at
[https://help.ubuntu.com/8.10/internet/C/troubleshooting.html#troubleshooting-device](https://help.ubuntu.com/8.10/internet/C/troubleshooting.html#troubleshooting-device) 
"...some devices can be switched off from Windows and may need to be turned back on from Windows." 

Well, that's pretty great--there is no Windows on the laptop any more.  I switched over to ubuntu because I was fed up with Windows and because the restore disk for it fails.  Now am I relegated to a laptop with no wifi?

---

### Post by t0mppa on 2009-05-04
More likely you just have some driver issues. Getting the wireless led working might be a bit of a project, not sure if all drivers even support it. Personally, I haven't bothered with it, since I don't need to switch wireless on/off on my daily use, so it doesn't really make any difference.

Open up a terminal, run the following commands in it and post back with the output to get a better picture of what the issue is:```
ifconfig
lshw -C network
lspci
```

---

### Post by movrshakr on 2009-05-04
I will do that, but it is hard because that machine (obviously) has no internet, so cut and paste into a post is impossible. 

Maybe I can put it on a stick and move it to this Windows (ugh) machine--but at least it gets on the internet.  Stand by.

---

### Post by movrshakr on 2009-05-04
As requested...
```
user@hp-laptop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0f:b0:07:0e:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x7000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98592 (96.2 KB)  TX bytes:98592 (96.2 KB)

user@hp-laptop:~$ sudo lshw -C network

  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:07:0e:5f
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Wireless interface
       physicalA id: 1
       logical name: wlan0
       serial: 00:90:4b:5b:15:44
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

user@hp-laptop:~$ lspci

00:00.0 Host bridge: nVidia Corporation nForce3 Host Bridge (rev a4)
00:01.0 ISA bridge: nVidia Corporation nForce3 LPC Bridge (rev a6)
00:01.1 SMBus: nVidia Corporation nForce3 SMBus (rev a4)
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 Audio (rev a2)
00:06.1 Modem: nVidia Corporation nForce3 Audio (rev a2)
00:08.0 IDE interface: nVidia Corporation nForce3 IDE (rev a5)
00:0a.0 PCI bridge: nVidia Corporation nForce3 PCI Bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 AGP Bridge (rev a4)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
02:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
```

---

### Post by wabbalee on 2009-05-04
I have a broadcom wireless in my laptop and jaunty supports it almost out of the box, it just needs enabling. before this I ran hardy (8.04) and i used ndiswrapper with its ndisgtk front end and wicd for network management using the original windows driver. wicd removes ubuntu's network manager but that is ok. get the windows driver file which is most likely a file named bcmwl5.inf and use ndisgtk to install this file. then use wicd and tell it that wireless is ndiswrapper (not its default wext? not sure anymore what it has for default as in jaunty i have no need for this) it has always worked seemless for me.

---

### Post by movrshakr on 2009-05-05
Wow...

ndiswrapper
ndisgtk front end
wicd
windows driver file

I think that if I could just get the adapter "on" to transmit and receive, this thing would work.  Is there no way to get it to power up without all those hoops?

---

### Post by t0mppa on 2009-05-05
It isn't really all that troublesome. You don't even have to install WICD, if you get the wireless working without it. There are also lots of good tutorials on how to do all that, [Ubuntu Wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") for instance. And I bet you'll save a lot of time just trying it out, rather than keep searching for an alternative one-click solution.

---

### Post by movrshakr on 2009-05-05
The link in the previous post says 

"Before you install any wireless driver with ndiswrapper or ndisgtk, make sure there are no other drivers trying to use your wireless card. If there are, your ubuntu may freeze."

However, it does not say how to do that, which would be minorly (!) helpful.

---

### Post by movrshakr on 2009-05-05
As a related side question, does anyone know for sure that there is a Linux driver for the particular adapter mentioned in the command outputs previously posted--and the name/version?

description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation

---

### Post by movrshakr on 2009-05-05
"It isn't really all that troublesome???!!!"

ohmigosh, I've gotten into trying to go the ndswrapper route and keep running into pages that lead to other pages then to other pages.  Don't anybody try to tell me this is the simple route.

Apparently the Broadcom 43xx series are a major problem for ubuntu.  I am running into references to blacklist things, b43, b43-legacy, b43-fwcutter, cafuego distributions, things that don't work without proprietary firmware (unincluded), and on and on.

Here is but one of the MANY pages I have been reading...
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Hardy)

This appears to be a week long project with no guarantee of being successful at the end.  I don't want to fight with this;  I want to USE it.  I give up.  Most unimpressed with wifi and ubuntu.  I will order the $16 Windows recovery disk from HP and go back to Windows.

---

### Post by wabbalee on 2009-05-05
you want to go back to windows, well that is your choice. but I can assure you that i am no master at the command line and what I explained to you requires you to install those packages through your package manager (it will uninstall ubuntu's networkmanager automatically) and you can 'mouse' your way through. it is as easy as I explained. the reason why these things can give some trouble on Ubuntu is a legal issue and the fact that manufacturers do not supply linux drivers. people who give up easy will go back to using windows. these forums are here to help you. you need to find your own way in how you choose to do it. I have been using linux for about 5 years now and yes it has been hard at times but things have changed and gotten a lot easier. as t0mppa mentions, there is no one click solution, neither is there a one click solution in windows. why don't you just do what one of us suggests here (do your pick) and we will step you through. have you ever tried getting help from microsoft? they are not even half as friendly as we are, plus they want your $$$.

good luck.

---

### Post by wabbalee on 2009-05-05
I am not sure if your windows driver is the same as mine as I have:
Broadcom Corporation **BCM4318** [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
and you have:
BCM4306 
otherwise I would even email you my file, but you will need to hunt down your driver, preferably the one for XP. you'll have some fun getting that of the web unless you can find it on a cd that you may own.

---

### Post by t0mppa on 2009-05-06
Like wabbalee said, just take a moment to relax and post here on the forums, if you run into trouble along the way. The support online is what has most amazed me with Linux/Ubuntu after swapping from the Windows world, since people actually know what they're doing and really want to help. Personally, I've never set up a Broadcom card, so can't really help much further than point you to the right direction, but there are lots of others who have and will help, if you simply ask for it. It might take a while longer, since you have to wait for replies, but you won't run into all the dead ends, when following instructions that aren't clear.

---

### Post by movrshakr on 2009-05-06
Thanks, folks.  And I have calmed down a bit.  However, I was and am frustrated in that, while I don't mind doing the research, it became clear that it was not a matter of read, do...because the instructions often routed you from page to page (if...read _here_) and contained things like, for example, "get the Windows driver" (how, where?);  install it (how?); be sure to remove the xxx (how?).  

I guess the summary is that the instructions invariably were for someone way more knowledgeable in linux than I.  A day to make it work I can endure.  A week I cannot.

---

### Post by wabbalee on 2009-05-06
> **movrshakr said:**
> while I don't mind doing the research, it became clear that it was not a matter of read, do...

I have done heaps of research and I am giving that away in this thread,

> A day to make it work I can endure. A week I cannot.

...so that you can get it up and running quickly.

> for example, "get the Windows driver" (how, where?);

that's what I mean when I said earlier that you will have some fun with that one. finding that driver means you will have to get back into the mad world of windows, where you have to register with driversite such and such and you are constantly rerouted from here to there until you go nuts. The easier way is to get it of a working windows (xp) system with your particular Broadcom4306 card. In wxp device manager (right click 'my computer' -> 'properties' -> 'hardware' -> 'device manager' (from the top of my head, so...)) rightclick on the wireless card and choose properties and look for 'driver file details', it will give you the location of the file on the file system.

alternatively you can use windows' search tool and look for bcm*.inf (unless you know the exact name, you must use the '*' in the search)

> install it (how?);

that's easy, but first get the file and store it on a place where you can find it (even a usb stick or cd will do) once you have ndisgtk installed on your system it speaks for itself, really. one step at the time..

do you know what a package manager is? and if so, which one do you use?

> be sure to remove the xxx (how?)

not sure what you are getting at here, but removing the default network manager in Ubuntu happens automatically when you install WICD (which is in the 'universe' repository), providing you use the package manager of course.

do you know about repositories? and how to enable them?

as you can see it is all a matter of mutual communication here, and it would be handy if we could get an idea of your (and mine [IMG]http://ubuntuforums.org/images/smilies/confused.gif[/IMG]) level of expertise here, like I said earlier: i am no master at the command line but I can manage quiet well thanks to the hard work of those that write graphical front ends for us to click our way through this.

the package manager is so clever that should you want to install the front end called 'ndisgtk'(a front end is nothing without a back end), but you initially do not select ndiswrapper (the back end for this), the package manager will automatically suggest to install ndiswrapper. ndisgtk *depends* on ndiswrapper.

as you can see I have done a bit of writing here now, I woke up in the middle of the night (I am in Brisbane, Australia btw) switched on my laptop with working Broadcom wireless [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG], and checked my email and guess what? now I am here answering you and losing sleep, do you think a MS tech would even think of you at all?

if you want this fixed in a day then you better hurry, can't speak for others but I will be here throughout the day checking frequently (as I am doing all my other things around the place) and I will guide you as much as I can, the day after tomorrow (saturday) I am at work and unable to go online, same on sunday and monday.

it is all up to you.

---

### Post by movrshakr on 2009-05-06
wabbalee, that is very nice.  I may decide to tackle it, but there is a message in having to use the word "tackle."  That in itself describes it as a not insignificant *process* -- and that is what I was conveying.  If engaging in a significant process is up your alley, ubuntu is for you. Otherwise...???

Also, the things I cited were only intended as examples -similar- to what I was encountering, not precise questions for this specific situation.

package manager?  assume that is synaptic?  yes, it is installed by default.  A number of repositories are in its gathering realm.

I have done lots of things at command line, but none but the simplest commands are in my head.  Given ones to type, I can do that.

Lurking in my mind is a feeling that the HARDWARE has the wifi adapter powered off, so I seriously wonder whether software is going to be able to turn it on.

A missing question is whether there is a pure linux driver for this BCM4306 adapter.

---

### Post by t0mppa on 2009-05-06
> **movrshakr said:**
> A missing question is whether there is a pure linux driver for this BCM4306 adapter.

[Here's something]("http://www.ing.unibs.it/openfwwf/") I stumbled upon today, it claimed to support your chip as well. And a [tutorial]("http://bviktor.bplaced.net/?b43") for setting it up.

---

### Post by wabbalee on 2009-05-06
the method t0mppa recommends is pure open source (unlike mine which utilises the proprietary windows driver) and that should be the prefered method if you want your system to exist of open source free software only. so in that respect I would say there is a pure open source driver and it comes in this form.

you cannot have both on the same system, they bite eachother, so you will have to make a choice here.

I am using Jaunty now and on Jaunty my wireless works basically out of the box, after enabling the driver in 'hardware drivers'. You on the other hand use Hardy, which is excellent, but I was unable to get mine to work with Hardy this way so I decided to go with ndisgtk, ndiswrapper and wicd using the proprietary windows xp driver.

I understand your concern about the fact that you think your hardware was once turned off in windows, I have no answer to this other than to go ahead with one of the suggestions here. I know I can turn mine off and on when ever I want with the actual button on my laptop. A message appears that states the status. On my system I can use either the software method or the hardware method to turn it on/off. I prefer using the button as it is just quicker. I never actually tried that in Hardy with wicd so I don't know how it would work there.

and yes synaptic is a package manager, my favorite btw. I am using Kubuntu so on mine it is not installed by default. have you enabled all the repositories in synaptic? if so synaptic will tell you at the bottom of the screen that there are (roughly) 25000 packages listed, if not you will see only about a 1000 or so, not sure.

I think our levels of expertise on the command line are the same, which is close to hopeless.

---

### Post by movrshakr on 2009-08-24
Well, I tried to tackle this again.  My mistake.

Here
[http://www.pclinuxos.com/forum/index.php?topic=8631.90](http://www.pclinuxos.com/forum/index.php?topic=8631.90)
I found some had had success with bcm43-fwcutter which installs native linux support.

I got very excited after install when the wireless LED came on...hadn't seen that before.  However, after LOTS (2 days) of trying to set configurations, I never could get it to work. Router never showed it as an attached device, even though computer WAS seeing the SSID.

At some point, I decided it was the WPA2 router security probably preventing it, even though I had entered the passphrase in the computer.  Somehow decided wpa_supplicant might solve it.  NOT!  Another day wasted.  Used instructions here:
[http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/](http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/)

Again, ran into that "written for geeks" problem I have previously discussed.  This episode simply confirms the horrendous difficulty of making it work if you aren't a Level 3 geek.

---

