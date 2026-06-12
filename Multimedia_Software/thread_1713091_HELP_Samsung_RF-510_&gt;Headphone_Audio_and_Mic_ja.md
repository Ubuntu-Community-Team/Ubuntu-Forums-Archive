---
title: "*HELP* Samsung RF-510 &gt;Headphone Audio and Mic jacks not working in Ubuntu 10.04"
date: 2011-03-23
forum: Multimedia Software
---

### Post by stevpm on 2011-03-23
[IMG]https://lh3.googleusercontent.com/_HvKNh8ktS6M/TYpRD8-9RhI/AAAAAAAAAnw/2caTi-XTV_E/s576/Screenshot-Untitled%20Window.png[/IMG][IMG]http://ubuntuforums.org/%3Ctable%20style=%22width:auto;%22%3E%3Ctr%3E%3Ctd%3E%3Ca%20href=%22https://picasaweb.google.com/lh/photo/8DyDya3bCjYrU2P-A1XJjZ5U_90Qrby7fJc-XtjH6-k?feat=embedwebsite%22%3E%3Cimg%20src=%22https://lh3.googleusercontent.com/_HvKNh8ktS6M/TYpRD8-9RhI/AAAAAAAAAnw/2caTi-XTV_E/s144/Screenshot-Untitled%20Window.png%22%20height=%22128%22%20width=%22144%22%20/%3E%3C/a%3E%3C/td%3E%3C/tr%3E%3Ctr%3E%3Ctd%20style=%22font-family:arial,sans-serif;%20font-size:11px;%20text-align:right%22%3EFrom%20%3Ca%20href=%22https://picasaweb.google.com/stevpm/MyUbuntu?authkey=Gv1sRgCM6NnN_t9tqxBg&feat=embedwebsite%22%3EMy%20Ubuntu%3C/a%3E%3C/td%3E%3C/tr%3E%3C/table%3E[/IMG][IMG]https://picasaweb.google.com/lh/photo/8DyDya3bCjYrU2P-A1XJjZ5U_90Qrby7fJc-XtjH6-k?feat=directlink[/IMG][IMG]https://picasaweb.google.com/lh/photo/8DyDya3bCjYrU2P-A1XJjZ5U_90Qrby7fJc-XtjH6-k[/IMG]

***[SIZE=2]I was using ubuntu 10.10 before re-installing my system to ubuntu 10.04LTS.[/SIZE]*** Since I did that the headphone jack is not working.
Plz i need help, my machine is Samsung RF510..:(

---

### Post by stevpm on 2011-03-24
!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfcb00000 irq 34
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xddefc000 irq 35


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

[SIZE=2]**Please, that is my alsa information...**[/SIZE]

---

### Post by stevpm on 2011-03-24
***[SIZE=4]Anyone please!!!!!!!!!![/SIZE]***

---

### Post by lidex on 2011-03-24
You went back to an earlier version of alsa which may not have the correct support for your audio chip. Try updating your alsa-driver-modules.
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
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by stevpm on 2011-03-25
[SIZE=2]stephen@stephen-laptop:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-21-generic
stephen@stephen-laptop:~$ [/SIZE]

[B][FONT=Georgia]thats what i got back..i did that after adding the repository and updating the repository as the commands u gave me!
where can z problem be?
thanks:)
Should i upgrade to generic 2.6.32-23 etc?
[/FONT][/B]

---

### Post by lidex on 2011-04-01
> **stevpm said:**
> [SIZE=2]stephen@stephen-laptop:~$ sudo apt-get install linux-alsa-driver-modules-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-alsa-driver-modules-2.6.32-21-generic
stephen@stephen-laptop:~$ [/SIZE]

[B][FONT=Georgia]thats what i got back..i did that after adding the repository and updating the repository as the commands u gave me!
where can z problem be?
thanks:)
Should i upgrade to generic 2.6.32-23 etc?
[/FONT][/B]

Yes. When was the last time you updated your system?
Try this:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```

Reboot.

---

