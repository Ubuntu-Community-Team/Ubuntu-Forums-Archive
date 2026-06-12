---
title: "Weird no sound problem"
date: 2009-09-03
forum: Multimedia Software
---

### Post by Jimmy9pints on 2009-09-03
Hi everyone,

I have searched the forums and google to try to solve this problem but only partially solved it. 
The symptoms were:
1: sound at login
2. no sound on video or audio playback
3. No sound in flash (within Firefox)

The action I took was:
1. Went in to the mixer and made sure everything wasn't muted and was well turned up.
2. Went into System>Preferences>Sound  tested the sound, found it to be mute. I changed all three drop down boxes to "OSS Open Sound System" and could hear the test signal. This partially solved the problem so symptom #2 was out the way.
3.Purged and resinstalled Alsa - this seemed to have no effect. 

I still have no sound in Flash within Firefox. Considering this was a problem that suddenly affected sound on the whole system, I am not sure where the problem lies. 

Any ideas how to solve this?

Cheers,

James

---

### Post by Jimmy9pints on 2009-09-05
Bump.

Can anybody help?

---

### Post by Jimmy9pints on 2009-09-12
Got my very own thread here!

For anyone else experiencing this, here are some fixes (none of which have worked for me but they have for others):

#1[http://ubuntuforums.org/showthread.php?t=204022]("http://ubuntuforums.org/showthread.php?t=204022")
#2[http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/]("http://www.macewan.org/2006/06/01/howto-firefox-flash-video-sound-on-ubuntu-linux-dapper/")
#3[http://newtoubuntu.wordpress.com/2009/04/25/ubuntu-904-no-sound-with-flash-videos/]("http://http://newtoubuntu.wordpress.com/2009/04/25/ubuntu-904-no-sound-with-flash-videos/")

Annoyingly, I couldn't get the last fix (#3) to work because when I downloaded the .tar.gz from Adobe, it didn't contain an installer! I read instructions on "nenewtoubuntu.wordpress.com" and on the actual Adobe website, both said to open the installer, but it simply wasn't in the package!

#2 wouldn't work because there is no such file as firefoxrc in /etc/firefox/    so it's probably an out-of-date fix.

And just to tell you what else didn't work: From synaptic, I went for COMPLETE removal of flashplugin-nonfree and the flash installer (including configuration). I then reinstalled them both and restarted the computer. It didn't work either. 

Still without sound in flash. If I find a solution, I'll post it here.

---

