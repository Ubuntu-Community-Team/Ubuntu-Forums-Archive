---
title: "Ubuntu/Kubuntu Maverick RC Only Boots to Recovery Mode on Acer Aspire 4741z"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by karmila on 2010-10-06
It has 
Prosesor: Intel Pentium P6000 (1.86 GHz, L2 cache 3 MB) and
VGA: Intel HD graphics
 
How to know the cause of this problem?
 
At live mode and installation everything seems fine and running smoothly just until reboot...

---

### Post by cariboo on 2010-10-06
Is it actually booting to recovery mode, or to a console? You can tell, by noting whether it boots to a root prompt or you have to log in as a regular user.

---

### Post by karmila on 2010-10-06
> **cariboo907 said:**
> Is it actually booting to recovery mode, or to a console? You can tell, by noting whether it boots to a root prompt or you have to log in as a regular user.

I have to log in as a regular user. I chose normal boot but it looks like boot at recovery mode, is it a console? 

If I type *sudo service gdm start*, it says "process is already running" and then followed by blank screen and I have to push the power button for shutdown.

---

### Post by robert shearer on 2010-10-06
Can't help with your primary problem (there will be another bus along in a minute :) )
 
However...
For future reference, powering off/hard reset risks file corruption.

Here is a link to the right way to exit a freeze.

[http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/](http://www.arsgeek.com/2006/12/12/how-to-gracefully-reboot-your-ubuntudebian-system-if-all-else-fails/)

The commands put the keyboard into raw mode and allow file syncing and safe controlled reboot.
Worth writing down.

(sometimes you have to repeat the sequence to allow time for complete file syncing and it pays to go slow, 1 second pause between key sequences.)

---

### Post by cariboo on 2010-10-06
Type startx at the prompt, and note what the output on screen is.

---

### Post by karmila on 2010-10-06
Thanks for the tip.

I love that mnemonic "Raising Skinny Elephant Is Utterly Boring" lol :P

I had an experience before that hard reset made grub log in to busybox and my only options was to delete ubuntu partition with fedora live cd. Why Fedora? Because even from Ubuntu live cd i couldn't touch root partition. It always mounted.

------

OK, I'll wait for next bus so I can get home to my new build ubuntu :)

---

### Post by karmila on 2010-10-06
> **cariboo907 said:**
> Type startx at the prompt, and note what the output on screen is.

My notebook instantly goes to blank/black screen just after i type startx.

Then I hold Alt+SysRq+k buttons to kill processes and then Ctrl+Alt+Del to reboot.

Before reboot I got this message on the screen: "**init: failsave-x main process (1483)**"

---

### Post by karmila on 2010-10-08
Still happen with today's daily build iso installer.

---

### Post by karmila on 2010-10-08
I think the problem is i915 driver related. Read some bugs about it on launchpad.

---

### Post by karmila on 2010-10-08
I've found a fix. Installing kernel mainline v2.6.35-rc5-maverick and I can boot to x now. So far no issue found.

:guitar:

---

### Post by Catharsis on 2010-10-08
Can you link to your bug report on Launchpad? If you haven't filed one yet, run:
```
ubuntu-bug xserver-xorg-video-intel
```

---

### Post by karmila on 2010-10-08
> **Catharsis said:**
> Can you link to your bug report on Launchpad? If you haven't filed one yet, run:
```
ubuntu-bug xserver-xorg-video-intel
```

I haven't filed bug yet, but my notebook's bug similar with this report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)

Should I report new bug?

---

### Post by Catharsis on 2010-10-08
> **karmila said:**
> I haven't filed bug yet, but my notebook's bug similar with this report:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453)

Should I report new bug?

Do you have an E6510? If so, then yes, you can just follow that bug report. If not, you'll have to file a new one.

---

### Post by karmila on 2010-10-08
> **Catharsis said:**
> Do you have an E6510? If so, then yes, you can just follow that bug report. If not, you'll have to file a new one.

Ok, I'll file new report as soon as I'm on my Acer 

Thanks :smile:

---

