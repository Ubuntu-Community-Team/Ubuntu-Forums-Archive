---
title: "Sound works or doesn't work at random"
date: 2007-02-02
forum: Multimedia &amp; Video
---

### Post by goofdawg on 2007-02-02
Rather mysterious problem: My sound either works or does not work right from startup - I can tell by whether or not the Ubuntu startup noise gets played. Restarting fixes it, but it continues to happen every 4th or 5th boot.

My motherboard has onboard sound but it's disabled and I use a card from the Sound Blaster Audigy Value family.

When the sound works at boot, it continues working without issue. Yes, I checked the sound levels :) .

Any help is really appreciated.

---

### Post by sgx on 2007-02-03
> **goofdawg said:**
> Rather mysterious problem: My sound either works or does not work right from startup - I can tell by whether or not the Ubuntu startup noise gets played. Restarting fixes it, but it continues to happen every 4th or 5th boot.

My motherboard has onboard sound but it's disabled and I use a card from the Sound Blaster Audigy Value family.

When the sound works at boot, it continues working without issue. Yes, I checked the sound levels :) .

Any help is really appreciated.
I would try to end all sessions identically, removing CDs, shut down any system sound generators and screensavers (by default, preferably) and closing all running apps first, and then finally with root issuing the
halt -p
command... then see if sound starts or fails in a consistant reproducable way keeping  a chart. Note if the computer was off overnight, or many hours, as compared to reboots. If you are consistant, and sound is not, try re-seating all your pci cards, and related cables, with power unplugged, and in a static-shock free environment, and if it is still flaky, get in the bios, and shut off acpi, networking, power management, anything not directly sound, that might be a bully in the line, to cause a problem...check gooogle for signs your particular motherboard/chipset is a flearidden dog, same for your particular soundcard, and replace something if need be. Linux is backwards from windoze, you must buy the (limited, though quality)hardware that works with your OS, not an OS that works with monopoly-controlled hardware, and not like a mac, where it is 0sex, and you get what she gives you...
but linux reviewer/fanboys drool on about how wonderful it all is, leaving hapless newbies in long lines at the forum, just to accomplish the basics...the worst and most backwards marketing one can imagine...I hope this
helps a bit...

---

### Post by oswallt on 2007-02-04
I'm also having intermittent sound problems under Ubuntu 6.10.  Mine seems to only work every 4th or 5th reboot, though.  I'm using a SB Audigy SE pci card (it's recognized as an Audigy LS, but it has the same ALSA driver, ca0106, so I think I'm ok in that regard).  I recently did a fresh install of Edgy and noticed that sound worked every time with the liveCD and every time until I edited my xorg.conf to set up my wide screen monitor.  I'm going to try switching stuff off in the BIOS, but I wonder why it worked before I changed my xorg.conf.

---

### Post by twtmc on 2007-02-05
I have similar problems, but I am using onboard sound. From the looks of it, it is caused by problems with the alsa-oss drivers. For me, when I type aplay -l into the terminal, I will get this message when it works:

> tanner@tanner:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tanner@tanner:~$ 


and this when it doesn't

> tanner@tanner:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
tanner@tanner:~$ 


---

### Post by deadgobby on 2007-02-05
> **goofdawg said:**
> Rather mysterious problem: My sound either works or does not work right from startup - I can tell by whether or not the Ubuntu startup noise gets played. Restarting fixes it, but it continues to happen every 4th or 5th boot.

My motherboard has onboard sound but it's disabled and I use a card from the Sound Blaster Audigy Value family.

When the sound works at boot, it continues working without issue. Yes, I checked the sound levels :) .

Any help is really appreciated.
 My SB card works fine all the time. Yet, is your system a Dell?
Gobby

---

### Post by pencilpoint on 2007-02-15
I've just had the same problem for 3 months, and today I fixed it.  If you're havin probz, I think it might be usin teh wrong input device.  just to check, issue in a term

```
alsamixer
```

then press F5.

what I did was I just muted my IEC958 thing (press M for mute/unmute), that was blocking the correct device, and I heard some static and WA LA it worked.  OMG i was getting close to suicide there cause I had tried everything and nothing had worked.  But now it worked.

---

