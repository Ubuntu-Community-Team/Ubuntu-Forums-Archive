---
title: "[SOLVED] SPDIF stops working after passthrough"
date: 2008-08-04
forum: Multimedia Software
---

### Post by svenbertil on 2008-08-04
I have a problem with the SPDIF out. The card is a SB Live! of some sorts (it uses snd_emu10k1).

Problem is this: If I use DTS or AC3 passtrough in one application and that app crashes the card does not return to outputting normal PCM stream. Only way I've found to get it working again at this point is to apt-get purge linux-sound-base alsa-base alsa-utils, reboot and reinstall those packages. 

Just rebooting the machine does not help. If I do, the PCM indicator on the amp comes on for an instant during startup but then it goes away just as quickly.

AC3/DTS passthrough from e.g. VLC still works at this point but even exiting the program normally does not restore PCM output.

Does anyone have any ideas on how to solve this without the reinstall and reboot? I've mucked about with all settings in alsamaixer but that does nothing. The analog outputs still work fine.

Running 8.04, all updates installed.

---

### Post by svenbertil on 2008-08-08
This is driving me nuts. Any thoughts, tips, ideas etc are welcome at this point.

Correction: PCM indicator on AMP stays on from the moment of P.O.S.T til alsa is loaded.

Since posting the above I've tried taking backups of .asoundrc and asoundrc.asoundconf from a working state and restoring them when in failed state. /etc/init.d/alsa-utils restart/reset or rebooting does nothing even with them restored.

Also, if I apt-get purge, reinstall and then reboot problem persists, while purge; reboot; reinstall still solves it.

Since the PCM indicator stays on until Alsa is loaded there's got to be another conf-file that I've yet to find, someone has to know which one that might be.

---

### Post by svenbertil on 2008-08-10
Wohoo! I solved it!

Doing a `sudo alsactl store <cardnum>` when in a working state and then `alsactl restore <cardnum>` when in a broken state brings my PCM output right back, without any other hassle!

I'm quite happy now. :)

---

### Post by markbuntu on 2008-08-10
If you have an etc/asound.conf that will do that though the one in ~/ should override it. You can also edit your etc/pulse/default.pa as sudo
look for the line that says:

load-module module-default-device-restore

and comment it out. It may or may not help with your problem but you can give it a try and let us know if it works for you.

---

### Post by edvar on 2008-09-01
This is not working for me. I keep loosing all sound at least once a week.
Every time it happens I have to:

$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
$ sudo init 6
$ sudo apt-get install alsa-base alsa-utils fast-user-switch-applet gdm gdm-themes kubuntu-kde4-desktop linux-sound-base
$ sudo init 6

After that I have my digital sound back. However it's just a temporary fix as I'll have the same problem after a couple of days.

This is really annoying... alsactl store/restore doesn't do anything.

Isn't there a way to fix that once and for all?

---

### Post by at0mic on 2008-09-16
Hi,

This same thing happened to me after playing around with AC3 passthrough with SMPLAYEr.  i have a IEC958 SPDIF.  Lets face it. SPDIF out is broken which is a disaster for someone like me wanting a ubuntu based multimedia system. time to loook elsewhere. high def mkv playback codec that is smooth for linux also hasnt evolved yet. ACK BACK TO WINDOWS!

---

### Post by prince_niceguy on 2008-10-13
I too have this problem... only passthrough works but normal pcm has gone bonkers... no clue why... will give try to the post questions and see if it works or not...

---

### Post by prince_niceguy on 2008-10-13
solved my  issue. i have removed mplayer... as some one has posted that it is because of mplayer... hopefully it continues to work without problem...

---

### Post by svenbertil on 2008-10-30
> **at0mic said:**
> Hi,

This same thing happened to me after playing around with AC3 passthrough with SMPLAYEr.  i have a IEC958 SPDIF.  Lets face it. SPDIF out is broken which is a disaster for someone like me wanting a ubuntu based multimedia system. time to loook elsewhere. high def mkv playback codec that is smooth for linux also hasnt evolved yet. ACK BACK TO WINDOWS!

I know this is late as hell but give [XBMC]("http://xbmc.org/") a try, multi-threaded decoding, handles HD very well.

---

### Post by prince_niceguy on 2008-10-30
I have given xbmc a try but somehow it is taking huge cpu usage on mycomputer and virtually hangs, so probably wait for some more time beforing giving it another try.

---

### Post by svenbertil on 2008-11-19
> **prince_niceguy said:**
> I have given xbmc a try but somehow it is taking huge cpu usage on mycomputer and virtually hangs, so probably wait for some more time beforing giving it another try.

When was that? They've recently released the final version of 'Atlantis'.  Works pretty good for me, much more stable than the alphas.

---

