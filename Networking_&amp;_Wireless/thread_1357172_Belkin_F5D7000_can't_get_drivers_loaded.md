---
title: "Belkin F5D7000 can't get drivers loaded"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by cjwescott on 2009-12-16
I've been loving Ubuntu so far (new user) but I have to say that trying to get a wireless adapter installed in Ubuntu is very painful.  I searched for instructions on how to proceed and not one is the same and everyone seems to get to a point where I do not understand the instructions or nothing works/happens as a result of them.  Is there up to date instructions on how to install the correct driver for this card and how to get the wireless adapter configured?  I am willing to go out and get a new adapter if there is a brand which is a slam dunk in simplistic installation.   I am using WPA security BTW.  Seems that this adds another level of complexity which I am sure I am screwing up the instructions.  I also have couldn't get my laptop to hold a connection.  Got it connected once but it dropped it a minute or so later.  Not that I have tried getting the above card installed on a desktop it might be the WPA component that is causing the problem on the laptop.    Any guidance is much appreciated.  Chris

---

### Post by Bucky Ball on 2009-12-20
Plug in an ethernet cable if you haven't already and get your updates. System->Administration->Hardware Drivers. Anything there?

9.10 is nowhere near it for wireless as yet as evidenced by the many support request concerning 9.10 and wireless on the forums.

---

### Post by cjwescott on 2009-12-23
I decided to upgrade to Wireless N.
 
Since the D-link hardware appears to have linux drivers readily available, I have ordered a D-link router and D-link adapters.  Hopefully this install goes smoothly. 
 
Chris

---

### Post by hyperdude111 on 2009-12-23
I have see a couple of post with people having issues with the F5D7000, I fitted mine about a year ago without doing any research about compatibility. Once I had managed to free enough space around my PCI slots the install was smooth and the wireless card has worked out of the box on both Ubuntu jaunty + karamic and Windows 7.

I think the drivers may be less effective depending on some other hardware one might have.

Anyway good luck with the new card.

---

### Post by Bucky Ball on 2009-12-24
You don't need to do anything as far as software goes with a router. I use two D-Links. Just configure through a browser. Type:

192.168.0.1

... in the address bar.

---

### Post by cjwescott on 2009-12-25
Luckily I have that much figured out.  Only reason for changing out the router was to get faster speeds.  The wireless adapters is what I replaced for compatibility purposes.

Chris

---

### Post by OCNetGuy on 2009-12-29
Hi cj,
 
I just got my Belkin wireless F5D7000 PCI card to work in Ubuntu Desktop 9.10 32-bit. What I did was get it connected to the Internet by ethernet and do all the updates. Then go to System --> Admin --> Hardware Drivers, and it listed the "Broadcom B43legacy wireless driver" and is even tested by the Ubuntu developers. Select and install it. Afterward, reboot, and now you're ready to configure your wireless connection!
 
Hope this helps you -

---

### Post by Bucky Ball on 2009-12-29
> **Bucky Ball said:**
> Plug in an ethernet cable if you haven't already and get your updates. System->Administration->Hardware Drivers. Anything there?

9.10 is nowhere near it for wireless as yet as evidenced by the many support request concerning 9.10 and wireless on the forums.

My first post (#2), OCNetGuy. Exactly. Should be about that easy.

---

### Post by cjwescott on 2009-12-29
I actually installed my newly purchased D-Link DWA-552 card today.

I can't say it went easy but I did finally get that card operational.

I should have reviewed the replies here when I performed this, it may have gone much easier if I did.

Chris

---

### Post by SeaJayEmm on 2009-12-29
First off, hard wire the computer into the router and update your system. Then you will need the install disc that came with the network adapter. On this disc you can find the .inf and .sys file you will need. You should get these from the winxp driver. Use ndisgtk to install the .inf file, reboot your machine and you should have wireless connection. I have never had a problem with getting any wireless adapter working with ubuntu.

---

### Post by cjwescott on 2009-12-30
Well I'm good to go already, however, for any future installs this is great information.  It is the exact steps that someone like myself needs for getting things to work in Ubuntu, given how green I am.

Heck...I follow the steps given in Ubuntu Kung Fu and still to no avail I can't get the Tip to work. I don't know if using Karmic is the reason and the book was written based on an earlier version but so far two Tips haven't worked for me.

Struggling to get the card to work also gave me an excuse to go out and upgrade to the N series of cards.

Chris

---

### Post by cjwescott on 2010-01-01
Well I was good to go on my remote desktop and I thought the process would be straight forward for my laptop as well but I guess I was dreaming.

I decided to wipe out WinXP on the laptop (Toshiba) and do a full install of Ubuntu 9.10 32bit.
I installed the driver as mentioned above using ndisgtk.
Ubuntu sees the card.
I have an active connection to my router, yet I can not browse the internet nor download any packages.
I tried pinging using the network tools and I get no response.

So...I don't understand what is going on.  Ubuntu indicates an active connection to my wireless network.  Is is a driver issue?

Any continued help is much appreciated.
Chris

---

