---
title: "Dell XPS M1530"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by Ben Ward on 2010-03-28
Hi all I've just installed Ubuntu on my Dell XPS M1530 and aimed to use it along side of buiding a new PC unit that works with Ubuntu or Ubuntu[Sci] because I'm a Biology Student and want to use it for things like 'R' and other programs and maybe learn to do a bit of programming as one of my tutors is interested in putting together a toolbox of applications for studentrs and I'm getting an interest in this area and want to help him out. I'm gonna stress now, yes I'm a newb and my only experience has been with windows up until now. Anyway I've installed it using a live Cd and the wireless will not work, and I've tried and tried and I've been through godknows how many forum pages and installed and troubleshooted ndiswrapper on this very forum and still no luck. I'm completely at my wits end and not too far away from canning the whole thing before I've even begun because if I cant connect to the internet there is no point at all, so any help at all is greatly appreciated, I have read around and googled god knows how many times but all I get is jargon or solutions which don't work. Thanks.

---

### Post by bloodorange on 2010-03-28
I've got a Dell XPS M1530 and the wireless works without a problem.

Which version of Ubuntu have you installed?

---

### Post by Ben Ward on 2010-03-28
I downloaded the latest Karmic Koala version, I only just got it on thrusday.

---

### Post by bloodorange on 2010-03-28
Mmmm.  That should work.  When you click on the Network Manager icon (near the date and time at left of the top panel), what do you see?

---

### Post by Ben Ward on 2010-03-28
I hover my mouse over and it says no connection, and when I click on it it gives me a little drop down saying Wired Network (Disconnected) and then VPN Connections.

---

### Post by bloodorange on 2010-03-28
Have you still got Windows installed and, if so, does wireless work OK on that?

Has wireless been disabled in the BIOS? If not (and this may be a daft question) have you definitely turned wireless on with the switch on the side of the laptop?

---

### Post by Ben Ward on 2010-03-28
Yeah the wireless is definately on, I've currently got it dual boot with Widows 7 ad Ubuntu Koala and the net and everything works with windows 7.

---

### Post by bloodorange on 2010-03-28
> **Ben Ward said:**
> I hover my mouse over and it says no connection, and when I click on it it gives me a little drop down saying Wired Network (Disconnected) and then VPN Connections.

Did this look the same before you installed ndiswrapper?

Have you still got ndiswrapper installed?

---

### Post by Ben Ward on 2010-03-28
Yeah it looked the same, I installed ndiswrapper and tried to install the most suitable driver from the ndiswraper wiki but it hasn't seemed to help at all.

---

### Post by bloodorange on 2010-03-28
Can you see your wireless card if you run lspci in the terminal?  If so, how does lspci list your card?

---

### Post by Ben Ward on 2010-03-28
It lists the network controller currently a Broadcom thing, i think thats it, cuz the other thing it mentions is ethernet which is the wire connection which I don't use. Would it be a better idea for me to go back onto windows 7, delete the appropriae partitions and start again?

---

### Post by bloodorange on 2010-03-28
It looks like you might have to, unless someone else comes on and gives you better help than me.  I'm no expert, and I've reached the limit of my knowledge on this kind of thing I'm afraid.  Dell must've changed the wireless chip since I bought mine, as mine isn't Broadcom.

Sorry I've not been able to help you.  I hope you manage to get it working on Ubuntu sometime soon.

---

### Post by Ben Ward on 2010-03-28
That's ok I appreciate it anyway, thanks.

---

### Post by Ben Ward on 2010-03-28
Ok I'm taking off the current Ubuntu partitions off and installing again.

---

### Post by Ben Ward on 2010-03-28
I should probably give more info, the wireless card is Dell Wireless 1505 Draft 802.11n WLAN Mini-Card

---

### Post by Ben Ward on 2010-03-29
I found my solution at last! I did as Jomotis suggested in an earlier thread:

 				 				***9.10 Broadcom Wireless to Work*** 			
 			 			 		   		 		 		[I]Perhaps this  will help someone out there.

I was using Jaunty fine on my laptop (Dell e1705) with wireless working.   I installed 9.10 beta and could not get it to work.  In jaunty I was  using the Broadcom Wireless driver that showed up in System >  Administration > Hardware drivers.  [/I] [I]

When I installed 9.10 as a fresh install from the live cd, it would list  only the Broadcom Wireless driver.  I kept choosing "Activate" and  entering my password, but it would never activate.  Having no network  connectivity, I was unable get any updates.[/I] [I]

However this worked for me:[/I] [I]

1) Open Synaptic Pacakage Manager[/I] [I]
2) Ensure 9.10 LiveCd is in CD drive
3) Settings > Repositories > Ubuntu Software
4) Check the installable from cd and close
5) Refresh 
6) Search for "bcmwl-kernel-source"
7) Mark for installation
[IMG]file:///C:/Documents%20and%20Settings/Ben/Desktop/Ubuntu%20Forum%20Support%20Pages/showthrea3d.php_files/icon_cool.gif[/IMG] Install it
9) Reboot computer

That worked for me.  It was activated Hardware Drivers now.  Also, after  doing this (I think because dkms installed with it) now the graphics  drivers appeared in the Hardware Drivers scan, which hadn't before.[/I]  [I]

Basically, installing bcmwl-kernel-source was the key to success for me.   Handily, it is on the livecd.[/I] [I]

Jon[/I]

---

