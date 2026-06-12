---
title: "USB guitar and jack"
date: 2010-09-26
forum: Multimedia Software
---

### Post by bobosoft on 2010-09-26
Hello,

under 10.04 I can't get my iAxe 624 USB guitar to work. I clearly remember it was working under 9.04, but now it does not.

First of all, from sound preferences everything seems fine

[IMG]http://www.inf.unisi.ch/postdoc/bruttomesso/shot1.png[/IMG]

USB sound card is recognized. Also if I try the input volume

[IMG]http://www.inf.unisi.ch/postdoc/bruttomesso/shot2.png[/IMG]

it seems to receive some input from the guitar.
When I run Jack however, even though it starts without any problem, I can hear no sound :(

[IMG]http://www.inf.unisi.ch/postdoc/bruttomesso/shot3.png[/IMG]

As I said, I made it to work once with 9.04, so I don't see why now it does not anymore ...

Thanks in advance for your time !
Roberto

---

### Post by bobosoft on 2010-09-26
The problem might be connected with some ALSA settings: alsamixer says that there is no capture device associated with the guitar's USB card

[IMG]http://www.inf.unisi.ch/postdoc/bruttomesso/shot4.png[/IMG]

is it somehow possible that I need to install something else from alsa ?

---

### Post by bobosoft on 2010-09-26
if it helps this is the output of amixer

[IMG]http://www.inf.unisi.ch/postdoc/bruttomesso/shot5.png[/IMG]

---

### Post by cchhrriiss121212 on 2010-09-26
Do you get anything from arecord -l?

---

### Post by bobosoft on 2010-09-26
> **cchhrriiss121212 said:**
> Do you get anything from arecord -l?

hi crhis, this is what I get

```

card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by cchhrriiss121212 on 2010-09-26
In jack setup you have input and output as hw:1, do you get anything if you select hw:0 (which will be your onboard sound) for your output?

---

### Post by bobosoft on 2010-09-26
No I can't hear anything ... notice that when the output card actually works if I set it as "main" output in sound preferences (i.e., I can hear system sounds, skype sounds etc. from the USB card output)

---

### Post by cchhrriiss121212 on 2010-09-26
May I ask what other programs you are using with jack? 
Do you know that you need to manually connect everything up using the connect window?

---

### Post by bobosoft on 2010-09-27
> **cchhrriiss121212 said:**
> May I ask what other programs you are using with jack? 
Do you know that you need to manually connect everything up using the connect window?

yes I know, I was trying to use tuxguitar, guitarx, and other software for guitar ...

anyways, yestarday I tried to install audacity and I was able to record a track using the guitar (without jack). However now jack does not work anymore ... I think I totally messed up the sound system with purging and reinstalling stuff. I will reinstall linux, it's much easier for me

Thanks for your help so far ! I'll tell if I get the same problem after reinstalling

Roberto

---

