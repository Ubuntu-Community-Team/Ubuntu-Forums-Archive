---
title: "Embarassing sound problem"
date: 2008-02-14
forum: Multimedia &amp; Video
---

### Post by merinette on 2008-02-14
Sigh. Anybody wanna play "Help Me Figure Out What My Buddy Did To My Box"? :oops:

I'm on a Lenovo Thinkpad T60 with Kubuntu Gutsy; everything worked right out of the box, all of my chips are Intel and natively supported. I've been running Kubuntu single-boot for more than a year and updated to Gutsy about a month ago with no problems. Then I left someone alone with my computer...

I guess I should mention that my wireless stopped working at the same time that the sound stopped working, in case that means something. I restored wireless functionality by reinstalling Madwifi, but I don't understand what is happening when I try to install my ALSA drivers (or why they disappeared in the first place). If anyone can tell me where to go from here, it would be greatly appreciated. 

I [think I] followed [help.ubuntu.com Sound Troubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") ... and yes, I am 100% certain my sound is ON and the volume is up. 

```

merinette@twylo:~$ aplay -l
aplay: device_list:204: no soundcards found...
```

```

merinette@twylo:~$ lspci -v
# 
# Tidied up:
#
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Lenovo ThinkPad T60/R60 series
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at ee240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

According to alsa-project.org, my AD198x audio controller uses driver intel8x0, which I selected when I ran:  
```

merinette@:~$ sudo dpkg-reconfigure alsa-source

```
& I guess that went normally, but the output of this...
```

merinette@twylo:~$ sudo modprobe snd-intel8x0
merinette@twylo:~$ 

```
...is nothing. Still no sound... and now I'm stuck. I can get proper output from ' aplay -l ' when I boot from my oldest kernel (as well as play .oggs in Amarok) but I can't get any sort of internet or networking on that kernel. 

Hopefully I am simply overlooking something obvious. Any/all suggestions welcome.

---

### Post by xc3RnbFO8P on 2008-02-15
Make a fresh install if you can, backup all the things you wan to keep (mostly in homefolder).
Then install Ubuntu (not Kubuntu, it is very easy to break).

---

### Post by merinette on 2008-02-15
Awwww. I was hoping someone could think of something *else* I didn't do, besides "re-install". :)

---

### Post by AlanR8 on 2008-02-15
Ringi wasn't suggesting a re-install, he was suggesting you install Ubuntu. He said Kubuntu was easy to beak!

Not my experience with over a year on Kubuntu........

However, a re-install of KUBUNTU will probably solve your problem, unless you've go a hard ware failure.

---

