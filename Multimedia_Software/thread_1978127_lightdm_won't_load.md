---
title: "lightdm won't load"
date: 2012-05-11
forum: Multimedia Software
---

### Post by jsfergus on 2012-05-11
Hi,

First time here on the forums. I've done my best to solve this problem but I'm at my wits end. I'll try to describe my problem succinctly.

My computer crashed while I was running the upgrade from 11 to 12 forcing a restart. After this several things were very broken:

system tools wouldn't open, trying to open a new tab in the Xwindow would break the window closing it and prompting an error report, update manager wouldn't open and would prompt an error report and there were some (relatively) minor graphical artifacts.

I tried to finish the upgrade using the xterm with apt-get update then apt-get upgrade and when I restarted after this I no longer had a GUI. It would hang on a black screen after listing several processes that are part of its boot sequence forcing me to use crtl+alt+F1 to log in with only a command line.

Because I'm on a residential network that requires users to log in on a web browser I no longer had internet connectivity on my Ubuntu partition at this point.

I went to Nvidia's site on my windows partition and downloaded the drivers they provide for my card (9800 GT). Installing these drivers I was informed I needed to disable nouveau to load the proprietary drivers.

Using sudo jockey-text -l I got the list of video drivers the system is aware of but all of them were listed as disabled and jockey-text was unable to enable them.

To remove nouveau I blacklisted nouveau in /etc/modprobe.d/blacklist.conf, backed up, ran sudo apt-get remove --purge nouveau, and updated the initramfs image

Actually I ended up having to blacklist nouveau and a few other things in another file; /etc/modprobe.d/blacklist-oss.conf for that to take. I might have that file name slightly wrong since I'm writing this from my windows partition.

After doing this the Nvidia proprietary package unpacked and updated everything (or at least gave me no errors now) but still nothing would work.

Additionally I still see nouveau listed when I use lsmod and I still get the same four options when I use jockey-text -l, none of which have started working.

To try to see if the Nvidia install took properly I checked for components that their page here:
[http://us.download.nvidia.com/XFree86/Linux-x86/295.49/README/installedcomponents.html](http://us.download.nvidia.com/XFree86/Linux-x86/295.49/README/installedcomponents.html)

claims should be installed. I found most of them, though in somewhat different places than the file paths their documentation said (I'll happily list details on this if anyone feels it's relevant, I'm trying to not write a novel here).

I'm sure this description of my problem is incomplete but I've tried suggestions from many sources to reach this point and I'm not sure what details would be of any help. I'll gladly do my best to provide any details that someone thinks might be relevant. I relatively new to Linux and I apologize if I've just made this more of a mess than I started with.

Thanks for any guidance.

---

### Post by kc1di on 2012-05-11
Sound like quite a challenge :) 

But here's one thing you did not do go to the terminal and use the following to upgrade the system to 12.04 

```
sudo apt-get update && sudo apt-get dist-upgrade
```
Try that first and see if it helps. 

If not we will go from there. 
(Note: I'm a big fan of fresh installs, just find too many problems with distro-upgrades.)

---

### Post by jsfergus on 2012-05-11
I'm sorry, I shoulda mentioned that. >.<

Those were the first things I tried in the hopes that it would figure out where the holes in my upgrade were and patch them up. Also now that I don't have a connection on my Ubuntu partition I can't really use apt-get anymore (except to remove things).

If it seems necessary that I have an internet connection I will try to talk the IT people into temporarily giving me a connection without making me log in (the system requires all terminals log in through a browser so without a GUI I'm a bit stuck).

Thanks again for any help!

---

### Post by BicyclerBoy on 2012-05-11
text based browser ? (don't need X server running)

w3m

you need to know the url of the internet gateway/server..
Use this to gain internet access & finish the upgrade..
This requires your internet server to have support for txt interface.

Have upgrade 2 PCs to 12.04..one (old intel netbook) had problems with X server not starting. This PC had existing xorg.conf file & it remains unchanged by the following.
Fixed with:
Xorg -configure
sudo service lightdm start

You can try:
sudo nvidia-xconfig
sudo service lightdm start

check the log files for X server & lightdm in /var/log/*

---

