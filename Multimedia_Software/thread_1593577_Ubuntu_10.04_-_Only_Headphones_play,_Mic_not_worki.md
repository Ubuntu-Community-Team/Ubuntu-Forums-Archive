---
title: "Ubuntu 10.04 - Only Headphones play, Mic not working. On a laptop."
date: 2010-10-11
forum: Multimedia Software
---

### Post by Antonpup on 2010-10-11
Hello, I have been looking around for solutions for my two main problems, when I plug in Headphones into my laptop, speakers just die. And My microphone doesn't seem to be working at all.

Here are outputs for some basic commands:
aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
cat /proc/asound/card0/codec#* | grep Codec
```

Codec: IDT 92HD75B2X5
Codec: LSI ID 1040

```

My computer is Compaq Presario CQ61-410US.

Audio Driver in Windows 7 is IDT High Definition Audio CODEC.

Any advice?

Edit, I did something, and now my headphones don't work at all. And sound is coming out of speakers only, even if I plug headphones in. Help?

---

### Post by Antonpup on 2010-10-14
Umm.. Bump?

---

### Post by Antonpup on 2010-10-14
No help at all.. seriously?

---

### Post by przemek35 on 2010-10-18
> **Antonpup said:**
> Hello, I have been looking around for solutions for my two main problems, when I plug in Headphones into my laptop, speakers just die. And My microphone doesn't seem to be working at all.
 
Here are outputs for some basic commands:
aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```
cat /proc/asound/card0/codec#* | grep Codec
```

Codec: IDT 92HD75B2X5
Codec: LSI ID 1040

```
 
My computer is Compaq Presario CQ61-410US.
 
Audio Driver in Windows 7 is IDT High Definition Audio CODEC.
 
Any advice?
 
Edit, I did something, and now my headphones don't work at all. And sound is coming out of speakers only, even if I plug headphones in. Help?
 
did you try upgrading alsa to 1.0.23?

---

### Post by james_fried on 2010-10-24
Hi - I've got this problem as well on the same machine...

Regarding the speakers / headphones, I've found it's pretty random as to whether they switch over reliably on plug in of the headphones or not. I've usually just manually switched the output in the system > preferences > sound > output pane.

For the mic, I think the standard option is to update Alsa as per here : [http://ubuntuforums.org/showthread.php?t=1462123](http://ubuntuforums.org/showthread.php?t=1462123)

---

### Post by james_fried on 2011-01-19
An update on where I am with this...

Still not working :sad:

I'm now on 10.10 with the latest stable version of alsa 1.0.23 and I have had the microphone working for about five minutes, then closing a few programs so that my skype wouldn't be laggy and it died again... hasn't come back since.

Shame really - any other help or advice would be wicked.

J

---

