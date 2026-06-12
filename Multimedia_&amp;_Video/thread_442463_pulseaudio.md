---
title: "pulseaudio"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by rygar on 2007-05-13
i have a laptop, and i usually wander around the house with it.  i've been told i can use pulseaudio to redirect the mix from my sound card to speakers on another computer across the network (ideally, id have all the processing done on my laptop, as its faster, and just have the audio stream transfer to the speakers)

i installed pulseaudio, but cant seem to find a decent how-to for this.  some pages look like they might help, but im not too sure, and i dont know too much about this.  can anyone point me towards a decent tutorial?

---

### Post by rygar on 2007-05-13
i gave up on pulseaudio--the windows binaries are kind of crappy

esound works really well and easily

windows machine:
esd.exe -tcp -public

ubuntu machine:
sudo apt-get install esound-clients
use the esound plugin that comes with audacious

hopefully pulseaudio will step up and be able to do this in the future

---

### Post by diaa on 2008-07-18
This is more than a ago, but I just wanted to mention that I was able to use PulseAudio to listen to the sounds played on my Linux PC from my Windows PC.

Here is the mini howto, right from PA's FAQ: [http://www.pulseaudio.org/wiki/FAQ#HowcanusemyWindowsboxtoplaythesoundfrommyLinuxbox](http://www.pulseaudio.org/wiki/FAQ#HowcanusemyWindowsboxtoplaythesoundfrommyLinuxbox)

---

