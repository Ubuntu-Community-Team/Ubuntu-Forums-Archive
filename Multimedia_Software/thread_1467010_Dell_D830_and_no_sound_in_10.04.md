---
title: "Dell D830 and no sound in 10.04"
date: 2010-04-30
forum: Multimedia Software
---

### Post by nixIT on 2010-04-30
Hello all,

I have been running 9.04 since, well, last year, and it took me a while to get the sound working.  I grabbed the 10.04 Live CD to give it a shot, an wouldn't you know it, no sound.  Though 10.04 looks AMAZING!

A big part of my job has me in a storage closet in the basement of our office and with sound/music to play, my day would be unbearable.  

I know the live CD isn't the same as installing fresh, but I've also seen many posts from people with laptops not having sound.  Any idea how to get the sound working?

I would love to upgrade, but will need to get the sound working pretty quickly.

any ideas would help out.  then again, I may do a fresh install this weekend and give it a shot, so hopefully someone will find a solution by the end of the weekend.

--nixIT

---

### Post by dino99 on 2010-04-30
need to know the exact sound hardware to help you

but you can install paprefs and gnome-alsamixer then check the settings (apps sound)

---

### Post by nixIT on 2010-04-30
Here is the output of aplay -l

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by nixIT on 2010-05-03
Update.

I installed Lucid on my laptop this weekend, and I had sound, however when I plug the laptop into the docking station my sound no longer works.  Any idea?

--nixIT

---

### Post by AvantSavant on 2010-08-15
I don't know if you got this worked out or not, but this happens because the sound output is set for the digital output of the Dell docking station.  You can only hear this output when the laptop is docked, otherwise you need to set the sound output to analog to hear it through the speakers.  

I'm working on a way to set up docking profiles that will change the audio configuration, video settings and network adapter.  No elegant solutions yet.

---

