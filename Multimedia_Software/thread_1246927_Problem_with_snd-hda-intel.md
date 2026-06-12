---
title: "Problem with snd-hda-intel"
date: 2009-08-22
forum: Multimedia Software
---

### Post by Lusse on 2009-08-22
Hi folks!

My company just bought me a new laptop and the first thing I did was ofc to install Ubuntu on it. It's a HP dv7-1265eo, with 64-bits processor (I installed Ubuntu 9.04 64-bit).

Been having some issues with the sound thought, when the login-sound is about to play it just repeats the first half second of it over and over again even after I have logged in. The volume decreases with tiny steps over time and after about 5 minutes you can't hear it anymore. I did some browsing on the forum and was able to find some pushes in the right direction.

I think that this can be solved by upgrading alsa to a newer version (1.0.20) so I downloaded the following packages made for Karmic Koala:

alsa-base
alsa-utils
libasound2
libasound2-plugins
lib32asound2

They installed fine but after a reboot I still have the same issue. I then ran a script downloaded from the alsa-project website: alsa-info.sh. It gave me a lot of information that can be found on: [http://www.alsa-project.org/db/?f=3d32c27c587fd18c9d3508dd029d36e6f38c7651](http://www.alsa-project.org/db/?f=3d32c27c587fd18c9d3508dd029d36e6f38c7651)

Here is a short part:

!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.20
Utilities version:  1.0.20

It looks like I wasn't able to update the driver and only updated the librarys and utilites.

So if someone knows the packages that needs to be updated to make the driver become 1.0.20, please share your knowledge!

//Linus Unnebäck
(sorry for bad english)

---

### Post by Lusse on 2009-08-22
Some more info:

I've updated linux-sound-base to 1.0.20 after searching for packages with version: 1.0.18. It didn't help.

The source package alsa-driver is used to build the following packages:

alsa-base
alsa-source
linux-sound-base

All of which I has updated to 1.0.20 (except alsa-source since it wasn't installed to begin with).

Please someone help me!

//Linus Unnebäck

---

### Post by Earl_Maroon on 2009-08-22
ALSA is not your only option. You could try installing OSS4 (not in repos: [http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi). The repo OSS is long outdated.) If you do this you will need to change your settings in System>Preferences>Sound.

---

### Post by Lusse on 2009-08-22
Not that OSS is bad but I would prefer ALSA, gonna try installing alsa-source and compile the drivers to see if it will do the trick, will ofc post back with info if it works or not.

Thanks for the tip, if I can't get alsa to work I will try it out.

//Linus Unnebäck

---

### Post by Lusse on 2009-08-22
Hi everyone!

I have now manage to get the driver up to 1.0.20. The steps I did to upgrade ALSA to 1.0.20 was:

1.
Download the following packages from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) choose Karmic as distribution

alsa-base
alsa-utils
libasound2
libasound2-plugins
lib32asound2
linux-sound-base
alsa-source

2.
Install some needed packages:

```
sudo apt-get install debconf-utils debhelper dpkg-dev build-essential linux-headers-$(uname -r) module-assistant
```

3.
Install the downloaded packages:

```
sudo dpkg -i ./libasound2*.deb ./alsa-*.deb ./lib32asound2*.deb ./linux-sound-base*.deb ./alsa-source*.deb
```

4.
Configure:

```
sudo dpkg-reconfigure alsa-source
```
I choosed:
yes
no
all

5.
Compile:
```
sudo module-assistant a-i alsa-source
```

6.
Reboot:

Instead of rebooting you could probably close all programs using alsa and then do ```
sudo alsa reload
``` but a reboot would be safer.


My sound still ain't working, but it is working better. The login sound now only repeats itself for about 1-2 seconds. Gonna look more into this problem later as I haven't got time right now.

If anyone has some relevant information please post it here because I really would like to have functional sound.

//Linus Unnebäck

---

### Post by SakJur on 2009-08-22
Hi Linus!

Have you tried Jaunty Jackalope and/or Hardy Heron?
As Karmic Koala ain't stable yet, use for any reason other than testing purposes not recommended.

Quickly searching gives this bugreport: [https://bugs.launchpad.net/ubuntu/+bug/100114](https://bugs.launchpad.net/ubuntu/+bug/100114) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424)

I hope that any of these two bug reports will help you further in your search to fix it. As I haven't got any experience with and SND-HDA-Intel chipset, I can't confirm or help you much further.

Send me an e-mail if your problem ain't solved in Karmic beta and/or stable.

Best wishes
Emil Tullstedt
Ubuntu Server Team

---

### Post by Lusse on 2009-08-23
> **SakJur said:**
> Have you tried Jaunty Jackalope and/or Hardy Heron?
As Karmic Koala ain't stable yet, use for any reason other than testing purposes not recommended.


Yes I have, as stated in the first message I use Jaunty Jackalope 64-bit.

> **SakJur said:**
> 
Quickly searching gives this bugreport: [https://bugs.launchpad.net/ubuntu/+bug/100114](https://bugs.launchpad.net/ubuntu/+bug/100114) and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/274424)
Ubuntu Server Team

The links actually helped me, had read the first before but the second one was new to me and it linked me in to the alsa-projects bugtracker. There I was able to find the solution to my problem. The only thing I needed to do was to add "options snd-hda-intel enable_msi=1" to my "/etc/modprobe.d/alsa-base.conf".

So now it works!! The login-ready-sound is gone thought but after login all sound is fully functional, big thanks to all that helped me. Now I just need to figure out why my computer freezes all the time aswell as why the network-manager sometimes crashes.

Should I file a bugreport about this? I'm gonna do some investigation to see what enable_msi really do...

EDIT: Message Signaled Interrupt, seems like all pci-express devices has this so maybe the alsa-base packages should check for pci-express at install and add this config-option in that case. I think that, correct me if I'm wrong, it's better to use MSI than not to so it should be standard to do; but is ofc just imho.

Info: [http://lwn.net/Articles/44139/](http://lwn.net/Articles/44139/)

//Linus Unnebäck

---

