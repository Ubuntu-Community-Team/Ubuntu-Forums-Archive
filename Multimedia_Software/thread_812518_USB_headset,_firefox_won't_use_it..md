---
title: "USB headset, firefox won't use it."
date: 2008-05-30
forum: Multimedia Software
---

### Post by DavidGX on 2008-05-30
I'm using a USB headset in ubuntu 8.04 AMD64. In the sound settings in gnome I've set everything to "USB Audio" and set the mixer accordingly.

The sound in firefox (flash, etc) works but it will only output to my laptops speakers. I can't seem to find a way to make firefox use my USB headset.

Any ideas?

---

### Post by DavidGX on 2008-05-31
Nothing yet...

---

### Post by DavidGX on 2008-05-31
Is there REALLY no solution for this? Does ubuntu just plain NOT like USB headsets?

---

### Post by DavidGX on 2008-06-01
Nothing yet...

---

### Post by Grigorius on 2008-06-19
I had the same problem, one thing that I noticed was that the same USB headset woked fine on my brothers comp which has the 64 bit version of UBUNTU ... so I uninstalled flash and reinstalled-it with nspluginwrapper ... and sound somehow worked ... well for me ... the second way is to buy a normal headset :)

[http://gwenole.beauchesne.info//en/projects/nspluginwrapper](http://gwenole.beauchesne.info//en/projects/nspluginwrapper)

Please tell me if it worked.

---

### Post by jepperstone on 2009-06-14
I have the same issue. I use Ubuntu 9.04 and Logitech ClearChat Comfort USB headset. Rhythmbox works fine but Firefox and VLC don't work at all :(

aplay -l returns the following:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Headset [Logitech USB Headset], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


cat /proc/bus/input/devices returns (among other things):

> I: Bus=0003 Vendor=046d Product=0a0c Version=0100
N: Name="Logitech Logitech USB Headset"
P: Phys=usb-0000:00:1d.1-1/input3
S: Sysfs=/devices/pci0000:00/0000:00:1d.1/usb6/6-1/6-1:1.3/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=13
B: KEY=c0000 0 0 0
B: MSC=10


can anyone help?

---

### Post by kostkon on 2009-06-17
> **jepperstone said:**
> I have the same issue. I use Ubuntu 9.04 and Logitech ClearChat Comfort USB headset. Rhythmbox works fine but Firefox and VLC don't work at all :(

aplay -l returns the following:


cat /proc/bus/input/devices returns (among other things):



can anyone help?
You could have made a new thread for your problem.

Anyway, you need to install the *PulseAudio Device Chooser* utility using *Synaptic*.

Run it and it will put its icon in your system tray. Left-click on it and select *Volume Control*.

Select the *Output Devices* tab and you should see your USB headset listed there. You can right-click on its entry and enable the *Default* option if you want to make it the default output device in your system.

For some applications (like *Flash* in *Firefox*) you may need to manually move their audio stream to your USB headset. Don't worry you only need to do this once.

In the case of *Flash*, for example, just open the *PulseAudio* volume control again and select the *Playback* tab. You should see there the audio stream of the *Flash* you are playing. Right-click on it and select *Move Stream...* and in the list that will appear select your headset.

You can set *PulseAudio Device Chooser* to start every time you login from its preferences, if you want.

For more info check [this thread here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

