---
title: "green double vision for skype webcam with HP VGA 640x480"
date: 2009-12-08
forum: Multimedia Software
---

### Post by cwik on 2009-12-08
I have an IBM ThinkPad T41p running ubuntu 9.10 (i386) with an HP VGA 640x480 webcam (EW192AA).  When using skype 2.1.0.47 (installed either through medibuntu or the deb package from skype.com), I'd get video showing up in green.  It sort of looked like double vision, where I'd see 2 of myself stretched tall.

Running:
```
vim `which skype`
```

opens the executable file that is run when you run "skype" in the terminal.  The file (/usr/bin/skype) looks like this for me:

```
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype.real "$@"
```

This meant that by running "skype" from a terminal would already be doing the LD_PRELOAD "fix" that seems to work for everyone but me.  I swapped the v4l1compat.so with v4l2convert.so in /usr/bin/skype, and no luck.

I realized that I am indeed getting some video signal, and not just static, so I wondered if there was something wrong with frequency.  Poking around online led me to /home/<user login>/.Skype/<skype user name>/config.xml.  I read about some mystical <Video> section, but clearly, things are never that easy, and I didn't have a Video section :).  Found out the hierarchy for the Video section should be config -> Lib -> Video.  I added the green section below to my config.xml file (using vim, gedit, xedit, or your editor of choice):

```

<?xml version="1.0"?>
<config version="1.0" serial="67" timestamp="1260258773.0">
  <Lib>
    <Account>
      ...
    </Account>
    ...
    [COLOR="DarkGreen"]<Video>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <Fps>25</Fps>
    </Video>[/COLOR]
  </Lib>
  <UI>
    ...
  </UI>
</config>

```

And voila, it worked!  I guess it was trying to use some (wrong) default values, and I just had to tell it what to use.  I'm sure you can mess with the frames per second <Fps> value to improve/degrade quality for your own reasons.

---

### Post by oooh on 2010-03-04
Hi there 

I just solved it apparently because of the following:

In video voice calls the image is crap, double and stripped

But in the options menu, in test camera, I can see the image PERFECT

Any idea?

I have a Ricoh camera, from Sony VAIO, running on a r5u87x driver.

---

### Post by no2498 on 2010-03-04
hope this does not break skype for you
try your can in ekiga softphone you can set the color in it
if it still has 2 of you set it to 320x240 not 640x480
hope this helps

---

### Post by oooh on 2010-03-07
OK, deal done !

The problem was the version of skype. I installed the following skype version, and all went smooth: 2.1.0.81

    <Video>
      <AutoSend>1</AutoSend>
      <CaptureHeight>480</CaptureHeight>
      <CaptureWidth>640</CaptureWidth>
      <Fps>32</Fps>
      <RecvPolicy>callpolicy</RecvPolicy>
    </Video>

So it works fine now ! 

So the r5u87x driver is definitely better than the r5870, and the problem was being caused by skype it self.

---

