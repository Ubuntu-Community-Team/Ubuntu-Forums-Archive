---
title: "added new card, won't boot"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by SC2Sick on 2006-09-14
I recently added a new card.  It's a Chaintech MX420 PCI based.  adding this to an HP system w/ 766 celeron and 512MB RAM .  In any case I had it working fine with the onboard video, but wanted 3D so I can CS from this box as well or have others do it.

I run through the full boot just before it's going to the login screen and it hangs with an _ in the upper left hand corner.

I tried swapping the cable to the onboard to see if it defaulted back and it didn't.

Tried the rescue disk and got lost.

Distro: Ubuntu 6.06 installed be alternate install disk text mode.

---

### Post by xmastree on 2006-09-14
My guess is your xorg.conf is trying to load the driver for the onboard. edit it, change the driver to vesa.

---

### Post by SC2Sick on 2006-09-14
please educate me on the matter.  how would i do that from a recovery console.

---

### Post by xmastree on 2006-09-14
Sorry, I assumed a deeper knowledge.

Right, first thing is to get to a terminal. This is usually done with Ctrl-Alt-F1
Once there you can login as usual.

Rather than editing the file, it's probably better to let the system figure it out itself.

(I copied this next bit from a different thread...):rolleyes: 

Make a backup of xorg.conf with this command:
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup**
and then try to reconfigure with this command:
**sudo dpkg-reconfigure xserver-xorg**
You can just hit enter for any questions you don't know the answer to, to take the default.
then **startx** and see if it starts.

---

### Post by SC2Sick on 2006-09-14
i can't seem to find xorg.conf...

if i can't get it easily, i'll just reinstall tonight from scratch i supposed.  i'd rather not though.  d/ling steam took a while.

---

### Post by xmastree on 2006-09-14
You can do the reconfiguring thing without first backing up the file, since it doesn't work anyway there's nothing to lose.

---

### Post by SC2Sick on 2006-09-14
Tried that, no success because i couldn't find any driver to work.

Gonna reinstall, thx for the assistance though..  maybe it will assist somebody else.

---

### Post by xmastree on 2006-09-14
FWIW, nVidia are the best supported with linux. I'm not sure about yours, but if it's new you might be able to exchange it.

---

### Post by SC2Sick on 2006-09-14
actually it is an nvidia card.  i reinstalled.  no luck.  so i removed the card and i'm installing the drivers via easyubuntu.  i'm gonna reboot again in a second and try the card again.

---

### Post by SC2Sick on 2006-09-14
i'm kind of upset now.  I read some of the FAQs after doing a full reinstall...

how i fixed it was i booted the sytem and hit 'esc' during grub bootup, i selected the repair console kernel

i don't know if this step was necessary, but from command line i did

```
(sudo) apt-get install linux-686
```

then rebooted
then booted the same way and
```

(sudo) apt-get install nvidia-glx nvidia-kernel-common linux-restricted-modules-2.6.15-26-686
```

only to find i already had the most recent packages

so i did 

```
(sudo) nvidia-xconfig
```

and it did the rest and i rebooted.

then it worked.

---

### Post by xmastree on 2006-09-15
Well done! Glad to hear it.

Why upset? Because you did a reinstall? Oh well, you're wiser now. 8)

---

