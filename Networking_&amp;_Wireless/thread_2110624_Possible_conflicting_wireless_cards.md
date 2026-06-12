---
title: "Possible conflicting wireless cards"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by jack454 on 2013-01-30
Here's the problem. I have three laptops: HP G7 with broadcom 4313 (Ubuntu 12.04), HP Probook with broadcom 4313 (Mint 14), HP DV6000 with broadcom 4311 (Mint14). The G7 and DV6000 have no trouble. However the Probook is extremely slow on the internet, until I disconnect the G7. Then the probook connection works perfectly. The Probook and the G7 both have 4313 cards. I tried moving one to the other end of the house to see if it changed anything and it didn't. In the router they do have different IP addresses. Hope I explained this clearly because I could sure use some help to sort this out. Thanks. Almost forgot. All three are using bcmwl-kernel-source driver. AKA(wl.ko)

---

### Post by Warprunner on 2013-01-30
> **jack454 said:**
> Here's the problem. I have three laptops: HP G7 with broadcom 4313 (Ubuntu 12.04), HP Probook with broadcom 4313 (Mint 14), HP DV6000 with broadcom 4311 (Mint14). The G7 and DV6000 have no trouble. However the Probook is extremely slow on the internet, until I disconnect the G7. Then the probook connection works perfectly. The Probook and the G7 both have 4313 cards. I tried moving one to the other end of the house to see if it changed anything and it didn't. In the router they do have different IP addresses. Hope I explained this clearly because I could sure use some help to sort this out. Thanks. Almost forgot. All three are using bcmwl-kernel-source driver. AKA(wl.ko)

Off hand I would think you have a packet storm going on. The G7 might be flooding things? Go get Etherape or IPTraf and put it on the G7 machine. Then examine ...
One thing you didn't say mention is if the ethernet is hard connected and not wirelessly connected? When you do, is the problem still there?
Can you switch the wireless cards and see if the DV6000 then becomes the issue?

---

### Post by jack454 on 2013-01-30
All systems are using wireless. Haven't got a cable to try hard wiring, however I have tried a usb wireless on the G7 and everything works fine. The Probook connection is still Ok. Will have to try swapping the DV6000 and G7 cards. Thanks for the help so far.

---

### Post by Warprunner on 2013-01-30
Without sounding too premature... sounds like that G7 has a bad card but will await your troubleshooting.

---

### Post by jack454 on 2013-01-30
Well I can't swap wireless cards among these laptops because HP whitelists the hardware and if it isn't the exact part number you get an error on boot. (Unsupported wireless device detected system halt) Isn't that nice of them? I for got to say the problem just started yesterday. These units have been sitting a few feet apart and working fine for weeks. Is it possible for a router to cause this? Thanks

---

### Post by Warprunner on 2013-01-30
> **jack454 said:**
> Well I can't swap wireless cards among these laptops because HP whitelists the hardware and if it isn't the exact part number you get an error on boot. (Unsupported wireless device detected system halt) Isn't that nice of them? I for got to say the problem just started yesterday. These units have been sitting a few feet apart and working fine for weeks. Is it possible for a router to cause this? Thanks

Ok here is a long shot... go here to see your channel of the G7 machines card. 
[http://askubuntu.com/questions/56622/how-can-i-see-a-wireless-networks-frequency-and-or-channel](http://askubuntu.com/questions/56622/how-can-i-see-a-wireless-networks-frequency-and-or-channel)

Then go here to change it:
[http://ubuntuforums.org/showthread.php?t=1630584](http://ubuntuforums.org/showthread.php?t=1630584)

I think the default is Auto select and as I said this is a long shot. But maybe, just maybe, they are talking on the same channel and somehow getting confused? (Said it was a long shot.)

Still think the best thing is to get an ethernet cable. They usually come with every machine.

---

### Post by jack454 on 2013-01-30
They are both on channel 6 and neither will change. I truly do thank you for your help. Gonna keep plugging away and maybe I'll get lucky.

---

### Post by Warprunner on 2013-01-30
> **jack454 said:**
> They are both on channel 6 and neither will change. I truly do thank you for your help. Gonna keep plugging away and maybe I'll get lucky.

:( Ok, I am going to think about this tonight. I have two sons on the Air Force Base's Help Desk. Will ask them too.

If you do find a solution please post it here?

---

### Post by jack454 on 2013-01-30
If I stumble across anything I'll surely let you know. Thanks again for the help. Something I just noticed is when the G7's card is active none of the systems can see each other with samba.

---

### Post by jack454 on 2013-02-01
Looks like the problem was caused by a recent update. Finally noticed the ubuntu system (G7) was using a newer version of the driver. Uninstalled it and replaced with the older version. Now all systems can surf with no problem. The G7 (Ubuntu) can see and connect to both Mint machines, but they can't see it. The mint machines can connect to ubuntu if I use it't IP address. So I'm almost back where I was before the problem. Guess it will do. Thanks for the help Warprunner.

---

### Post by Warprunner on 2013-02-01
> **jack454 said:**
> Looks like the problem was caused by a recent update. Finally noticed the ubuntu system (G7) was using a newer version of the driver. Uninstalled it and replaced with the older version. Now all systems can surf with no problem. The G7 (Ubuntu) can see and connect to both Mint machines, but they can't see it. The mint machines can connect to ubuntu if I use it't IP address. So I'm almost back where I was before the problem. Guess it will do. Thanks for the help Warprunner.

Ahhhh ya schooled me!!! Hahahaahahah I deserve no credit... you did this all on your own. Thinking I will see your name helping others in Networking now???

Best of luck to ya!

---

