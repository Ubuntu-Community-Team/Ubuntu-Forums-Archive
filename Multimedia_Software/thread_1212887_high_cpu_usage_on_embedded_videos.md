---
title: "high cpu usage on embedded videos"
date: 2009-07-14
forum: Multimedia Software
---

### Post by HoboGarden on 2009-07-14
I'm using the following packages:
Mplayer and it's plugin (removed totem), whatever gstreamer plugins that were already installed in ubuntu 9.04, and adobe flash 10 plugin.

When watching an embedded video, my cpu usage averages around 50% 

Is there any way to lower the usage?  Is this normal?

my specs:
Intel® Core™2 Duo processor T8300 (2.4GHz, 800 MHz, 3MB L2 Cache)
nVidia Quadro NVS 140M 128MB discrete
2 gb of ram

---

### Post by igorzwx on 2009-07-14
It is "normal" today.
It is PulseAudio, the evil.

---

### Post by lovinglinux on 2009-07-14
> **igorzwx said:**
> It is "normal" today.
It is PulseAudio, the evil.

I have pulseaudio disabled and I get the same result. Same video played with gecko-mediaplayer uses 9% of CPU while Flash uses 45%.

[http://ubuntuforums.org/showthread.php?t=1208331](http://ubuntuforums.org/showthread.php?t=1208331)
[http://ubuntuforums.org/showthread.php?t=1200496](http://ubuntuforums.org/showthread.php?t=1200496)

You might try some workarounds from the "Flash Performance" section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567), but there is definitely a problem with flash and the new html5 video.

---

### Post by igorzwx on 2009-07-14
you cannot just disable PulseAudio.
I tried.
Complete removal.
Blacklist ALSA modules,
reboot.
Install OSS4

This works well for me.
But USB audio devices are not supported by OSS4,
and something else too.

---

### Post by lovinglinux on 2009-07-14
> **igorzwx said:**
> you cannot just disable PulseAudio.
I tried.
Complete removal.
Blacklist ALSA modules,
reboot.
Install OSS4

This works well for me.
But USB audio devices are not supported by OSS4,
and something else too.

Oops, I mean I removed it. Overall performance improved a lot, but not enough for flash and html5 video.

Also check this: [http://ubuntuforums.org/showthread.php?t=1152095](http://ubuntuforums.org/showthread.php?t=1152095)

---

### Post by igorzwx on 2009-07-14
I can believe this.
But OSS4 works better than ALSA.
In theory and in practice.
I have it now on all my boxes.

---

### Post by lovinglinux on 2009-07-14
> **igorzwx said:**
> you cannot just disable PulseAudio.
I tried.
Complete removal.
Blacklist ALSA modules,
reboot.
Install OSS4

This works well for me.
But USB audio devices are not supported by OSS4,
and something else too.

Could you explain how and why do you blacklist ALSA modules?

---

### Post by igorzwx on 2009-07-14
ALSA modules are a kind of trojan, or rootkit, if you want.
OSS4 is the same sort of things.
How do you remove or disable trojans on Windows.
In the same way.

the most interesting experiment, I made yesterday (or more exactly today)

Compiled OSS4 from Mercurial in Ubuntu Lite Beta (netboot)
on the old box.
These howtos were applied:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
[http://brainstorms.in/?p=172](http://brainstorms.in/?p=172)

osstest played the sound well.

Audacity works well (playback and recordings)
Sky works well to. Fantastic performance. 
no delay, no latency
But you should install skype-static-oss

Ubuntu Lite Beta (netboot) has a kind of 8.04 inside.
You have to compile therefore.
And blacklist something manually

---

### Post by lovinglinux on 2009-07-14
thanks

---

### Post by igorzwx on 2009-07-14
Try it on the old box first

---

