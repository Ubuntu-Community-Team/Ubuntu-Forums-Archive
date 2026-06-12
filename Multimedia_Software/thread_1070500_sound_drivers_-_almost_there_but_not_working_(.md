---
title: "sound drivers - almost there but not working :("
date: 2009-02-15
forum: Multimedia Software
---

### Post by zigga15 on 2009-02-15
hey all,

I have an X-FI sound card. I have just installed the OSS drivers for it.

When I run osstest I hear the test music, I also hear sound when I pipe the result of running cat on a .wav file to ossplay. However I don't hear sound when I run ossplay on a .wav file directly.

It appears the problem is with gnome recognizing the device, although OSS is chosen as the sound device in System>Preferences>Sound.

If I run ossinfo I get this:
```

Mixer devices
 0: High Definition Audio ALC268 (Mixer 0 of device object 1)
 1: Sound Blaster X-Fi (SB046x/067x (Mixer 0 of device object 2)

Audio devices
HD Audio play speaker             /dev/oss/oss_hdaudio0/pcm0  (device index 0)
HD Audio play headphone           /dev/oss/oss_hdaudio0/pcm1  (device index 1)
HD Audio rec select               /dev/oss/oss_hdaudio0/pcmin0  (device index 2)
HD Audio rec select               /dev/oss/oss_hdaudio0/pcmin1  (device index 3)
Sound Blaster X-Fi (SB046x/067x/076x) output  /dev/oss/oss_sbxfi0/pcm0  (device index 4)
Sound Blaster X-Fi (SB046x/067x/076x) input  /dev/oss/oss_sbxfi0/pcmin0  (device index 5)

```

Is there a file i can edit to get the device selected by gnome, thanks. Any help would be great.

P.S

Also it says that the GNOME settings daemon cannot be started when I login. :S

---

### Post by zigga15 on 2009-02-15
**bump**

---

### Post by Trubbel on 2009-02-15
I have an X-fi sound card and I use the linux driver supplied by Creative. It works well for me, except after hibernation.

Both 32 and 64 bit versions can be found here:

[http://support.creative.com/downloads/download.aspx?nDownloadId=10792](http://support.creative.com/downloads/download.aspx?nDownloadId=10792)

If you have to use the OSS driver I can't help.

---

### Post by zigga15 on 2009-02-16
Hey, sorry for the late reply.

I got the drivers you suggested (they didn't exist last time i tried this :P). Thanks very much for pointing them out.

now When I "sudo make install" I get this error:

```

Update module dependency relationships...
FATAL: Error inserting snd (/lib/modules/2.6.24-23-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

Is this because I was messing around with oss? I noticed that the readme is fairly consise for these drivers. Will I have to hack up the Makefile?

~ Thanks.

---

