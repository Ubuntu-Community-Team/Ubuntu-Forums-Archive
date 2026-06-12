---
title: "USB Audio Mixer Problems"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by arcadia on 2008-03-12
I am attempting to use my Altec Lansing FX5051 USB speakers in Ubuntu Hardy. Opening up Volume Control, I find that File > Change Device > lists the speakers (Alsa Mixer), and so I switch to them. However, when I do so, I am unable to adjust the volume. It simply stays locked at 100%. I can configure Ubuntu to play sound through these speakers, but again, at nothing less than full volume.

I can say that these speakers work in Windows out-of-the-box without any additional drivers, so I am assuming there is some generic driver for them and that it _should_ be possible to get them working in Ubuntu, but I have had no luck so far finding one.

Thanks so much in advance for any help or advice you can offer, but in doing so, keep in mind that I am pretty new to Linux and might need some specific instruction if you have any.

---

### Post by breakerfall on 2008-03-19
well, i wish i had an answer for you...

I have some Altec Lansing XT1 speakers, and the the ubuntu sound mixer, i am unable to get both halves of the main audio volume to slide at the same time.  as a matter of fact, the left channel will only go up one 'notch' from the bottom, but i can move the right side wherever i want...

thus, i only really get sound from the right side speaker!

works well in vista (ugh) and the speakers sound ridiculous for such a small set!

---

### Post by breakerfall on 2008-03-20
okay, now i dunno if my fix is applicable to the OP, but i seem to have fixed my half-audio issue.

i used kmix.

actually, first i did:
asoundconf list

then:
asoundconf set-default-card Audio

where Audio was what was in the list that wasnt obviously my pci sound card...

then i started kmix, even though im in gnome...  the deal (i think) here is that since kmix doesnt separate the left and right channels into separate sliders like the gnome vol control does, i am able to raise and lower the volume correctly...

good luck, OP!

---

### Post by atrus on 2008-04-20
Just filed this one:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/219990](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/219990)

---

### Post by tripple_face on 2008-05-02
i have the same problem too.. any updates, atrus?
thanks

---

### Post by atrus on 2008-05-03
> **tripple_face said:**
> i have the same problem too.. any updates, atrus?
thanks
Nope, no change. I did file upstream, but haven't heard anything yet:


[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3841](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3841)

---

### Post by acheong87 on 2008-05-07
I used to have this working in Gusty Gibbon (7.10), but once I upgraded to Hardy Heron (8.04)... I can't seem to figure it out.  I have Altec Lansing XT1 Speakers as well.

@breakerfall - I have the same issue about left/right volume control.  Here's what I do.  I set the right volume at about 90%, letting the left one fall.  Then, I increase the left volume until it matches 90%.  After that, I don't touch these settings, and just control volume from RhythmBox/Totem/etc.

If I figure out how I did it for Gusty Gibbon, I'll let everyone know...

---

### Post by santogiuseppe on 2008-05-22
[QUOTE=acheong87;4901394]
(cut)

@breakerfall - I have the same issue about left/right volume control.  

(cut)


The same weird problem with m-audio usb soundcard :(

the problem IMHO is the gnome mixer applet (on ubuntu hardy), i just installed the gamix package and the sound volume is perfectly adjustable
it is not too much comfortable to launch a program just for the volume control, but better than nothing until the applet is not fixed :(

---

### Post by Ron F. on 2008-06-03
Boy this is irritating. I had this problem with Gutsy, and just assumed it would be fixed in the future. I guess we cannot expect working volume control in Linux.:frown:

Anyway, I got it to work by noticing that the microphone control was muted. So, I unmuted the mic, and then I could, one time only, move the left volume slider up to the top. I did that, and then linked the left and right volume controls together. I then got greedy and tried to slide them together ... the left side fell back down to zero. I could not fix it again until I muted, and then unmuted the mic volume again on the left side of the panel - and then I had one chance again to set the USB speaker volume.

Is this nuts or what? I set left-right to max, and I moderate the volume in Amarok. I won't touch it again until it is time to upgrade to Intrepid. Until then its to time to :guitar:

-Ron

---

