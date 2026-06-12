---
title: "DVD Audio issues - VLC"
date: 2008-02-27
forum: Multimedia &amp; Video
---

### Post by vo!d on 2008-02-27
Hi there,

I'm having serious audio issues with DVD playback (in vlc, totem doesn't play dvds a all, it asks to install a plugin and fails) - the sound is crackly and "jumps" constantly. I've installed the ubuntu-restricted-extras package, libdvdcss and the other one (forgot the name.. something like dvdxxxxread3).


I'm using intel HDA sound card with ALSA (which I am pretty sure is correctly configured), ALSA is also chosen as audio output module in vlc. I've messed with all the settings, no joy.

DMA - edited /etc/hdparm.conf and uncommented the section for /dev/cdrom/cdrom0 and enabled dma "dma = on", no joy. I remember having spotted a DMA option somewhere in vlc itself (am i wrong?), but I can't seem to find it anymore.

Note that the video plays back fine, it's just the sound that isn't working. No issues with other formats.

Any idea what it could be? I've searched pretty much every forum post, forum and article both in German and English, followed instructions, but nothing seems to fix it!
I would also prefer using VLC as opposed to installing other software (note: mplayer refuses to install for some bizarre dependecy reason). Hope someone can help!


specs:
Ubuntu 7.10
LG S1 Express Dual
1024 or + ram
intel core2duo
ATI Radeon Mobility X1600 (fglrx, working flawlessly)
Intel HDA sound via ALSA (flawless)



Chris

---

### Post by vo!d on 2008-02-27
bump

---

### Post by vo!d on 2008-02-28
bump

---

### Post by vo!d on 2008-02-29
bump


last try....:confused:

---

