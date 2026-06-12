---
title: "Rhythmbox will always crash if try to adjut the volume when playing music in 9.10rc"
date: 2009-10-24
forum: Multimedia Software
---

### Post by skygunner on 2009-10-24
Fresh installed 9.10 RC AMD64, updated

Rhythmbox will always crash if try to adjut the volume(Rhythmbox's one not the system's one) when playing music.

syslog
kernel: [ 4580.229932] rhythmbox[3453]: segfault at 0 ip (null) sp 00007fff929f0a28 error 14 in rhythmbox[400000+8000]
kernel: [ 4790.945573] rhythmbox[3480]: segfault at 0 ip 00007fd08e79a2dd sp 00007fff17d595d0 error 4 in libgtk-x11-2.0.so.0.1800.3[7fd08e550000+3ff000]
kernel: [ 5240.506851] rhythmbox[3581]: segfault at 0 ip (null) sp 00007fffaf31ec58 error 14 in rhythmbox[400000+8000]

I also got this message in user log
 pulseaudio[1629]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Oct 24 22:55:22 -desktop pulseaudio[1629]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Oct 24 22:55:22 -desktop pulseaudio[1629]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.

Also the sound does not start smoothly (bot rhythmbox and system sound).

What could be the problem?
mb: Gigabyte GA-MA790X-UD4P with Realtek ALC889A codec 
Nvidia GTS 250 with Nvidia driver actived

Thanks

---

### Post by robvas on 2009-10-30
Having the same thing with 9.10 final that just came out. Rhythmbox 0.12.5

[FONT=Courier New]Oct 30 16:27:35 rob-desktop kernel: [16014.737346] rhythmbox[1983]: segfault at 0 ip (null) sp bff2221c error 4 in libsoup-gnome-2.4.so.1.3.0[110000+5000]
Oct 30 16:27:54 rob-desktop pulseaudio[1632]: ratelimit.c: 93 events suppressed
Oct 30 16:27:55 rob-desktop wpa_supplicant[1276]: CTRL-EVENT-SCAN-RESULTS 
Oct 30 16:27:56 rob-desktop kernel: [16035.994528] rhythmbox[3177]: segfault at 0 ip (null) sp bfb1c80c error 4 in libgdk-x11-2.0.so.0.1800.3[110000+92000]
Oct 30 16:28:20 rob-desktop pulseaudio[1632]: ratelimit.c: 113 events suppressed
Oct 30 16:28:32 rob-desktop kernel: [16071.945379] rhythmbox[3200]: segfault at 0 ip (null) sp bfa655ec error 4 in libglade-2.0.so.0.0.7[110000+16000]
Oct 30 16:28:43 rob-desktop pulseaudio[1632]: ratelimit.c: 117 events suppressed
Oct 30 16:28:51 rob-desktop kernel: [16091.083006] rhythmbox[3217]: segfault at 0 ip (null) sp bfa316bc error 4 in libgnome-media-profiles.so.0.0.0[110000+d000]
Oct 30 16:28:54 rob-desktop pulseaudio[1632]: ratelimit.c: 116 events suppressed
Oct 30 16:29:55 rob-desktop wpa_supplicant[1276]: CTRL-EVENT-SCAN-RESULTS 
Oct 30 16:30:44 rob-desktop pulseaudio[1632]: ratelimit.c: 116 events suppressed[/FONT]

Nothing in user.log, however.

0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe9f4000 irq 22

---

### Post by iaswni on 2009-11-10
Same here...

---

### Post by 5ulo on 2009-11-11
](*,)argh.. the same 

```

[ 1623.253124] rhythmbox[6738]: segfault at 0 ip (null) sp bff3decc error 4 in libglade-2.0.so.0.0.7[110000+16000]
[ 4711.678279] rhythmbox[21848]: segfault at 0 ip (null) sp bff91fec error 4 in librhythmbox-core.so.0.0.0[110000+111000]
[ 4736.549563] rhythmbox[21987]: segfault at 0 ip (null) sp bfd84c2c error 4 in libgnome-media-profiles.so.0.0.0[110000+d000]

```

---

### Post by valtert on 2009-11-15
same here, though it crashes randomly when adjusting the volume (not always)

```
kern.log.1:Nov 15 01:52:42 centaurus kernel: [38948.016485] rhythmbox[19107]: segfault at 0 ip (null) sp bf98419c error 14 in rhythmbox[8048000+6000]
messages.1:Nov 15 01:52:42 centaurus kernel: [38948.016485] rhythmbox[19107]: segfault at 0 ip (null) sp bf98419c error 14 in rhythmbox[8048000+6000]
syslog.1:Nov 15 01:52:42 centaurus kernel: [38948.016485] rhythmbox[19107]: segfault at 0 ip (null) sp bf98419c error 14 in rhythmbox[8048000+6000]
```

Ubuntu 9.10
Rhythmbox 0.12.5

---

### Post by valtert on 2009-11-15
this seem to be the very same bug:
[https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/472985](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/472985)

---

### Post by valtert on 2009-11-16
which happens to be a duplicate of [https://bugs.launchpad.net/bugs/455421](https://bugs.launchpad.net/bugs/455421)

---

### Post by hwttdz on 2009-11-25
Using rhythmbox-client --volume-up/--volume-down is a workaround, however this is hugely annoying.

---

### Post by JEdwardP on 2010-03-01
Every version later than 0.12.0-0ubuntu4 has either crashed for me when attempting to adjust the volume, or gradually lowered its volume level to mute when a file is played.

Oddly enough, I see this behavior on only one of my two machines, in spite of the fact that their hardware configurations are very similar to one another. The one with the older on-board audio chip works perfectly with all versions of Rhythmbox, but the one with the newer chip does not.

---

### Post by goldencako on 2010-03-17
I only experience errors when playing VBR. Maybe it's a gstreamer bug?

---

### Post by MelRia on 2010-12-12
same here, I turned the net inside out, no solutions.

---

### Post by jon armand on 2011-04-01
I'm experiencing the same in 10.04. I've seen it in Totem as well.

---

### Post by potiphera on 2011-04-28
This also happens for me in 10.04, although it seems to depend on the song.  Also, the volume adjusts smoothly on some songs, but with zipper noise on others.

---

