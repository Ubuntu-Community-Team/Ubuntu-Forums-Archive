---
title: "Amarok -&gt; Pulseaudio &amp; ATI HDMI driver problem"
date: 2009-04-28
forum: Multimedia Software
---

### Post by xkuruma on 2009-04-28
hello, i'm having a little trouble with amarok on jaunty.-

i configured my ubuntu to sound through PulseAudio sound server, but when i open amarok, it displays an error like: The audio playback device HDA Intel (ALC999 Analog) does not work. Falling back to HDA ATI HDMI (Output).

but the thing is i have connected my audio through the analog output, not hdmi.. so..   how can i make amarok to sound through pulseaudio?
or how do i make pulseaudio my default "playback device", so when the HDA Intel blah blah does not work, it'll sound through pulse audio??

hmm i hope anyone could understand my problem

any answers are appreciated

thanks !! :P

---

### Post by markbuntu on 2009-04-28
first of all make sure you have

phonon-backend-xine

This seems to be a particular issue with 32 bit users and usually fixes them right up.

If you are using 64 bit then you already should have it which was my case. What i had to do was get 

xine-ui

And change the audio settings to pulseaudio. You need to be "master of the known universe" to see these settings.
You especially might need to do this if you used my guide here since it changes all the sound to pulseaudio instead of automatic so everything can play together.

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by ectospasm on 2009-05-13
Thanks, setting the output device to pulseaudio in xine was enough to get Amarok to play nice with all the other applications (in essence, other system sounds work while Amarok is playing).

---

### Post by titi4u on 2009-07-16
Thank you, setting the output device to pulseaudio in xine worked for me too.
Hope this will be corrected in next ubuntu version !

---

### Post by boigaz on 2010-02-23
thanks so much for the help.  works now for me too

---

