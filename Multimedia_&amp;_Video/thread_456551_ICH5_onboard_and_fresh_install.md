---
title: "ICH5 onboard and fresh install"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by madmalice on 2007-05-27
What else, no sound! After a month of learning wireless networking to the hilt and being so happy to get online (router to router with dd-wrt) my fresh install of ubuntu killed my onboard sound...

madmalice@madmalice-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and in my lspci listing its there!

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

So I know my driver is intel8x0

nothing is muted that shouldn't be and I checked my headphone jack sense, line in, mic,  etc to make sure they are muted

Install ubuntu again? I have gotten sound automatically on previous installs, although my x-fi card is still plugged in a pci slot is that my problem? 

(edit: no my speakers are not plugged in to that card)

Do I Need to file a bug claim?

I really don't know what else I can try besides reinstalling everything again ( I didn't notice for a while that my sound didn't work and I installed most everything I needed already, aye [grins] ) and everything looks ok.

I am so sad!

=)

---

### Post by MrFSL on 2007-07-01
Mine doesn't work either ... 

Same issue.

All the correct modules are loaded and nothing is complaining, just no sound output.

I have an Intel D865GLC motherboard.

If you find a solution please let me know.

---

### Post by MrFSL on 2007-07-01
I found a solution to my issue:

[http://ubuntuforums.org/showthread.php?t=489697](http://ubuntuforums.org/showthread.php?t=489697)

---

