---
title: "ENUWI-N wireless adapter not working after upgrading to 9.10"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by japonetza on 2009-11-01
Hi Evryone,
 this problem kind of sucks for me. Today I updated my ubuntu from 9.04 to 9.10 via update manager. Probably the 9.10 has been there for a while but I just noticed the update. Either way, the update went smoothly and I restarted the machine after the update. Here are the steps that I took.  
 
[LIST=1]
[*]Upon login I got the window for my 	key chain and I entered my password that was working fine in 9.04.
[*]My wireless adapter did not 	connect to my network and asked me for my WEP key
[*]I gave it the key and it still did 	not work.  	
[*]I deleted the default keyring from 	the gnome2 folder, rebooted, after being asked I gave my router WEP key 	and put a new password in the keyring. Still no connection.
[*]I see my router, but I cannot 	connect to it. I have never had any problem with any of the previous 	versions of Ubuntu. And I lost my wireless only after I updated to 	9.10... what the hell?
[*]I have Encore Electronics 	ENUWI-N 802.11n wireless adapter, which has been working fine with 	any of the previous versions of Ubuntu.
[*]I tried installing the drivers 	using the Windows Wireless Drivers application, and then trying to 	feed the .inf file from my memory stick as suggested in some other 	article that I found. It did not work.   	
[*]I spent 2 hours reading forums and 	many of them complain that the 9.10 ruined their wireless 	connectivity. If this version is so bad then why release it, before 	fixing the bugs?  	
[*]I am fairly new to Ubuntu, but I 	have been able to solve most of the problems by doing some research. 	Now I am dead in the water with no clue as to what caused my 	wireless adapter to quit working, when it was working just fine few 	hours ago.
[/LIST]
 

 Please if you have any suggestions let me know or:
 
[LIST=1]
[*]suggest a basic diagnostic (step 	by step) to check if all my wireless drivers are working fine
[*]I can copy paste my screen if you 	need to see some of the details, just let me know what may be of 	interest to you.
[*]If I need to reinstall any drivers 	please let me know how to do it. I can't remember installing any of 	them. The first time I used the adapter, I just plugged in the USB 	and it worked right away.
[*]Anything else to try?
[/LIST]
 

 Thanks

---

### Post by henryhmo on 2009-11-01
I also meet such an issue for ENUWI-N.  It looks like the driver problem, because it can search networks, but cannot connect to both encrypted or unencryted networks after upgrading.  And I also to fail to re-compile the driver from ralink.

Also waiting for reply and instructions, for Karmic.

---

### Post by carcar1 on 2009-11-01
Why am I the only one that has mine working since 9.04 with no problems what so ever?  I get better speeds and reception then windows its a bug or problem with your mobo try re installing the card.

---

### Post by liljetw on 2009-11-03
This is how I got mine working. Type this in the terminal.
sudo nano /etc/modprobe.d/blacklist.conf
enter password
add these two lines
blacklist rt2800usb
blacklist rt2870sta
exit and reboot
hope this works for you.

---

### Post by henryhmo on 2009-11-05
> **liljetw said:**
> This is how I got mine working. Type this in the terminal.
sudo nano /etc/modprobe.d/blacklist.conf
enter password
add these two lines
blacklist rt2800usb
blacklist rt2870sta
exit and reboot
hope this works for you.

I tried, but still can't work. After backlist that ralink driver, the green light even does not flash and no wireless network is detected.
Probably because my Xubuntu Karmic does not carry such a wrapped up driver. Can you check what driver you are using and I can install it by apt-get? Thank you!

---

### Post by srhlefty on 2009-11-23
> **liljetw said:**
> This is how I got mine working. Type this in the terminal.
sudo nano /etc/modprobe.d/blacklist.conf
enter password
add these two lines
blacklist rt2800usb
blacklist rt2870sta
exit and reboot
hope this works for you.

I just tried this for my setup (regular Ubuntu 9.10 installed from Update Manager), and can happily say that it worked!  I'm curious though, why does it work?

---

