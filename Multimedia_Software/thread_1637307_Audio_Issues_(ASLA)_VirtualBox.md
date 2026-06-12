---
title: "Audio Issues (ASLA) VirtualBox"
date: 2010-12-04
forum: Multimedia Software
---

### Post by Toxcity on 2010-12-04
Afternoon guys, 

I am having audio issues in my host operating system (Ubuntu 10.10 64bit) when running my Virtual machine (Windows Server 2008 R2) through VirtualBox. 

At the moment I need the virtual machine to run all the time my issue comes when trying to play a movie on the host OS, video is fine but audio is choppy to the point of not understanding what is being said. 

I used gstreamer to test the audio outputs while the VM was running, ALSA is choppy but Pulseaudio is clear. I then change VLC to pulseaudio and I get no output what so ever. :(

The VM does not need sound so I have it disabled in VirtualBox's settings (I have tried enabled, same issue). 

Any ideas?

---

### Post by gradinaruvasile on 2010-12-04
Make sure the vm does not hog the cpu (it happens even if there is no activity in the virtual machine to use 50-100% cpu). This might cause problems for pulseaudio if you have only 1 core (Edit: you probably have 2 if the machine you use its the one from your sig).
Because of this is not practical to have one running al the time in background in a desktop machine (maybe if you have a cpu core to spare...).

And check if you have vlc-plugin-pulse package installed. Vlc does not use gstreamer, it has its own pulse plugin (as do many of the apps, so gstreamer is not good for general sound debugging).

PS: try running the vm headless (VBoxHeadless -s vmname), it might use less resources. Connect to it with rdesktop if needed.

---

### Post by Toxcity on 2010-12-04
The Pulse VLC plugin is installed and resources doesn't seem to be much of an issue, using about 60% RAM and 10-20% CPU and as you said I have two cores. 

I have a feeling ALSA has issues when a VM is running. But it's weird that Pulseaudio doesn't work with VLC at all. :( 

I'll have a look into Headless. ;)

Cheers

---

