---
title: "HVR-2250 Analog Status ???"
date: 2011-04-22
forum: Mythbuntu
---

### Post by rabid_gnome on 2011-04-22
I seem to remember a post on this forum with step to get the analog tuners on the HVR-2250 working, but can not seem to find it. Was I mistaken? will this card still only work in digital mode?

Thank you for any help

---

### Post by LowSky on 2011-04-22
Search is your friend
[http://ubuntuforums.org/showthread.php?t=1567490](http://ubuntuforums.org/showthread.php?t=1567490)

Last I checked it basically works, I think, but in doing so you sorta lose function of half the tuner capability. One analog on digital, not two and two.

Honestly development is slow because very few need analog support these days. The spectrum is near dead. I feel bad for the people who live in towns with cable companies that didn't upgrade. it just as bad as the places that still don't have high speed internet (which probably are the same towns).

---

### Post by agamotto on 2011-04-23
True, but you are forgetting about all of the countries that are nowhere near converting...

---

### Post by rabid_gnome on 2011-04-23
Thanks that was the thread I was looking for. I will try out what they came up with and post the status.

I need analog support, as the cable in my college housing is analog only for some reason.

---

### Post by rabid_gnome on 2011-04-24
Well no luck. Like many people in that thread I have been able to get digital working and analog working in mplayer by manually setting the frequencies. However no luck getting mythtv to recognise any of the channels. I even tried to manually enter the channel frequency with no luck. If anyone has any idea I would appreciate it. I have attached the results of running **dmesg | grep saa7164** which look good to me.
```

[   22.145731] saa7164 driver loaded
[   22.145777] saa7164 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   22.146874] CORE saa7164[0]: subsystem: 0070:8851, board: Hauppauge WinTV-HVR2250 [card=7,autodetected]
[   22.146880] saa7164[0]/0: found at 0000:06:00.0, rev: 129, irq: 17, latency: 0, mmio: 0xfb800000
[   22.146885] saa7164 0000:06:00.0: setting latency timer to 64
[   22.341646] saa7164_downloadfirmware() no first image
[   22.341654] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
[   22.396955] saa7164_downloadfirmware() firmware read 4019072 bytes.
[   22.396958] saa7164_downloadfirmware() firmware loaded.
[   22.396965] saa7164_downloadfirmware() SecBootLoader.FileSize = 4019072
[   22.396971] saa7164_downloadfirmware() FirmwareSize = 0x1fd6
[   22.396972] saa7164_downloadfirmware() BSLSize = 0x0
[   22.396973] saa7164_downloadfirmware() Reserved = 0x0
[   22.396978] saa7164_downloadfirmware() Version = 0x1661c00
[   29.695380] saa7164_downloadimage() Image downloaded, booting...
[   29.805284] saa7164_downloadimage() Image booted successfully.
[   32.143271] saa7164_downloadimage() Image downloaded, booting...
[   33.791857] saa7164_downloadimage() Image booted successfully.
[   33.852522] saa7164[0]: Hauppauge eeprom: model=88061
[   34.536246] DVB: registering new adapter (saa7164)
[   37.806671] DVB: registering new adapter (saa7164)
[   37.806996] saa7164[0]: registered device video0 [mpeg]
[   38.036981] saa7164[0]: registered device video1 [mpeg]
[   38.247461] saa7164[0]: registered device vbi0 [vbi]
[   38.247492] saa7164[0]: registered device vbi1 [vbi]
```

edit:
So at this point I can change the channel with:
**ivtv-tune -c <channel number>**
and watch the channel with:
**mplayer /dev/video0**

I can also record the channel by using:
**cat /dev/video0 > save.mpg**

Since all of this is working am I wrong in believing that the card is set up fine, and the problems are with how I have mythtv setup?

---

