---
title: "Nvidia driver woes"
date: 2006-03-11
forum: Multimedia &amp; Video
---

### Post by Mutch on 2006-03-11
i have a GeForce FX 5700LE and i am attempting to install the nvidia drivers for my system. I have followed a couple of guides
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
[*][https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
[/LIST]
both of which resulted in an error on reboot "Failed to start xserver" leaving me with a nice CLI.
i did a "sudo dpkg-reconfigure xserver-xorg" and changed my drivers back to vesa. But im no closer to getting the nvidia drivers installed. 
Any ideas how to get them installed? 
Do i even need to install them? (i want to run dual monitors and games).
:confused: 

Mutch

P.S. Im very new to linux but learning fast :)

---

### Post by sirlancelot on 2006-03-12
So you've tried just doing```
sudo apt-get install nvidia-glx
```I'm still learning how to tweak linux too so I can't help much...

---

### Post by klahjn on 2006-03-12
I understand the stuff you are going through.  When i first faced the same problem, i was frustrated also.  if you followed the guides properly, you should actually have a backup of xorg.conf from before you edited it.  Usually it is either xorg.conf~ or xorg.conf.backup or something like that.  When you are in command line it can be frustrating, but it does seem very simple.  you may need to type sudo before some of these commands to actually get what you need done.  hope this helps

login to cli

cd /etc/X11
mv xorg.conf xorg.conf2
mv xorg.conf~ xorg.conf

then restart and you should be back to where you started
then login to gui
System>Administration>Synaptic Package Manager
i checked:
linux-restricted-modules-*
nvidia-glx
nvidia-kernel-common
nvidia-kernel-source
__________________________
that should give you what you need to get nvidia stuff working
then hit apply at the top and let it install
restart the system when you are done
that should be it.

I've also included my sources.list & my xorg.conf in case you wanted to see that as well

---

### Post by codejunkie on 2006-03-12
[QUOTE=Mutch]i have a GeForce FX 5700LE and i am attempting to install the nvidia drivers for my system. I have followed a couple of guides
[LIST]
[*][http://ubuntuforums.org/showthread.php?t=75074](http://ubuntuforums.org/showthread.php?t=75074)
[*][https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)
[/LIST]
both of which resulted in an error on reboot "Failed to start xserver" leaving me with a nice CLI.
i did a "sudo dpkg-reconfigure xserver-xorg" and changed my drivers back to vesa. But im no closer to getting the nvidia drivers installed. 
Any ideas how to get them installed? 
Do i even need to install them? (i want to run dual monitors and games).
:confused: 

Mutch

P.S. Im very new to linux but learning fast :)[/QUOTE]

before you install the nvidia driver from **[www.nvidia.com](www.nvidia.com)** you need to first remove the nvidia drivers provided by ubuntu, because they conflict with the official nvidia driver. do that by opening a terminal and copy and paste this in there.
```
sudo apt-get remove --purge nvidia*
```
now make sure you have install the required packages the nvidia installer needs to build the driver do that by copying and pasting this into a terminal.
```
sudo apt-get install build-essential linux-headers-`uname -r` gcc-3.4
``` now take the nvidia driver package you downloaded and place it in your home dir this just makes it easier to find when you go to install it.
now install the driver like this press ctrl+alt+F1 login now you need to stop the running xserver so run
```
sudo /etc/init.d/gdm stop
```
and 
```
sudo /etc/init.d/kdm stop
```
just incase kdm is running instead.
now login as root with```
sudo su
```
now you have to change your gcc version to work with nvidia installer so run
```
export CC=gcc-3.4
```**[COLOR="Navy"]linux is case sensitive so make sure the CC is capitalized and the rest is lower case[/COLOR]**, or the installer will fail on the gcc check.
now run the installer, type sh NVIDIA then hit the tab key and it will automaticly fill in the rest for you let it finish.
and the last thing you have to do is change the driver line in your /etc/X11/xorg.conf file do that by running
```
sudo nano /etc/X11/xorg.conf
```
scroll down to the "Device" section and change the driver to "nvidia" save the file by pressing ctrl+x and reboot.

---

### Post by Mutch on 2006-03-12
Well that kinda worked....
Instead of getting the error i was getting my monitor just turns off.
Progress?
Followed instructions word for word.
/me sighs
Thanks for the help tho :)
Is it because i have 2 monitors plugged in? or maybe its trying to run a stupid resolution? or something?

Mutch

---

### Post by codejunkie on 2006-03-12
[QUOTE=Mutch]Well that kinda worked....
Instead of getting the error i was getting my monitor just turns off.
Progress?
Followed instructions word for word.
/me sighs
Thanks for the help tho :)
Is it because i have 2 monitors plugged in? or maybe its trying to run a stupid resolution? or something?

Mutch[/QUOTE]
yes if your running dual monitors it can cause some strange things to happen, if you don't have your xorg.conf file setup to use dual monitors. try unplugging one monitor install the nvidia driver and get everything working correctly with the nvidia driver first, then if everything is working correctly with one monitor follow the howto on this board on how to configure a dual head/monitor setup and it should work fine using both monitors.

---

