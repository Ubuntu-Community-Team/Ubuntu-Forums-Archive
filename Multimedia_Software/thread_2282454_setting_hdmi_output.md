---
title: "setting hdmi output"
date: 2015-06-14
forum: Multimedia Software
---

### Post by jgw on 2015-06-14
I am running with ubuntu 14.04  
I have no sound.  I have tracked the problem down to the hdmi output.  I can watch audio play in pulseaudio (no sound but output moving).  I have posted the results of aplay at [http://pastebin.com/dcFt7GVh](http://pastebin.com/dcFt7GVh) .

This is giving me fits.  I have no idea what caused this to happen.  I have spent a lot of time running through all suggestions to no avail.  (and fear, if I keep it up, I will have a genuine mess >G>)

Thank you............

---

### Post by ajgreeny on 2015-06-14
have you set the output in pulseaudio-volume-control to use the HDMI output?  I don't have any HDMI on my desktop to be able to try this myself, but it is often an incorrect level set there that causes the problem.

---

### Post by efflandt on 2015-06-14
Which Nvidia card/chip and which nvidia driver are you using?

If you click on the speaker icon in upper right and click on **Sound Settings...** what is highlighted for **Play sound through**? Mine is **Analog Output *Built-in Audio*** for my 2.1 speaker system or selecting **HDMI/DisplayPort *HDA Nvidia*** selects HDMI (on GTX 750 Ti currently using nvidia-352 from xorg-edgers ppa, not that version should make any difference).

---

### Post by jgw on 2015-06-14
thank you for the replies.

efflandt 
I am using a nvidia 450  and the nvidia driver 331.113  (I have used the plain and the updated - no difference)

According to pulseaudio:
I have two options to play through: digital surround 5.1 (hdmi) output and 2.0 (hdmi) output.
the port is hdmi/display port4 (plugged in)

I have posted all available ports here:  [http://pastebin.com/dcFt7GVh](http://pastebin.com/dcFt7GVh)   (just click on it to take a look)  It also shows the built in stuff but I have disabled that as I am pulling no sound for that.  Basically hdmi available.  


I seem to have fixed the problem.  I have no idea what I might have done.  I found out that I had not connected the cd/dvd when I put this thing back together.  So, I had to take it apart and do the deed.  Then I found that the on/off (intermittent) was screwed so I drilled a new hole in the case and fixed that too.  Then I ran the ubuntu 14.10 cd to see if the sound worked with that (it didn't).  Then I got it all back together and thought I would just test the sound on the odd chance that it might work (its all done with mirrors and magic).  In this particular case it just started working.  using gf 108 high definition audio controller.  This is very strange.  When it was not working it always referred to hdmi.  This time its using hdmi (my only connection to sound and video) but just not saying it.  Mysterious abound!!!  I am going to mark this solved even though I have no idea how that happened. <G>
Thanks again!!

---

