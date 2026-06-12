---
title: "TvTime: no sound with ATI tv wonder 600, Hardy"
date: 2009-11-18
forum: Multimedia Software
---

### Post by xxguitarist on 2009-11-18
Got video working by changing video card drivers, all the channels come in great. 
No sound, and all the mixer channels have been activated.
Volume control displays in the TvTime window, and will change with arrow keys.'



Solution: 
run the following in terminal:

```
tvtime | arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -
```

---

### Post by xxguitarist on 2009-11-18
Anyone?

---

### Post by JBAlaska on 2009-11-18
Been a long time..but I think you have to use a cable between your sound card and the capture/tuner card. you can use the internal CD sound cable or an external Mini male to mini male cord..TV card out to sound line in..I think.

---

### Post by xxguitarist on 2009-11-18
> **JBAlaska said:**
> Been a long time..but I think you have to use a cable between your sound card and the capture/tuner card. you can use the internal CD sound cable or an external Mini male to mini male cord..TV card out to sound line in..I think.
Thanks for trying to help.. this is a USB tuner, however. Perhaps I should have stated that.

---

### Post by JBAlaska on 2009-11-18
My fault I should have googled your device.

This may help:
- Use tvtime for analogue channels, but there won't be audio (see ATI/AMD TV Wonder HD 600 USB - LinuxTVWiki).
To get the sound start sox after starting tvtime like this:
sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t alsa default

**Do NOT attempt to access the sound capture device of the em28xx module (so something like sox -r 48000 -w -c 2 -t alsa hw:1,0 -t alsa default): that will result in immediate kernel panic!**

Found it [url=http://www.linuxforums.org/forum/peripherals-hardware/131790-ati-tv-wonder-600-usb-2-0-0438-b002-linux-2-6-26-kernel.html
]Here[/url]

---

### Post by xxguitarist on 2009-11-18
I installed some updates earlier today, the tuner is no longer recognized by the computer. ](*,)

Lets see if I can backtrack & fix that...

---

### Post by JBAlaska on 2009-11-18
Gotta love that in Linux, when you install a driver thats not registered with DKMS (Dynamic kernel module support).

Once you get all working you might want to add DKMS support for your manually installed drivers.

---

### Post by xxguitarist on 2009-11-18
Well, last time it was just by switching to the nvidia one in the hardware driver category.. but previously it detected the tuner, just wouldn't display anything from it. Now it won't detect the tuner at all.

---

### Post by xxguitarist on 2009-11-19
> **JBAlaska said:**
> My fault I should have googled your device.

This may help:
- Use tvtime for analogue channels, but there won't be audio (see ATI/AMD TV Wonder HD 600 USB - LinuxTVWiki).
To get the sound start sox after starting tvtime like this:
sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t alsa default

**Do NOT attempt to access the sound capture device of the em28xx module (so something like sox -r 48000 -w -c 2 -t alsa hw:1,0 -t alsa default): that will result in immediate kernel panic!**

Found it [Here]("http://www.linuxforums.org/forum/peripherals-hardware/131790-ati-tv-wonder-600-usb-2-0-0438-b002-linux-2-6-26-kernel.html%3Cbr%20/%3E")
Got back to the point of having video with my 3rd or 4th attempt at re-installing v4l-dvb, this time with mercurial?

Entered your line from above: 
```
desktop:~$ sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t alsa default
sox soxio: Failed reading `/dev/dsp1': unknown file type `ossdsp'

```Installed libsox
Now the error is:
```

desktop:~$ sox -r 48000 -w -c 2 -t ossdsp /dev/dsp1 -t alsa default
sox soxio: Can't open input file `/dev/dsp1': No such file or directory
```

---

### Post by xxguitarist on 2009-11-22
Anyone?

---

### Post by xxguitarist on 2009-11-27
I'd really like to solve this :mrgreen:

---

