---
title: "Can't connect to network"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by pveurshout on 2009-07-28
Hello,

After having used Ubuntu (8.04) for over a year, I decided to give Kubuntu a try for a change. I installed 'kubuntu-desktop' using the package manager and all worked just fine. However, my luck changed when I did a fresh install of Kubuntu 9.04 and couldn't connect to my network - neither wireless nor wired. I installed Ubuntu (9.04) to see if it'd work there - which it did - and then switched to Kubuntu again by installing kubuntu-desktop.

On my new laptop I freshly installed Kubuntu 9.04 (64-bit), only to find out there was no way on earth to connect to my network either. I've been looking around the internet for a while and found out that the standard network manager simply is a piece of ****. Unfortunately, many solutions for the problem consist of simply downloading another network manager, which will not work for me as I have no connection whatsoever. The problems generally relate to wireless connections only, as far as I know.

Anyway, I was wondering if anyone knows a way to get another network manager installed (like using a USB-storage device or something) or if there's another way to get at least the wired connection working? Thanks!

---

### Post by mediumcool on 2009-07-28
If you have a wired connection and you know your network range you could pick an ip in that range (say 192.168.1.180 in a 192.168.1.0 network) and run

sudo ifconfig eth0 192.168.1.180 

You should now be connected to download another network manager.

HTH,
Sean

---

### Post by pveurshout on 2009-07-28
Hi, thanks for your quick reply. Unfortunately, it didn't work :( I picked 192.168.0.99 in the Network Manager and then ran the command sudo ifconfig eth0 192.168.0.99 (am I supposed to see anything happen btw? I just got a new command line). I then again tried connecting using the network manager, it kept saying 'Setting network address' for a while, but eventually gave the error message "Connection on Network interface eth0 failed".

edit: I found [this]("http://webupd8.blogspot.com/2009/06/how-to-manually-set-up-your-wired.html"); perhaps it'll work. However, I'm kind of afraid to remove the network manager as I won't be able to get it back without a working connection. Do you happen to know whether I can somehow disable it so I can try this out without removing it?

---

### Post by mediumcool on 2009-07-28
ifconfig will not give you feedback, just return you to the command prompt.

The link you gave should work - there is no need to remove network-manager first though - it should bypass any interfaces that are configured in /etc/network/interfaces.

You can disable network manager from system --> preferences --> startup applications but will need to reboot.

---

### Post by pveurshout on 2009-07-28
Hey,

The manual editing of /etc/network/interfaces worked, although I haven't been able to get my wireless connection working with any network manager. I guess I'll just switch back to Vista until 9.10 comes out, which will hopefully have my network connections work just as good as 'regular' Ubuntu :) Thanks for all your help!

edit: couldn't help but install Ubuntu Jaunty after all..it all works there and, although I like KDE better, it still beats having to use Vista ;-)

---

### Post by TravisNRG on 2011-06-18
> **pveurshout said:**
> Hello,

After having used Ubuntu (8.04) for over a year, I decided to give Kubuntu a try for a change. I installed 'kubuntu-desktop' using the package manager and all worked just fine. However, my luck changed when I did a fresh install of Kubuntu 9.04 and couldn't connect to my network - neither wireless nor wired. I installed Ubuntu (9.04) to see if it'd work there - which it did - and then switched to Kubuntu again by installing kubuntu-desktop.

On my new laptop I freshly installed Kubuntu 9.04 (64-bit), only to find out there was no way on earth to connect to my network either. I've been looking around the internet for a while and found out that the standard network manager simply is a piece of ****. Unfortunately, many solutions for the problem consist of simply downloading another network manager, which will not work for me as I have no connection whatsoever. The problems generally relate to wireless connections only, as far as I know.

Anyway, I was wondering if anyone knows a way to get another network manager installed (like using a USB-storage device or something) or if there's another way to get at least the wired connection working? Thanks!

i just installed kubuntu 11.04 or something, and my light for wireless is on and i can scan the area and select my wifi and then it says Configuring interface, then gets stuck on "setting network address" ...??   its making me so angry ..

---

### Post by nbound on 2011-06-18
post output of **lshw -C network**

---

### Post by dld521 on 2012-01-25
[COLOR=Navy][SIZE=3][FONT=Times New Roman]I'm not the person who originally posted this problem, but I have it as well, with it hanging up at the same place as the last post described.  Here's the output of the command you requested:

 *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 01
       serial: c0:cb:38:39:01:a0
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:fbdf0000-fbdfffff
 
Thanks for whatever suggestions you may be able to offer.
[/FONT][/SIZE][/COLOR]

---

### Post by jonobr on 2012-01-25
Guys

Id recommending starting your own new threads.. its free.

---

