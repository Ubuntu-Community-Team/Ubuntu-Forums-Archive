---
title: "Newbie, in over her head"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by notclaimed on 2011-01-20
Hi, let's see if I can recap this correctly.

I'm running 10.10 on two different laptops at home, via an Apple Airport Express. I wanted to use audiopulse to stream my music, o I installed that, and the Airport express utility for windows using Wine. 

I got everything working swimmingly, then my internet input wouldn't work. I can, say, upload from Transmission, but not use browsers or download anything. In a stupid fit of panic, I uninstalled everything I had set up, to see if that would help, and reset all I could. Still nothing, and now my sound is gone. Where to start, please?

---

### Post by grahammechanical on 2011-01-20
You are not the first person to do something that turned out to be stupid 2 seconds later. You have just joined the club!

May I suggest that we work this out one thing at a time? Do you still have an internet connection on both of the laptops? If not what messages do you see that tell you that you are not connected? It is best to solve one problem on one laptop at a time.

Your sound preferences may be muted. The answer may simply be to tick a check box in System>Preferences>Sound.

Regards.

---

### Post by notclaimed on 2011-01-20
Hi, and cheers for replying!

As for sound, I get a prompt saying "waiting for sound system to respond". I assume I messed something up with setting during the setup of pulseaudio?

It appears that I'm connected on both computers, but opening a browser promts server cannot be found on both, even if I've just faffed around with settings on one of them. So wifi seems to be working, yet not properly. Network manager claims all is dandy, however. 

Thanks again, I hope my ramblings make somewhat sense, the lingo is still greek to me unfortunately.

Thanks again!

---

### Post by Rubi1200 on 2011-01-20
Are you using a firewall? Did you change any settings?

Go to Applications > Accessories > Terminal and copy/paste the following commands in:

```
ifconfig

sudo lshw -C network
```

Copy/paste the output from the terminal back here please.

For everything else, I suggest you follow the very sensible advice posted by grahammechanical; do this one step at a time or you run the risk of messing other things up too.

---

### Post by grahammechanical on 2011-01-20
The server cannot be found message is what we get if (1) we have entered the wrong website address, or (2) The router/modem is not connected correctly to the ISP. The Wireless adapter in the laptop may be disconnected. The modem may be switched off. The settings in the modem may be wrong. It is not connecting to the ISP. I am just thinking of the reasons for that message. It might give you an idea of where to check. The LEDs on the modem will tell you if it is connected to the ISP.

Right click the network icon, select Connection Information and confirm the Default Route and the Primary route are the correct addresses. It should be the same set of numbers that you use in a web browser to connect to the setup program of the modem. In my case it is 192.168.1.254. If I put that address in the address bar of a web browser then I can access the modem's settings to check that it is actually connected to the ISP. You might want to confirm that. That same address allows Ubuntu to use the modem to connect to your ISP.

I know I am not giving you answers but this information may help more knowledgeable people help you.

Regards.

---

### Post by notclaimed on 2011-01-20
Rubi1200: Thank you. Here's the output I get while connected to wifi. I'm using a wired connection to get online now.


ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:cc:3c:28:b9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:11603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:700061 (700.0 KB)  TX bytes:700061 (700.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5e:7a:44:c0  
          inet addr:10.0.1.2  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe7a:44c0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1319  Metric:1
          RX packets:69330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:62255108 (62.2 MB)  TX bytes:6482362 (6.4 MB)




 sudo lshw -C network
[sudo] password for l: 
  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 00:26:5e:7a:44:c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-24-generic firmware=N/A ip=10.0.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:18 memory:f0200000-f020ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:21:cc:3c:28:b9
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:42 ioport:a000(size=256) memory:f0410000-f0410fff memory:f0400000-f040ffff memory:f0420000-f043ffff

I've not changed any settings, to my knowledge at least, except for those connected to Pulseaudio and the airport express. 

Thanks for helping!

---

### Post by notclaimed on 2011-01-20
grahammechanical: Everything seems connected, LEDs are all aglow, and the connection information accurate. Everything seems to be connected just fine, except for loading information in to the computer, if that makes sense. I can still upload in Transmission, for example. 

Going out on a limb here, but is it possible that while streaming music over the airport express, the internet couldn't be accessed because the music steals to much bandwidth, and then me panicking and uninstalling things left settings unchanged that I now somehow have to redo? This might be chasing unicorns, though.
 
Thanks again to all.

---

### Post by grahammechanical on 2011-01-20
Hi notclaimed

I hope that you understand that it is all Greek to me, as well.

If you look at the output from ifconfig you will see that wlan0 is UP and RUNNING. There is also an inet addr: This means, I would guess , that the wireless adapter is working and you are connected to the modem. You have also received 62.2 MB and sent 6.4 MB (RX= Received. TX=transmitted). so, something is working.

If you look at the output from lshw -C network you will see that wireless interface has link=yes. Whereas ethernet interface has link=no. This is as it should be because you are connected by wireless and not by wire.

I think that you know this already as you said that you could still upload from Transmission. Yes, I do think something hogging all the bandwidth will create difficulties using the internet. I am using Ubuntu One and I see that there is an option to Limit Bandwidth. So, these issues must arise. 

At this point I would be looking at the setting of the browser to see if something stupid is stopping it from working.

Regards.

---

### Post by grahammechanical on 2011-01-20
Hi notclaimed

I hope that you understand that it is all Greek to me, as well.

If you look at the output from ifconfig you will see that wlan0 is UP and RUNNING. There is also an inet addr: This means, I would guess , that the wireless adapter is working and you are connected to the modem. You have also received 62.2 MB and sent 6.4 MB (RX= Received. TX=transmitted). so, something is working.

If you look at the output from lshw -C network you will see that wireless interface has link=yes. Whereas ethernet interface has link=no. This is as it should be because you are connected by wireless and not by wire.

I think that you know this already as you said that you could still upload from Transmission. Yes, I do think something hogging all the bandwidth will create difficulties using the internet. I am using Ubuntu One and I see that there is an option to Limit Bandwidth. So, these issues must arise. 

At this point I would be looking at the setting of the browser to see if something stupid is stopping it from working.

Regards.

---

### Post by notclaimed on 2011-01-20
I'm at a loss for figuring it out. Everything works well when the computer is wired, but nothing seems to be wrong with the wireless, except for the fact that it's, well, not. Using the same browser, Chrome, on the same computer when on wired network works. At this point it's a mystery to me.

As for the sound issue, turns out the uninstall of pulseaudio didn't remove the startup items, so removing those and a clean install of pulseaudio has solved that for now.

It remains beyond me why the wireless is teasing me, however, I'm looking up ubuntu for extra-dummies as we speak. Mind, Problems are really the best tutors.

---

### Post by notclaimed on 2011-02-01
Bumping this, in case someone has ideas. 

Computer connects to the wifi network just fine, but internet connection won't work. I've tried redoing everything, but nothing has any effect. I'm sure there's a relatively obvious solution that I'm just not seeing.

Cheers.

---

### Post by walt.smith1960 on 2011-02-01
wlan0     Link encap:Ethernet  HWaddr 00:26:5e:7a:44:c0  
          inet addr:10.0.1.2  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5eff:fe7a:44c0/64 Scope:Link

I'm not much more knowledgeable than you but I noticed inet6 mentioned and I know that IP6 has caused grief for some, including me when I enabled it to see what would happen:redface:   Mine is disabled.  You might look at your setting.  Assuming your using the Ubuntu defaults, top left of the screen  System -> preferences -> network connections. Click then click on the wireless tab. Click your connection name then click "edit". You may have to enter your administrative account name.  One of the tabs is "IPv6 settings".  Mine is set to "ignore".  I wish I could be of more help.

---

### Post by notclaimed on 2011-02-02
Thanks for replying! Turns out the problem was with the airport utility, a new install of wine and the software and a few tweaks sorted it out. So all turned out well in the end.

---

