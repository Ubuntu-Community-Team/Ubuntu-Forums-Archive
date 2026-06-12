---
title: "Some applications have sound, other applications don't"
date: 2008-11-14
forum: Multimedia Software
---

### Post by goldust on 2008-11-14
what can I do about this? What is some other information I can share to help this along?

example, I open up exaile to play music
I goto system prefernces sound and test my soundcard and I get this:
 
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback. Device is being used by another application.

I'm trying to use alsa. I'm really stumped.

---

### Post by Euphorion on 2008-11-14
Hallo Goldust

I assume that you are using Ubuntu Intrepid 8.10. Currently many users are experiencing problems with sound in Intrepid. The main issue is that the Volume levels are extremely low. I recommend that you follow the link below and the other references to further Threads in the Ubuntu Forums contained therein. The Problems are centered on the correct installation of Pulse Audio including in some cases the total removal of pulse audio.

[http://ubuntuforums.org/showthread.php?p=6169413#post6169413](http://ubuntuforums.org/showthread.php?p=6169413#post6169413)

I may self have carried out the following and can now hear Videos, MP3 and CDs at reasonable audio levels. My experiences can also be found in the above thread, along with a description of my Hardware.

1. Setup Pulse Audio Correctly. See Sticky Link in this Forum.

2. In Administration -> Preferences -> Sound set all Audio Outputs to OSS

3. In mplayer and Smplayer (should you use these) set Audio to OSS. In SMPlayer active the Software Sound Volume option and set the Amplification to around 250

4. In VLC set the Audio to OSS

5. Set Master Volume to max.

I have been unable to activate the Audio Output in Grip - this application remains silent. But it rips and encodes correctly. Sound in Cineralle and Open Movie Editor are still corrupt.

---

### Post by goldust on 2008-11-14
Thank you for responding.

what sticky where?

---

### Post by goldust on 2008-11-14
it's really hard to know what exactly I did or what the trick was or what the problem was. I just stayed persistent with getting this to work and I restarted with OSS as my sound drivers and now everything works the way it used to. thanks.

---

