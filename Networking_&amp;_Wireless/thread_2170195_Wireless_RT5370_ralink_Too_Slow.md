---
title: "Wireless RT5370 ralink Too Slow"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by jhay2 on 2013-08-25
I have a problem in my wireless USB ralink rt5370 (CD-R king) , it seems that my wifi if i am connecting through usb it is too slow than connecting through wired connection (Android Tethering) 

Can you help me solve my problem ? 

my Ubuntu version is 12.04 LTS 

i am new in linux .So i dont have any idea on some of advance codes for terminal .. 

Sorry for my bad English , Thank you

---

### Post by kurt18947 on 2013-08-25
Hi

No need to apologize for your english, you're fine.  I have that device and could never get it to really work well until I installed the in-development 13.10.  I tried disabling hardware encryption & power management but those did not appear to make a difference.   It was always 'plug 'n' play' but the signal was a little weak and speeds were around 26 mb./sec on an N150 connection in wavemon.  Using 13.10 speeds are indicating 72 mb./sec or more consistently.  I don't know, perhaps enabling backports would help.  That adapter seems to be sensitive to position relative to the wireless access point.  If you have a USB 'extension', perhaps you could plug the adapter into that and try some different positions, or if plugged into a laptop try repositioning the laptop.  Sorry I don't have any guaranteed improvements.

---

### Post by jhay2 on 2013-08-26
Thanks for your reply sir , 



So it means upgrading ubuntu 12.04 to 13.10 may fix my problem sir?

---

### Post by kurt18947 on 2013-08-27
> **jhay2 said:**
> Thanks for your reply sir , 



So it means upgrading ubuntu 12.04 to 13.10 may fix my problem sir?

I'm not sure I'd do that just yet.  13.10 is a work in progress, it won't be released until October.  I'm using it but I also have a stable install of 12.04.3.  If 13.10 goes crazy, I can just wipe and reinstall it.  I don't count on development releases to be reliable.  I don't know about upgrading your kernel to 3. 11 to get the newest driver, I've never tried it but wouldn't be surprised if it damaged your install.  You could try a live CD/USB of 13.10 to see if your wifi is stronger using a live session.  That way you wouldn't be risking your current installation.

---

### Post by jhay2 on 2013-08-29
I see. maybe i will try to live boot 13.10 . and see if it will work . Thanks for your response sir . i will give a feedback once i try it ..

---

