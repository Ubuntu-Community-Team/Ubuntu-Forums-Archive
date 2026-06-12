---
title: "I have been trying for months to get consistent audio to work"
date: 2011-03-22
forum: Multimedia Software
---

### Post by McManCSU on 2011-03-22
I have an intel HDA chipset that desperately wants to work.  I have it plugged into my receiver and sound only occassionally works.  I say occassionally because I will hear some sound, then my receiver will flash hdmi, as if it is switching to the new stream, I hear silence.  Then shortly later, the receiver will provide sound, then again it will 'switch' and i hear silence.  To work around this, I had an optical line working and somehow had alsa using ONLY that for the audio (bypassing  the HDMI completely).  Then one day when I was trying to the audio fixed for some specific application, I broke it!  I cannot figure for the life of me how to make alsa ONLY use my optical line.  Of course any suggestions on how to get the hdmi to work is even better.

My settings:
[http://michie.homelinux.com/alsa.txt](http://michie.homelinux.com/alsa.txt)

---

### Post by lidex on 2011-03-22
Try this:
```
sudo mv /etc/asound.conf /etc/asound.conf.bak
```
Now reboot.
That renames asound.conf, you can restore if needed.

---

### Post by McManCSU on 2011-03-23
Thanks for the tip Lidex, but still not working.  Alsa will not optical line.  I remember it being hw:0,1 and the hdmi seemed to me hw:0,3.  The quickest way for me to test is through vlc and I choose 'prefer spidf' but to no use.  What else could it be do you think?

One thing that seems odd is that I do this, and the subdevices is 0/1 - is that an issue?
```
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Thanks!

---

### Post by McManCSU on 2011-03-25
Bump.  I also did 
```
aplay -D plughw:0,1 blah.wav
```which use to work on the optical line, but now seems to use the hdmi.  I noticed that after doing this, the subdevices with to 1/1 instead of 0/1 (not sure what that means).  Any thoughts?

Thanks

---

### Post by McManCSU on 2011-03-27
Anyone?

---

### Post by lidex on 2011-03-31
Have you seen this:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

---

