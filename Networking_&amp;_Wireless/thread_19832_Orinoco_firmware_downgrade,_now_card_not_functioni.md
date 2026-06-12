---
title: "Orinoco firmware downgrade, now card not functioning"
date: 2005-03-13
forum: Networking &amp; Wireless
---

### Post by mcleod9 on 2005-03-13
This is my first post to the forums :) With the end goal of getting monitor mode working with Kismet, I've downgraded the firmware to 6.16 on this Orinoco Gold card. Originally, it had worked out of the box with Ubuntu Warty 4.1. 

Now the card doesn't work. I downloaded and installed the correct kernel-headers and build-essential (from the CD), as mentioned elsewhere. Also, the most recent Orinoco driver 0.15rc2 installed correctly. 

The output of dmesg is [this](http://threespeed.org/~ibm/dmesg_screenshot.jpg) (I can only take a photo and post it, as the laptop isn't online  :???: .

In Network Setting, I activate the card, but the checkbox becomes unchecked after a few seconds.  Also, the two lights on the card itself flash both simultaneously and intermittently. 

Doing 'iwconfig eth1 mode monitor' sets the card to monitor mode, but I'm not online anyway so it doesn't matter much. 

Doing 'ifconfig eth1 down' actually brings the light that indicates the card is detected on steady. 'iconfig eth1 up' causes the lights to start blinking simultaneously and about every 10 seconds. 

If anyone has any thoughts on the matter, they would be much appreciated.

---

### Post by Kemotaha on 2005-03-13
This sounds Vagualy familar since I have an Orinoco Gold card and had the same problem a while ago.  I was playing with the firmware and don't remember which I settled on.  I don't have the monitor mode working under Ubuntu.  But it works under Knoppix STD 0.1 which I just boot into to do anything like that.  

If I remember right it was the 7.xx firmware that gave problems with Linux.  It was fixed with 8.xx that I remember was a pain to find.  I will check tomorrow if I still have it on my laptop.  I will also let you know what firmware version is on my card.

---

### Post by mcleod9 on 2005-03-13
The card had the 8.72 firmware installed originally and worked fine. I downgraded to 6.16 because monitor mode is disabled in the 7.x and 8.x firmwares, but not in the 6.x versions.

---

### Post by Kemotaha on 2005-03-13
I have a 8.xx firware installed, or atleast I am almost positive.  I don't think it is the 8.72 though.  I will check tomorrow and let you know

---

### Post by wernst on 2005-03-14
How, how do you check the version number of the Orinoco firmware? I played around with it YEARS ago and don't remember what I have now.

Whatever I have works in Monitor mode and XP just fine though...

-Warr

---

### Post by Kemotaha on 2005-03-15
To check run "dmesg" after you insert the card and it shoudl tell you.

I have the 8.10 firmware on my card and I can do the monitor mode just fine.  

I hope that helps you so you can use it for both purposes.

---

