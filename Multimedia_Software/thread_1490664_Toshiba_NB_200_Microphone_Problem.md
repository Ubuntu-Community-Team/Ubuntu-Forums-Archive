---
title: "Toshiba NB 200 Microphone Problem"
date: 2010-05-22
forum: Multimedia Software
---

### Post by i_surf_the_turf on 2010-05-22
Hello

I have recently solved the internal speaker problem on my Toshiba nb 200 netbook, by adding a line in a .conf file, as pointed out in a launchpad thread. (It's easy to find it through google! Just make sure you avoid kernel upgrades, it only needs one extra line)

The Toshiba netbook has a Realtek ALC272 chipset as specified in the ALSA Mixer, and it is supposed to be working but neither skype nor sound recorder works. I even tried changing the multimedia devices through System->Preferences but still nothing. The worst of all is that on threads people report that it works fine!

I have ubuntu 10.04 LTS, and I can now do anything but skype on linux.

Please, any ideas?

---

### Post by lidex on 2010-05-23
Try this. Use a terminal="Applications->Accessories->Terminal"
Enter these commands, one line at a time:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```

Reboot.

---

### Post by i_surf_the_turf on 2010-05-23
Worked!
You are a genious!
What do those commands do exactly?

---

### Post by lidex on 2010-05-23
> **i_surf_the_turf said:**
> Worked!
You are a genious!
What do those commands do exactly?
It basically adds a repository for some updated audio drivers and then installs them (linux-alsa-driver-modules).
Please mark the thread as solved using 'Thread Tools' up top.

---

### Post by Mspirit on 2010-06-07
Thanks fixed my problem..Have Toshiba nb205 but completely different sound problem...XD

---

### Post by mc10 on 2010-07-07
> **i_surf_the_turf said:**
> Hello

I have recently solved the internal speaker problem on my Toshiba nb 200 netbook, by adding a line in a .conf file, as pointed out in a launchpad thread. (It's easy to find it through google! Just make sure you avoid kernel upgrades, it only needs one extra line)

The Toshiba netbook has a Realtek ALC272 chipset as specified in the ALSA Mixer, and it is supposed to be working but neither skype nor sound recorder works. I even tried changing the multimedia devices through System->Preferences but still nothing. The worst of all is that on threads people report that it works fine!

I have ubuntu 10.04 LTS, and I can now do anything but skype on linux.

Please, any ideas?

I've got the same problem ! Moreover, I haven't solved the internal speaker problem yet... #-oAs I am brand new to ubuntu, I'm afraid I hardly could help you on that side at the moment (but I'm a quick learner...).
Maybe you might help me with the internal speaker instead.
Thanks.
P.S. ubuntu 9.10 on toshiba nb 200. I also tried older versions and 10.04 too (the netbook edition as well), but boot is too slow and still no sound from the internal speaker. I'm hopeless,
bye Marco

---

### Post by lidex on 2010-07-07
> **mc10 said:**
> I've got the same problem ! Moreover, I haven't solved the internal speaker problem yet... #-oAs I am brand new to ubuntu, I'm afraid I hardly could help you on that side at the moment (but I'm a quick learner...).
Maybe you might help me with the internal speaker instead.
Thanks.
P.S. ubuntu 9.10 on toshiba nb 200. I also tried older versions and 10.04 too (the netbook edition as well), but boot is too slow and still no sound from the internal speaker. I'm hopeless,
bye Marco

Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=auto 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

