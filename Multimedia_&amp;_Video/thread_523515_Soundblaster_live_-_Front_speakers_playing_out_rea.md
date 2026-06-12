---
title: "Soundblaster live - Front speakers playing out rear speaker jack"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by holomorph on 2007-08-12
I have a soundblaster live card and it's exhibiting some rather odd behavior.  I'm pretty sure I had things working at some previous time, but I'm not sure how long ago that was. .  .anyway, here is the trouble.

The card has 4 analog ports: 1, 2, mic, and line in. port 1 should be front speakers, and 2 should be rear.  It used to be that in the alsa mixer, the Master and PCM channels would adjust the volume for port 1 (front), and the Wave Surround would be port 2 (rear). 

After recently taking appart my computer to install a new drive, I plugged my two front speakers in to port 1 on my soundcard, only to discover I was getting no sound from them.  After some fiddling, it became apparent that I was only getting sound out of port 2.  The odd thing is, though the volume for this port is still controlled by the Wave Surround, when I run 'speaker-test -c4 -twav' I hear "Front Left" and "Front Right" comming out of the left and right speakers (which are hooked to the rear speaker port), and I don't hear anything when it is testing the rear channels.  

So apparently, the sound that should be getting sent to my front channels is getting sent to the rear, and what should be sent to the rear is not getting sent anywhere.  Any ideas what might be wrong?

---

