---
title: "Problem with Sound Card......"
date: 2010-07-04
forum: Multimedia Software
---

### Post by KrishnaMohan.A.M on 2010-07-04
My sound card..TECH-COM PCI 4 sound card isn't working with Ubuntu............I don't know where I can get its driver........pls help me............

---

### Post by Vorless DarkChaos on 2010-07-04
Have you checked sound Preferences first?

---

### Post by lidex on 2010-07-05
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by KrishnaMohan.A.M on 2010-07-05
> **lidex said:**
> Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

**Output after executing the above commands........**

krishna@DeviDasan:~$ uname -a
Linux DeviDasan 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
krishna@DeviDasan:~$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8768 [C-Media CMI8768], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8768 [C-Media CMI8768], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
krishna@DeviDasan:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
krishna@DeviDasan:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC888

[B]
System Configuration[/B]:

1 GB RAM
Intel Core2 Duo 1.8 GHz
Intel Motherboard

---

### Post by KrishnaMohan.A.M on 2010-07-05
> **Vorless DarkChaos said:**
> Have you checked sound Preferences first?
  
**Yes........**

---

### Post by lidex on 2010-07-05
Alsa seems to recognize both of your soundcards and it looks like the c-media card is default. What profile are you using for that soundcard in Sound Preferences>Hardware Tab? You have no audio at all, including headphone?

Try gnome-alsamixer. Make sure of your levels/muting.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by wonderingwhy on 2010-07-07
Hi 

I think I have a similar problem. When I go to system>preferences>sound, my sound card is listed under input, but not under output.  I can see that the TV is getting sound with the picture because the input level follows the talking, but there's no output the only device listed is the internal audio analogue system.  

How do I link the sound card to the output?  

Thanks

---

### Post by lidex on 2010-07-07
> **wonderingwhy said:**
> Hi 

I think I have a similar problem. When I go to system>preferences>sound, my sound card is listed under input, but not under output.  I can see that the TV is getting sound with the picture because the input level follows the talking, but there's no output the only device listed is the internal audio analogue system.  

How do I link the sound card to the output?  

Thanks
Try selecting the soundcard on the hardware tab and adjusting the profile - try 'Analog Stereo Duplex' first.

---

### Post by wonderingwhy on 2010-07-07
Hey lidex

Under my sound card I only get two options 1.off; 2.Analogue Stereo input.

I think Analogue Stereo duplex is what I need.  That's the profile listed for internal audio.

I ran```
aplay -l
```
and this is all I got:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
I think this shows that in someway my Hauppauge WinTV HVR 4000 card isn't linked in.  I believe I have it listed as device card 2.  At least I think this is what it's telling me
```
cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio
 2 cx88_alsa
```

I think 1 is my webcam.

I've been looking at this [linuxtv]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-4000#Audio.2FVideo_capture") site and this [sound]("http://wiki.archlinux.org/index.php/Advanced_Linux_Sound_Architecture#Getting_SPDIF_Output") site, but I feel like I'm reading gobbledygook.

Thanks for the suggestion.  It's much appreciated.

---

### Post by KrishnaMohan.A.M on 2010-07-09
[SIZE=4][SIZE=3][SIZE=2]I could hear sound when I tried the following command.....[/SIZE]

[/SIZE][/SIZE]**speaker-test -Dplug:surround51 -c6 -twav**


[FONT=Arial][SIZE=2]but not when i play movies in vlc or any other players.........[/SIZE][/FONT]

---

### Post by lidex on 2010-07-09
> **KrishnaMohan.A.M said:**
> [SIZE=4][SIZE=3][SIZE=2]I could hear sound when I tried the following command.....[/SIZE]

[/SIZE][/SIZE]**speaker-test -Dplug:surround51 -c6 -twav**


[FONT=Arial][SIZE=2]but not when i play movies in vlc or any other players.........[/SIZE][/FONT]
In vlc, what is your audio output set to in preferences?

---

### Post by KrishnaMohan.A.M on 2010-07-09
[SIZE=5]**After a lot of research............I got it........Thanx 4 Ur help..................**[/SIZE]:p:p

---

### Post by lidex on 2010-07-09
That's fantastic *KrishnaMohan.A.M*. Can you post your fix and mark the thread solved to help anyone else who might have this problem? Thanks!

---

### Post by KrishnaMohan.A.M on 2010-07-10
1.Installed gnome als-mixer as adviced by lidex.
2.Go to System>Administration>Users and Groups>Advanced>User privilages     and enable use audio devices...:popcorn:

---

