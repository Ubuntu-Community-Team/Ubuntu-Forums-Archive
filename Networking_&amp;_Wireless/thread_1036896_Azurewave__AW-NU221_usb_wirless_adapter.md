---
title: "Azurewave  AW-NU221 usb wirless adapter"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by maroo1 on 2009-01-11
Hi...
First things first, im am complete noob with linux/ubuntu, but I am okay at windows. I have done a new installation of 8.10 on my single hd (no dual boot or anything, ubuntu is my only os). Most of the stuff has been working fine BUT my usb wifi adapter hasnt been picked up by ubuntu. I do have a cd with the windows driver, but the cd does not contain the specfic sys and inf files- it has an exe which installs a utility which installs the driver(windows only). I tried running the cd through wine but but doesnt work with it properly. I have managed to get a file callled rt2870.sys which is the driver being used in xp for this device. However this does not work with ndiskwrapper via the windows wireless drivers program.
I know this will not be easy to get working as it is not a very popular device... but i hope someone can give me step by step detailed instructions as to how to get this working. ( I have currently have a ethernet cable running from downstairs, out the garden and through my bedroom window into my pc - not a long term solution)
Any help is much appreciated
Jay

---

### Post by maroo1 on 2009-01-11
Update:
Found the appropriate inf file
used it on windows wirless driver utility (rt2870: hardware present: yes
When i press the configure network button it says "Could not find a network configuration tool."

---

### Post by maroo1 on 2009-01-11
So i got past the "could not find network configuration tool" by installing gnome network manager
But now when i click on configure network in the wireless network drivers program, a new window opens called network settings but everything is greyed out and unchangeable - the only thing i can do in that window is press the close or help button?

---

### Post by maroo1 on 2009-01-11
please help

---

### Post by kayvortex on 2010-01-16
Edit: this may be a dead thread, but if somebody else stumbles upon it (like I did) then this is my solution:

I recently installed Karmic on my PC and also needed some decent wireless drivers for it seeing as there seems to have been a regression in this particular driver from previous releases. This is what I did (note, this was for an amd64 installation, so I'd imagine it'd work for i386 too):

Target system: Ubuntu 9.10 Karmic Koala amd64.
Product: Azurewave AW-NU221 IEEE 802.11n/g/b Wireless USB Adapter
Chipset: Ralink RT2870

**What to not bother doing:**
Don't bother finding the Windows driver and using ndiswrapper, and don't bother downloading Azurewave's windows driver and trying to cabextract or unshield a .inf file. You shouldn't need to do it.

**What to do:**
Google around. By the time you read this things may have changed (for one thing, you might be using Lucid, or M*, or N*, etc.).
Read these references:
1) [ubuntu forum topic on the installation procedure]("http://ubuntuforums.org/showthread.php?t=960642")
2) [some clearer instructions]("http://ubunturt2870.pbworks.com/FrontPage")

**Steps to follow:**
[LIST=1]
[*] Install the necessary compiling tools. Open the file **/etc/apt/sources.list**:
```
gksudo gedit /etc/apt/sources.list
```
and remove the "#" from the top line. In my file, the line reads:
> #deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted
Change it to:
> deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release amd64 (20091027)]/ karmic main restricted

[*] Put your Ubuntu installation CD in your CD Drive and then type in:
```
sudo aptitude install build-essential
```

[*] Get the Ralink drivers. [This is the link as of January 2010.]("http://www.ralink.com.tw/support.php?s=2") Click on the link "RT2870USB(RT2870/RT2770)" and fill in your details (or just make something up!) and download the file.
If that link doesn't work, then google "Ralink linux drivers" to look for the Ralink site for their linux drivers. Then look for the "RT2870" drivers.

[*] Go to where the file was downloaded to ("Downloads" folder in Karmic), and enter:
```
tar xjf RT2870_LinuxSTA_V2.3.0.0.tar.tar.bz2
```
**NOTE: your file may not be called "RT2870_LinuxSTA_V2.3.0.0.tar.tar.bz2": use whatever file you downloaded instead!**

[*] After tar finishes extracting, change into the directory it created (on my system, the directory was called "RT2870_LinuxSTA_V2.3.0.0"). Open the file **os/linux/config.mk**:
```
gedit os/linux/config.mk
```
and change the line
> HAS_WPA_SUPPLICANT=n
to
> HAS_WPA_SUPPLICANT=y
and
> HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
to
> HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y.

[*] Now, let's make the driver. Just run "make":
```
make
```

[*] If this finishes OK and no errors occur (ignore the warning messages), then run:
```
sudo make install
```
If errors occur, then read the file "README_STA" and see if there's any suggestions in there. Otherwise, google the error message I suppose! (There's not much I'll be able to help with I'm afraid, but I'll try).

[*] Open the file **/etc/modprobe.d/blacklist.conf**:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and add to the end of the file:
> # Blacklist the included driver
blacklist rt2800usb

[*] That's it! The easiest thing to do is to simply reboot your machine, and you *should(!)* be able to connect now.
[/LIST]

---

