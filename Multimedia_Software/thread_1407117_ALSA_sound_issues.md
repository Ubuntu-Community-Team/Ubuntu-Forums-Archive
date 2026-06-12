---
title: "ALSA sound issues"
date: 2010-02-14
forum: Multimedia Software
---

### Post by higashi on 2010-02-14
If i watch a video on youtube, sound on FCE Ultra (and possibly other programs, i havent tried them all) won't work until the next time i log out/ back in.

If i play a game on FCE Ultra, sound on youtube (or any other flash sites) won't work until the next time i log out/ back in.

(using ALSA Sound System in Karmic)

Any way to fix this?
Thanks in advance

---

### Post by higashi on 2010-02-16
BUMP!

If i run gfceu interminal, it opens fine along with sound, but the video's choppy. I tried to open it w/o running in terminal again and it was soundless. 
Here's the output i get when running it in terminal (well, the sound part at least)
```

Initializing sound...
 Bits: 16
 Rate: 48000
 Channels: 1
 Byte order: CPU Native
 Buffer size: 8192 sample frames(170.666667 ms)

```

---

### Post by VertexPusher on 2010-02-17
> **higashi said:**
> using ALSA Sound System in Karmic
Have you removed PulseAudio? Are you using Adobe's Flash plugin or one of the replacements (swfdec, gnash)?

If one of your applications is configured to use OSS or to bypass ALSA's stream mixer (dmix), it will completely occupy the sound card and block it for any other application, including Flash.

There is a library named "libflashsupport" which is known to route sound from Flash player to OSS. This library is part of the package "flashplugin-nonfree-extrasound". If this package is installed on your system, remove it.

---

### Post by higashi on 2010-02-17
I have removed PulseAudio, and i'm using Adobe's Flash plugin.

I don't see any sound options for FCE, so I can't tell if it's using OSS, but i'm pretty sure it's ALSA.

I removed flashplugin-nonfree-extrasound , but it didn't make a difference.

---

### Post by VertexPusher on 2010-02-17
> **higashi said:**
> I don't see any sound options for FCE, so I can't tell if it's using OSS, but i'm pretty sure it's ALSA.
FCE uses SDL (Simple Directmedia Layer), a cross-platform API for multimedia. On Linux, SDL uses OSS by default unless you set an environment variable:

SDL_AUDIODRIVER=alsa

---

### Post by Yellow Pasque on 2010-02-17
> **VertexPusher said:**
> On Linux, SDL uses OSS by default unless you set an environment variable

In Ubuntu, the sdl-oss shared library files aren't installed unless the user goes out of his/her way to install them, so SDL uses ALSA (should use pulse since they ship Pulseaudio.. [https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/203158](https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/203158) ).

---

### Post by VertexPusher on 2010-02-17
Well, something is blocking the sound card, and it's not Flash.

Make sure that libsdl1.2debian-alsa is installed and libsdl1.2debian-oss is NOT installed.

There's a (remote) possibility that dmix is not configured for the sound card. Save the following script as ".asoundrc" in your user home directory (/home/username/.asoundrc), then log out and log in again. Start the applications and see if it makes a difference.
```
pcm.!default {
    type plug
    slave.pcm {
        type asym
        playback.pcm "dmix:0"
        capture.pcm "hw:0"
    }
}
```If that doesn't work either, enter the following command and post the output here.
```
lsof | grep snd
```This will help identify the application that is blocking the sound card.

---

### Post by higashi on 2010-02-18
wow, thank you so much. your post made me realize what was going on.
I was having sound problems when i was using pulseaudio a while ago, and i read on a thread to save something as .asoundrc.
I did, and left it there.
Now, i deleted it, and everything works fine. (facepalm)
Thanks for all the help!!

EDIT: False alarm, it only worked for a while, and now everything's the same.
here's the output for lsof | grep snd
```

gnome-set 1603     george  mem       REG        8,1   420372       5263 /usr/lib/libsndfile.so.1.0.20
gnome-vol 1679     george  mem       REG        8,1   420372       5263 /usr/lib/libsndfile.so.1.0.20
chrome    1841     george  mem       CHR      116,8                3873 /dev/snd/pcmC0D0p
chrome    1841     george   68r      CHR      116,2      0t0       3718 /dev/snd/timer
chrome    1841     george   70u      CHR      116,8      0t0       3873 /dev/snd/pcmC0D0p

```

---

