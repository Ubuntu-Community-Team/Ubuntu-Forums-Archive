---
title: "Simply cannot get my mAudio Ozone USB working. :L"
date: 2006-12-14
forum: Multimedia &amp; Video
---

### Post by mrthingy on 2006-12-14
Hi everyone,

I'm trying to get my M-Audio Ozone working with ALSA, and I've done absolutely everything I can think of to get it to work, but to no avail. 

It's detected instantly in 64Studio, a Debian distro, so I know that this card has drivers, and that it provides some good low latency with Jack. 

So far, I have:

1. Completely compiled, built and installed the latest (stable) alsa-libs, alsa-driver (--with-usb-audio), alsa-utils and alsa-firmware. No errors. All seems to install fine.
2. Installed the mAudio firmware, which I believe is required. [http://usb-midi-fw.sourceforge.net/](http://usb-midi-fw.sourceforge.net/) (attaches itself to UDEV)

Here is what I get from lsusb:
```
Bus 004 Device 007: ID 0763:2808 Midiman
```

Device Manager (System->Administration menu) used to show the Ozone (both the name and as USB Audio capable). Now it just says "Unknown".

"cat /proc/asound/cards" was showing the Ozone for a while, but now just says "--- no soundcards ---", which is bizarre, as I have done nothing that would change that. 

I'm kinda at my wits end and about to just give up. I don't understand how this can foul up so badly, when a quick install of the firmware was all that was needed in 64studio. Please give any assistance you can, as I have completely hit the end of the road with regards to ideas. :(

---

