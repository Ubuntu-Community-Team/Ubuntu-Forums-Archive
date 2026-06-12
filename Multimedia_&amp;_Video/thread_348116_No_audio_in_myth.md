---
title: "No audio in myth"
date: 2007-01-28
forum: Multimedia &amp; Video
---

### Post by J0ris on 2007-01-28
Hi,

I recently installed Mythtv following a How-To in the Ubuntu documentation pages ([https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend")). Many things work, others do not. Audio, for instance does not. 
First things first: I have a Asus A8M-VM CSM motherboard with onboard nVidia-based audio and a Hauppauge hvr1100 dvb-t video capture card. Audio seems to have installed smoothly. For instance, when I do an 'aplay -l' it outputs one analogue and one digital nVidia device (AD198x)) on Card 0. I also went through a thread here: [http://www.ubuntuforums.org/showthread.php?t=205449]("http://www.ubuntuforums.org/showthread.php?t=205449"). Consequently, I had a look at alsamixer and checked whether the current user was part of the audio group. To no avail. Am I missing out on something basic? Oh, I also tried some of the sound settings in frontend setup.
Thanks for any help you can give me.

Oops, problem resolved. The audio output device within myth was somehow set to /dev/dsp1 instead of just /dev/dsp. Seems to work now.

---

