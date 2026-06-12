---
title: "USB sound card missing after Edgy upgrade"
date: 2006-11-14
forum: Multimedia &amp; Video
---

### Post by cronholio on 2006-11-14
I have a sound card which seems to be connected via USB internally. It worked well in Dapper. I dist-upgraded to Edgy and now the OSS device in the mixer is gone and I have no sound at all. XMMS shows this at startup:

```
** WARNING **: alsa_get_mixer(): Attaching to mixer hw:0 failed: No such device
```

This is the output of "aplay -l".

```
**** List of PLAYBACK Hardware Devices ****
card 1: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Obviously, lspci doesn't show the device but lsusb does.

```
  idVendor           0x0d8c C-Media Electronics, Inc.
  idProduct          0x0201 
  bcdDevice            0.10
  iManufacturer           0 
  iProduct                2 PnP Audio Device 
```

There are 2 drivers listed for this manufacturer on the ALSA website: [http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-C-Media](http://www.alsa-project.org/alsa-doc/index.php?vendor=vendor-C-Media)

Inserting the 8330 driver fails. I can insert the other one but it doesn't change a thing. Any idea where to go from here?

---

### Post by cronholio on 2006-11-14
Anybody?

---

### Post by cronholio on 2006-11-14
Okay, just in case somebody is having the same problem, here is how I solved it: in ~/.asoundrc there was a line 

```
pcm "hw:0,1"
```

which should have been

```
pcm "hw:1,0"
```

as shown above by aplay. I changed it and it works now.

---

### Post by Alukurd on 2006-11-16
Well I have the same motherboard as you "ASRock 939Dual-VSTA" 
I still have the weird sound on playback, how did you fix that problem? it seems that all you have this motherboard has the same problem, thinking of getting a Creative SB Audigy SE as a last resort :(

---

### Post by cronholio on 2006-11-16
I don't have any weird sound. Are you referring to this problem: [http://ubuntuforums.org/showthread.php?t=278341](http://ubuntuforums.org/showthread.php?t=278341)

It can be solved by creating a file called .asoundrc in your home folder. For your mainboard, the file should look like this:

```
pcm.!default {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:1,0"
        period_size 1024
        buffer_size 8192
        rate 44100
    }
}
```

If you run Dapper, change "hw:1,0" to "hw:0,1". If that doesn't help, feel free to contact me so we can compare our setups.

---

### Post by Alukurd on 2006-11-17
> **cronholio said:**
> I don't have any weird sound. Are you referring to this problem: [http://ubuntuforums.org/showthread.php?t=278341](http://ubuntuforums.org/showthread.php?t=278341)

It can be solved by creating a file called .asoundrc in your home folder. For your mainboard, the file should look like this:

```
pcm.!default {
    type dmix
    ipc_key 1234
    slave {
        pcm "hw:1,0"
        period_size 1024
        buffer_size 8192
        rate 44100
    }
}
```

If you run Dapper, change "hw:1,0" to "hw:0,1". If that doesn't help, feel free to contact me so we can compare our setups.

Naw, still the same problem ](*,) 
you mean the hardware setup or the configfile?

---

### Post by cronholio on 2006-11-20
> you mean the hardware setup or the configfile?

Both, if needed. What exactly do you mean by weird sound?

---

