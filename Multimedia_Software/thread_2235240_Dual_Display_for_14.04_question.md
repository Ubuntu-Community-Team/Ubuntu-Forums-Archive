---
title: "Dual Display for 14.04 question"
date: 2014-07-19
forum: Multimedia Software
---

### Post by riverguy99 on 2014-07-19
I would like to upgrade from 12.04 to 14.04 and keep this setup: Dell D620 laptop docked to a 22" (HP2207) display, so that the laptop is an extension of the HP (primary) display.  It works fine with 12.04.  What do I need to know to make this same setup work with 14.04? It was easy to set this up from within the System Settings GUI in 12.04.  From what I can find on the Forum so far, this functionality has mysteriously not made it through to 14.04.  Any help here would be appreciated, as I can't proceed with this upgrade without knowing I can use my dual displays.

Thank you!

---

### Post by ubudog on 2014-07-21
I haven't had any problems on 14.04 with dual displays myself, but I might suggest you boot up a Live CD/USB disk and see if it works before you do the upgrade.

---

### Post by kostkon on 2014-07-21
> **riverguy99 said:**
> From what I can find on the Forum so far, this functionality has mysteriously not made it through to 14.04.
Where did you read that? Display settings have improved in 14.04, not regressed.

---

### Post by riverguy99 on 2014-07-22
> **kostkon said:**
> Where did you read that? Display settings have improved in 14.04, not regressed.

On this Forum, and below is another one from a different forum with a specific "fix."  This post also suggests that the issue is one specific to 14.04 that was not there in 12.04.  I set up my dual displays in 12.04 right from the "Displays" GUI, but had to disable "3D" to make it work.  Maybe I should just get real brave and go ahead with the 14.04 install . . . I just didn't want to spend hours on a fix since my 12.04 is woking fine!

[http://bernaerts.dyndns.org/linux/74-ubuntu/309-ubuntu-dual-display-monitor-position-lost](http://bernaerts.dyndns.org/linux/74-ubuntu/309-ubuntu-dual-display-monitor-position-lost)

---

### Post by Bucky Ball on 2014-07-22
*Thread moved to **Multimedia & Video***

How are you doing it now? Did you just plug it in and it worked or did you need to tweak? If the latter, check your tweaks and write them down. Duplicate in 14.04 LTS, if it doesn't 'just work'.

As mentioned, boot a Live DVD/USB and see what happens. Better still, install on another partition and troubleshoot there in a new thread.

---

### Post by riverguy99 on 2014-07-22
> **Bucky Ball said:**
> *Thread moved to **Multimedia & Video***

How are you doing it now? Did you just plug it in and it worked or did you need to tweak? If the latter, check your tweaks and write them down. Duplicate in 14.04 LTS, if it doesn't 'just work'.

As mentioned, boot a Live DVD/USB and see what happens. Better still, install on another partition and troubleshoot there in a new thread.

With my 12.04 setup (Dell D620 laptop docked to an HP 2207 Display), I first tried setting it up in the Settings --> Displays GUI.  Didn't work, so I got on the Forum and after many complcated Terminal-entry suggestions, somebody offered this: Log out.  In the resulting "Password" box, click on the small Ubuntu logo in the upper right corner.  You will then get a choice of "Ubuntu" or "Ubuntu 2D."  Click "Ubuntu 2D."  After I did that, it all just worked as it was supposed to.

The only downside to using "2D" is that the slider to resize the screen icons had vanished.  Small price to pay, for me.

So I have another laptop with 14.04 running on it (no external display), and when I try the log-out thing, that little "Ubuntu" logo is no longer there.

Why would they change something that worked?  Don't lots of folks use multible displays?

Thank you for your help with this!

---

### Post by riverguy99 on 2014-09-24
Well, thank you all for your assistance.  I finally decided that since 12.04 worked flawlessly in every respect and 14.04 has been nothing but one hassle after another, I dod a new clean install of 12.04 and everything just worked as intended.  Every driver, my printers, my dual displays, all configured themselves during install and worked right out of the chute.  YES!!!

---

### Post by Bucky Ball on 2014-09-27
Great to hear. Even though I use 14.04 LTS as my main squeeze now, there are sometimes some weird issues with dual monitors (one serious one recently which I won't go into here). 12.04 LTS is rock solid and I don't have the same issues in that, either. Supported til 2017 so not a bad choice, not by a long shot. Good luck. ;)

---

