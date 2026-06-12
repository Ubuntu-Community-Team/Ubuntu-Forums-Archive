---
title: "Problems with Sound 9.04 (There's sound, but weird)"
date: 2009-05-01
forum: Multimedia Software
---

### Post by Mandala 13 on 2009-05-01
Hi! I know that the Sound Problems in 9.04 are just saying that there's Global Warming; we all know about it, and all. But reading some of the problems that are posted here and there, I have realized that maybe, my problem might be slightly different, considering that I do have some sound coming out, but it's a creepy-kinda-sound, like bells or something like that. 

Now, officially, when I installed the 9.04, I had no sound whatsoever. Then, I followed this guide of [Sound Solutions for 9.04]("http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html") and after a while, reboot computer and surprise, I had some sound in the Startup Window. But well, nothing more.

Then, I end up following all the instructions of that Sound Solution and now I have the mute on, 'cause of that weird sound. Tried following the Comprehensive Sound Problem Guide on the Sticky Note but couldn't exactly find where to look for the driver, and even more, there's sound; it's just that is not the right sound that should be coming out, hehe.

So, I would like to know if someone else have a similar problem. Thanks! Here's some info:


mandala13@Amaterasu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
mandala13@Amaterasu:~$ 
mandala13@Amaterasu:~$ 

lspci
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Toshiba America Info Systems Device ff10
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at c0003400 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

Anything else that you might need, just ask. I might be a partial noob, but at least there are some things that I can do, hehe.

Mandala13


Just have something to add, that I didn't say in the first place. When I get this weird sound, the only way to turn it off is with the Volume Control of the Pulse Audio Device Chooser. In other words, regarding the volume controls of the Ubuntu itself, of the computer, that's not controlling any sound whatsoever. Not sure if I'm getting myself clear, but it's like the computer still has no sound, only that one that Pulse Audio is giving, although is a bad one, :) Just thought I needed to add that little thing.

---

### Post by psyke83 on 2009-05-01
Please follow my linked guide on PulseAudio. It's possible that your PCM mixer is set to 0%, which causes crackles to emanate from your speaker while audio is playing. It's explained in the guide.

You may also be suffering from an ALSA kernel bug. See: [http://ubuntuforums.org/showpost.php?p=7181380&postcount=1245](http://ubuntuforums.org/showpost.php?p=7181380&postcount=1245)

---

### Post by Mandala 13 on 2009-05-02
> **psyke83 said:**
> Please follow my linked guide on PulseAudio. It's possible that your PCM mixer is set to 0%, which causes crackles to emanate from your speaker while audio is playing. It's explained in the guide.

You may also be suffering from an ALSA kernel bug. See: [http://ubuntuforums.org/showpost.php?p=7181380&postcount=1245](http://ubuntuforums.org/showpost.php?p=7181380&postcount=1245)


Well, I followed your guide and funny enough, I just had to put all the audio options in Auto Detect and I had my sound working all right: System, music, etc. The only problem is that after a few second hearing a song, it crashes and start with the whole cracking again, and I have to reset. Or there are times that it don't work at all.

So, now that I the sound is working, somewhat, what to do for fixing it completely? Anything you would like from me now?

Mandala13

---

### Post by Mandala 13 on 2009-05-02
Ok, now, I don't even know if someone is reading this, but well...

Just discovered something thing. Ok, sound systems okay and I already told you that trying to put some music, sound crashed. But additionally, I just realized two grave things:

1) Even Flash Sounds in websites make the sound to crash.
2) When the sound crash, the wireless connection also crash, for some reason that I don't seem to understand. And the only way to get it back, is disabling Wireless connections with the icon in the panel, then enabling again (and because after disabling, no wireless connections appear), restarting computer and voila, there's internet again... and sound, until I play a song, or something else happens. 

System's sounds are the only one, in this moment, that can work without making either sound or internet to crash.

Any help or ideas on why both things, wireless and sound, are so linked?

Mandala13

---

### Post by Wi7ahc4l on 2009-06-08
I'm suffering from almost identical problems. I also have an ATI chipset as well!
here is my aplay -l 
```
logan@logan-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
logan@logan-laptop:~$
```

---

