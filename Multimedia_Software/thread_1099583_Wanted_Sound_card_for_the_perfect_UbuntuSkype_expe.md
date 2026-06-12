---
title: "Wanted: Sound card for the perfect Ubuntu/Skype experience"
date: 2009-03-18
forum: Multimedia Software
---

### Post by achelis on 2009-03-18
Hi

It seems like getting Skype to work in Ubuntu is a common problem, and I am one of those who can't get it to work.

I remember seeing somewhere that the drivers for my onboard sound card might be the issue, so now I'm looking for a proper sound card with good Linux support - specifically one where I can use Skype (or Ekiga if I can get my friends to change :) ).

Suggestions welcome.

---

### Post by markbuntu on 2009-03-18
If you want toget skype working properly go here

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

Before you do that though, it is important that your microphone is working. If you want a quick and easy solution for skype just get a usb headset.

---

### Post by achelis on 2009-03-18
Thanks. I'll try a USB headset. And, yeah, problem is that I can't get the mic to work with my current sound card.

---

### Post by markbuntu on 2009-03-18
What sound card do you have?

---

### Post by achelis on 2009-03-19
An Onboard Sound card.

```

lspci | grep Audio

```

Gives:
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

```

Looking in my motherboard's manual gives:
```

Realtek ALC889A
High Definition Audio
2/4/5.1/7.1-channel
Support for S/PDIF In/Out
Support for CD In

```

No out of the box success with my USB headset by the way.

---

### Post by markbuntu on 2009-03-19
Try this for your usb headset

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

Look in here for getting your ALC889 mic working. The list is by machine but the links have more info for specific chips

[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)


[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

For more extensive troubleshooting and configuration help go here


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by achelis on 2009-03-19
Thanks a lot. I'm going away for the weekend, but will check out the guides when I come back.

---

### Post by acimmarusti on 2009-03-19
Skype works. The problem is that it doesn't like pulseaudio. So, whenever you want to use skype, make sure you've exited all other programs that use sound in anyway (including your web browser, unless the sites your visiting have no audio).

Then run skype and go to options > audio settings and instead of leaving it as default, choose your sound card (plughw) for output and input.

For the mic, you have increase its volume using alsamixer and increasing capture volume.

Hope this helps

---

### Post by achelis on 2009-03-23
Got it working with my USB headset now. Thanks a lot for the help, much appreciated.

---

### Post by kendon on 2009-04-28
you mind telling us the brand and model of the headset, if it is working fine?

---

### Post by markbuntu on 2009-04-28
I have a plantronics usb headset that works OOB. I am not sure about the model but it is the one with a separate usb dongle with headphone and mic jacks. It shows up as a c-media. 

I use my $100 Sony headphones with it.

---

