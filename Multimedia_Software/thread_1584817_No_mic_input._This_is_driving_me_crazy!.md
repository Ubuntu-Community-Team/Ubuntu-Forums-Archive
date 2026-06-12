---
title: "No mic input. This is driving me crazy!"
date: 2010-09-29
forum: Multimedia Software
---

### Post by uMany on 2010-09-29
Have had this problem since installed Ubuntu Karmic in my Sony Vaio VPCF11FD laptop.

No input sound at all!
Now I have Ubuntu 10.04

I really need help with this. I NEED input sound for work and I cant stand the lack of it any more.

Please help me.

Here is the info of my system:

Linux 2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:05:27 UTC 2010 x86_64 GNU/Linux

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC275 Analog [ALC275 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC275 Digital [ALC275 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1

dpkg -l | grep "alsa"
ii  alsa-base                                       1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware                                   1.0.17-0medibuntu2.9.10.1                       Contains firmware for ALSA devices - Medibuntu package
ii  alsa-firmware-loaders                           1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                        1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                                     1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                      1.0.22-0ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                  1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                                      1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                      4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                 0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                              0.10.28-1                                       GStreamer plugin for ALSA
ii  libclalsadrv1                                   1.2.2-2                                         ALSA driver C++ access library
ii  libesd-alsa0                                    0.2.41-6ubuntu1                                 Enlightened Sound Daemon (ALSA) - transitional package
rc  libsdl1.2debian-alsa                            1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA options)
ii  libsox-fmt-alsa                                 14.3.0-1.1build1                                SoX alsa format I/O library
rc  linux-backports-modules-alsa-2.6.31-20-generic  2.6.31-20.22                                    Ubuntu supplied Linux modules for version 2.6.31 ALSA s
ii  linux-backports-modules-alsa-2.6.31-21-generic  2.6.31-21.23                                    Ubuntu supplied Linux modules for version 2.6.31 ALSA s
ii  python-alsaaudio                                0.5+svn36-1ubuntu1                              Alsa bindings for Python

---

### Post by 0N3 on 2010-09-29
Can you post a pic of your your sound preferences or describe the settings to me?
I can confirm alot of people on 10.10 are who never had sound have it now including myself.

---

### Post by 0N3 on 2010-09-29
preferably your hardware settings, input settings and output settings would be really helpful to attach a pic for each of these settings

---

### Post by uMany on 2010-09-29
> **0N3 said:**
> preferably your hardware settings, input settings and output settings would be really helpful to attach a pic for each of these settings

Do you mean this?

---

### Post by 0N3 on 2010-09-29
Can you tell me the available options from the drop down menus in each picture also sorry its a little different to mine i am using 10.10 better Mic and sound support on it full release is due 10th of next month id recommend using it. 10.10 is still in Beta so its a little buggy if I don't get back to you tonight i definitely will tomorrow. List as follows

Pic 1 : options 

Pic 2 Options ect.......

Have you tried playing around with the configuration? Also try install this 

sudo apt-get install gnome-alsamixer (check nothing is muted mic, input source ect.....)

---

### Post by uMany on 2010-09-29
Yes of course,

In Configuration the options are:
under High Definition Audio Controller
only there are 
-> Digital Stereo (HDMI) Output
-> Off
Under internal Audio
-> Analog Surround 4.0 Output + Analog Stereo Input
-> Analog Stereo Duplex
-> Analog Stereo Input
-> Digital Stereo (IEC958) Output + Analog Stereo Input
-> Digital Stereo Duplex (IEC958)
-> Analog Surround 4.0 Output
-> Analog Stereo Input
-> Off

Input Devices
-> All input Devices
-> All Except Monitors
-> Hardware Input Devices
-> Virtual Input Devices
-> Monitors

Output Devices
-> All Output Devices
-> Hardware Output Devices
-> Virtual Output Devices

I've been trying every combination of configuration
I've already installed gnome-alsamixer and everything is unmuted

Thanks a lot for your help.

---

### Post by 0N3 on 2010-09-30
Under configuration Tab:

Change your Internal Audio Profile to Analog Stereo Duplex

You should see a Mic 1 and a Mic 2 you need to select Mic 2

---

### Post by 0N3 on 2010-09-30
Try ignore any HDMI configuration it was brutal on 10.04 slightly better on 10.10 user your internal device the Intel sound card worked for me

---

### Post by lidex on 2010-09-30
I see you have alsa-backports for kernel 2.6.31.x installed. You are currently using 2.6.32.x I would suggest removing them and installing the generic package which will automagically update to the correct kernel version. Should be something like:
```
linux-backports-modules-alsa-lucid-generic
```

---

### Post by uMany on 2010-09-30
ON3:
I changed everything as you said but still no mic :-(

Lidex:
I uninstalled the linux-backports-modules-alsa-2.6.31-20-generic
but when I run the grep command, it is still listed.
How do I get ride of it?

Thanks you both

---

### Post by lidex on 2010-10-01
> **uMany said:**
> ON3:
I changed everything as you said but still no mic :-(

Lidex:
I uninstalled the linux-backports-modules-alsa-2.6.31-20-generic
but when I run the grep command, it is still listed.
How do I get ride of it?

Thanks you both

Probably doesn't matter as long as the correct version for your current kernel is in there. What is this output now:
```
dpkg -l | grep "alsa"
```

---

### Post by uMany on 2010-10-02
Hi Lidex, here is the output
dpkg -l | grep "alsa"
warning, in file '/var/lib/dpkg/available' near line 53080 package 'virtualbox-3.1':
 error in Version string '3.1.6-59338_Ubuntu_karmic': invalid character in revision number
ii  alsa-base                                       1.0.23+dfsg-1ubuntu4                            ALSA driver configuration files
ii  alsa-firmware                                   1.0.17-0medibuntu2.9.10.1                       Contains firmware for ALSA devices - Medibuntu package
ii  alsa-firmware-loaders                           1.0.23-3ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                        1.0.17-4                                        ALSA wrapper for OSS applications
ii  alsa-source                                     1.0.23+dfsg-1ubuntu4                            ALSA driver sources
ii  alsa-tools                                      1.0.23-3ubuntu1                                 Console based ALSA utilities for specific hardware
ii  alsa-tools-gui                                  1.0.23-3ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                                      1.0.23-2ubuntu3                                 Utilities for configuring and using ALSA
ii  bluez-alsa                                      4.69-0ubuntu2                                   Bluetooth audio support
ii  gnome-alsamixer                                 0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                              0.10.30-2                                       GStreamer plugin for ALSA
rc  libclalsadrv1                                   1.2.2-2                                         ALSA driver C++ access library
ii  libclalsadrv2                                   2.0.0-3                                         ALSA driver C++ access library
rc  libsdl1.2debian-alsa                            1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA options)
ii  libsox-fmt-alsa                                 14.3.1-1build1                                  SoX alsa format I/O library
rc  linux-backports-modules-alsa-2.6.31-20-generic  2.6.31-20.22                                    Ubuntu supplied Linux modules for version 2.6.31 ALSA snapshots.
ii  linux-backports-modules-alsa-2.6.32-25-generic  2.6.32-25.23                                    Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
ii  python-alsaaudio                                0.5+svn36-1ubuntu1                              Alsa bindings for Python

Note that I upgrade to 10.1 last night
And I think I have to run the ALSA Upgrade Script, Am I right?

---

### Post by lidex on 2010-10-02
> **uMany said:**
> Hi Lidex, here is the output
dpkg -l | grep "alsa"

Note that I upgrade to 10.1 last night
And I think I have to run the ALSA Upgrade Script, Am I right?

No. If you are on 10.10 (maverick) your kernel version is 2.6.35.xx. The upgrade script won't work with that and you're at alsa 1.0.23 anyway.

Need updated info. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by uMany on 2010-10-03
Mr. Lidex here is the link:
[http://www.alsa-project.org/db/?f=eaa4cdef38d0892dd1b7c12ac3649ed0544e6321](http://www.alsa-project.org/db/?f=eaa4cdef38d0892dd1b7c12ac3649ed0544e6321)

---

### Post by lidex on 2010-10-03
You are fully updated. Sorry to take you to boilerplate:
First, for mic problem, check this.
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

Then go to 'Sound Preferences' to select and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by uMany on 2010-10-03
Hi Lidex,
I did everything, as you can see in the captures, but still no mic... I don't know what else to do...
In the sound preferences, there is no level input but I don't know why because is not muted at all.

---

### Post by lidex on 2010-10-03
Actually all I'm seeing here is a mic boost & front mic boost. 
Time to get dirty. I want you to go into synaptic and search 'alsa'. Select 'Installed' filter on the left. 
Any packages with backports in name, mark for complete removal and apply. 
Now reboot (if there were changes).
Next re-install alsa:
Using a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
```
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
This will get you back to the default install.
Now this:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Last:
```
apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**

---

### Post by uMany on 2010-10-03
Finally input sound!
Thanks A LOT mister Lidex, the next ubuntu version should be call lidex!
I follow you instructions letter by letter, but as an a teaching/learning experience, can you please, if is not too much from me, explain me what was happening and how did you know what needed to be done?
Thanks, thanks thanks again.
You rock!

---

### Post by lidex on 2010-10-05
> **uMany said:**
> Finally input sound!
Thanks A LOT mister Lidex, the next ubuntu version should be call lidex!
I follow you instructions letter by letter, but as an a teaching/learning experience, can you please, if is not too much from me, explain me what was happening and how did you know what needed to be done?
Thanks, thanks thanks again.
You rock!

Wow - yah - finally!!
The final step I felt necessary to get alsa to correctly "see" your pin configuration. Looking back through all the info you've posted I realized alsa did not recognize the mic input, only showing mic boost and front mic boost. My thinking was that we needed to get back to a default, correctly installed alsa and then apply the latest alsa-modules as newer versions support more hardware.

Basic troubleshooting requires a known configuration to debug with any accuracy. You probably did a lot of different things in this process that could have affected your install.

---

### Post by uMany on 2010-10-09
Well all in all it is fantastic to have input sound.
I started to make some screencast for my work fellows...
The only tiny thing, its that my laptop has an input port that seems not to be working...But it is really a minor flaw to me right now.
If you know a way to get it to work I'll appreciate it.
Thanks, thanks thanks.

---

### Post by lidex on 2010-10-10
> **uMany said:**
> Well all in all it is fantastic to have input sound.
I started to make some screencast for my work fellows...
The only tiny thing, its that my laptop has an input port that seems not to be working...But it is really a minor flaw to me right now.
If you know a way to get it to work I'll appreciate it.
Thanks, thanks thanks.

If it is a mic input it may require 'mic boost'

---

### Post by jgrocha on 2010-11-09
Thanks, lidex. It is now working on a Sony Vaio VPCF13Z1E, with Ubuntu amd64 10.10.

I've simple done:
```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
apt-get install linux-alsa-driver-modules-$(uname -r)

```
The internal mic has some noise on the background, but the input jack works great.

Regards!

---

### Post by scratch178 on 2010-11-19
hi

i followed lidex instructions and it worked.

my mic is working fine!!!!
but my left speaker is not working anymore, the right one is okay.

Need some Help with this, using ubuntu 10.10 x64

---

