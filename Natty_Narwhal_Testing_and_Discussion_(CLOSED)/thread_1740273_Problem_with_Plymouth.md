---
title: "Problem with Plymouth"
date: 2011-04-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aljazek on 2011-04-26
I upgraded fresh install ubuntu 10.10 to 11.04 with "update-manager -d" and now I have some problems with plymouth. I use just ubuntu and not dual boot. So when I restart or turn on my computer, I don't get the usual ubuntu logo with moving dots but blank screen and few glitches (some green colour appears). And just before login screen that ubuntu logo with dots appears for a second. I tried re-installing plymouth but it doesn't help. Any idea?

---

### Post by ranch hand on 2011-04-26
Edit /etc/default/grub so that your instruction string does not include "splash".  This will not get you your plymouth boot eyecandy but it will stop that from messing with your box.  Remember to run update-grub so that the new change will be generated in your /boot/grub/grub.cfg file.

---

### Post by Harry33 on 2011-04-27
> **aljazek said:**
> I upgraded fresh install ubuntu 10.10 to 11.04 with "update-manager -d" and now I have some problems with plymouth. I use just ubuntu and not dual boot. So when I restart or turn on my computer, I don't get the usual ubuntu logo with moving dots but blank screen and few glitches (some green colour appears). And just before login screen that ubuntu logo with dots appears for a second. I tried re-installing plymouth but it doesn't help. Any idea?

What is you graphics card model and what drivers are you using?

---

### Post by aljazek on 2011-04-27
I am using ATI Mobility X1600 with Xorg drivers. Yes, problem is probably with graphic card (drivers), because I also had some problems with displaying icons in dash (now fixed)([http://ubuntuforums.org/showthread.php?t=1719647](http://ubuntuforums.org/showthread.php?t=1719647)).

EDIT: and removing splash doesn't help

---

### Post by Harry33 on 2011-04-27
> **aljazek said:**
> I am using ATI Mobility X1600 with Xorg drivers. Yes, problem is probably with graphic card (drivers), because I also had some problems with displaying icons in dash (now fixed)([http://ubuntuforums.org/showthread.php?t=1719647](http://ubuntuforums.org/showthread.php?t=1719647)).

EDIT: and removing splash doesn't help

Removing splash just removes the plymouth screen during boot process revealing a few lines of text.

But back to your issue.
Ati graphics cards (also the newer HD series cards) do have a known issue with the visibility of Plymouth.
Often Plymouth is seen only a second or so, otherwise the screen is black.
You see this even though you use open source drivers (xserver-xorg-video-ati).

---

### Post by aljazek on 2011-04-27
Hmm, what else I can do? What if I remove plymouth, will I still get that login screen where I type my account name and password?

---

### Post by Harry33 on 2011-04-27
> **aljazek said:**
> Hmm, what else I can do? What if I remove plymouth, will I still get that login screen where I type my account name and password?

Actually then you would do exactly as Ranch Hand adviced:
remove the work splash from the file /etc/default/grub
then run this in terminal
```
sudo update-grub
```
then reboot

You cannot uninstall Plymouth though, the package mountall depends on it (plymouth, libplymouth2).
You may of course uninstall the Plymouth theme (plymouth-theme-ubuntu-logo).

And yes, this does not affect gdm (login screen) in any way.

---

### Post by lucazade on 2011-04-27
> **Harry33 said:**
> Actually then you would do exactly as Ranch Hand adviced:
remove the work splash from the file /etc/default/grub
then run this in terminal
```
sudo update-grub
```
then reboot

You cannot uninstall Plymouth though, the package mountall depends on it (plymouth, libplymouth2).
You may of course uninstall the Plymouth theme (plymouth-theme-ubuntu-logo).

And yes, this does not affect gdm (login screen) in any way.

Plymouth can also be disabled from init scripts!

sudo mv /etc/init/plymouth.conf /etc/init/plymouth.conf.disabled

---

### Post by aljazek on 2011-04-27
Yeah, removing plymouth doesn't solve anything...the glitch with blue or green rectangle is still there.

---

### Post by Harry33 on 2011-04-27
> **aljazek said:**
> Yeah, removing plymouth doesn't solve anything...the glitch with blue or green rectangle is still there.

Those odd glitches are not made by Plymouth, they are there because of graphics drivers, mesa and kernel modules.
You just have to accept the fact that there still are issues with the open source drivers and this leaves some work for the future too.
Like I said already, even newer ATI Graphics Cards have these issues.

---

