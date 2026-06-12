---
title: "Need help with ICS through a Windows server from a 10.10 client"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by sidk47 on 2010-11-14
Respected Ubuntu gurus,

I have a wireless router situated in another room. I am able to access this router (and consequently the internet) through a Windows laptop that has a wireless card in it. However, my other laptop that has Ubuntu 10.10 installed on it, doesn't seem to have a wireless card in it, and I have confirmed this by running the commands ```
lspci
``` and ```
iwlist scan
```.

I briefly was able to share a folder in my Windows machine, and access it through my Ubuntu machine, after connecting both laptops with a cross-over cable. However, I can't even ping the Windows machine from my Ubuntu machine anymore, after trying to configure the IP addresses. I think I screwed it up.

Also, although this is not an Ubuntu issue, I have a weird Windows problem, where I can't access the Internet when both wireless and wired ethernet controllers are active at the same time. It would be a bonus if you could solve this problem too for me.

I was surfing online for a solution to this problem for quite some time, but I was unable to comprehensively understand and implement what I browsed through. Also, some of the guides, like for example, that on configuring Samba, seem to be outdated, as the terminal tells me something like the package (that was required to be installed by the guides through sudo apt-get install) has been superceded. Hence I post here for clear, concise and easy-to-understand help from you gurus.


I am a total noob, and really need help from you guys. I will be glad to provide more information as you request it. It would be great if I could achieve the end result of being able to access the internet on my Ubuntu machine (through the Windows one).

Thanking you sincerely and eagerly awaiting your responses,
sidk47.

---

### Post by sidk47 on 2010-11-15
> eagerly awaiting your responses,

Ubuntu gurus? Where are you guys? Could you please help me out here?

---

### Post by Abir Valg on 2010-11-17
Hi,
I have a similar setup to yours.
I have Windows 7 connected to my provider via cable. Windows 7 does ICS to Ubuntu 10.10 via wireless.
In order to enable ICS on W7, I click my wired connection's property and check Allow others to use this connection.
(i'm writing this by memory - menu name not necessarily verbatim).
At this point W7 informs me that its gonna assign IP 192.168.137.1 to my wireless card.
Then in w7 I create a new Ad-hoc network without any passwords. After the network is created I connect to it and I get "awaiting users" in the tray menu icon.
Now, in Ubuntu I simply select the newly created ad-hoc network in NetworkManager or wicd and connect to it. That's it.

The caviat for me was that wicd couldn't associate with the ad-hoc network automatically, I had to resort to using wpa_supplicant utility directly (but this is a separate issue).
Let me know if this helps.

---

### Post by sidk47 on 2010-11-17
Thank you for your response Abir Valg,

Unfortunately, my situation is slightly opposite to yours. Yes, the operating systems are the same, but whereas you connect to the internet through cable, and get Ubuntu to connect through wireless, I connect to the internet though wireless, and want to get Ubuntu to connect through a wired connection. In essence, I want Ubuntu to utilize the wireless card of my other Windows PC.

If you or anyone else could guide me, in detail, through the steps required to achieve this, I would be most grateful. Please bear in mind that I'm a complete noob kinda user (and I didn't really understand what you meant by that wpa supplicant thing you mentioned).

Thanking you sincerely and eagerly anticipating responses from the Ubuntu community,
sidk47.

---

### Post by sidk47 on 2010-11-17
By the way guys, the Windows OS I have is XP. I'm keeping my fingers crossed, and hoping that someone somewhere knows the solution and is willing to share it.

---

### Post by Abir Valg on 2010-11-17
(I dont have XP machine to hand so Im going by memory as far as menu names)
In Control Settings->Network Connection you see at least your wireless connection and a wired one.
In wireless connection choose properties and on one of the tabs you'll find "share this connection" (something like that). You check that. OK
Right click your wired connection, select properties and there select Internet Protocol v.4 or IPv4. There you should enter IP address like 192.168.5.1 netmask 255.255.255.0 OK

Now go to your 10.10. I assume you use NetworkManager(that's a program's actual name) and not wicd(which is an alternative)
Right click NetworkManager (NM). Choose Edit Connections. Click on your wired connection->Edit->IPv4 Settings->Method MAnual->Add
Address 192.168.5.2 netmask 255.255.255.0 gateway (i donno if its necessary) 192.168.5.1 Press OK
Sometimes NM may not change its icon to  show that connection is established.
Please do these steps and let me know how it worked.

---

### Post by sidk47 on 2010-11-18
Respected Abir Valg,

I tried to do as advised, but I ran into some glitches. There was an option to share the wired connection, so I did, and I also set the IP addresses like you told me to.

1. But there wasn't an option for sharing the wireless connection, or I couldn't find an option to, anyway.

2. The moment I enabled my shared wired connection, I was unable to access the internet. The moment I turned off AND unshared my wired connection, internet connectivity was operational again.

I hope you can help me overcome these glitches.

Thanks for trying to help,
sidk47.

---

### Post by Abir Valg on 2010-11-18
So, there is no option to enable Internet Connection Sharing on the wireless conection. It's a shame, then I don't know what to do.
The only reason I can think of is that ICS is already enabled on some other connection. But apparently you have only two, so if ICS is not enabled on your wired, Im completely at a loss why there is no option to turn it on on your wireless.

---

### Post by Abir Valg on 2010-11-18
Just do a search on something like:
XP no ICS tab on wireless
I stumbled upon:
[http://thedailyreviewer.com/windowsxp/view/missing-ics-checkbox-in-the-advanced-tab-on-network-properties-108158757](http://thedailyreviewer.com/windowsxp/view/missing-ics-checkbox-in-the-advanced-tab-on-network-properties-108158757)

It can be anything: XP glitch, other software blocking, non-administrator rights to name a few.

---

### Post by sidk47 on 2010-11-18
Respected Abir Valg,

I think that it's not me that's doing anything wrong. But rather that Windows XP just doesn't provide an option to share a wireless connection. You can confirm this by checking out your wireless connection properties in Windows 7. Please check it out and please get back to me with your findings.

Thanks for trying to help,
sidk47.

---

