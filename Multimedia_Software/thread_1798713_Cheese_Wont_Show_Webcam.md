---
title: "Cheese Wont Show Webcam"
date: 2011-07-06
forum: Multimedia Software
---

### Post by CarlosinFL on 2011-07-06
For some reason Cheese works for the 1st time when I launch the application fresh but after I use it and I close the application, the next time I go to use it, it doesn't show any video from my web cam. I can see the web cam turn on and it activates the flash LED however I don't see any video. I reboot my Ubuntu PC and it works fine the next time but I have to always reboot my PC and it sucks. Anyone know what could fix this problem?

---

### Post by CarlosinFL on 2011-08-10
Anyone? I don't understand why when I launch cheese a 2nd time it fails to show / display my monitor webcam. I have to reboot my entire system for it to work / display the USB web cam in my LCD. What causes this?

---

### Post by no2498 on 2011-08-11
try these programs guvcview and wxcam
guvcview is in your repose 

you can get wxcam in a deb file if you look at all files

[http://sourceforge.net/projects/wxcam/](http://sourceforge.net/projects/wxcam/)

---

### Post by cheapodonuts on 2011-08-29
> **CarlosinFL said:**
> Anyone? I don't understand why when I launch cheese a 2nd time it fails to show / display my monitor webcam. I have to reboot my entire system for it to work / display the USB web cam in my LCD. What causes this?

I know it's not ideal, but try 'unplug and replug' your webcam, before starting Cheese, it's less annoying than rebooting and it works for me. It's still a problem though. Plus, I can't view any resolution higher than 600x480 even though my webcam is HD enabled.

---

### Post by MarjaE on 2011-08-29
> **cheapodonuts said:**
> I know it's not ideal, but try 'unplug and replug' your webcam, before starting Cheese, it's less annoying than rebooting and it works for me. It's still a problem though. Plus, I can't view any resolution higher than 600x480 even though my webcam is HD enabled.

I have the same problem with Camorama. How do I unplug and replug the built-in webcam?

---

### Post by no2498 on 2011-08-30
try this in a terminal type
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so Camorama click enter

---

