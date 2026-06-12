---
title: "Very slow Realtek RTL8211B on 8.10"
date: 2009-08-14
forum: Networking &amp; Wireless
---

### Post by nicoloks on 2009-08-14
I've had my htpc up and running for over half a year without too many issues. Apart from the issue where the built in Realtek RTL8211B NIC in my ASrock motherboard caused Mythbuntu to [read the MAC address in backwards]("http://ubuntuforums.org/showthread.php?p=4156690#post4156690"), it has been really stable.

Until about a week ago that is. 

Previously I had a very simple setup where the htpc (mythbuntu 8.10) was plugged into my Linksys WAG54G V2 ADSL modem/router (configured as the DHCP server) along with my ESXi server (in my study) and my laptop which I connected via Wireless G or fast ethernet. During this time the Realtek card in my htpc worked at a full 100Mbit. I now have the cable that was plugged into my ESXi server plugged into a Billion GS08 gigabit switch, and plugged into this switch is an ESXi server and my workstation. 

Since I've added this new switch network transfer speeds (internal or external) have gone from 100Mbit across my LAN to 50Kbit (dial up modem speed). Weird thing is if I take the cable that is connecting my Linksys and Belkin switches and plug the htpc so that is is connected directly to the belkin switch I get full performance again. What is weirder again is that looking at /var/log/messages I can see that eth0 was been going up and down every few minutes (around 3500 time) in the 5 days since I put my new switch in.

I'm by no means a Linux guru, and wa just wondering if anyone had any suggestions on what might be causing this? Every other device on my network is working perfectly, except for this Mythbuntu 8.10 box, and only since I put in a new Belkin GS08 switch.

---

### Post by nicoloks on 2009-08-14
Well it looks like there is nothing wrong with my Mythbuntu box. Connecting it directly to my Billion GS08 gigabit switch results in it working at ull pace, as does linking my laptop directly to it. THe only way I can get this slowness issue to occur is when my Linksys router is involved. 

I did a cold restart on my router last night and the transfer speed from my Mythbunti box jumped up to around 10Mbit. Tried transferring again this morning and it has slowed again to around 5Mbit. Seems there is some sort of issue with my Linksys router and the use of MDI/MDI-X. Good excuse to upgrade to a Gigabit router with Wireless N :P

---

