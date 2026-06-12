---
title: "USB sound card problems"
date: 2010-03-24
forum: Multimedia Software
---

### Post by Donny Bahama on 2010-03-24
I'm running XBMC (Ubuntu Karmic) on my HTPC which is using an M-Audio Transit USB as its soundcard. 

lsusb returns:
```
Bus 005 Device 003: ID 0763:2806 Midiman M-Audio Transit DFU
```
so it's being recognized properly. But aplay -l returns:
```
aplay: device_list:223: no soundcards found...
```

Per [this thread]("http://forum.xbmc.org/showthread.php?t=42955"), I edited /etc/modprobe.d/alsa-base.conf so that the first autoloader alias reads:
```
install sound-slot-0 /sbin/modprobe snd_usb_audio
```
but that didn't seem to do the trick.

Help?

---

### Post by Donny Bahama on 2010-03-24
I've made a bit of progress. Using the suggestions [here]("http://ubuntuforums.org/showthread.php?t=1216581"), I got the card to show up properly when I execute aplay -l. But I still have no sound, and alsamixer returns:
```
alsamixer: function snd_ctl_open failed for default: No such file or directory
```

---

### Post by Donny Bahama on 2010-03-24
I must be very close...
```
speaker-test -D plughw:1,0 -c2
```
gives me pink noise alternating between left and right front speakers.

---

### Post by Donny Bahama on 2010-03-24
GOT IT!!! [http://forum.xbmc.org/showpost.php?p=442512&postcount=3](http://forum.xbmc.org/showpost.php?p=442512&postcount=3)

---

