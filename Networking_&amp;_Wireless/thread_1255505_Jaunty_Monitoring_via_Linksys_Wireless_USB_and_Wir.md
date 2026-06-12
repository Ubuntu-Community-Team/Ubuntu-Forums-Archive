---
title: "Jaunty Monitoring via Linksys Wireless USB and Wireshark?"
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by beetee2 on 2009-09-01
Hello everyone,

I have several questions here and am going to try to present them as cleanly as possible, as I have been doing a lot of research and can't find a lot of information regarding my particular hardware configuration.  I am trying to self-teach myself network monitoring / logging and just general networking skills using the best tools available (including packet analysis, decryption / encryption, etc).  Anyway, here is a rundown of my network topology, pc configuration, and installed software.  I am open to any and all suggestions, tips, resources, etc.  :)

_Router:_ Linksys WRT610N [2 wireless channels configured, 5ghz streams media to my xbox 360 and ps3, the 2.4ghz is for my blackberry and wireless pc internet connection]

_Networked Devices:_ PC1 [wired, Windows XP]
                      PC2 [wireless via [Linksys Wireless USB Adapter]("http://www.newegg.com/Product/ShowImage.aspx?ISList=33-124-346-S01%2c33-124-346-S02%2c33-124-346-S03%2c33-124-346-S04&S7ImageFlag=1&Item=N82E16833124346&Depa=97&WaterMark=1&Description=LINKSYS%20WUSB600N-RM%20USB%202.0%20Wireless%20Adapter%20with%20Dual-Band"), Ubuntu / Kubuntu 9.0.4 Dual-Boot
                   Cell [Blackberry Curve 8900]

***Note: the following network monitoring software is installed only on my linux box!
_Network Monitoring Software:_ *****Here is where I would appreciate someone who is more knowledgeable's input*****
   *:Wireshark* - I have this installed but cannot get it to pickup anything from any other source IP other than PC2.  I previously was using WallWatcher (On Winblows) to analyze network traffic but the mechanism which made it effective was turning on logging in my WRT610N's admin panel and directing that log to the LAN IP of PC2 (which is still turned on, btw).
   *:Tcpdump* -  I currently have this running and logging to a .txt file on my external HDD which my /home directories live. I'll analyze this data when I get home and see if it is picking up anything from PC1. I do believe I need to configure my output to write to a file rather than the generic "output.txt".
   *:Ntop* - I have been reading a lot of good things about this network monitor and am going to give it a shot as a last resort this evening if I can't hook anything up with wireshark and / or tcpdump.

***So now, on with the questions!***  :D

**1)** is monitoring network activity from all pcs and my cell phone even possible using only wireshark?  If yes, how?
**2)** is my tcpdump that is running right now logging anything from PC1? If not, how do I configure my network to capture this information _using the hardware I currently have_? Is this even possible using my current hardware?  If yes, how?  If no, what would you recommend in order for me to be able to capture this information?
**3)** Is it possible to take an Ntop log and analyze it in wireshark?

Again, sorry if my post was long-winded. Honesty I'm still really fuzzy in regard to networking in general (C# .net developer here), and it is one area in which I am pushing to become more knowledgeable.  Thanks in advance to anyone who has any input, whether valuable or constructive criticism!  

:KS

---

### Post by beetee2 on 2009-09-01
Anyone?

Turns out I opened my tcpdump file in wireshark, and I have the packet information, but all I have from PC1 is the following:

31535  8761.387002  192.168.1.100  239.255.255.250  IGMP  V2 Membership Report / Join group 239.255.255.250

No real destination IPs or anything outgoing from there... Maybe I'll just have to install WINE, Windows, and Wallwatcher b/c I can't find anything that will "just work" like wallwatcher did for my router without any configuration other than just turning on logging in my linksys router and pointing to the IP of the logging PC... =(

---

### Post by dbalascak on 2009-09-02
Wallwatcher is a program that collects log info from routers and switches and does an analysis of the log data. Wireshark is built to capture and/or display packets coming and leaving an interface on the system it is installed on.  More for troublshooting connectivity issues between systems.  The system only receives packets destined for it because of the way the router/switch operates.  A switch learns what systems is on each port ( by the MAC address of the systems NIC card).  It will then forward packet from the source port to the one port that has the destination system.  There are special packets that are meant to be sent to all ports and those are "broadcast" to all switch ports.  So Wireshark looks at files that contain network packets not log files.  Wallwatcher and NTOP use ascii based log files.  so question 1 no,2 only if PC1 is communicating with PC2, and 3  no.

---

### Post by beetee2 on 2009-09-02
Thanks for the reply dbal... That actually cleared things up for me a bit. So when you say "no, unless PC1 is communicating with PC2". Can you just give me a quick configuration where this would be possible, regardless of hardware?  Are you talking about using a switch also, and running tcpdump against all activity on the switch?  Or possibly routing all traffic from PC1 through PC2 somehow, and then running tcpdump on PC2?

---

