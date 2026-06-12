---
title: "Problems connecting Wirelessly with TP-Link TL-WN727N USB adapter"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by Stabadie on 2010-12-15
Hello,
I'm having some issues getting connected with a TP-Link TL-Wn727N wireless USB adapter. I will warn, I am newbish to Linux. The major issue I am having is that I have no way to connect hard wired with the computer, but I have another working notebook to possibly download files. However, the second notebook is a Mac, so most of the posts I've found are not filling in all of the answers. Also forgot to note, I am using Ubuntu 10.10.

I followed along with [COLOR=Purple][this]("http://community.linuxmint.com/hardware/view/1518")[/COLOR] and managed to get the card to find the wireless connection. However, the connection would never connect. After entering the security password the wireless icon would do it's thing and then pop up asking to ok the password again. I double, triple checked the password and it is correct.

I found elsewhere that I should probably install wicd. This is where I've run into problems with finding the way to get files that I can download on the Mac and then installed on the Ubuntu computer. I managed to find [COLOR=Purple][this forum thread]("http://forums.debian.net/viewtopic.php?f=17&t=44946")[/COLOR] and downloaded [COLOR=Purple][this file]("http://packages.debian.org/lenny-backports/all/wicd/download")[/COLOR]

I transferred the file from the Mac to the Ubuntu with a flash drive and tried to install. First the install said that Network Manager needed to be removed, so I removed it. Next it says "Dependency is not satisfiable: python-urwid." I'm not sure how to go about getting this dependency as it is not showing up in the package manager.

I may be doing something completely wrong here. Please tell me if that is the case.

---

### Post by Stabadie on 2010-12-15
Just found the [How to post a wireless issue thread]("http://ubuntuforums.org/showthread.php?p=6183681"). So, here is some of the asked info.

lsusb:
Bus 001 Device 007: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless adapter

iwconfig:
wlan0        Ralink STA ESSID:''
                Mode:Auto  Frequency=2.412 GHz
                Link Quality 10/100 Signal level:0 dBm Noise level:-143 dBm
                Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
                Tx excessive retries:0 Invalid misc:0 Missed beacon:0

lsmod:
No wlan listed here...

Ok,...now this is all getting too long to retype. Is there anyway to save the output in the terminal so I can transfer it over to the Mac to add to this post?

---

### Post by r3load on 2010-12-16
[SIZE=2][B]i was having issue regarding same model wireless adapter few days, follow the instructions below may it will work on 10.10 as well :)

ust to the terminal write the following command
[SIZE=3]
[/SIZE] [COLOR=DarkRed][SIZE=3]sudo gedit /etc/modprobe.d/blacklist.conf[/SIZE]
[/COLOR]
terminal will ask for the password after this command provide ur password 

then a txt file will be open.. scroll down the file go to in the end write

[SIZE=3][COLOR=DarkRed]blacklist rt2800usb[/COLOR][/SIZE]

and saved it.

Reboot your System, plug in your wireless adapter, click on the network  indicator on top right near by clock, your wireless connected should be  visible now, click on it, provide the network key if u have and enjoy. :smile:

i have tried it on 9.10, and 10.4. Cheers ... :grin:

Regards.

Mazin Jawaid[/B][/SIZE]

---

### Post by jacksonstewart on 2010-12-16
I am new to Linux..getting problem in linking..so tell me the solution for it..

---

### Post by r3load on 2010-12-16
> **jacksonstewart said:**
> I am new to Linux..getting problem in linking..so tell me the solution for it..
kindly elaborate your problem

---

### Post by Stabadie on 2010-12-18
r3load, I tried your fix but have still not been able to connect. After adding the line into the blacklist file the wireless is again finding wireless connections. However, the network indicator just pulses up and down for a minute or two and then a wireless network Authentication Window pops up.

Hmm...I just got it working for a few seconds. I opened the wireless connections and on the Ipv4 tab, switched from Auto(dhcp) to Manual, then back to auto and it connected for about 30 seconds. Now it is beck to the authentication window popping up.

The authentication password is definitely correct. I'm not sure what is wrong here. It appears the wireless card is working, but network manager is not connecting properly.

Any help here?


> **r3load said:**
> [SIZE=2][B]i was having issue regarding same model wireless adapter few days, follow the instructions below may it will work on 10.10 as well :)

ust to the terminal write the following command
[SIZE=3]
[/SIZE] [COLOR=DarkRed][SIZE=3]sudo gedit /etc/modprobe.d/blacklist.conf[/SIZE]
[/COLOR]
terminal will ask for the password after this command provide ur password 

then a txt file will be open.. scroll down the file go to in the end write

[SIZE=3][COLOR=DarkRed]blacklist rt2800usb[/COLOR][/SIZE]

and saved it.

Reboot your System, plug in your wireless adapter, click on the network  indicator on top right near by clock, your wireless connected should be  visible now, click on it, provide the network key if u have and enjoy. :smile:

i have tried it on 9.10, and 10.4. Cheers ... :grin:

Regards.

Mazin Jawaid[/B][/SIZE]

---

### Post by Stabadie on 2010-12-18
I also just removed 10.10 and then installed Ubuntu 10.04 and am still having the same problems. I hate to say this, but I'm at the point where I've been having a computer with no internet connection for 5 days now. My only option may be to return to WindowsXP.

Recap: the Wireless USB adapter is partially working now. Using network adapter I can find my wireless signal but cannot connect to it. The wireless authentication windows keeps popping up every minute or so.

I have read that using wisd may help, but cannot figure out how to install it without an internet connection.

---

