---
title: "Two different ALSA or OSS inputs in jack?"
date: 2006-10-09
forum: Multimedia &amp; Video
---

### Post by eric71 on 2006-10-09
I've been using Ubuntu for quite awhile, now playing around with edgy eft.  I also try and record simple music from time to time.  On Windows I use Kristal as a multitrack recorder with VST effects.  It's the only thing I still use Windows for. I've recently begun playing with Ardour to see if I can do similar multitrack recording with LADSPA effects in Ubuntu. 

I often do recording and mixing at night and have to be quiet.  With Kristal I plug my guitar in the computer soundcard's mic input, and set the main output to a USB headset.  I sometimes also use the USB headset for recording comments or vocals. With Ubuntu I can do something similar in Audacity(an OSS progam, I guess), choosing dsp(the soundcard mic) for input and dsp1(the usb headset) for output. I just can't seem to do the same for Ardour.  The USB headset doesn't show up as an input or output device in jack, whether I run jackd with the ALSA or OSS driver option. I only get two outputs, one for the left channel and one for the right of the computer's soundcard. I know the USB headset functions well in Ubuntu.

In the Gnome Volume Control (Alsa mixer), I can select either the soundcard or the USB headset.  Can Jack use both at once, like Kristal in Windows or Audacity in linux, or will I only be able to use one at a time?

Thanks,

Eric

---

### Post by eric71 on 2006-10-09
I think I answered my own question by studying the image in the wiki tutorial about qjackctl configuration.  Seems I can choose a different device for input and output.

Which leads me to the problem of recording through my soundcard and my USB headset mic at the same time.  If I can only choose one input device in qjackctl, is this possible? Maybe I have to have two instances of jackd running? i.e., how can I use 2 different input devices at the same time? I'd like to record my guitar through the soundcard while my friend records vocals through the usb mic.

Thanks.

---

### Post by zettberlin on 2006-10-09
I do not think, that this is possible at the moment. I read some "2 soundcards with jackd at the sametime"- threads on the linux-audio-list quite often and I had the impression, that something as inferior regarding quality and sync as cascaded soundchips makes the jack-folks hair stand up ;-) Of course you can choose to use your headset (that would be "hw1" in the interface-chooser of qjackctl as your sessions audiodevice yet I dont think, you can use the soudcard at the same time for in and out.

Word is said, that there is a way to hack alsa.rc to do such tricks yet this is a crude way to solve this....

---

### Post by eric71 on 2006-10-10
I only had a few minutes to play with my laptop last night, but I was able to start 2 instances of qjackctl (and presumably 2 instances of jackd).  In the qjackctl setup for each instance I was able to choose a different input device.  I didn't have a chance to look at the connections and see if anything useful actually came from it though. If it does work, I'm sure syncing won't be great, but at least I'll feel better about not being stuck with Kristal and Windows.  What I really need to do is buy a real professional soundcard with multiple inputs if I want to get serious about recording. 

I've also found tutorials on making ALSA see the two devices as one, but I'm afraid I would mess up my sound for my everyday apps in favor of my music hobby.

Thanks,

Eric

---

