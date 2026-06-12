---
title: "ATI 8.40.4 promised a lot but failed to work as promised for me"
date: 2007-08-15
forum: Multimedia &amp; Video
---

### Post by sdowney717 on 2007-08-15
I was using 8.39 and had google earth working. So I read that the 8.40.4 driver now allows you to log out and change users without the black screen of death. 

So I installed it using ENVY, and the screen still dies.

And, now I have no 3D rendering.

SO, how would I go back to the other driver?
[http://news.softpedia.com/news/ATI-AMD-8-40-4-Display-Driver-Released-62642.shtml](http://news.softpedia.com/news/ATI-AMD-8-40-4-Display-Driver-Released-62642.shtml)

" A black screen is no longer observed on some hardware when switching to the console or leaving the X window system when a Vesa framebuffer console driver is used."

yes, but still I get a black screen

DO I need to perhaps uninstall the old driver before installing the new one when using ENVY??

---

### Post by tseliot on 2007-08-15
> **sdowney717 said:**
> DO I need to perhaps uninstall the old driver before installing the new one when using ENVY??

You can try that way.

Then if it still doesn't work you can post both your /var/log/Xorg.0.log and your /var/log/envy-installer.log

---

### Post by sdowney717 on 2007-08-16
well, I uninstalled the new driver and reinstalled the new driver and it is working, except for google earth hangs at initializing. funny as it used to work fine.

The interesting thing is
When I uninstalled the ATI driver, it installed the mesa driver, and when I went to reboot, left me with a system that could not startx.

So, I loogged in to the console. I typed ENVY, ran the text based installer, reselcted the new driver 8.40.4, and when it rebooted it was working.
So, thanks for writing this program. I was kind of at a loss to know what to do and was pleased to see ENVY run like this.

---

### Post by maxrisc on 2007-08-16
When I was using 8.43.x I was getting ~20fps in WoW under Wine 0.9.42.

After updating to 8.40.4 I get less than 10fps outside! :-x

ATI should change their name to "ALL TEXT INTERFACE!!!"

F#$%#Ckers!

---

### Post by Neo4 on 2007-09-09
> **sdowney717 said:**
> well, I uninstalled the new driver and reinstalled the new driver and it is working, except for google earth hangs at initializing. funny as it used to work fine.

The interesting thing is
When I uninstalled the ATI driver, it installed the mesa driver, and when I went to reboot, left me with a system that could not startx.

So, I loogged in to the console. I typed ENVY, ran the text based installer, reselcted the new driver 8.40.4, and when it rebooted it was working.
So, thanks for writing this program. I was kind of at a loss to know what to do and was pleased to see ENVY run like this.

with the restricted driver manager I had direct render and I've installed the new one drivers and now I get mesa when I tipe fglrxinfo!

I try to do the same thing as you but had no success for me =( any one knows how to do that? =/

---

### Post by QOLIM on 2007-09-09
> **maxrisc said:**
> When I was using 8.43.x I was getting ~20fps in WoW under Wine 0.9.42.

After updating to 8.40.4 I get less than 10fps outside! :-x

ATI should change their name to "ALL TEXT INTERFACE!!!"

F#$%#Ckers!

Just stick with the old driver till 8.41 comes out
which will have +50% or more performance then the old drivers according to some brenchmarks

---

