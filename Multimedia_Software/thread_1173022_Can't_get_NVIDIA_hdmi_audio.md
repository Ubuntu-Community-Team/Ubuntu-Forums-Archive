---
title: "Can't get NVIDIA hdmi audio"
date: 2009-05-29
forum: Multimedia Software
---

### Post by Chrisn02 on 2009-05-29
Hi everyone,

I'm trying to get audio going though HDMI with no success. 
Only thing that works in video output.  Both video and audio work in XP.  

OS:       Ubuntu Jaunty x64
Laptop:   Clevo M860TU
Graphics: GeForce 9800M GTS
Driver:   nVidia  180.53  
Kernel:   kernel 2.6.30-020630rc6-generic
   one of the suggested fixes for random corruption.  I've yet to see that again but I'm not convinced its gone yet.
   [http://ubuntuforums.org/showthread.php?t=1135055&page=3](http://ubuntuforums.org/showthread.php?t=1135055&page=3)  &&  [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)
   and all related stuff from it

aplay -L
```

front:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC662 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC662 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

```

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
No nVidia sound devices have ever been listed no matter what I try.

lspci  (striped down but if you need a full list I'll post it)
```

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0628 (rev a1)

```

cat /proc/asound/card0/codec#* | grep Codec
```
Codec: Realtek ALC662 rev1
Codec: Motorola Si3054
Codec: Nvidia ID 5
```
Windows shows it as a separate sound device.  Vendor id 10DE Device id 0005.  I could not find this anywhere within gnome device manager.

What been tried...
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)  Alsa Upgrade Script, only with default kernel
PPA nVidia Drivers from [https://launchpad.net/~thefirstm/+archive/ppa](https://launchpad.net/~thefirstm/+archive/ppa)
nVidia drivers from nVidia web site. 185
IEC958 and IEC958 PCM in all possible combinations
Made all the controls visible in volume controls and made sure that all items are unmuted
Various suggestions from other threads.  Lost track of them all.
Second display as both Twinview and new X screen though nVidia setting.

The only thing I seem to achieve is either killing the install completely or somehow killing sound altogether. ](*,)

What I would like to know is.. Is it possible?  If so how?  :popcorn:
Thanks in advance.

---------------------
Solved in #5/#6
---------------------
edit: Fixed in Alsa 1.0.22, a modified version of [ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?p=6589810") can install it.  My version of it is attached but will still say its 1.0.21.

---

### Post by xzero1 on 2009-05-29
This thread  [http://ubuntuforums.org/showthread.php?t=1154388&page=2](http://ubuntuforums.org/showthread.php?t=1154388&page=2) may help, see post #15.

---

### Post by Chrisn02 on 2009-05-31
> **xzero1 said:**
> This thread  [http://ubuntuforums.org/showthread.php?t=1154388&page=2](http://ubuntuforums.org/showthread.php?t=1154388&page=2) may help, see post #15.
Thanks for the info.  So far nothing but I will keep trying different models.

I've updated the information in the original post with some other information that might be useful.  

Thanks.

---

### Post by jeegiz on 2009-06-01
i have HP DV4 laptop, with "Codec: Nvidia ID 3" HDMI output. I did not try latest alsa snapshots, but the only way to get HDMI output working  (and listed in aplay -l) with 2.6.29 kernel was to patch alsa source with "Nvidia ID 3" model value. 

I cannot provide patch now, i found it somewhere in Asus laptop forums. 

It seems that Nvidia hdmi audio is implemented, but not all models are listed in drivers, so some patching may be required until alsa maintainers update alsa code.

---

### Post by Chrisn02 on 2009-06-01
> **jeegiz said:**
> i have HP DV4 laptop, with "Codec: Nvidia ID 3" HDMI output. I did not try latest alsa snapshots, but the only way to get HDMI output working  (and listed in aplay -l) with 2.6.29 kernel was to patch alsa source with "Nvidia ID 3" model value. 

I cannot provide patch now, i found it somewhere in Asus laptop forums. 

It seems that Nvidia hdmi audio is implemented, but not all models are listed in drivers, so some patching may be required until alsa maintainers update alsa code.

Success!
After seeing your post I had a bit of a dig around on the net but didn't find anything about it so I had a go at patching the alsa drivers myself.  Turned out to be easier than I thought.


In "alsa-driver-1.0.20\alsa-kernel\pci\hda\patch_nvhdmi.c"
I added
```
{ .id = 0x10de0005, .name = "9800m HDMI", .patch = patch_nvhdmi },
```
to the snd_hda_preset_nvhdmi list then added 
```
MODULE_ALIAS("snd-hda-codec-id:10de0005");
```
with all the other MODULE_ALIAS just below when I added the others.
then compiled/installed.  
After a restart HDMI appeared in the list although volume was low and still played no sound even with the volume up.  Next went to the volume controls and enabled "IEC985 1" on HDA Intel.  After that sound played no trouble though HDMI.

I'm now doing a reinstall to make sure it works.

Thank you both xzero1 and jeegiz for your help with this. :D

---

### Post by Chrisn02 on 2009-06-01
Reinstall worked.  
The file attached is the "patch_nvhdmi.c" that I used.
It will probably only work on Alsa 1.0.20 and only id 10de0005 has been added to it.  

[ALSA Upgrade Script]("http://ubuntuforums.org/showthread.php?p=6589810") can be used to compile this by first downloading with 
```
sudo ./AlsaUpgrade-1.0.x-rev-1.17.sh -d
```
 then copying the file to "/usr/src/Alsa-1.0.20/alsa-driver-1.0.20/alsa-kernel/pci/hda/" then continue the compile by using 
```
sudo ./AlsaUpgrade-1.0.x-rev-1.17.sh -i
```
After restart "IEC985 1" needs enabling on HDA Intel.

---

### Post by sherl0k on 2009-06-03
Wow, I'm having this same problem and I'm going to give it a shot myself when I get home. My nVidia ID is the same as yours (5) so hopefully this will do the trick! Thanks for posting this info, saves me a headache and a half.

edit: Alright, I did everything from a shell, followed the directions as you posted and an aplay -l output shows the HDMI :) While I can't 100% confirm it works since I'm not at home, but I'm almost positive it works! Thank you thank you thank you!

---

### Post by balomenos on 2009-10-22
Chrisn02 I would just like to say thank you. I have been struggling to fix the hdmi problem, and with your patch everything was a success! Great job!

---

### Post by kvcckid on 2011-01-14
Hello, I recently built a new computer and got an evga 570GTX (Nvidia)
I was using windows 7 pro that I got for free from school (MSDN or something) but it was crashing every 5 minutes.  I could get on a play a game for 4 hours, but cuz cursing around or surfing the web was crashing all the time.  Complete freeze.  Couldn't start the task manager, number lock and caps lock jammed ect...

I was starting to think it was my MOBO failing because of the reviews until I installed ubuntu and everything was fine, no crashing no bull$#!7 no evil sauce.

Only problem was I installed 10.04 and fought it for a day with no luck installing the graphic card drivers but today I installed 10.10 and it picked up the nvidia drives right away.

Now the only problem I am having is audio.

In Windows I could play audio over the HDMI cable but in ubuntu I cannot.

I've tried using a headphone cable and that doesn't work either, and I know it's not the cable or the green sound port on my MOBO because other speakers work in the port, headphones work, all the cables work ive tested them on other computers and speakers and in cars, so the only thing left is the OS.  I want to be able to play audio from the computer over the hdmi cable to the TV.  

I've played around in the sound settings for hours... NOTHING.

I dont get how something so as audio over HDMI or a headphone jack/cable can be done by windows and not UBUNTU!!!

---

### Post by BicyclerBoy on 2011-01-14
*buntu 10.10 has alsa 1.0.23 modules which is requirement.

I don't think you are using the nvidia driver.
But you need to get the latest nvidia driver for GTX5xx from nvidia maybe from here.
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) 

Then your hdmi audio devices will show up (after reboot).

---

### Post by lidex on 2011-01-15
It may be helpful to update to the latest alsa-snapshot.
Try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
[COLOR="Red"]Have a look here:
[http://ubuntuforums.org/showthread.php?t=1552250](http://ubuntuforums.org/showthread.php?t=1552250)[/COLOR]

---

### Post by kvcckid on 2011-01-15
> **BicyclerBoy said:**
> *buntu 10.10 has alsa 1.0.23 modules which is requirement.

I don't think you are using the nvidia driver.
But you need to get the latest nvidia driver for GTX5xx from nvidia maybe from here.
[http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) 

Then your hdmi audio devices will show up (after reboot).

Hello and thank you for your response. 
I do have the proper nvidia driver installed and the nvidia HDMI audio option shows up in the sound preferences but nothing comes out my TV.

---

### Post by BicyclerBoy on 2011-01-15
What version nvidia driver..??
Your super duper video card needs a recent driver...

I think your 10.10 kernel version is okay..

Remember windows has thousand of developers working for 15 years.
Microsoft is a gatekeeper to all APIs drivers everything...
Everyone writes drivers for windows.
Everyone buys windows & windows only hardware ...

Microsoft did not have OSS alsa pulse jack,  to overcome..
But Linux is very dynamic: this is a blessing & a curse... 

You may only need to select the correct sound card & device ...

---

### Post by tjones00 on 2011-01-15
Commercial os developers want their userbase to be dependant upon them. It's not about how easy something is to setup it's about loss of control. It's like buying a car with the hood welded shut. And the kicker is you paid extra to have them weld it shut.

As to hdmi try the probemasks apparently they worked for one person today.

```
sudo gedit /etc/modprobe.d/sound.conf
```add

```
options snd-hda-intel probe_mask=0x102
```save the file and reboot

test the probemask by typing in a terminal
```

aplay -Dhdmi:NVidia /usr/share/sounds/alsa/Front_Center.wav
```if that doesn't work try 0x101 0x104 and 0x108

If aplay works but you still don't get sound being passed through your desktop try editing the /etc/pulse/default.pa pulseaudio file specifically the static section load-module module-alsa-sink device=hdmi:NVidia to point to your hdmi device and remove all user settings. If that fails purge pulseaudio from the system.

---

### Post by lidex on 2011-01-16
My new sig:
> And the kicker is you paid extra to have them weld it shut

---

