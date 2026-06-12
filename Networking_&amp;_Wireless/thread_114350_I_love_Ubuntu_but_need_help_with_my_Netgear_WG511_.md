---
title: "I love Ubuntu but need help with my Netgear WG511 wireless card"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by amitab09 on 2006-01-08
Hi guys, Ive just tried installing Linux for the first time and had no problems until i tried to get my wireless card, a Netgear WG511 (version 1 i believe, made in china) working! I read and tired various solutions endlessly but cant seem to get it working. I think its because im a linux newbie. I need someone to work through this with me... I guess this is where all you guys come in. 

So far so good, i think :confused: ....  The driver is installed and the hardware is recognised, but the lights dont come on......

I managed to get the ini and sys files from the official driver from the exe installation file from netgear and get them wrapped by ndiswrapper. I checked by looking into the /etc/mdiswrapper folder and I also ran the command:

[I]ndiswrapper -l 

Installed ndis drivers:
netwg511 driver present, hardware present[/I]

I also typed in the iwconfig command and got the following:

[I]lo no wireless extensions.

eth0 no wireless extensions.

sit0 no wireless extensions.
eth1 NOT READY! ESSID:"belkin"
Mode:Managed Channel:0 Access Point: 00:00:00:00:00:00
Tx-Power=31 dBm Sensitivity=0/200
Retry min limit:0 RTS thr=0 B Fragment thr=0 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/I]

Im not sure what to do now, I am really stuck. Could someone please assist me. Thanks (PS, please be gentle, im new with Linux.) Thanks again

---

### Post by DeadEyes on 2006-01-08
Your access point is all zeros, that means you are not connected to it, trying working through the [WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide")

---

