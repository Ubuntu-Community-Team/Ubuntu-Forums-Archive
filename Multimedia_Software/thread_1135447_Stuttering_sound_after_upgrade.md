---
title: "Stuttering sound after upgrade"
date: 2009-04-24
forum: Multimedia Software
---

### Post by isecore on 2009-04-24
I upgraded from Intrepid to Jaunty earlier today. Went quite fine, some minor snafus but nothing serious. However, an annoying thing is that occasionally sound will stutter (or cut out completely) as if there was some huge CPU-load or whatever.

I found the tip about adding load-module module-hal-detect tsched=0 to /etc/pulse/default.pa but I noticed that it was already in there anyway so I didn't really see the point of adding something that was already there.

Any ideas? Thanks :)

---

### Post by eragon100 on 2009-04-24
Same problem here. Anybody got any ideas on how to fix this? :(

---

### Post by Heidegger on 2009-04-24
I'm having the same problem. 

I did a clean install of 9.04, and at the first sound (login screen) It started looping and/or stretching (stuttering) the sound. 

Someone recommended to remove pulse audio which I did, but the problem wasn't fixed so i instaled it again. 

something i did that temporarily fixed the problem was to set everything in sound preferences to pulse audio. after that, sound worked fine for a while but then after some time it started doing the same thing.

---

### Post by eragon100 on 2009-04-25
I only had the problems with videos and tough that was the case for you too because you posted it in multimedia & video.

Anyway, turned out only totem suffers from this problem, and you can fix that by uninstalling totem-gstreamer and then install totem-xine.

To solve the stuttering sound, the following might work:

open a terminal and type "alsamixer". If the volume bars are in red, then they are set too high, lower them with the arrow down key until they become green, en press escape to exit alsamixer. You shouldn't hear any more stuttering then :wink:

---

### Post by maravingian on 2009-04-26
I have the same problems you guys have been experiencing.  So far no luck with any of the ideas you have suggested.  Login screen still stutters and jumps, rhythmbox and totem and vlc all run sound that stutters and jumps as well.
 I just thought it was me upgrading from 32 bit to 64 bit.  Is this not the case?  Any ideas on how to resolve the problem?

Cheers

---

### Post by 243kof on 2009-05-07
Hi, I have the same problem (occasional sound stuttering) since upgrading to jaunty. Actually, there is a HowTo about PulseAudio Fixes on this forum:

[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")

In Appendix B there, there is a question that seems to describe this exact problem and its corresponding solution. I've just tried it, and am currently waiting to see what happens.

---

### Post by kpkeerthi on 2009-05-07
I had this problem on fresh Jaunty install. I followed [this]("http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay") guide to get rid of pulseaudio completely and my sound was back to normal. My soundcard can do hardware mixing and I don't need other fancy pulseaudio features.

---

### Post by megamania on 2009-05-11
I'm having the same problem since one of the last updates.

I've been using 9.04 since Beta, and everything was fine until a couple of days ago...

---

