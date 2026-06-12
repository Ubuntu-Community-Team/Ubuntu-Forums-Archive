---
title: "Can't record through LIne-In OR Mic-In"
date: 2011-01-15
forum: Multimedia Software
---

### Post by CosmicFlux on 2011-01-15
Hi,

I'm having trouble recording through either my Line-In or Mic-In inputs on my laptop through Audacity.

Nothing happens at all. 

The device options are as follows:

[B]HDA Intel: ALC883 Analog (hw:0,0)
HDA Intel: ALC833 Analog (hw:0,2)
pulse
default[/B]

Is this a driver issue?

Cosmic

---

### Post by marin123 on 2011-01-15
go into your mixer and see whats happening there. System -> Preferences -> Sound
under Input tab see where do you get your input from, then connect something to line in or mic (depending what you have choosen as your input) and see if it detects anything (input level bar should be jumping)...
once you have what you want, set audacity recording to default and start recording. you should see waveform of recorded track.

you also have sound recorder in Menu -> Sound & Video, i use that for audio recording...

---

### Post by CosmicFlux on 2011-01-15
OK, thanx!

I'm getting a huge amount of electrical noise through the integrated line-in port. 

Would buying an external audio interface reduce this substantially?

---

### Post by marin123 on 2011-01-15
it would, but i there shouldnt be much noise on that channel. what device did you connect to the input? mp3 player, turntable?

also, what version of ubuntu are you using? i had problems in 10.04 and had to upgrade alsa. you could check it out and see if it helps you reducing the noise...

did you try recording in sound recorder? does that have much noise?

and also check your cables (try different cables), maybe theyre making all of the noise.

---

### Post by CosmicFlux on 2011-01-15
I had an electric guitar connected then a digital piano. 

I'm using 10.10. It was sound recorder I was recording on but I don't have shielded cables so maybe that has something to do with it. I also have quite a lot of electrical equipment within close proximity.

I've read that using any of the integrated ports on a notebook will cause noise. It wasn't really bad, but it wasn't a high quality, clean recording, which is what I want.

Maybe an external interface and shielded cables will give me what I want? I should have maybe turned off the wireless hub too as it's in the same room.

---

### Post by marin123 on 2011-01-16
i recorded with a dj mixer and also didnt get crystal clear sound, but it was ok for me. i also use unshielded cables 5 meters long, passing around the speakers :D so i dont think i was careful... integrated sound cards arent the best, and simple external usb cards should provide better results...

---

### Post by CosmicFlux on 2011-01-17
I managed to get it working at a higher quality by turning off my Broadband hub! 

This is the quality I'm getting:

[Band DEMO]("http://www.kosmicflux.com/publicfiles/Anarchy_In_Blue__Demo_Multitrack____Guitar_2__2nd_Cut_.mp3")

---

### Post by marin123 on 2011-01-17
not bad :)

when recording, try to set the volume so your peaks dont exceed max input (to avoid clipping). you should get better sounding high freqs...

---

