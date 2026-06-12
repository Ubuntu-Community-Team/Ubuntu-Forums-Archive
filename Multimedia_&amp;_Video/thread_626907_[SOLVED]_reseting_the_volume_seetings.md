---
title: "[SOLVED] reseting the volume seetings"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by azelter on 2007-11-29
This thread has come up several times in some shape or form, however, I cannot find an answer to my question.
My problem is that having played with the sound settings on my gutsy desktop using gnome-volume-control and alsa mixer I can no longer record sound using my external mic.
I know there are no hardware problems as if I boot the gutsy live CD my sound playback/recording works perfectly.
I tried writing down the settings as seen in gnome-volume-control on the live-cd and changing my standard system to that, but still I have no sound recording.
I have searched and searched for a way to reset my sound settings to default, but cannot find one. It seems like by default /var/lib/alsa is empty, therefore alsactl restore will have no effect.
I know the gnome sound settings are shared accross users, as if I use the gnome-volume-control to change the sound settings as one user and then logout and in again as a different user, the sound settings are kept. This is also true through reboots.
My question is - where are gnome-volume-control's settings stored and how can I revert them?
Any help would be greatly appreciated.
Thanks,
Alex

---

### Post by kyphi on 2007-11-29
Perhaps you have not given yourself the necessary permission:  Go to System -> Administration -> Users and Groups,  Left click on the user entry, which should be your name so that the Properties button becomes available.  Go to 'User Privileges' and make sure that there is a tick next to 'use audio devices'.

---

### Post by azelter on 2007-11-29
Thanks for the suggestion. It wasn't that. I checked to be sure. Basically, all I did was fiddle with alsamixer and with the gnome-volume-control.
I have also checked - if I log in to a kde (rather than gnome) session I still have a dead mic.
Really strange as I have now written down the exact alsamixer settings and gnome-volume-control settings that exist when running this same system using the live CD. When I change everything the same I still get no joy although everything functions perfectly running from the live CD.
So frustrating, when I know the hardware is good and I'm just messed up with some setting in some file somewhere that I can't for the life of me find or reset.
Cheers,
Alex

---

### Post by azelter on 2007-11-29
Well, I managed to solve my problem, but I'd still like to know what happened.
For the record. This did not work (I did it previously):
sudo dpkg -P --force-depends alsa-oss alsa-base alsa-utils gstreamer0.10-als linux-sound-base
followed by reinstalling the same packages

However, I went to
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
which advised:
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
followed by reinstalling those packages (plus others autoremoved)

I did this, but also rebooted the machine before reinstalling those packages as I noticed that sound still worked after their removal (presumable as the modules were not removed from the running kernel).

When I rebooted with no alsa my sound icon showed everything muted. I then reinstalled the packages I had removed and rebooted again. Sound was still muted. I then changed the settings using gnome-volume-control to those I observed in my working live-CD sessions. After that everything (including my mic) worked fine.

What I don't understand, is that I had to uninstall/reboot/reinstall as well as changing the sound settings with gnome-volume-control. Therefore some file was causing me problems that was wiped in the reinstallation but I do not know what it was. Also, the I would have thought my initial attempt at removing the sound packages using dpkg (not apt-get) would have worked. Perhaps it would have if I had rebooted once alsa was removed.

Well, all works now so that's good. I'd still like to know what was going on though...

---

### Post by kyphi on 2007-11-29
I was pleased to read of your success in resolving this issue.

As to what went wrong, I could not even guess.  Perhaps a corrupted file that may have been picked up by fsck.

---

