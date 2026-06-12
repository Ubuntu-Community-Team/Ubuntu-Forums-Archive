---
title: "Poor sound quality in Kubuntu 7.04"
date: 2007-08-23
forum: Multimedia &amp; Video
---

### Post by Go2doug on 2007-08-23
Hi guys, I have a Sound Blaster Audigy SE card on a new Dell PC running an up-to-date Kubuntu 7.04.

When I first installed Kubuntu, the sound card was automatically detected and the driver was installed. The problem is that when I listen to music, the sound quality is poor compared to when I listen to the same MP3s in XP or Vista.

I use Amarok to play the MP3s, and I use Kmix to adjust the volume. In Amarok, the "sound system" is Xine and the "output plugin" is Alsa. The other choices for "output plugin" are Autodetect, OSS, Pulseaudio, and File. I have played around with Amarok's equalizer. The onboard audio is diabled in BIOS.

In the Adept Package Manager, I have the following packages installed the match the search term "alsa":

alsa-base
alsa-utils
alsamixergui
libasound2
libesd-alsa0
libqt-plugins-alsa
libsdl1.2-debian-alsa
linux-sound-base

Should I install anything else?

Any recommendations for improving the sound quality of my system? Thanks.

---

### Post by Go2doug on 2007-08-25
I thought that perhaps I need to upgrade the sound driver, so using the command cat /proc/asound/version I got these results:

[INDENT]*Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).*[/INDENT]

However, on the [Alsa website]("http://www.alsa-project.org/main/index.php/Download"), it appears that 1.0.14 is the latest version! Now what?

---

### Post by Go2doug on 2007-08-28
Could it be that the Alsa driver is simply inferior to the Windows-specific driver in terms of quality?

---

