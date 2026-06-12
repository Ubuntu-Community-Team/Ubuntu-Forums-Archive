---
title: "HP wireless works, can't get online"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Ragtop on 2009-12-15
My HP mini 1030NR came with XP, but I loaded Ubuntu 9.10. I get the blue light on the front of the 'puter, indicating wireless connection working, but can't get online. The light comes on as the Mini boots, the little gizzies chase each other around in circles, and I get a flag that says I am offline!:sad:

Placing cursor on the antenna icon gives "no network connection". Clicking the antenna gives list of networks, and in the middle of the list is my secured net, showing full signal strength, but with a padlock on it. 

Selecting and clicking it results in the same "gizzie dance" and the "You are now offline" flag - - like I didn't know that! :frown:

Seems like it's a password (passphrase?) issue, but I don't get an opportunity to enter it.  Well , I'm not prepared to accept "offline" as the only operating condition on this machine, so I keep pokin' around dropdown lists and mostly being puzzled.  Under the "System - Preferences - Network Connections - Wireless" tab, I found my network name and "never" in the "last used" column with options to Add, Edit, or Delete

That looks like one of them **_*might*_** be the key, but it's late and I'm tired and sinus runny miserable.  May I please have a pointer or a little guidance from one more knowledgeable than I? (Meaning anyone who knows what the heck is going on here and how to get past this roadblock) ](*,)
I'd be deeply appreciative!

ATB:biggrin:

BC

---

### Post by uncaspi on 2009-12-15
9.10 have problems with the password. I think you must use WEP or no encryption at all. ;)

---

### Post by haribol707 on 2009-12-15
Hi, changing to WEP will solve the problem?

---

### Post by uncaspi on 2009-12-15
You could try:D

---

### Post by Bucky Ball on 2009-12-15
Changing to 9.04 or better still 8.04 LTS will solve the problem! 9.10 remains buggy.

---

### Post by Mski35 on 2009-12-15
I'm running 9.10 and my wireless only worked after I was prompted to save my credentials in my keyring.  Once I clicked on network manager and chose show available networks, I chose my secure network and was prompted to enter my security information in my keyring.

---

### Post by yumgnomeandthensome on 2009-12-16
i use 9.10 with HP laptop and can connect using WPA, however i do have my problems. 
I often have to delete and recreate my wireless settings and i connect. 
However the last two times its booted up already connected!!

---

### Post by Ragtop on 2009-12-16
> **Bucky Ball said:**
> Changing to 9.04 or better still 8.04 LTS will solve the problem! 9.10 remains buggy.

Somehow, I got the idea that 9.10 was a stable release.  I've got no problem loading back releases, but is there some danger in Ubuntu pitching a product that still needs so much tweaking?  I've resented the big dog's habit of letting their customer base be the final testers for years.  I thought the linux crowd were NOT using them as models.
Hello, Redmond - come in Redmond.....are you there Redmond???.......:lolflag:

ATB:biggrin:

BC

---

### Post by Ragtop on 2009-12-16
Well, here's one for the Gurus!  Per the hint from buckyball, I decided to install 8.04lts.  So, I found the file, downloaded and burned the ISO and started to boot my HP1030 that's been stumbling on 9.10 from that CD.  I changed the bios boot order, and the boot process was interrupted but it didn't seem that it did a full install, but suddenly I noticed that I was ONLINE!!!  

Fearfully, I shut the computer down, disconnected the CD drive, and rebooted.  Boot process seemed faster than any I'd seen with 9.01 and it searched for wireless briefly and brought up my secured network!!!

Was there "something" in the 8.04 ISO that automatically patched the flaw in the existing 9.01 install?   At any rate, it takes the "Darndest thing I've seen _*lately*_" prize

I clocked 25 seconds from power on to wireless contact (blue light on the 1030). And at 46 seconds, I had "Connected to network" message!   It's a lean, mean, network hookin' machine!!!  Any explanations out there?

Anyone else with stumbling 9.01 wanna try it?

I claim no expertise, just pure dumb luck & following a hint that was offered.  It's booted that way three times in the last few minutes.  If it sticks, I'll TAKE IT:shock: - with gratitude to member "buckeyball"

ATB:biggrin:

BC

---

### Post by Bucky Ball on 2009-12-18
More than a pleasure. 8.04 LTS is still the current enterprise release. If you want stability (I need that) LTS is probably the way to go, for servers DEFINITELY recommended ....

FYI: 

8.04 = April 2008
9.04 = April 2009 
9.10 = October 2009

... etc.

---

