---
title: "NVIDIA FX5500 updrade issues"
date: 2006-07-09
forum: Multimedia &amp; Video
---

### Post by solracarevir on 2006-07-09
Hi everyone!

   I had installed on my desktop computer a spare FX5500 graphics card(used to have intel integrated) and it messed up my Suse 10.1 system ( My brother is the main user of the desktop and he likes it,that's the main reason, i have ubuntu in my laptop) So that was the perfect time to install ubuntu on my desktop too!!!!! But my brother insist on re-intalling SuSE, but the SuSe intallation keep failing. the i tried to install ubuntu, but when i tried to load the livecd/intallcd (ubuntu 6.06) It wont boot!!! i tried with another install cd ( i have the shipped cd's) and it fails also. So here is my question: do you know of any issue with the Fx5500 that make both, SuSE 10.1 and Ubuntu unable to install?? My brother is taking his first steps into linux and i want to make things as easy as posible for him, cause he is a windows lover and i had a very hard time trying to convince him to use linux.. ANY Help??????

---

### Post by tseliot on 2006-07-09
Please follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by solracarevir on 2006-07-09
Thanks i will try it right know... in a minutes i will let you know the results...

---

### Post by solracarevir on 2006-07-09
nope... not wrking... tried to boot in recovery mode but i receive the following error:

```
[4294689.907000] <0> Kernel panic - not syncing: Attempted to kill init!
```


Any Idea?

---

### Post by tseliot on 2006-07-09
> **solracarevir said:**
> nope... not wrking... tried to boot in recovery mode but i receive the following error:

```
[4294689.907000] <0> Kernel panic - not syncing: Attempted to kill init!
```


Any Idea?
Are you sure that the graphic card (or some other device) is not damaged?

---

### Post by solracarevir on 2006-07-09
All my hardware is ok linux was working ok until I upgraded the video card.
... I had dual boot (windows xp) and it works great on windows so the fx5500 is not damaged....
now i tried to install ubuntu 5.10. The instalation finished successfully but after reboot, the same problem. Starting in normal mode it hangs during the hotplug, starting in "safe mode" i had a kernel panic. I will try removing the video card and installing ubuntu using the integrated video...

---

### Post by tseliot on 2006-07-09
> **solracarevir said:**
> All my hardware is ok linux was working ok until I upgraded the video card.
... I had dual boot (windows xp) and it works great on windows so the fx5500 is not damaged....
now i tried to install ubuntu 5.10. The instalation finished successfully but after reboot, the same problem. Starting in normal mode it hangs during the hotplug, starting in "safe mode" i had a kernel panic. I will try removing the video card and installing ubuntu using the integrated video...
If that doesn't solve the problem check the RAM (in case you have a bad module) (even if it works in Windows)

---

