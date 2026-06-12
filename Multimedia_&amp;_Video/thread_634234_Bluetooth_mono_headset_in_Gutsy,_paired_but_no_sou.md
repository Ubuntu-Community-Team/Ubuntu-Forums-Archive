---
title: "Bluetooth mono headset in Gutsy, paired but no sound"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by sceo on 2007-12-07
I'm pretty sure I've managed to pair my bluetooth device using gbtsco.  It asked for the password, etc.  hcitool dev shows:
```
Devices:
        hci0    00:02:72:B0:00:26

```

hictool con shows the active connection to my headset
```

Connections:
        < SCO 00:03:89:ED:D6:C6 handle 0 state 5 lm SLAVE 
        < ACL 00:03:89:ED:D6:C6 handle 3 state 1 lm MASTER 

```

but when I run
```

**aplay -B 1000000 -D plughw:Headset /usr/share/sounds/login.wav **
Playing WAVE '/usr/share/sounds/login.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Aborted by signal Interrupt...

```

as you see - nothing really happens... no sound in the headset (once I kinda got static maybe?) - but else, it seems normal/fine/correct.

any assistance you can offer would be mucho appreciated!

incidentally, it's a plantronics 330 headset and an IVT Blue Soleil type dongle

---

### Post by glennric on 2007-12-08
You might try adding the line
```
options hci_usb force_scofix=1
```
to the file /etc/modprobe.d/bluez
I was having troubles getting anything to play to a headset until I added that.  You may have to reboot for this to take effect.  Either that or remove the bluetooth dongle (if you can) and do 
```
sudo modprobe -r hci_usb
```
Then reinsert the dongle

With that I can play to or record from the headset once.  Then there is a beep in the headset and I can get no further response from it until I unplug the dongle and plug it back in again.

---

### Post by sceo on 2007-12-09
Thanks for the reply.  I think that that's just making it use snd-bt-sco, which I was doing before anyway.  I can get SOMEthing (kinda staticy) in the earpiece the first time I try:

```
aplay -D plughw:Headset /usr/share/sounds/login.wav
```

But, then I ctrl-C the player and it doesn't work.  I see [this]("http://forum.skype.com/index.php?showtopic=103677") on the Skype forums, but my (very similar) problem is that aplay won't work either.

I think I'm currently in some kind of hodgepodge'd version of using btsco and bluez. :(

---

### Post by hrabeX on 2007-12-10
I have exactly the same problem.
```

$ btsco -r -f -v 00:0C:78:17:C5:4F
btsco v0.42
Device is 1:0
Voice setting: 0x0060
RFCOMM channel 1 connected
Using interface hci0
$ aplay -D plughw:Headset /usr/share/sounds/KDE_Startup.wav
P&#345;ehrávám WAVE '/usr/share/sounds/KDE_Startup.wav' : Signed 16 bit Little Endian, Rate 22050 Hz, Mono

```
and I have no sound. I have added above described Option line in /etc/modprobe.d/bluez, but with no results. Any help is appreciatded.

---

