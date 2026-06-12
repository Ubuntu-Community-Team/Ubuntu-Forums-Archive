---
title: "Older vs Newer Nvidia video cards"
date: 2010-09-23
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by TBerk on 2010-09-23
There seems to be a lot of "My Nvidia doesn't work any more, now that I upgraded to 10.10...".

One thing I see happening is the jump to a conclusion that all video cards are alike.

I myself am running an Nvidia GeForce 5 series card.

[http://www.nvidia.com/page/fx_5200.html](http://www.nvidia.com/page/fx_5200.html)

 (My mother board uses AGP...). In my case, no Express-nothing, later family of chipsets nvidia goodness, just a decent video card that does what I need it to do. 

My current trouble is that I can not get the 'X' environment to load by default, my whole start up routine is to use the failsafeX option and choose 'restart X', which gets my to a gui log-in prompt, and if I currently check 'additional drivers' from the System pull down menu, I see that I have currently "Nvidia accelerated graphics drivers version current" and they are active.

(So, why cant I have this be the default, unattended login default?)

In any case, lets perhaps be more specific, both in the the body of the post, and in the subject line, to help differentiate just what you are working with.


I thank you.


TBerk
I keep having to remind myself, "it's a BETA version, and _I_ installed it myself..."

---

### Post by VinDSL on 2010-09-23
Hrm...

Well, if it was me, I'd purge all the canned Ubu nVidia drivers that came with 10.10

```
$ sudo apt-get --purge remove nvidia-*
```

That's what I did...  8-)

And, install [[COLOR="Red"]these drivers[/COLOR]]("http://www.nvidia.com/object/linux-display-ia32-173.14.27-driver.html") (click on the "Supported Products" tab to verify it works with your card).

I'm running a 7600 GT AGP, on a 7 year-old mobo, and the factory beta drivers are working great!

[IMG]http://vindsl.com/images/compiz-22-sep-2010.png[/IMG]

I guessing it's NOT an old nVidia card / AGP problem -- just a driver(s) issue.

---

### Post by cariboo on 2010-09-23
There is a driver for your video card [here]("http://www.nvidia.com/object/linux-display-ia32-173.14.27-driver.html").

---

### Post by TBerk on 2010-09-24
> **cariboo907 said:**
> There is a driver for your video card [here]("http://www.nvidia.com/object/linux-display-ia32-173.14.27-driver.html").


yeah, Thx. Both of you guys pointed me @ Nvidia for my board alright, but following the remove all and in non-gui mode reload just those drivers lead to a fail; nvidia-ro  (maybe? I've rebooted too many times since then....) 

Sorry I should be journaling this saga so I can relate it better but I'm back in low-graphics mode, running Synaptic and trying to get either the 173 or the NVidia-current to work.


TBerk

---

### Post by rasmus91 on 2010-09-24
sounds much like my problem. Try loking in your xorg.0.log file, to see what the error is.

sorry i can't be of any help, but its like my questions are just left hanging, unanswered.

---

### Post by TBerk on 2010-09-24
MuHahahahahahah

[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/173.14.27-0ubuntu1](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/173.14.27-0ubuntu1)

[http://www.ubuntuupdates.org/packages/show/219230](http://www.ubuntuupdates.org/packages/show/219230)

“nvidia-graphics-drivers-173” 173.14.27-0ubuntu1 source package in Ubuntu

I'll post a more detailed "How I did it" tomorrow, just now I'm off to watch videos again. In Maverick this time. (Will it deal with my failure to boot? Haven't rebooted yet.)

- SMPlayer (based on Mplayer) is reloaded and streaming w/o the jumps I was getting last night w/ xine.  Good enough for now.


TBerk

---

