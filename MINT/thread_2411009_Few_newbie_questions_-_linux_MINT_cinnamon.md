---
title: "Few newbie questions - linux MINT cinnamon"
date: 2019-01-23
forum: MINT
---

### Post by eternafali on 2019-01-23
Hi there, so lets check this linux mint (cinnamon).

First thing I need to install nvidia drivers to adjust hue/saturation etc. - but when I run software menager and type nvidia - there is a LOT of stuff here - how should I know what to install - I need latest working drivers only (quadro M3000)!

Why does RESTART, >TURN OFF< my computer?!

What to do with this VLC player (everybody recommended it) - "pk-gstreamer-install requires to install plugins to play files of the following types:
- MPEG-4 ACC decoder
- H.264 (High Profile) decoder

and

"The playback of this movie requires a MPEG-4 decoder plugin which is not installed."

What to do, what to do!?


I need to get windows counterparts of HyperSnap, 4k downloader (to fast download videos and for annoying youtube commercials), winamp at start. Let me know what soft I can download to get similar usability.

And last but not least I have 2 HDD - one with windows 7 whole encoded with truecrypt (7.1a) and second HDD with linux. When I boot from linux HDD there is nice boot manager (I guess this boot manager is called GRUB?) - to chose what system I want to run. I would like it be use all the time so change in BIOS that llinux HDD should be started as a primary, but then when I choose windows 7 to start, the truecrypt manager is not run - how to fix this?

---

### Post by slickymaster on 2019-01-23
Thread moved to **MINT** for a better fit

---

### Post by oldfred on 2019-01-23
This is an Ubuntu forum. 
You may do better for Mint specific issues to check the Mint forum.

Assume Mint has synaptic which I prefer as it gives more details and exact file name of software.But not fancy gui, but basic gui.
And if you know exact name, you can then install from command line.
sudo apt install synaptic
Then start synaptic and search for vlc or plugins.
I see mp4 and libmp4v2 library  files in Ubuntu, again Mint may be different.

NVidia has a series of video drivers. Older cards need older driver as newer driver has features not supported by old card.
Older drivers may get some update for security but otherwise do not change.

       Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 
            # make sure system is up to date
sudo apt-get update
sudo apt-get upgrade 
            # should show versions available  - this may be an Ubuntu only command, do not know Mint equivalent
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX  

    
If nVidia suggested driver is newer than available in repository, you can add a ppa. It works for Ubuntu, again do not know about Mint.
 # should show newest versions available in addition
      
 sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
    
More info on ppa
      
 [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) 
           
 Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html) 
    
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX

---

### Post by eternafali on 2019-01-23
@[**[COLOR=#990303][B]slickymaster**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1753126")      [IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG], sure thing.

@[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711") 	 [IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG], thanks I try that.

---

