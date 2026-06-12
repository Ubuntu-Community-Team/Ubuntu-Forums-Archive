---
title: "Please help: Sound stopped working"
date: 2011-11-06
forum: Multimedia Software
---

### Post by izak on 2011-11-06
Hi all 
My multimedia PC is a couple of years old and runs ubuntu 9.10 without problems... until recently when the sound stopped working.

**What could have caused this**:
1) prior to the sound failure, the old nvidia graphics card I had broke, so I took this out and switched to the onboard graphics.

This either caused some software configuration change that also affected the sound or, in touching the motherboard the onboard sound might have become damaged. 

**What I have tried so far**:
1)In the GUI under sound->preferences the volume is enabled ajd not muted
2) Tried plugging in my headphones into all possible front and back sockets (it is not clearly indicated which socked it for sound output vs input on my motherboard)
3) To eliminate possibility of software problem, I loaded a boot CD of an older version of Ubuntu (which in the past gave me sound) - no sound.
4) Then I thought it must be hardware related - so a friend gave me an old soundblaster16 card. Insert it into PC and in GUI under Sound->Preferences I now have a second  soundcard (also listed under hardware tab as "Internal audio, 1 Output/1 Input Analog stereo duplex). This is exactly the same description as my onboard sound, so I was not sure which one Ubuntu was using - tried both of them, but neither caused any sound to come out of any of the sockets on the soundcard.Now I am thinking that this is a software problem again.
5) Removed the souncard and read the "Comprehensive Sound solution problem sticky. The results are (manually typed over- so there might be a type here and there)
```
aplay -l
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
Subdevices 4/4
card0: V8237 [VIA 8237]: device 1: VIA 8237 [VIA 8237]
Subdevices 1/1
```

```
lspci -v
00:11.5 Multimedia audio controller: VIA technologies, Inc. VT8233/A/8235/8237 A
C97 Audio controller (rev 60)
Subsystem: Biostar michrotech intl corp device 8212
Flags: medium devsel, irq 22
i/o ports at d200 [size=256=]
capabilities:<access denied>
Kernel driver in use: VIA 82XX Audio
Kernel modules: snd-via82xx
```

```

lsmod
snd_mpu401     9288 0
snd_mpu401_uart 8480 2 snd_via82xx, xnd_mpu401
```

Could anyone please help me debug this sound problem. No sound from both onboard and soundcard makes it seem unlikely that this is a hardware problem...

---

### Post by izak on 2011-11-07
Maybe I scared people off by giving too much information in my initial post :(.

What I am going to try next is to confirm whether the SoundBlaster16 soundcard still works by plugging it into a different PC, then I can at least eliminate hardware problems.

---

