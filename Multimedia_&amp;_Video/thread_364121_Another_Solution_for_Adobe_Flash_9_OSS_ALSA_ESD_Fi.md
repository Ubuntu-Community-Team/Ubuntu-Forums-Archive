---
title: "Another Solution for Adobe Flash 9 OSS ALSA ESD Firefox Iceweasel Sound Problem"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by xiota on 2007-02-17
The esd library I found installed on my computer was libesd0, which uses oss drivers.  I installed libesd-alsa0 because all of my computers use alsa drivers.  After that, flash sound worked.  I do not use the alsa-oss package because it has not worked well for me in the past and it seems like an inelegant solution.

When I switched from esd to PulseAudio, flash sound stopped working again.  Sound worked again after I installed libflashsupport ([available as a deb package here]("http://blog.paulbetts.org/index.php/2007/06/08/native-pulseaudio-with-flash-9-fix-video-crashes/")).

---

### Post by Abhi Kalyan on 2007-03-07
Dear Xiota
Having problems with installing flash plugin for Firefox 2002 in drake 6.06. ANy ideas?
Please

---

### Post by xiota on 2007-03-09
I probably would not be of much help if the libesd-alsa0 package does not just make flash sound work in whatever browser you happen to be using.  You do have to be using esd for that package to have any affect though.

If you do not use esd and flash works, except for sound, but sound generally works for everything else, you might want to try some of the other solutions mentioned in other threads on this topic.  One popular solution seems to be to use the alsa-oss package.

---

### Post by enopepsoo on 2007-03-09
try closing and repening firefox.  if that doesn't work try
```
killall esd
```
I need to do this occasionally to hear sounds on youtube or what have you.:popcorn:

---

### Post by tripleee on 2007-03-21
libesd-alsa0 appears to be included in Ubuntu by default already. I'm too focused (-: to go and investigate this properly, but it's already installed on this Edgy system I'm writing this on now ... and I nevertheless have the problem of disappearing sound between Firefox (Flash sites like YouTube in particular ...?) and other applications (primarily Rhythmbox).

(Rhythmbox, for example, seems to prefer libesd-alsa0 over regular libesd0 in its dependencies.)

One of the replies in [http://planet-geek.com/archives/003048.html](http://planet-geek.com/archives/003048.html) suggests changing FIREFOX_DSP to "auto".  I intend to investigate that before trying out aoss.

---

### Post by tripleee on 2007-03-21
Acually looking at [https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760](https://launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/29760) it looks like libesd-alsa0 was introduced as a dependency for flashplugin-nonfree in Edgy in order to work around problems with ESD with the non-free Flash player.

Because people are still having problems, I guess it's not a proper solution; the bug has some additional discussion and suggestions. If you are using Flash Player 9 this supposedly ought to suffice, but I have version 9 (it's what the flashplugin-nonfree thingy installs on Edgy) and I still have some issues.

---

### Post by xiota on 2007-03-21
I have several debian installs with flash sound working after having done nothing special except make sure the libesd-alsa0 package was installed.  I wonder what is different between debian and ubuntu that would result in flash sound working in one and not the other.  Maybe we should compare package selections?

---

### Post by tripleee on 2007-03-22
I think this is a bit of apples and oranges. My sound works most of the time but there are intermittent problems. I don't have solid evidence but it would seem that visiting Flash sites and then trying to use other sound applications results in some sort of deadlock. This would seem to be confirmed with other reports I see out there, and the bug report in Launchpad has a background explanation which, to me, also seems to explain this. The bottom line appears to be that you need libesd-alsa0 but also the ALSA dmix thingy and alsa-oss (which is not properly covered in the bug discussion -- maybe I'll post a followup there).

---

### Post by xiota on 2007-03-22
The launchpad page says that libesd0-alsa is a recommendation, not a dependency.  The behavior of synaptic and aptitude on my computers is to ignore recommendations, so the wrong library might still be installed after updates.

I have removed as much of oss from my computers as I can, so flash probably does not require oss.  However, the package 'oss-compat' might help.

I also have found that sound does not work reliably when programs that use alsa are used while esd is enabled.  Usually installing esd-based libraries fixes the problem (eg, sdl and many media players have an esd version).  Some people prefer to disable esd instead.  I think esd is worth the effort to keep packages consistent.

---

### Post by tripleee on 2007-03-23
Quick note: Aptitude installs recommended packages by default, Synaptic doesn't.

---

