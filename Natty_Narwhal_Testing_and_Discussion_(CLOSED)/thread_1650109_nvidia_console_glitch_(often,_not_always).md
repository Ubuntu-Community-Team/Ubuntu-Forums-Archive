---
title: "nvidia console glitch (often, not always)"
date: 2010-12-21
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by efflandt on 2010-12-21
I often (not always) have a problem with natty text (tty) consoles (nvidia-current 260.19.21), where instead of login starting in upper left, it ends up lower right, a little above 3 lines from the bottom.  I am using a 1080p display with HDMI (X is 1920x1080), but text consoles are 80x30, so I believe they are 1024x768.  So they end up like this at the bottom of the screen

```
                                                  ubuntu natty (development branch
) natty-ssd tty1
                                                  natty-ssd login:
```and then just the very top edge of password prompt. It does not scroll up (probably because it thinks it has not filled 30 rows yet) so any commands have to be done blind, unless you **clear** to bring current prompt up to the ubuntu natty position.  **stty sane** does NOT fix it.

Occasionally everything starts in upper left where it should be, and (recovery) consoles are always fine.

It has been an ongoing issue with natty, just not sure what causes it or how to report it. Any idea how to fix the consoles when they glitch like that?

---

### Post by lucazade on 2010-12-21
same issue here with nvidia-current, a 250gts card and a 1080p display DVI.
it happens random, haven't found a solution yet.
i believe we should open a bug if there is not.

---

### Post by dino99 on 2010-12-21
have you run startup-manager ?

---

### Post by lucazade on 2010-12-21
> **dino99 said:**
> have you run startup-manager ?

to fix grub and tty resolution?

---

### Post by efflandt on 2010-12-21
How would startupmanager help.  I have no trouble with grub menu or booting.  The issue is only with text consoles (ie, Ctrl+Alt+F1 through F6) while X is running.  For some reason it thinks the top of the screen is column 51, approximately row 28 (of 80x30 display).

Thinking maybe it was a plymouth issue, I tried booting without **quiet splash** and that was weird.  The purple background of the grub menu goes solid purple, then only about 10 lines of invisible text (black text and background) on the purple background, then gui login.  But at least the text consoles (tty's) are normal, this time.

---

### Post by lucazade on 2010-12-21
> **efflandt said:**
> How would startupmanager help.  I have no trouble with grub menu or booting.  The issue is only with text consoles (ie, Ctrl+Alt+F1 through F6) while X is running.  For some reason it thinks the top of the screen is column 51, approximately row 28 (of 80x30 display).

Thinking maybe it was a plymouth issue, I tried booting without **quiet splash** and that was weird.  The purple background of the grub menu goes solid purple, then only about 10 lines of invisible text (black text and background) on the purple background, then gui login.  But at least the text consoles (tty's) are normal, this time.

I've tried with fbgrab to take a screenshot of tty1.
Unfortunately resulting pic (640x480) looks "good" so not so useful to attach it to a bug report! :)

---

### Post by dino99 on 2010-12-21
Open a terminal and type "cp /etc/skel/.bashrc ~" to overwrite
your .bashrc with the default version.

---

### Post by lucazade on 2010-12-21
> **dino99 said:**
> Open a terminal and type "cp /etc/skel/.bashrc ~" to overwrite
your .bashrc with the default version.

two .bashrc files are identical (checked with meld)

using nouveau driver this issue is not present, so it could be related to nvidia-current and latest changes to grub (like gfxpayload=keep without a KMS driver) i believe.

---

### Post by lucazade on 2010-12-21
attached a screenshot made with a camera

---

### Post by dino99 on 2010-12-21
ubuntu have uploaded a new package: grub-gfxpayload-lists

" The 'set gfxpayload=keep' facility in GRUB provides smooth graphical
handover to the Linux kernel.  Unfortunately, this does not work on all
systems, resulting in a black or corrupt display.  This package provides a
blacklist of PCI IDs which fail.

We maintain this separately from GRUB because it is likely to be updated on
a different schedule. "

i dont have made tweaks with it yet, but looking at your screenshot, i'm thinking about some "tab" spaces inserted into bashrc (might look at source)

---

### Post by lucazade on 2010-12-21
> **dino99 said:**
> ubuntu have uploaded a new package: grub-gfxpayload-lists

" The 'set gfxpayload=keep' facility in GRUB provides smooth graphical
handover to the Linux kernel.  Unfortunately, this does not work on all
systems, resulting in a black or corrupt display.  This package provides a
blacklist of PCI IDs which fail.

We maintain this separately from GRUB because it is likely to be updated on
a different schedule. "

i dont have made tweaks with it yet, but looking at your screenshot, i'm thinking about some "tab" spaces inserted into bashrc (might look at source)

Installed grub-gfxpayload-lists and it fixed tty position! :)

Unfortunately it also set plymouth to text-mode (no ubuntu logo) and when I switch back to X i get a corrupted/artefacted display under Unity.

---

### Post by dino99 on 2010-12-21
hm i've not so much more idea :(

sudo dpkg-reconfigure -phigh -a

---

### Post by Harry33 on 2010-12-21
> **lucazade said:**
> Installed grub-gfxpayload-lists and it fixed tty position! :)

Unfortunately it also set plymouth to text-mode (no ubuntu logo) and when I switch back to X i get a corrupted/artefacted display under Unity.

Yes this is exactly what it is meant to do.
To disable "gfxpayload=keep".
This is an unfortunate consequence , but inevitable. While it is true that some graphics cards do not boot when gfxpayload is set to keep.

---

### Post by lucazade on 2010-12-21
> **Harry33 said:**
> Yes this is exactly what it is meant to do.
To disable "gfxpayload=keep".
This is an unfortunate consequence , but inevitable. While it is true that some graphics cards do not boot when gfxpayload is set to keep.

What i'm wondering is why plymouth is not disabled for these blacklisted pci or why is not used v86d/uvesafb to fix these kind of issues.
I hope nvidia-blob users will get an upstream fix for not kms-drivers in natty.

---

### Post by Harry33 on 2010-12-21
> **lucazade said:**
> What i'm wondering is why plymouth is not disabled for these blacklisted pci or why is not used v86d/uvesafb to fix these kind of issues.
I hope nvidia-blob users will get an upstream fix for not kms-drivers in natty.

Yes it seems Canonical likes Plymouth a lot.
The recent updates have made it ugly, though (antialiasing is missing).

---

### Post by cariboo on 2010-12-21
If you go back and watch Mark Shuttleworth's UDS-N keynote speech, you'll hear that they are going to make plymouth work with all graphics cards. I wouldn't fret to much about what things look like yet, at this point, as the artwork usually doesn't show up until the beta release.

---

### Post by lucazade on 2010-12-21
> **cariboo907 said:**
> If you go back and watch Mark Shuttleworth's UDS-N keynote speech, you'll hear that they are going to make plymouth work with all graphics cards. I wouldn't fret to much about what things look like yet, at this point, as the artwork usually doesn't show up until the beta release.

I've read the blueprint about boot process refinement for natty
[https://blueprints.launchpad.net/ubuntu/+spec/packageselection-foundations-n-grub2-boot-framebuffer](https://blueprints.launchpad.net/ubuntu/+spec/packageselection-foundations-n-grub2-boot-framebuffer)
I hope this will be fixed for natty release because to date i'm missing old usplash!

---

