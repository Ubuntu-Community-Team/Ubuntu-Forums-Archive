---
title: "Urgent help needed with wireless recogition! Ubuntu 10.04"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by IVirOrfeo on 2010-10-13
I have never had a problem with connecting to the internet wirelessly before.
I was on ubuntu studio 9.4 for a year, no problems
I use a Belkin Wireless G network adapter Model number F5D7050
I am using ubuntu 10.4, and I am having a problem with recognizing my signal from my wireless router, a westell verizon router. I updated a couple of days ago (from 9.4) and it went well, with no problems. I was able to communicate with my router using the adapter, and I was able to update the System and Apps using system update. I was still able to use the internet after this. I used the internet alot, and had no problems after this. The next day, in the morning, I was able to use the internet flawlessly.I turned off my computer and I went off to work and when I came home eight hours later and turned my computer on, the icon I have become accustomed to, the bars, or wave was gone and replaced by two computers along side each other, with a red X next to it. when I left clicked the icon, I saw a greyed out "wired network" and beneath it, the word disconnected, and a VPN options menu. None of these things were in reference to my wireless, and I could not change them, so I right clicked and saw a checked box for enable networking, and a checked box for enable notifacations, connection information, which I cannot click on (it won't let me) and edit connections. (in the help menu, I saw that it was supposed to have an option to "enable wireless" it DID NOT) I entered into edit connections with the intent to somehow activate the wireless connection and access the internet again, however within this menu, there was no option to use the wireless instead. foolishly perhaps, I deleted the original wireless connection in a bid to reactivate the connection. Of course, I remembered most of the information but cannot recall (one wonders if I should) the BSSID number or the DHCP Client ID under the IPv4 Settings tab. however I do remember the WEP key, the SSID(I believe that is the name of the network correct?) and the  MAC address. I checked the boxes Connect automatically and Available to all users and I hoped that the computer would recognize the measures and ignore the nonexistant wired connection. It did not. In an act of despiration, I connected my computer to the wireless router via a wired connection (I believe RJ-45) Still, the icon was the same as before, Wired connection, disconnected. 
At first, I thought that it might be a router issue so I called verizon, the checked the router and I was informed that the signal was fine on their end, On my end, the router seemed to be doing as it always does, All the lights that display function were on. Then, I though it was a issue with the adapter, so I unplugged it several times and rebooted the computer also several time each with a different usb port selected, (I have six) The same result occured, however the adapter seemed operational, with the light on, and in the help menu for ubuntu I was able to go to the terminal and 
sudo lshw -c network 
which gave me
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: [EMAIL="pci@0000:04:00.0"]pci@0000:04:00.0[/EMAIL]
       logical name: eth0
       version: 02
       serial: 00:21:85:9d:2f:94
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:e800(size=256) memory:f8fff000-f8ffffff(prefetchable) memory:f8fe0000-f8feffff(prefetchable) memory:febf0000-febfffff(prefetchable)
so it seems that the adapter can communicate with the computer at least,So I thought that maybe something I did in the update caused this issue. I thought "let me try to live into the system" as I have gotten internet with the live CD for ubuntu before. So, I booted from CD (10.04) and I received the same result as my installed partition the "wired network, disconnected" status once again. I tried again with Ubuntu 9.10, same result. I attempted to live from SUSE and Fedora, alas, my DVD reader would not recognize them, (I have been having sporadic issues for the last month with my DVD burner, it will write to disc and then not recognize it. perhaps this is related) I am hoping it is a problem I can change within my system, as it is, I am posting this from a college computer and I wish I could do more research, my time is limited here and I must go to class soon, i will probably not have time to research this problem much further today. I am very worried about the prospects however. I must say that I am very discouraged, as someone who has made both linux and networking a big part of their life and career plans I am severely demoralized by this turn of events. Furthermore, without the internet over the week, I am at a severe disadvantage in my studies. I chose linux because I love it, however now no one can help me because no one I know knows as much as me about it. Please, help me. In my free time I do all I can to assist, convert, and make others aware of what linux has to offer.
Please contact me at my email [EMAIL="IVirOrfeo@gmail.com"]IVirOrfeo@gmail.com[/EMAIL] or by posting in this thread my number is 914 739 0211 and I would prefer you contact me there as I can be reached more easily due to me not having access to the internet, please don't leave a message, I cannot retreve them, just call again later. Moderators. If it is against the TOS to put phone numbers, edit my post to reflect what is proper, however, please don't delete it entirely, this problem is utterly urgent and necssiary.

---

### Post by kreggz on 2010-10-13
If you have recently updated you might be able to try using the previous kernel version in the Grub menu.

---

### Post by IVirOrfeo on 2010-10-13
that would be great, but I used a fresh install.
any other suggestions?
do you need to know anything else about my setup?

---

### Post by kreggz on 2010-10-13
So when you click network manager you can see your Wireless network there? What happens when you click it?

---

### Post by IVirOrfeo on 2010-10-20
There is nothing there...

---

### Post by necromonger on 2010-10-20
I had trouble with 9.10 wireless also 10.10 solved all of my wireless problems.

---

### Post by IVirOrfeo on 2010-10-21
Network adapter simply says 
Wired connection
Disconnected
There is no reference to the wireless connection or wireless adapter AT ALL
This is doubly worrying because for the first two days, worked as it always has, I wish I knew what caused the change... I worry that it is a hardware issue with the usb ports, however, my mouse and flash drives still work with the usb ports.
I tried to recognise the wired connection with my nic card as well did not work...
I am wondering what this could be... please help if you can. any information you need, just ask.

---

### Post by IVirOrfeo on 2010-11-01
I have fixed my issue in a somewhat kludgy way. I hit ctrl alt F1 everytime I login, and then I enter username and password, and then I type help. I then do sudo service gdm restart. it works everytime!
I am happy because beside from this issue, it is a beautiful setup!
It boots in 5 seconds and it only has 512MB RAM and core 2 duo

---

