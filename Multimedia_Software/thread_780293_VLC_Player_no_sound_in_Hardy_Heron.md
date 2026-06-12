---
title: "VLC Player no sound in Hardy Heron"
date: 2008-05-03
forum: Multimedia Software
---

### Post by mgybran on 2008-05-03
Hi have spent the last couple of days trying to get sound in my VLC player in Hardy Heron.  Judging by other forum postings there does seem to be a lot of people with the same problem as me.  At last, I found a solution that worked for me.  I hope by my sharing it now it will help others.  

I followed the guide at link:

[http://www.alterego7.com/2008/04/vlc-with-pulseaudio-on-ubuntu-804.html](http://www.alterego7.com/2008/04/vlc-with-pulseaudio-on-ubuntu-804.html)

The Pulse audio I could never get working in vlc.  In the end I added the following package which I found in the Synaptic package manager:

vlc-plugin-alsa

I then pointed in the vlc preferences to: ALSA audio output
instead of Pulseaudio output.  Worked for me.

I myself am a novice in Ubuntu. I hope this will help someone else.

---

### Post by dragonfoundry on 2008-05-03
I did a fresh install of Hardy, got sound as normal apart from when playing videos in VLC despite having installed the codecs, etc.

It turned out to be the "Force Detection of Dolby Surround" (under Settings > Preferences > Audio) which was set to "Auto". I changed the setting to Off and I now have sound in VLC.

---

### Post by MaindotC on 2008-06-21
I did a nice, fresh, clean install a while ago and I never really tested VLC because I just wasn't doing anything requiring VLC.  Sure enough - today I try and play a podcast I downloaded, and no sound!  Kind of the important part, eh?  So i followed OP's  instructions and now I have sound.  Much as I appreciate the work of the developers, if things work in Gutsy I wish they'd just leave it alone.

---

### Post by MaindotC on 2008-06-24
I changed the System -> Preferences -> Sound settings to ALSA for each component.  Everything works fine now.  I hope a majority of Hardy users had better luck with PulseAudio than I did!

---

### Post by rahulrrao on 2009-09-11
I tried all the given solutions, but in vain. I then installed Dragon Player and the sounds works perfectly. Time to watch a movie now!:popcorn:

---

