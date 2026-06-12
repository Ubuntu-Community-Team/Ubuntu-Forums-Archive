---
title: "NVIDIA driver issue. Cannot log on to X"
date: 2012-09-30
forum: Multimedia Software
---

### Post by StepNjump on 2012-09-30
Hi,

I have a big problem. 
Up to recently, there were some components that wouldn't successfully complete when system would attempt to update. Somebody told me that those NVIDIA components were no longer available from the server.

Yesterday, I unchecked those two and the Ubuntu update successfully completed.

After this, I found out that nautilus was no longer working. So I checked on a board and attempted to remove all the drivers related to NVIDIA by dpkg -l NVIDIA* & dpkg -P ...

However, with my typical luck, after I rebooted, I received the following message after trying to log on to X:

XBMC needs hardware accelerated OpenGL rendering. 
Install an appropriate graphics driver.

Please consult XBMC Wiki for supported hardware
[http://wiki.xbmc.org/?title=Supported_hardware](http://wiki.xbmc.org/?title=Supported_hardware)

What I tried:
1- sudo apt-get update (successfully completed)
2- sudo apt-get upgrade 
Reading state information... Done
0 upgraded, 0 newly installed, 0 to reove and 0 not upgraded
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
do you want to continue Y or N
Setting up nvidia-current (304.51-0ubuntu1~natty~xup1) ...
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 2
 nvidia-current
E: Sub-process /usr/bin/dpkg returned an error code (1)

3- ..:/home$ sudo apt-get distro-upgrade (error)
E: Invalid operation distro-upgrade


I have no problem returning back to an ATI card if it would be easier but I have no idea how to install the ATI drivers and ensure that whatever is left of my NVIDIA drivers will not be in conflict.

If one of you could help me with this, I would appreciate a lot!!!

Thanks for all your help in advance.


StepNjump

---

### Post by BicyclerBoy on 2012-09-30
Are you running XBMCbuntu ?
I think this is 11.10 (natty) based.

11.10 is out of support because or age & it is not an LTS distro.

Why would you remove the graphics drivers because the file manager is not right?

You probably removed packages that are now not available from the server.
Try to find an nVidia driver with a different version name..(not current)

apt-get -s install nvidia*
(-s is simulated install)
If there are none you may have to find another ppa that still has natty packages.

You might be better to upgrade to 12.04 LTS (& stay there).
apt-get dist-upgrade

Warning you could end up with a working buntu box but with a dead XBMC..

---

### Post by StepNjump on 2012-09-30
Hi BicyclerBoy, you are very nice to get back at me...
I'm not a very proficient user... I was thinking of upgrading to the LTS version but the last time I did this, I ended up with a broken system so I didn't even try. As a last resort, I will have to do it but before, I thought maybe I could try other avenues.
As usual, I don't have a backup and I have an expensive software installed on my system and unfortunately lost the install CD thus the reason why I am trying to fix the system instead of reinstalling everything like I would normally do.

No i don't think I am running XBMCbuntu. What happened is that when nautilus refused to load due to missing NVIDIA components yesterday, I installed thunar and another file manager as a work around. Maybe that's why it's asking me that?

Would it be just as simple as deinstalling thunar and the other file manager?

Thanks for being there.

StepNjump, Pete.



> **BicyclerBoy said:**
> Are you running XBMCbuntu ?
I think this is 11.10 (natty) based.

11.10 is out of support because or age & it is not an LTS distro.

Why would you remove the graphics drivers because the file manager is not right?

You probably removed packages that are now not available from the server.
Try to find an nVidia driver with a different version name..(not current)

apt-get -s install nvidia*
(-s is simulated install)
If there are none you may have to find another ppa that still has natty packages.

You might be better to upgrade to 12.04 LTS (& stay there).
apt-get dist-upgrade

Warning you could end up with a working buntu box but with a dead XBMC..

---

### Post by StepNjump on 2012-09-30
attempted to remove thunar. It still gives me an error when processing nvidia-current (--configure)
errors were encoutered while processing: nvidia-current

---

### Post by BicyclerBoy on 2012-09-30
Try to find an nvidia driver in jockey (GUI tool additional drivers) or using:
apt-get- is install nvidia*

failing both those try to install the open source nouveau driver.

---

### Post by StepNjump on 2012-09-30
oh and I remember, I think I might have attempted to desinstall nautillus and replaced it with Dolphin and Thunar... Would that be the reason why?

---

### Post by StepNjump on 2012-09-30
I did a dpkg -l nautilus and it's in ii status

---

### Post by StepNjump on 2012-09-30
I guess it was a typo apt-get- is install nvidia* but I tried apt-get install nvidia* and looks like we MIGHT getting closer bicyclerboy...

Now I get

Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
nvidia-180-modaliases: ...
nvidia-common: ...
nvidia-current: ...
E: Broken packages

---

### Post by StepNjump on 2012-09-30
Maybe this is good news... I desinstalled xbmc. I thought it was an important driver but found out it was nothing important.
It looks like the system is reinstalling what it needs... 
For now, I have a black screen.. I'm waiting to see what will happen.

---

### Post by BicyclerBoy on 2012-10-02
apt-get -s install package_name
- the -s option is simulation only..

XBMC is a media player..

apt-cache depends nvidia-common
apt-cache depends xbmc

From a ubuntu 12.04 perpective:
these cmds show both have python &/or (2.7) dependencies.

Removing nautilus breaks gnome-session (X session manager).

You might be able to re-install xbmc after the nvidia-common package..

sudo apt-get install nvidia-common nvidia-settings

Worry about xbmc after..

---

