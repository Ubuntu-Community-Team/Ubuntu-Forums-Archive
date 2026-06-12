---
title: "Cant get any sound from ALC1200"
date: 2010-04-18
forum: Multimedia Software
---

### Post by 2chi on 2010-04-18
Hey,

 After a few days of battling with ubuntu 9.04, I still cant get no sound:popcorn:, eventually on one of the forums someone told me to upgrade to
10.04 beta, so i did but still nothing. Realy need some help to figure
this one out.

Things i did:

1; Installed pulseaudio using [this]("https://wiki.ubuntu.com/PulseAudio") tutorial.  
2;Also tried to change hda_intel.conf using this command : 
options snd-hda-intel model=auto probe_mask=1 - No luck.
3; Also tried to update realtek driver from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false") , still nothing.
4; Checked the alsamixer and other volume control, everything is up to max.

 So now i ran out of ideas, and and cant find nothing new on Google.
 Please help.

dan@dan-laptop:~$ aplay -l 
**** List of PLAYBACK Hardware Devices **** 
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog] 
Subdevices: 1/1 
Subdevice #0: subdevice #0 
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital] 
Subdevices: 1/1 
Subdevice #0: subdevice #0

dan@dan-laptop:~$ sudo lshw -class sound
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f8ef8000-f8efbfff

 Thanks.
 Dan.

---

### Post by 2chi on 2010-04-18
Bump;

 Thanks

---

### Post by lidex on 2010-04-18
Is this an upgrade or a fresh install? If upgraded, you probably have some cruft. Do "Part A" on this page:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by 2chi on 2010-04-19
> **lidex said:**
> Is this an upgrade or a fresh install? If upgraded, you probably have some cruft. Do "Part A" on this page:
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.


Thanks for you replay lidex.

This is my output before making any changes("Part A")

dan@dan-laptop:~$ uname -a
Linux dan-laptop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
dan@dan-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
dan@dan-laptop:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.
dan@dan-laptop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC1200

I am going to try Part A, and get back to you with the resaults

---

### Post by 2chi on 2010-04-19
Ok I am trying to make the first part of Part and this what i get :


[HTML]dan@dan-laptop:~$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
mkdir: cannot create directory `/home/dan/pulse-backup': File exists
dan@dan-laptop:~$ rm -r ~/.pulse ~/.asound* 
rm: cannot remove `/home/dan/.pulse': No such file or directory
rm: cannot remove `/home/dan/.asound*': No such file or directory[/HTML]



This is upgrade from Ubuntu 9.10, sound didn't work there also.
One more thing, in part A said "[SIZE=1]Part A: Common instructions (Hardy, Intrepid, Jaunty  & Karmic)[/SIZE]"
And my version of ubuntu is lucid(10.04). Am i talking nonsense ?

Thanks again.

---

### Post by 2chi on 2010-04-19
Continued Part A:

```
dan@dan-laptop:~$ sudo rm /etc/asound.conf
[sudo] password for dan: 
dan@dan-laptop:~$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2-plugins is already the newest version.
padevchooser is already the newest version.
padevchooser set to manually installed.
libsdl1.2debian-pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dan@dan-laptop:~$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not installed, so not removed
Package flashplugin-nonfree-extrasound is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
dan@dan-laptop:~$ pulseaudio & pavucontrol
[1] 3812
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:3813): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio
```

---

