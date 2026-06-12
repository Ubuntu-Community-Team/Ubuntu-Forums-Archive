---
title: "no sound - nvidia"
date: 2015-06-13
forum: Multimedia Software
---

### Post by jgw on 2015-06-13
I am running ubuntu 14.10 with an nvidia card.  I have lost all my sound.  I have no idea what happened.  I have recently updated.  I have run a number of tests which can be seen at
[http://pastebin.com/nc6v3ReF](http://pastebin.com/nc6v3ReF)
[http://pastebin.com/1987BEnh](http://pastebin.com/1987BEnh)

I have configured something wrong.  I can, for instance, play something with sound, at the same time I can run pulseaudio.  I can see the thing playing but its not going to the speakers.  I don't know how to figure out just where it is going or how to control that.

I have disabled the motherboard sound and now have one device, nvidia (GF108 High Definition Audio Controller)   All other stuff is now gone.  Files above have not been updated.
Sound is still gone.

If I disable pulse audio (using system monitor) I can no longer test the sound with the system sound thing.  I can also run pulseaudio, play something, and watch the line bounce around like its actually getting something.  I have no idea, however, where its going.  Pulseaudio tells me that its using "digital surround 5.1 (hdmi) output" profile and the gf 108 high definition audio controller.  The port is the hdmi/display port4 (plugged in)

I have this machine connected to my regular tv (dish) and made sure my speakers were working and there was sound, outside of ubuntu. 

I do not understand why there are all these deviced when there is really on 1:

greg@greg-N61PB-M2S:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Thoughts?

---

### Post by kryten35 on 2015-06-13
Its normal to have 4 seperate entries.Thats the way the nvidia controller is installed.
Turn motherboard sound back on ,you need it.

I think an update has reset your sound output settings.Check sound output or device settings.
For my tv i have to select  digital stereo (HDMI 2) output   HDMI 3 wouldnt work since the cable isnt connected to it.

And check that your tv supports  the outputted format.
 Surround 5.1 wont work for my tv because it cannot decode it.

---

### Post by jgw on 2015-06-13
Thanks for the reply.

This is driving me nuts.  Spent all day on it.  If I keep it up I will be reinstalling everything because I have REALLY screwed it up <G>

I have been running this same system for about 5 years and have had everything working until now.  Its very strange.  Since I can see something playing (no sound) I know wherever its going that is wrong.  I will start researching that stuff and see what I can find.   I am using a pass through for my hdmi.  This handles all my hdmi stuff from my regular tv and my computer tv stuff (it all goes to the tv).  

You have given me food for more thought, thanks again!!

Thanks again!

---

### Post by jgw on 2015-06-14
I seem to have fixed the problem.  I have no idea what I might have done.  I found out that I had not connected the cd/dvd when I put this thing back together.  So, I had to take it apart and do the deed.  Then I found that the on/off (intermittent) was screwed so I drilled a new hole in the case and fixed that too.  Then I ran the ubuntu 14.10 cd to see if the sound worked with that (it didn't).  Then I got it all back together and thought I would just test the sound on the odd chance that it might work (its all done with mirrors and magic).  In this particular case it just started working.  using gf 108 high definition audio controller.  This is very strange.  When it was not working it always referred to hdmi.  This time its using hdmi (my only connection to sound and video) but just not saying it.  Mysterious abound!!!

---

