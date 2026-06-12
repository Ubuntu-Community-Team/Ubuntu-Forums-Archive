---
title: "HDMI on GA-H55 Audio not working fully - 10.04"
date: 2010-12-09
forum: Multimedia Software
---

### Post by McManCSU on 2010-12-09
I have been pining over and over through 100s of forum posts to no avail.  My problem is that my audio through HDMI does not work fully.  I upgraded to 1.0.23 alsa release, which seemed to help, but I cant get anything besides 'Digital Stereo (HDMI) Output' from System-Preferences-Sound.  Maybe this is normal, and I will have to rely on xbmc, etc. to provide 5.1 surround sound?  I am pretty noob here, so maybe someone could clear this point up at the least.

From slightly outdate ([http://www.alsa-project.org/db/?f=c888280d62b546e084b2d43e904669f127bee0c9):]("http://www.alsa-project.org/db/?f=c888280d62b546e084b2d43e904669f127bee0c9%29:")
Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.22

Anyway, the main problem is that my audio out goes into my new Onkyo receiver and during moments of sound, the receiver 'switches' like it is detecting a new input.  So something like this:
```
speaker-test -Dhdmi:Intel -c6 -twavq
```will indeed hit all 5 channels (FL, FC, FR, RR, RL, etc), but it will get cut off periodically because the receiver is switching.  To clarify, 'switching' entails an audible clicking noise from the receiver.

```
mcdizz@MediaMadness:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
```
```
mcdizz@MediaMadness:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=Intel
    HDA Intel, ALC889 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC889 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC889 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=Intel,DEV=0
    HDA Intel, INTEL HDMI 0
    HDMI Audio Output
  Subdevice #0: subdevice #0
```
I have tried several 
```
options snd-hda-intel model=xxx
``` for the alsa-base.conf (=auto, =intel, =intel-x58), but still same result.  It seems like the audio might not be getting controlled through alsa and rather pulse?  For example, when I 
user alsamixer with sound in the background, muting the master does nothing, but muting Volume Control from Applications does...??

Please help!  I am almost about to revert to Windows!

---

### Post by McManCSU on 2010-12-09
Bumping

---

### Post by sydbat on 2010-12-09
In a terminal (Applications > Accessories > Terminal) type in```
gstreamer-properties
```When the "Multimedia Systems Selector" pops up, under the Audio tab, change 'Default Output' to ALSA. Also, change the 'Device' to your digital out. See if that works.

---

### Post by McManCSU on 2010-12-23
Tahnks for the tip, but still no luck.  It is weird because the sound test will kind of work (meaning I get some choppy audio) but VLC doesnt output anything.  Any other suggetions?

---

### Post by deanjm1963 on 2010-12-23
Are you using the inbuilt gpu? If so you'll need to upgrade to 10.10 - the version of the intel driver (which has good hdmi support) which is included in 10.04 doesn't fully support clarkdale i3/i5/i7 chips when using the inbuilt gpu.


Hope this helps.

---

### Post by McManCSU on 2010-12-24
Yes I am using i3 - I will try 10.10 then - I was holding off because I didnt want to have upgrade unless I had to.  Thanks!

---

### Post by McManCSU on 2011-01-05
Alright, I upgraded to 10.10 and still had similar problems.  I then uninstalled pulseaudio and began to get true surround sound instead of just stereo.  However, I am still having intermittent audio cutouts where it is mostly silent with bursts of sound.  Any ideas?  I am not sure where to go anymore...  I am going through an Onkyo receiver - is it possible that is having issues??

---

### Post by McManCSU on 2011-01-06
bump

---

### Post by lidex on 2011-01-07
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by McManCSU on 2011-01-24
Thanks for taking a look Lidex.  I currently have sound working through the optical line, but would still like to fully use the HDMI audio output because of the principle of the matter!  :)

[http://michie.homelinux.com/alsa.txt](http://michie.homelinux.com/alsa.txt)

Thanks again!

---

### Post by jamesdew on 2011-01-24
I also struggled with the only stereo issue for months. I can't believe that the answer is not easier to find via googling. I also had to un-install pulse. 

As for your audio cutouts, are you using passthrough in XBMC

Can I ask do you still get regular OS sound? XBMC menu sounds? Because I don't.

---

### Post by jamesdew on 2011-01-24
also do you get this

xbmc@xbmc-htpc:~$ speaker-test -D hdmi:NVidia -c6 -twavq

speaker-test 1.0.22

Playback device is hdmi:NVidia
Stream parameters are 48000Hz, S16_LE, 6 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 5440
Period size range from 32 to 2720
Using max buffer size 5440
Periods = 4
was set period_size = 1088
was set buffer_size = 5440
 0 - Front Left
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
Write error: -32,Broken pipe
 4 - Centre

---

