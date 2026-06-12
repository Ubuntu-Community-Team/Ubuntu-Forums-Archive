---
title: "no surround on ALC887-VD2 (asus e35m1 pro)"
date: 2011-04-02
forum: Multimedia Software
---

### Post by Lotof on 2011-04-02
Hi,

  I'm trying to set up at least 5.1 sound in my fresh ubuntu 10.10. I have stereo sound but failed when trying to set up the rest. I've googled it, read through couple of pages and tried the following:
- I've installed alsa 1.0.24
- I've added the following lines to /etc/pulse/daemon.conf 
```
default-sample-channels = 6
default-channel-map = front-left,front-right,rear-left,rear-right,center,lfe

```
- I've added ```
options snd-hda-intel model=3stack-digout
``` to /etc/modprobe.d/alsa-base.conf

There is no 'Profile' button/menu in Sounds preferences/Hardware.


```

$speaker-test -Dplug:surround51 -c6

speaker-test 1.0.24.2

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Playback open error: -2,Nincs ilyen fájl vagy könyvtár

```
This means 'No such file or directory' 

```
$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$cat /proc/asound/card1/codec#* | grep Codec
Codec: Realtek ALC887-VD

```

Do you have any suggestion I should try? 

thanks

---

### Post by lidex on 2011-04-03
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by Lotof on 2011-04-03
alsa-info.sh:
[http://www.alsa-project.org/db/?f=7c9e12c58e69e2c3fdaf3b3aedb341ff0def6715](http://www.alsa-project.org/db/?f=7c9e12c58e69e2c3fdaf3b3aedb341ff0def6715)

---

### Post by naasking on 2011-04-03
For what it's worth, I have the ASUS E-35M1-I Deluxe. I was struggling with sound after a minimal Ubuntu install, even though it worked with a full desktop install.

I got it all resolved by installing pulseaudio, launching it in daemon mode (edit /etc/defaults/pulseaudio and /etc/pulse/daemon.conf), and adding myself to the pulse and pulse-access groups.

I have no idea what PulseAudio is doing to fix the ALSA config, but it all seems to work well.

---

### Post by lidex on 2011-04-03
That option in alsa-base.conf is not working for you so remove it. Alsa is seeing your hdmi as default. What outputs are you wanting to use for audio?

---

### Post by Lotof on 2011-04-04
lidex: I have 3 jacks in the rear panel (mic, line out, line in) and 2 jacks in the front (line out, mic). In the manual it says that it's possible to configure the rear panel as: rear speaker out for line in, and bass/center for the mic.
  My original thoughts was to have the possibility of changing between this 2 setup. Most of the cases I need the 5.1  output. When I need to record from tv I need to switch the line-in back to line-in. The reason is that I have a pixelview playtv tuner card. It has a line-out which needed to be connected to the line in to get the sound of the tv. 
  However I saw the '06:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)' which made me think that it is may not be necessary (not sure how to set it up though. 

naasking: I've added myself to the groups you recommended, will let you know if it worked after the restart.

---

### Post by lidex on 2011-04-05
> **Lotof said:**
> lidex: I have 3 jacks in the rear panel (mic, line out, line in) and 2 jacks in the front (line out, mic). In the manual it says that it's possible to configure the rear panel as: rear speaker out for line in, and bass/center for the mic.
  My original thoughts was to have the possibility of changing between this 2 setup. Most of the cases I need the 5.1  output. When I need to record from tv I need to switch the line-in back to line-in. The reason is that I have a pixelview playtv tuner card. It has a line-out which needed to be connected to the line in to get the sound of the tv. 
  However I saw the '06:00.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)' which made me think that it is may not be necessary (not sure how to set it up though. 

naasking: I've added myself to the groups you recommended, will let you know if it worked after the restart.

Have a look here:
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html](http://www.sabi.co.uk/Notes/linuxSoundALSA.html)

---

### Post by manu.kollam on 2011-08-24
[http://www.alsa-project.org/db/?f=e8d6231f8630db995d3d6f9b8df8d46611b4a698](http://www.alsa-project.org/db/?f=e8d6231f8630db995d3d6f9b8df8d46611b4a698)

---

### Post by lidex on 2011-08-28
> **manu.kollam said:**
> [http://www.alsa-project.org/db/?f=e8d6231f8630db995d3d6f9b8df8d46611b4a698](http://www.alsa-project.org/db/?f=e8d6231f8630db995d3d6f9b8df8d46611b4a698)

Follow the link in my sig for the alsa-upgrade script. Once you have the latest version check aplay to make sure you have more than one device:
```
aplay -l
```

EDIT: Actually you have a different hardware set. I'm assuming you have the asus e35m1 pro as per
the thread subject, but apparently not. What is your make/model and what is the problem?

---

### Post by carchaias on 2012-02-08
Hello, could you help me. I could not get surroundsound running. It is an Asus A5ION board with ALC887 chip onboard. It has 3 jacks on back that should offer 5.1 sound according to the manual of the board and 2 jacks on front panel.  Speaker-test -D surround51 -c 6 gives me sound on LF,Center,RF and very low volume sound on RR,RL with some mubel from the sub, sub test mubles sub. In alsamixer LFA Mixer affects nothing and surround mixer affect backspeakers and sub. Here comes my alsatest result:

[http://www.alsa-project.org/db/?f=21a09c6037cc84a08c1650f5684ab43f6e583ca5](http://www.alsa-project.org/db/?f=21a09c6037cc84a08c1650f5684ab43f6e583ca5)

There is an entry in alsa-base.conf

options snd-hda-intel model=auto

Any ideas are welcome..

---

### Post by creador4 on 2012-12-25
> **Lotof said:**
> Hi,

  I'm trying to set up at least 5.1 sound in my fresh ubuntu 10.10. I have stereo sound but failed when trying to set up the rest. I've googled it, read through couple of pages and tried the following:
- I've installed alsa 1.0.24
- I've added the following lines to /etc/pulse/daemon.conf 
```
default-sample-channels = 6
default-channel-map = front-left,front-right,rear-left,rear-right,center,lfe

```
- I've added ```
options snd-hda-intel model=3stack-digout
``` to /etc/modprobe.d/alsa-base.conf

There is no 'Profile' button/menu in Sounds preferences/Hardware.


```

$speaker-test -Dplug:surround51 -c6

speaker-test 1.0.24.2

Playback device is plug:surround51
Stream parameters are 48000Hz, S16_LE, 6 channels
Using 16 octaves of pink noise
Playback open error: -2,Nincs ilyen fájl vagy könyvtár

```
This means 'No such file or directory' 

```
$aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: SB [HDA ATI SB], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
$cat /proc/asound/card1/codec#* | grep Codec
Codec: Realtek ALC887-VD

```

Do you have any suggestion I should try? 

thanks

The problem is gone if you do this:


gksudo gedit /etc/modprobe.d/alsa-base.conf

search this line: 

options snd-hda-intel model=generic

if its there, change that for: 

options snd-hda-intel model=6stack-dig 

If not add it. And Restart.

---

