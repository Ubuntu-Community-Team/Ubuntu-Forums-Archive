---
title: "Ubuntu 8.10 manual networking settings"
date: 2008-12-29
forum: Networking &amp; Wireless
---

### Post by varun_saa on 2008-12-29
Hello,

I have installed Ubuntu 8.10.

I have set network settings as 192.168.0.1 - eth0.

When I reboot I have two settings eth0 & auto-eth0 Why ??

How to stop this auto-eth0 ?

Thanks

Varun

---

### Post by kevdog on 2008-12-29
I don't follow -- where are these settings?

---

### Post by Bölvaður on 2008-12-29
hmm I also would want to know this.


This seems to be a new bug in *NetworkManager Applet 0.7.0*. When you make new connection under *wired* and delete the auto one, you are connected to your settings... ok all good now.
But when you restart the computer NetworkManager adds that auto one back in and sets it as default so you have to switch back to your settings.

*added*

uh apparently this is horrifyingly easy. When you make new connection make sure you have the MAC address filled out correctly (copy it from the auto eth0) and fill in the ticks to Connect automatically and perhaps also System setting. Works well for me.

---

### Post by OldTimeTech on 2008-12-29
Yes and many messages on Launchpad about the problem...there is no "fix" for it as yet, except what you have found.

Unfortunately my computer wouldn't allow me to save the "added" and so I've reverted back to 8.04 and now I can get back to the internet without all the hassle.

Ever since I started with Ubuntu, I've never had the problems that I had today trying to install or upgrade Ubuntu.

Hope they fix the problem Soon!!!

---

### Post by varun_saa on 2008-12-30
Thanks a lot 

Varun

---

### Post by Gizmo69 on 2009-01-02
> **Bölvaður said:**
> hmm I also would want to know this.


This seems to be a new bug in *NetworkManager Applet 0.7.0*. When you make new connection under *wired* and delete the auto one, you are connected to your settings... ok all good now.
But when you restart the computer NetworkManager adds that auto one back in and sets it as default so you have to switch back to your settings.

*added*

uh apparently this is horrifyingly easy. When you make new connection make sure you have the MAC address filled out correctly (copy it from the auto eth0) and fill in the ticks to Connect automatically and perhaps also System setting. Works well for me.
Thanks Bölvaður, This works for me.

Making only a new connection, didn't work. Deleting auto-eth0 and rebooting works!
:-D

---

### Post by wamorita on 2009-01-02
I am assuming you created a new "manual" set of settings.
If you look at the setup for both the "auto" and your new settings, you file find a check box labeled "system setting".
If you uncheck this in the "auto" setting and check it in the new settings, the new setting will be what takes effect.

The way they did is is dumb, in that if the "system setting' is checked in multiple settings, no change occurs.  Once you uncheck in the "auto" settings, it will go to the end of the list of setting and your new setting will be used on the next reboot.

---

