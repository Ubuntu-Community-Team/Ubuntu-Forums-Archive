---
title: "Almost there? or am i? (Belkin f5d7010)"
date: 2006-01-09
forum: Networking &amp; Wireless
---

### Post by amitab09 on 2006-01-09
I just bought a Belkin f5d7010 wireless pcmia card for my laptop but cant quite get it to work. The lights dont show, although the wireless card is able to scan the wireless network (stange!) Im not sure if it is in some kind of sleep mode that needs to be turned off....

the following comes up when i type ipconfig:

[I]lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2500 Wireless  ESSID:"belkin"
          Mode:Managed  Frequency=2.412 GHz  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Encryption key:6636-6132-3431-3732-3834-3033-38   Security mode:open
          Link Quality=0/100  Signal level=-120 dBm  Noise level:-200 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.[/I]

Another thing ive noticed is that in the network connections part of the task bar, the network connections tab tells me my card is ra0 is that a problem?
(not eth1 or eth0 although it has at least been placed in the wireless part) There is also no signal being picked up.

I used ndiswrapper to install the drivers and when i type the command:

sudo ndiswrapper -l

it tells me that the driver is installed and hardware is installed. So im not sure what to do now. Please could someone help me. Many thanks in advance.

---

### Post by Lambert on 2006-01-09
You probably have a driver conflict. ra0 tells me the card uses a the rt2500 driver which is a native linux driver. but you've also installed a driver with ndiswrapper.

You have to decide which driver you want to use, I suggest native linux driver so uninstall ndiswrapper.

There are links on this page for information on this driver.

[http://doc.gwos.org/index.php/RalinkDrivers](http://doc.gwos.org/index.php/RalinkDrivers)

If you want to use ndiswrapper, you'll need to prevent the ralink driver from loading. Go to the device driver section of the link to the WTG in my signature. It tells how to blacklist a driver.

---

### Post by amitab09 on 2006-01-09
I dont know how to thank you enough, i had so many problems with my old wireless card that i bought this hoping i could get it to work. From what ive read, this card should work out of the box! Apparantly all i have to type is: 
sudo ifconfig ra0 up at the command line - and the lights should start twinkling! 

I will delete the module from my ndiswrapper and take it from there i think. Im new with Linux but love Ubuntu. I think if that doesnt work then I might just format and try again....

Thanks for your rapid response, I really hope it works, fingers crossed.... If not I'll ask you for some more advice. 

i cant wait to try this out when i get home now. Thank you! :smile:

---

### Post by amitab09 on 2006-01-09
ok, I went home and removed the driver from ndswrapper and typed sudo ifconfig ra0 up at the command line but no lights came up. I figured there must still have been a conflict somewhere so I then formatted the computer and tried it again, same response. I know that the native linux driver is correct but it still is not waking my card up (ie the lights arent coming up)

What exactly should I do? I have read things about me installing the kernel source and other people commenting on editing files etc but I am really confused what to do now. 

I have basically left the system untouched since formatting and really need somebody to tell me exactly what to do from here because my inexperience with linux is not helping at all... Also does it matter that my card is f5d7010(UK) and not f5d7010 the normal version?

---

