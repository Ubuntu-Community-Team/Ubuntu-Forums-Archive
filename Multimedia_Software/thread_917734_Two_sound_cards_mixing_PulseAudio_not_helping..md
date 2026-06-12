---
title: "Two sound cards mixing? PulseAudio not helping."
date: 2008-09-12
forum: Multimedia Software
---

### Post by rick3878894 on 2008-09-12
So I have two sound cards installed. I went as far as installing pulse (How to said nothing about second sound card) audio and configuring it as my default mixer for every thing. Now my thinking was that pulse would allow me to do what I am trying to do but I think I missed some thing some where.

My gaol is to set up both sound cards to run mirroring each other. That is to say that the Mic and line ins on will mix together as well as the line outs. Some control over what program gets what would be cool but for my purposes just getting them input and output together would be awesome.

If you have dual sound cars any info including just dumping you config files on me would be nice. The more I know about this the better, I intend to do a lot more along these lines in the coming year. 

Thank you for reading. Have a freaking sweat day.

---

### Post by markbuntu on 2008-09-12
If you want to combine your sound cards you can use the pulseaudio combine module. 

Add these lines to your etc/pulse/default.pa:
```

#Make both card play simultaneously
load-module module-oss-mmap device="/dev/dsp0" sink_name=output0
load-module module-oss-mmap device="/dev/dsp1" sink_name=output1
load-module module-combine sink_name=combined master=output0 slaves=output1
set-sink-default combined

```

It is explained here:

[http://pulseaudio.org/wiki/Modules](http://pulseaudio.org/wiki/Modules)

Then you will see it in the PA Volume Control listed as Simultaneous Output.....like in the attachment below:

Then you can select it in Playback by right clicking on the stream and using move stream. I use it for my two sound cards and it works very well. They stay in sync and I can select which streams I want to go to each card or to both.

---

### Post by rick3878894 on 2008-09-17
Thanks man, worked like a charm. Well the input is still not working right but I think I will play with it a little more before I declear it broken.

---

### Post by markbuntu on 2008-09-17
You can look in my guide for more info. There is some info there about making some small changes that help the pulse-audio sink work better. There is a Pulseaudio-jack section near the bottom.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by rick3878894 on 2008-09-20
> **markbuntu said:**
> You can look in my guide for more info. There is some info there about making some small changes that help the pulse-audio sink work better. There is a Pulseaudio-jack section near the bottom.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Thanks I'll probably work on that a little later to night.

---

