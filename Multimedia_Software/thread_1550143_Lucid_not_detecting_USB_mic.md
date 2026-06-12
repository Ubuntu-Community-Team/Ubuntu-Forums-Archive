---
title: "Lucid not detecting USB mic"
date: 2010-08-10
forum: Multimedia Software
---

### Post by getack on 2010-08-10
Well I have this really shweet Samson C01U usb studio condenser mic. When it is plugged in before I boot my machine, everything works like a charm, and I can sound like a rockstar recording my stuffs in UbuntuStudio 10.04 x64.

But when I'm not being a rockstar, I'm using my normal Lucid distro to go about my everyday tasks. So when I decide to call someone on skype, I plug the mic in, and nothing happens. The sound config window does not show the device? I do not want to reboot every time to use the mic (and that's all that works), and I do not want to leave it standing on my desk either.

Any ideas? Maybe I should restart Pulse or something? Help would be appreciated!

---

### Post by lidex on 2010-08-11
Restarting pulse may well do it, but it should work automatically. Have you tried switching devices in 'Sound Preferences' once plugged in?
[http://ohioloco.ubuntuforums.org/showthread.php?t=843012](http://ohioloco.ubuntuforums.org/showthread.php?t=843012)

---

### Post by getack on 2010-08-11
Well I tried to restart Pulse using ```
pulseaudio --kill
``` and then starting it again, didn't work. It looks like the mic is not being detected by the USB? The little LED on the mic is working, but lsusb does not show any mic!

Any ideas?

---

### Post by lidex on 2010-08-11
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

### Post by getack on 2010-08-14
Thanks for the interest!

The machine I'm using is a desktop PC with an Intel DG35EC mobo, Intel E7300 dual core 2.4 GHz CPU, with 4GB of ram, a random array of HDD's and screens :-).

Here is the output for previous poster's commands:


```
daniel@daniel-linux:~$ uname -a
Linux daniel-linux 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux

daniel@daniel-linux:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
daniel@daniel-linux:~$ dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA

daniel@daniel-linux:~$ head -n l /proc/asound/card*/codec#*
head: l: invalid number of lines
```

Another strange thing I realised today, Like I said, when I reboot with the mic plugged in, then it works and everything is fine. Otherwise it doesn't work. However, This morning I rebooted with the mic in, and my sound panel is picking it up as an input device, like it should. But if I unplug it, it's gone, and when I plug it back in, it works again! So it looks like only a reboot without the mic plugged in that causes the problems? As if some driver is not loaded when I reboot without the mic, and then it never works after that.

---

### Post by lidex on 2010-08-14
If it fails to work when hot-plugging, try loading the sound module. Probably 'snd-usb-audio':
```
sudo modprobe snd-usb-audio
```
Your alsa-base.conf file may need to be tweaked. It probably has this listed twice:
```
options snd-usb-audio index=-2
``` to keep it from loading as default device. A change to that may help, not sure though. Try starting up without mic attached and run this command:
```
lsmod | grep snd
```
Post the results here.

---

### Post by HeadHunter00 on 2010-09-04
hey mate, i have sorta a similar problem, but instead of a usb mic, its a normal analog mic. my problem is that the analog mic works on vista, but not ubuntu, it doesnt even get detected. i have a laptop with built in mic, but that doesnt help me in my work, and thats the only one that worx. my kernel is 2.6.35.4 custom compiled, but it doesnt work in any kernel, i have booted into each one. rebooting doesnt help either. any tips on how to change the mic from my internal laptop mic to external mic?

---

### Post by lidex on 2010-09-04
> **HeadHunter00 said:**
> hey mate, i have sorta a similar problem, but instead of a usb mic, its a normal analog mic. my problem is that the analog mic works on vista, but not ubuntu, it doesnt even get detected. i have a laptop with built in mic, but that doesnt help me in my work, and thats the only one that worx. my kernel is 2.6.35.4 custom compiled, but it doesnt work in any kernel, i have booted into each one. rebooting doesnt help either. any tips on how to change the mic from my internal laptop mic to external mic?

You should be able to do that with alsamixer. I suggest using the gui version: gnome-alsamixer.
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

### Post by HeadHunter00 on 2010-09-05
That doesn't work for me at all. Even if I plug in my external analog mic, alsa will still use my internal laptop mic. My laptop mic is working though, its just not that good. Note that usb mics work on my machine by changing the sound card, but analog mics dont work at all because unlike the analog headphones, analog mic isn't replaced with the internal mic, you know for inputting sound. It used to work in karmic, then after upgrading I didnt really give a <self-censored> about the mic until now when I have to work on my school project, and need a crazy good mic.

---

### Post by HeadHunter00 on 2010-09-05
also, another interesting thing is that when i plug in the mic, the sound stop coming from the built-in speakers so i have to plug in a headphone as well. i dont know if thats really necessary, but just to let you know. Hmm, so I have come to an assumption that ubuntu thinks that my mic is a headphone. how do i convince it that its a mic and not a headphone? ANOTHER interesting thing, the line-in mic works on arch linux, gentoo, debian live cds. All of which dont have pulseaudio, only alsa. Which means, this problem has nothing to do with alsa, only pulseaudio sound server.

---

### Post by lidex on 2010-09-05
*HeadHunter00:*
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by HeadHunter00 on 2010-09-05
> **lidex said:**
> *HeadHunter00:*
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Enter your user password when prompted. Choose the upload option and provide a link for the output.
it says that my information is located at this link: [http://www.alsa-project.org/db/?f=35921c73de453e1c41a796a1ba9eb8b530769bcc](http://www.alsa-project.org/db/?f=35921c73de453e1c41a796a1ba9eb8b530769bcc)
also, i have an hp dv6000 laptop

---

### Post by HeadHunter00 on 2010-09-05
oh, i am so damned stupid. i was plugging in the mic in the wrong port. sorry for bothering you man, now go help those that are truly in need.):P

---

### Post by HeadHunter00 on 2010-09-05
oh thats right, i didnt start the thread. so, uh did u try changing the input device in your sound preferences. and also make sure u have alsa-firmware and alsa-oss installed in synaptics.

---

### Post by Sami_Sdata on 2010-09-25
Any new updates on this? I'm getting a similar issue with a USB headset.  It works fine if plugged in while booting.  If I plug it in afterward syslog shows it's detected but not loading the driver.

Sep 25 15:31:04 hu kernel: [ 1690.732410] usb 1-2.3: new full speed USB device using ehci_hcd and address 9
Sep 25 15:31:04 hu kernel: [ 1690.830485] usb 1-2.3: configuration #1 chosen from 1 choice

If I modprobe snd-usb-audio it loads and works fine.

lsusb shows

Bus 001 Device 009: ID 046d:0a01 Logitech, Inc. USB Headset

I'm running Lucid on an old eeepc 900.

---

### Post by lidex on 2010-09-26
> **Sami_Sdata said:**
> Any new updates on this? I'm getting a similar issue with a USB headset.  It works fine if plugged in while booting.  If I plug it in afterward syslog shows it's detected but not loading the driver.

Sep 25 15:31:04 hu kernel: [ 1690.732410] usb 1-2.3: new full speed USB device using ehci_hcd and address 9
Sep 25 15:31:04 hu kernel: [ 1690.830485] usb 1-2.3: configuration #1 chosen from 1 choice

If I modprobe snd-usb-audio it loads and works fine.

lsusb shows

Bus 001 Device 009: ID 046d:0a01 Logitech, Inc. USB Headset

I'm running Lucid on an old eeepc 900.

Have a look here:
[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by Sami_Sdata on 2010-09-28
I'll read through that link but it doesn't appear to be Lucid specific.  The hardware worked out of the box with 9.10.  The problem didn't start till I upgraded to Lucid.  I say upgraded but it was a clean new install.  I then copied my ~/ back over.

---

