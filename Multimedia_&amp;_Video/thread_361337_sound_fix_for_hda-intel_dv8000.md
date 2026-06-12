---
title: "sound fix for hda-intel dv8000?"
date: 2007-02-14
forum: Multimedia &amp; Video
---

### Post by simonsimon on 2007-02-14
Hi

I have an HP Pavilion dv8000 and I'm running edgy.  I finally fixed my sound yesterday.  It was the third time I'd lost it, but I finally fixed it by following a couple of guides.   

Unfortunately, I lost my sound again this morning!  Doing the same thing I did yesterday doesn't fix it.  

What fixed it yesterday was unistalling all the alsa stuff, reinstalling and then adding 
```
options snd-hda-intel index=0
``` 
to the end of alsa-base.   

That didn't work today.  I've also tried the acpi=off thing and editing etc/modules as suggested here:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)
[http://ubuntuforums.org/showthread.php?t=251877](http://ubuntuforums.org/showthread.php?t=251877)

...to no avail.  

I've also followed all the steps here:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)

What I'm wondering is if anyone has this computer and knows the exact steps that will fix this problem.  

Here's some more info:
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 30a5
        Flags: bus master, fast devsel, latency 0, IRQ 74
        Memory at d2400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```

I should also mention this is not a muted volume in alsamixer problem.  

Help would be ENORMOUSLY appreciated.  I'd love to fix this problem for good.

Thanks

---

### Post by simonsimon on 2007-02-14
You're all going to think I'm crazy...

Shortly after posting I was trying to figure out what I did differently yesterday.  The only thing I could think of was that I had shut the laptop down and unplugged it for a while.

So I shut down and unplugged my laptop for a good thirty seconds, turned it back on and, um, sound.  

Weird!?

Is this just a coincidence or is there a difference between a reboot and a shutdown+unplugging?

Thanks again.

Your most humble noob,
Simon

---

### Post by simonsimon on 2007-02-14
Update...

I changed absolutely nothing.  I shut my laptop down and brought it to work.  Turned it on and no sound.

---

