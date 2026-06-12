---
title: "JACK will not start"
date: 2006-11-23
forum: Multimedia &amp; Video
---

### Post by bramvandijk on 2006-11-23
Hi,

I'm trying to set up JACK, and I got it to start once, but now I get the following message

> creating alsa driver ... default|default|1024|2|44100|0|0|nomon|swmeter|-|32bit
configuring for 44100Hz, period = 1024 frames, buffer = 2 periods
You appear to be using the ALSA software "plug" layer, probably
a result of using the "default" ALSA device. This is less
efficient than it could be. Consider using a hardware device
instead rather than using the plug layer. Usually the name of the
hardware device that corresponds to the first soun
ALSA: cannot set period size to 1024 frames for capture
ALSA: cannot configure capture channel
cannot load driver module alsa
no message buffer overruns
09:48:57.049 JACK was stopped successfully.
09:48:59.176 Could not connect to JACK server as client. Please check the messages window for more info.

In the setup of qjackctl I tried to change the frames per second to each possible value but I just get the same error with another framerate. 

I just have a crappy AC97 on-board soundchip, but since I got it to work once, it should be able to handle JACK. I followed
[https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation) and I think it worked then, and then I tried 
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)
after which I got this error message. So I tried putting the settings back to what I think think they were before, but the error will not go away. My current settings can be seen here:

[http://ubuntuforums.org/gallery/showphoto.php?photo=4090&cat=500](http://ubuntuforums.org/gallery/showphoto.php?photo=4090&cat=500)

Help will be very much appreciated!

---

### Post by bramvandijk on 2006-11-23
It works!
I had to change interface to hw:0 instead of default!

Now the next bit, I thought that qsynth would play midi files,
but now it seems like I need another program to play the midi file, and the plug the midi output into qsynth, which can be done with JACK.

Which program can do that, play midi files so I can plug them into qsynth?

---

### Post by pussi on 2006-11-23
I pretty sure rosegarden should be able to do that

---

