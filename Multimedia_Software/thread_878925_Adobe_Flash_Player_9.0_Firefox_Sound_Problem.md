---
title: "Adobe Flash Player 9.0 Firefox Sound Problem"
date: 2008-08-03
forum: Multimedia Software
---

### Post by mikeMarek on 2008-08-03
I installed Adobe Flash Player 9.0 for Firefox. The video pops up, but even though I know for a fact that there is sound in the video, it doesn't play. Banshee works fine and other sound plays, but not for SWF files in Firefox. Any help?

Thanks for any replies and help,
-Mike

---

### Post by gobble on 2008-08-03
Been using flash player 10 for a while without problems.

want to check that out?

[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

Do other media files play with audio? Did you try only a local file or some embedded flash videos on the Internet?

How about the  youTube and Metacafe videos? 

Cheers

---

### Post by jualin on 2008-08-03
> **mikeMarek said:**
> I installed Adobe Flash Player 9.0 for Firefox. The video pops up, but even though I know for a fact that there is sound in the video, it doesn't play. Banshee works fine and other sound plays, but not for SWF files in Firefox. Any help?

Thanks for any replies and help,
-Mike

Are you trying to run Banshee and Firefox at the same time. You will lose sound if you do that unless you change the output plugin in Banshee. I had the same problem with Audacity and now it works. You need to restart Firefox after you close  Banshee since just closing Banshee once Firefox can't open the audio device doesn't do the trick.

---

### Post by mikeMarek on 2008-08-03
Thanks Jualin, I'll try that.

Gobble, that is where I was testing to see if Flash player worked: Youtube. Youtube videos wouldn't play sound.

---

### Post by jualin on 2008-08-03
Try running Firefox first with no other Media player open and check if you have sound. If you still don't have sound then it may be a problem with flash and not a problem with applications conflicting when using the same sound device. Good luck!

---

### Post by lokutus25 on 2008-08-03
I have the same problem, using the flashplugin-nonfree plugin from medibuntu. I think it's a problem with PulseAudio. Checking...

---

### Post by habtool on 2008-08-03
> **lokutus25 said:**
> I have the same problem, using the flashplugin-nonfree plugin from medibuntu. I think it's a problem with PulseAudio. Checking...

This may be off track, but Hardy with Pulse-audio when using skype amarok etc loosing sound when one source 'steals' it is a real pain.
Its OK for the casual PC user, but if you on your machine full time then it gets old very fast
(It is also a mess in Mint 5, so flash beta 10 is not only answer, as skype amarok etc still have issues)
I am sure pulse-audio will rock one day, but until that day I moved over to Debian testing/lenny Gnome and sidux for when i feel like KDE

(Kubuntu would work fine as they did not get caught up in the whole pulse-audio fiasco as far as i recall)

Love Ubuntu, but sitting this release out, that's the beauty of Linux, we are spoilt for choices :)

---

### Post by lokutus25 on 2008-08-03
I removed the flashplugin-nonfree (Adobe Flash Player 9) and installed the flash player 10. Seems to works for me. But yes habtool, you are right, I'll consider Kubuntu :-) Thanx

---

### Post by mikeMarek on 2008-08-04
I removed Flash Player 9 and install 10, but still don't have any sound. Any help with this?

Most appreciative for your help,
-Mike

---

### Post by jualin on 2008-08-05
Maybe changing the sound engine from PulseAudio to Alsa will make the trick for you. Go to System, Preferences, Sounds. And then change everything from "AutoDetect" to "ALSA". Restart Firefox with no music player open and then try to watch a flash video with sound. Hope this works!

---

### Post by mikeMarek on 2008-08-05
> **jualin said:**
> Maybe changing the sound engine from PulseAudio to Alsa will make the trick for you. Go to System, Preferences, Sounds. And then change everything from "AutoDetect" to "ALSA". Restart Firefox with no music player open and then try to watch a flash video with sound. Hope this works!

Still nothing. Thanks for all your help though!
-Mike

---

### Post by jualin on 2008-08-06
I am sorry to hear that I have run out of ideas so far. Maybe someone else in the forum might help you further. Something that might help is starting Firefox using the terminal by typing "firefox" and then trying to play a flash video and post the results of everything that is reported in the terminal. Maybe Firefox will tell you what's wrong such as "Audio Device being used by another application" or something similar. Good luck!

---

### Post by arthur_bear on 2008-08-06
> **mikeMarek said:**
> Still nothing. Thanks for all your help though!
-Mike

Try running "killall pulseaudio" (be sure that no sound is playing cause it can hang) after changing the settings to ALSA, before starting firefox. If that doesn't work change the settings back (autodetect) and install libflashsupport (it's a bit buggy sometimes but it works for me with pulseaudio). If all that fails see "ALSA Configuration" in [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio).

---

