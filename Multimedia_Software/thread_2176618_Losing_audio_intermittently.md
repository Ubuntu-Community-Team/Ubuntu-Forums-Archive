---
title: "Losing audio intermittently"
date: 2013-09-25
forum: Multimedia Software
---

### Post by niniendowarrior on 2013-09-25
I'm using Ubuntu 13.04 and recently, I've been experiencing some strange sound loses and it's not clear when this happens.  I could be playing a game or playing some music.  Suddenly, I will lose audio and nothing I do save for a reboot will restore the sound.

[http://www.alsa-project.org/db/?f=52f5f960e9297717cf897521ede925cdab7dd922](http://www.alsa-project.org/db/?f=52f5f960e9297717cf897521ede925cdab7dd922)

I've tried restarting pulseaudio.  I've also tried removing .pulse* and restarting pulse.  I've also tried alsa force-reload but it seems that nothing solves this issue.

Can someone help me because I'm at a loss at what is wrong.  I see no error entries in /var/log/syslog.

FYI.  My sound is via HDMI audio.

---

### Post by niniendowarrior on 2013-09-25
Going to try this.

[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

---

### Post by niniendowarrior on 2013-09-25
No good.  I still lose sound.  I started a game and let it run on its own and the sound goes after a while.  Then I have no sound permanently in my desktop.

Someone, please help.

---

### Post by lidex on 2013-09-29
Maybe I've been away too long, but what is this:
```
!!ALSA Version
!!------------
Driver version:     [COLOR="#FF0000"]k3.8.0-30-generic[/COLOR]
Library version:    1.0.25
Utilities version:  1.0.25

```

Mine looks like this:
```
!!ALSA Version
!!------------
Driver version:     1.0.24
Library version:    1.0.25
Utilities version:  1.0.25

```

---

### Post by niniendowarrior on 2013-10-16
It may have been from the experimental intel hd alsa stuff ([https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS))?  I think.  I have no idea what it is otherwise.  I'm hoping someone can help me.  I lose sound when I play specific games like Red Orchestra or Trine 2.

---

### Post by niniendowarrior on 2014-04-20
As a minor bump... I'm now in Ubuntu 13.10 with the same problem when running Trine 2.

[http://www.alsa-project.org/db/?f=82d6f9bf0250afb8bc3ff7b8c2dc383d6677607b](http://www.alsa-project.org/db/?f=82d6f9bf0250afb8bc3ff7b8c2dc383d6677607b)

I'm uncertain what to do at this point.

---

### Post by niniendowarrior on 2014-04-20
I have tried doing sudo alsa force-reload.  This is the output I get.

```

$ sudo alsa force-reload
Unloading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer (failed: modules still loaded: snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-seq-midi snd-seq-midi-event snd-seq snd-rawmidi snd-seq-device snd-hda-codec-realtek snd-hda-intel snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer.

```

---

### Post by niniendowarrior on 2014-04-24
I found this in the syslog.

```

Apr 24 12:03:39 pulseaudio[2135]: [alsa-sink-ALC888 Digital] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Apr 24 12:03:39 pulseaudio[2135]: [alsa-sink-ALC888 Digital] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Apr 24 12:03:39 pulseaudio[2135]: [alsa-sink-ALC888 Digital] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Apr 24 12:06:12 kernel: [  504.000596] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.

```

Attempted to get rid of the bdl_pos_adj log entry with this in /etc/modprobe.d/alsa-base.conf
```

options snd-hda-intel model=auto enable_msi=1 bdl_pos_adj=1

```

It did not solve the audio issues nor remove the log entry.

---

