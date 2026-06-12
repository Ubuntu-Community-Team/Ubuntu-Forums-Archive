---
title: "Firefox 3 And Flash And Other Distros"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Bosconian on 2008-07-19
I have had it with Firefox constantly crashing on sites with flash. I use flash player a lot and I get crashes all the time. Even nspluginwrapper only partly solves the problem. I've tried every solution there is.

So now I have read that other distros do not suffer the same problems. I am thinking it is finally time to leave Ubuntu and try another distro. Does anyone have an recommendations? Probably using Gnome. I am thinking of giving openSUSE a go - anyone have any experience with using flash in this?

---

### Post by nutznboltz on 2008-07-19
The last thing you should ever do is post about what distro to change to on the site of the distro you are abandoning (or contemplating abandoning.)  They don't want to hear it.  Go to the forums of the potential replacement distro and post there.

Meanwhile click on this:

[http://www.piratesoup.net/viewtopic.php?f=5&t=191](http://www.piratesoup.net/viewtopic.php?f=5&t=191)

I get a firefox crash in three seconds after that page loads.

---

### Post by gandaran on 2008-07-19
yes, other distros also have the same problem, at-least the new opensuse 11 and fedora 9, both have adopted pulseaudio just like the new ubuntu 8.04, which is the root of all the problems some users have (pulseaudio/flash problems), maybe you can just stick to a older ubuntu version like 7.10 or any other distro without pulseaudio, until the developers fix the problems.
now what type of solution have you tried? there are many around!
are you running ubuntu 32-bits or 64-bits?
have you tried adobe flash 10? flash 10 does fixes the issue with pulseaudio!

---

### Post by gandaran on 2008-07-19
> **nutznboltz said:**
> The last thing you should ever do is post about what distro to change to on the site of the distro you are abandoning (or contemplating abandoning.)  They don't want to hear it.  Go to the forums of the potential replacement distro and post there.

Meanwhile click on this:

[http://www.piratesoup.net/viewtopic.php?f=5&t=191](http://www.piratesoup.net/viewtopic.php?f=5&t=191)

I get a firefox crash in three seconds after that page loads.

I clicked on two flash videos, played them at the same time without any problems, video and sound and no crashers!
note: I,m using alsa not pulseaudio.

---

### Post by Bosconian on 2008-07-20
Well I fixed my problem with Firefox and Flash for now. All I had to do was go into the sound settings and change the devices from PulseAudio to ALSA and then also downgrade to Flash 9 rather than the 10 Beta.

Flash 9 with PulseAudio crashes constantly. Flash 10 Beta crashes for some other reason. I'll wait until there is a full release of 10. 9 is stable now but the framerate sucks.

To be fair, I tried openSUSE 11 in VirtualBox but it is nowhere near as user friendly as Ubuntu.

---

### Post by ibutho on 2008-07-20
> To be fair, I tried openSUSE 11 in VirtualBox but it is nowhere near as user friendly as Ubuntu.
Thats something thats always debatable. I personally find openSUSE to be a lot more user friendly and easier to administer (all your system config stuff can be done via YAST). Anyway thats besides the point. If pulseaudio is causing problems, you can uninstall it and revert to alsa.

---

### Post by gandaran on 2008-07-20
> Flash 9 with PulseAudio crashes constantly

if you have set everything to alsa and it works, remove libflashsupport if you happen to have it installed, libflashsupport fixes the flash 9/pulseaudio sound issue, but is the major source of firefox crashers.

>  Flash 10 Beta crashes for some other reason

flash 10 beta one was in-fact much better than the latest beta 2 release.

---

