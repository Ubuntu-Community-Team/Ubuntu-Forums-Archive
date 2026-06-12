---
title: "Set up external audio interface w/ Jack"
date: 2007-06-08
forum: Multimedia Production
---

### Post by sirwilliamjr on 2007-06-08
I just got Ubuntu Studio going last week, and was able to record audio and midi with Jack Control and Rosegarden, but was having some ground loop problems, so i bought an Edirol UA-1EX. I can set it as the device for playback/capture in Systems>Preferences>Sound, and I can select it as the in/out  for Audacity, and it works fine. All good so far...

 I can't, however, record w/ Rosegarden or Ardour, and I'm guessing it has something to do with running through Jack. Other than figuring out how to make connections between inputs and outputs, I don't know much about the Jack Connection kit. 

Anyone have any pointers for recording in Ardour or Rosegarden with my interface?

Thanks.

Will

---

### Post by eric71 on 2007-06-08
It's definitely an Alsa compatible device, meaning that Jack should also see it.  When setting up Qjackctl, you just have to make sure you select the correct input and output device. Ubustu recently had a nice article about Qjackctl setup:

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/#more-57](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/#more-57)

Just select the correct device (instead of default). It will probably be HW:1 for a USB device (whereas your 1st soundcard is usually HW:0).

---

### Post by sirwilliamjr on 2007-06-08
Thanks - that fixed it. I don't know why I didn't think to look under Setup...


Will

---

