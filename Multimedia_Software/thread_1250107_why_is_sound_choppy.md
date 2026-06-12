---
title: "why is sound choppy?"
date: 2009-08-26
forum: Multimedia Software
---

### Post by linuxhippy on 2009-08-26
I'm running xubuntu 9.04 and all seems to be ok except for my choppy sound.  I have an old ESS Solo PCI sound card that usually works ok with ALSA.  In xubuntu the sound is muted in alsamixer-when unmuted the sound is choppy with aplay, mplayer and VLC playing wav files and audio streams.  What should I change with the sound card?

Upgraded:

I rebooted and found out that sound has remained very choppy.  Then I installed kubuntu-desktop and gnome-desktop with apt-get so that I would have more sound tools.  Same result.  I followed this thread for Jaunty:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=choppy+sound]("http://ubuntuforums.org/showthread.php?t=789578&highlight=choppy+sound")

This didn't fix my choppy sound.  This card works fine in Fedora Core 10 which is also on my pc.  How can I get it to work in ubuntu?

---

### Post by linuxhippy on 2009-08-28
I seemed to have fixed this by googling old Ubuntu 8.10 posts:

puseaudio and VLC don't mix (said the poster) and this worked:

sudo apt-get remove pulseaudio

---

