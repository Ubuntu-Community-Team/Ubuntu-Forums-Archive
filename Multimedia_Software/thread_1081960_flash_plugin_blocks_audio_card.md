---
title: "flash plugin blocks audio card"
date: 2009-02-27
forum: Multimedia Software
---

### Post by untill on 2009-02-27
Greetings.

After one of the latter system upgrades in December or so, I have the problem that sound output to my audio card appears to be blocked. I suspect the Flash Player plugin and/or the plugin wrapper to be the culprit because after I have closed browsers (could be Firefox, could be Opera), it becomes usable again. Alternatively, I close all pages requiring Flash. I also kill any hanging pluginwrapper processes. All this becomes quite tedious, and I wonder if there's a more permanent solution.

I have an always updated 8.10 box, and all settings in the sound preferences show Default, but I have no idea if this means PulseAudio, OSS, or ALSA. The Test buttons in the preferences actually help quite a lot, because I can tell the audio card is blocked when there is no sound after pressing the button. When I can hear the test sound, I can start other audio applications, otherwise there is no sound. 

This applies to vlc, totem, ffplay and others, including Thunderbird. For instance, when the sound is blocked, the event dialog window which the Lightning (Calendar) Add-On wants to open in Thunderbird will hang the entire mail application.

TIA for any help.

---

### Post by untill on 2009-03-11
Hm, I'm apparently the only one having this problem.

Ok, you don't need to have the same problem, but any suggestions would help. :frown:

---

### Post by SoundreameR on 2009-03-11
Hi dude. I've registered here to reply your thread. I am an opensuse user. I use openSUSE 11.1 with KDE 4.2.1 on dell studio 1535 laptop and I have the same problem. Other people with the 100% same configuration don't have it.. I can't seem to find out why. As far as I know my issue - adobe flash player 10 (that I use) blocks the soundcard from being used by alsa and pulseaudio. That's why if I turn amarok on first it will play, but I will not be able to hear the sound of youtube videos, and if I turn firefox with youtube first then amarok can't play songs. How did I found out that the problem is in the flash player? - Well.. I've turned amarok, mplayer, xmms and vlc at one time and they all played music normally, but any player combined with firefox + some flash video had problems. vlc makes errors while playing, amarok and mplayer don't have sound at all. Solution? - not yet found... :(

---

### Post by SoundreameR on 2009-03-11
Hah... omg. The solution is so simple.. I had this problem for 2 months now and I've just fixed it. If you are using kde - go to Configure Desktop to setup kde. There go to Multimedia and set the default Audio Output to PulseAudio, not your soundcard directly. And that's ALL! :D

---

### Post by untill on 2009-03-12
Thanks for the reply. 

Anyway, I'm on Gnome. In the sound preferences, I set now all playback to PulseAudio, and the Mixer to OSS. Which let's me play back Flash inside Firefox (started first) and listen to radio (vlc) at the same time. Puh!

Problem solved? Not completely, there is no sound while playing Flash inside Opera. And when I start Opera first, operapluginwrapper blocks all other sound. This applies to Flash Player 9 and Opera 9.64.

Will upgrade Flash and then ask the Opera community.

---

### Post by untill on 2009-03-12
Problem solved.
Opera saw an older Flash, version 9 something, while FF ran 10 something, which obviously was installed in parallel. I removed 9, and now Opera sees 10 as well, and plays sound like a charm.

---

### Post by voltav on 2009-05-05
I have the same problem, but i cant fix it, i set all sounds to PulseAudio, here are a screenshot

[[IMG]http://img65.imageshack.us/img65/1548/screenshotsoundpreferen.th.png[/IMG]]("http://img65.imageshack.us/my.php?image=screenshotsoundpreferen.png")

Im using Ubuntu 8.04 and Firefox 2

any ideas?

---

### Post by voltav on 2009-05-10
I fix this problem with this tutorial, i follow all steps and now i can play .swf and music in rhythmbox at same time =D

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

And here are this bug in Adobe forums 

[http://bugs.adobe.com/jira/browse/FP-1154](http://bugs.adobe.com/jira/browse/FP-1154)

---

### Post by lonerunner on 2010-03-05
The link voltav posted helped me, i have Hardy on AMDx64 and flash10, didn't have to configure or install anything else except pulse audio and everything is working fine with firefox and flash, just last step to figure out is how to set quake 3 to have audio when Rhythmbox is playing... :)

---

