---
title: "Using WiFi card in monitoring mode"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by lz1dsb on 2013-06-07
I'm interested in using WiFi in monitor mode as I would like to capture also the signalling traffic in Wireshark. Spending handful of hours on the aircrack-ng's website confirmed my suspicion that the hardware I have at my disposal at the moment does not support working in monitoring mode :(
I have BCM4312 WiFi chip embedded on my laptop an it is explicitly listed as not supported. 
I also have DWA-131 USB WiFi card, which isn't supported either. 
So basically my question is. Based on you experience, could you recommend a USB WiFi card which I could use without any issues in monitoring mode?
Thank you.

---

### Post by dms489 on 2013-09-18
Not an answer, but a further question.  I am writing my own code using the pcap library to allow multiple Ubuntu boxes to make an ad hoc network.  What commands should I put in a bash script to disable the Network Manager and enable my wifi driver in monitor mode?

Nothing like solving your own problem ... I did some poking around and found this:
  --  [http://wiki.wireshark.org/CaptureSetup/WLAN#Turning_on_monitor_mode](http://wiki.wireshark.org/CaptureSetup/WLAN#Turning_on_monitor_mode)
Which led me to this interesting list:
  --  [http://wireless.kernel.org/en/users/Drivers](http://wireless.kernel.org/en/users/Drivers)
This  is talking about drivers and not devices, but I figured it's a start.   Somewhere it also mentioned that the Atheros hardware architecture was  recommended.

Off I go to see if I can actually find a device that works ...

For no good reason, I chose the AR5523 chipset, and ordered these:

TP-LINK TL-WN822N Wireless N300 High Gain USB Adapter
D-Link DWL-AG132

The TP-LINK was a bad idea - worked great out of the box on Windoze 7 with Wireshark, but when I looked for a Unix driver, discovered it doesn't use the AR5523 chip set, and the available driver had a bunch of caveats about the thing hanging up and incomplete functionality.  
I will use it on my Windows box to monitor the whole experiment.

Back to waiting for the D-Links to arrive.

---

### Post by dms489 on 2013-09-19
I am now the proud owner of 6 different USB wireless adapters, none of which seem willing to function in monitor mode.  One helpful suggestion was the probably the combination of USB and ndiswrapper was eliminating any possibility of success.  So I'm off searching for a lap-top whose built-in wifi adapter can be made to run in monitor mode.  When I'm less depressed / annoyed, I'll try to reconstruct the trail of tears.

Meanwhile, since the best 2 of the 6 candidates just install and run fine under Windows 7 in monitor or promiscuous mode, I am moving the while development back to Windows 7.  (TP-Link TL-WN722N and ...-WN822N)

The major problem with Ubuntu drivers for "exotic" devices is that the manufacturers are understandably reluctant to release their valuable intellectual property to the open source community.  So the Unix world has no choice but to develop a wrapper (ndiswrapper) allowing them to attempt to interact with the proprietary drivers.  There are three possible blockages between Ubuntu and the Windows drivers - the USB port, some sneaky Ubuntu setting or the capabilities of ndiswrapper.  Since my two chosen adapters both work fine via USB on the same box under Windows, this eliminates the USB port, leaving only ndiswrapper and a Ubuntu setting.  In view of the resonant silence from either community, and my reluctance to delve deep into either world, I reluctantly give up.  My application is already almost working under Windows, where I have spent months wrestling with Ubuntu wireless.

Bye.

---

