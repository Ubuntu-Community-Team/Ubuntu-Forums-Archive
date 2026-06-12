---
title: "Audio Jack not working MX14R2 15.04"
date: 2015-09-02
forum: Multimedia Software
---

### Post by darren27 on 2015-09-02
Hi, I've decided to make the jump of putting Ubuntu on my main Laptop after quite some time of Lubuntu giving my netbook a new lease of life.

Only issue is, on my laptop there are 3 audio jacks on the left side (1 mic, 1 headset, 1 headphone / line out), they are not working.
I use the headphone socket as a line out for a set of surround speakers normally, but now the jack is not detected and audio plays through the laptop speakers only.
The chipset is Intel 7 Series / C210 Series.

I have unmuted everything in alsamixer as noted in the thread below
[http://ubuntuforums.org/showthread.php?t=2225643](http://ubuntuforums.org/showthread.php?t=2225643)

But the audio output is the same.
I note this issue has come up on this model of laptop on quite a few threads but none of the resolutions I've seen have worked for me so far.

Please help

---

### Post by Yellow Pasque on 2015-09-03
There are only a few things I would think to try -
First, install latest kernel sound module (and then reboot):  [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201508311546%7Eubuntu15.04.1_all.deb](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201508311546%7Eubuntu15.04.1_all.deb)
If that doesn't help, try hdajackretask:
```
sudo apt-get install alsa-tools-gui
sudo hdajackretask
```


>  but now the jack is not detected
Did it work before on Linux/Ubuntu or are you referring to it working on Windows?

---

### Post by darren27 on 2015-09-07
Hi,

Thanks, when I use hdajackretask, I get the following error when trying to apply any changes
```
tee: /sys/class/sound/hwC0D0/reconfig: Device or resource busy
```

The output into the terminal is 

```
0x0b 0x010140100x0c 0x014580f0
0x0d 0x014570f0
0x0e 0x01c530f0
0x0f 0x0221401f
0x10 0x02216011
0x11 0x01014410
0x12 0x37a791f0
0x13 0x908700f0
0x18 0x500000f0
1


(hdajackretask:5848): GLib-WARNING **: (/build/buildd/glib2.0-2.44.1/./glib/gerror.c:383):g_error_new_valist: runtime check failed: (domain != 0)

```

Then all sound stops from any source and I must reboot before sound will play at all.


To clarify, the jack worked in Windows, but not Ubuntu.

---

