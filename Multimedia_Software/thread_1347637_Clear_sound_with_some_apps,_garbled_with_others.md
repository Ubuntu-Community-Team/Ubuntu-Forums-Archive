---
title: "Clear sound with some apps, garbled with others"
date: 2009-12-06
forum: Multimedia Software
---

### Post by americanknight on 2009-12-06
I'm running Ubuntu Studio 9.10 (though I was having the exact same issues before I installed the Ubuntu Studio packages) and most of the time have no sound issues, except with certain applications. For one, while the Ubuntu sound theme works fine, the login sound is very garbled and staticy. Videos and music play fine in programs like Totem, but in Kdenlive, my audio has a subtle (though annoying) repetitive clipping sound. Worst of all, in Linux Multimedia Studio, my sound is completely garbled and staticy.

I've done a lot to try to fix this already. For example, on my Compaq Presario laptop, also with Karmic, I was having the same issue with LMMS, and after uninstalling pulseaudio, it sounded fine. As far as I could tell, the only side effect was no longer having a handy volume control applet. But with my Dell Dimension desktop, with an SB Audigy (rev 04) sound card, uninstalling pulseaudio made my sound completely not work. Plus, I've gathered from forums that we're really stuck with pulseaudio now, so uninstalling it really isn't a good idea. One idea out there was to use esound instead, but that didn't work for me.

When I first installed Karmic (a fresh install from Windows), the sound wasn't working at all. That was fixed by simply opening System > Preferences > Sound, and under the "output" tab, selecting my soundcard. That got audio working with the exceptions I've noted. I've since tried all the tricks here: [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats") and here: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449"). I've also done things like adding my user to the groups "pulse" and "pulse-access" and checking my levels in the alsa-mixer. I've tried killing pulseaudio and running Jack before starting LMMS. When I do that, LMMS won't play at all.

Has anyone had problems similar to mine who could shed some light? Thanks!

---

### Post by americanknight on 2009-12-06
It's funny how I almost always find a solution just after I've given up hope on figuring things out myself and resort to begging for help on the forums :)

I overlooked a simple diagnosis, which was to ask myself if LMMS was even using pulseaudio. Sure enough, in LMMS, under Edit > Settings > Audio Settings, I found that it was using the Audio Interface was set to ALSA. I chose Pulse Audio, even though the option reads "(bad latency!)", and now the sound works fine. I'm wondering if this will come back to haunt me when I start adding lots of tracks.

Does anyone have any insight on the way to get the best performance out of LMMS on Karmic?  Also, my login sound is still garbled and Kdenlive is still sounding less than stellar, so any other insights would still be appreciated.

---

### Post by neu2buntu on 2009-12-13
for LMMS i have written a workaround [[SIZE=3][COLOR=Red]here[/COLOR][/SIZE]]("http://lmms.sourceforge.net/wiki/index.php?title=Installation"), which i tested on my current upgrade of karmic,and also a clean install, which allows you to use LMMS with its alsa driver .

---

