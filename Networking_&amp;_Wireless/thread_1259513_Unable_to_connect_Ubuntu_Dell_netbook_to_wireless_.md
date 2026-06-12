---
title: "Unable to connect Ubuntu Dell netbook to wireless WEP"
date: 2009-09-06
forum: Networking &amp; Wireless
---

### Post by Striding on 2009-09-06
My daughter has bought a new Dell Inspiron Mini 10 with Ubuntu 8.0.4

All works great apart from wireless networking.

We have spent hours trying to get it to connect to our Linksys WRT54GSV4 router using WEP. We have several windows laptops configured with little problem. I have tried removing MAC filtering, enabling ssid broadcast, and even tried taking the security off completely, but still cannot connect, giving 'The network connection has been disconnected.' I think that I can see the MAC address showing on the router, so it looks like it is making some contact.

Network manager is very difficult to use, local wireless networks are not showing up at all, and it is all very confusing. Tried the first 10 hex digit key, and various combinations of settings. adding router mac address, creating new connections, connecting to hidden network etc., but never yet connected. Wireless and networking are switched on.
Any ideas? Am I missing something obvious?
Please!

---

### Post by sanderj on 2009-09-06
With Ubuntu 8.04 I couldn't connect to WEP either. See my bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223111](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/223111)

To verify that this is your problem: can you connect to unencrypted AP? And to WPA2?

And: read the thread in the bug report for workarounds.

---

### Post by Striding on 2009-09-08
Thanks very much for the reply; I will think about that. I did try unencrypted briefly, and it did not seem to work, but we were struggling with odd behaviour of Network Manager, so I'll try that again. We have about 6 other devices set up for the WEP, some of which won't do WPA, so non-WEP would be a reluctant option. I must admit I don't understand the workarounds with different kernels etc. as I am very new to linux.

It does seem a bit poor of Dell to sell a hardware and software combination that has such a major fault, in what is one of the most important features of a netbook.

---

### Post by Striding on 2009-09-13
Tried those commands and got the updates to work.
Wireless and WEP even worse.
Dell service tag not recognised by Dell site.
Dell site only works with IE.
Not impressed.

---

### Post by Striding on 2009-09-13
After applying updates, have lost the option to Connect to Hidden Networks and Network manager shows 'The device is unmanaged'. 
We can configure a wireless connection, but can't find a way to try to make it connect.

---

### Post by cptrohn on 2009-09-13
If you don't mind me asking.... but why use 8.04?

9.04 seems to have much better wireless than 8.04 in my opinion... I know I had alot of problems in 8.10 and had to enable backports to get my card to work, but in 9.04 there is no problems at all with any of my cards.

---

### Post by JakP on 2009-09-13
Had some similar problems, this worked in 9.04 but don't know about earlier:
To get networkmanager to manage device:
In terminal:
sudo gedit /etc/NetworkManager/nm-system-settings.config

this will bring up a file where you need to change:
"managed=false"  to "managed=true" (no quote's) then save.

After this it started managing wireless.

in the end i switched networkmanager for wicd wich seems to work better

---

### Post by community nerd on 2009-09-13
Just curios but do you know what wireless card you have?

---

### Post by JBAlaska on 2009-09-13
According to dell website;

Mini 10 and 10v:
Wi-Fi:
Dell 1397 WLAN 802.11g - Half mini-card
Dell 1510 WLAN 802.11g /n Mini Card

Bluetooth:
Bluetooth®  Internal (2.1+EDR) mini-card

I also have had better luck with wicd on my Acer

---

### Post by Striding on 2009-09-15
Thanks for all of the help and advice. The network card is a Broadcom BCM4310 (rev 01), from doing lspci -n | grep '14e4:43'
and getting 14e4:4315 (rev 01) according to somewhere I found.
 
I'll try to get the netmanager back if I don't get any further tomorrow.
 
Why use 8.0.4 ?
I am not sure exactly how to upgrade, and still hold out some hope of Dell either getting it working or taking it back.
I don't know ubuntu, and only bits of old unix from large servers (still outperforming the Windows machines today).
 
Tried entering problem on Dell technical support site, but no luck. Details were routed to customer services who could not help with technical problems, or route it to the right department. Tried this again with similar result and failure to read the full details.
 
Phoned Dell support (using an 01344 number, not the expensive 0844..) and after about 3 minutes got through and gave the service tag, then after another 10 minutes gave it again, with great difficulty in understanding and being understood, having to resort to the phonetic alphabet letter by letter for many words. Apparently the service tag was still not recognised, hence the routing to customer services, who seem to be unable to diagnose that scenario.
Eventually the support guy tried to connect to the netbook through the ethernet connection, only to find 'Operating system is not supported' He hadn't realised it was ubuntu, despite the order, item and earlier comments all indicating that. That required a different ubuntu support department. By that time, after 35 minutes of the call, they had shut for the night, and I have a new number 0844 3381122, unless I can find a cheaper alternative) to try all over again tomorrow.
 
Is this normal for Dell?
 
I have struggled tracking deliveries before, but not had much cause to deal with the technical support.:confused:

---

### Post by Striding on 2009-09-15
I checked and the /etc/NetworkManager/nm-system-settings.conf
 
file shows managed=false.
 
How do I use gedit to do a simple change and save and exit. I have a fear of unix command line text editors like vi  (very poweruful I'm sure, but very different to what I was using at the time) from some bad experiences in the past, or is gedit a graphical editor? Searched online and answered my own question, I think I can manage that.

---

### Post by Striding on 2009-09-18
Spent  an hour on the phone to Dell 'ubuntu support'. What a waste of time and money.

After about 40 minutes reached the point where it was decided that ubuntu is not compatible with my router and ISP(!), and I should talk to my ISP, or another ISP(?). Ubuntu is a new product and is not compatible with some router and ISP combinations. I could send it back for diagnosis (7-10 working days), or put Windows XP on it. 

When I asked about version 9.0.4 or Netbook remix the 'support rep' would not answer, or did not know anything. Initially they refused to give a refund as it is more than 7 days since I received it (mainly due to their system not recognizing the service tag, and poor online and phone support). If I wanted to request a refund, I needed to talk to customer services who don't work after 6pm or weekends (I thought I was dealing with worldwide computer company Dell, not a 2 man backstreet dealer).:confused:

I could have tried to work out how to load 9.0.4 or netbook remix, but was concerned that if that did not work, Dell would be even less interested in fixing the problems, and it might never work. The product they have sold, with the hardware and software combination, is incompatible with many wireless networks, and they don't know what to do. The frustrating thing is that I'm sure the solution is out there, but it is clearly beyond Dell's staff or will to find it, and I haven't got the time, and am not prepared to take the risk.:(

So the outcome is Dell are coming to collect it next week, and I will get a refund.
We are deciding whether to get another netbook from elsewhere, possibly with Windows XP this time, which we know (and tolerate).

I would love to switch to ubuntu and open source, but not yet. I haven't got the time,
 and certainly if I do it will not be from Dell, after my experiences with their support and customer services. Sometimes you wonder how such companies stay in business?

---

