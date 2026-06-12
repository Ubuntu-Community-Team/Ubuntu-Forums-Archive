---
title: "blank duel screens"
date: 2009-03-08
forum: Multimedia Software
---

### Post by rob_wizard on 2009-03-08
Hello. i posted a thread a few days ago regarding the use of two monitors on ubuntu and since then i have made some progress.. i have used the Nvidia drivers "Envyng" to achieve some success though now i am having some quite challenging problems.

My first problem is when i finally get my two monitors to work at the same time they sort of overlap in the middle.. nothing i does seems to affect this. Secondly everything turns a sort of off white color.. EVERYTHING. This is sometimes remedied by changing the res of the monitors but even then the background image is all squashed on one screen and the other says "video cannot be displayed on this monitor" in the middle of the screen?

i tried to revert back to my original one monitor setup and thought i had succeeded but many of the windows are as the background on the duel monitor setup, completely blank? also the minimize, maximize and close buttons are gone from my windows?

due to not being able to use terminal, detect hardware or anything else i cannot tell you what graphics card i am using other than it is an Nvidia one, my monitors are both dell and im using ubuntu 8.10

if anyone has experienced anything similar or has any advice i would be greatfull otherwise im gonna have to reinstall and just use one monitor.. i would like to run two though as i am so far enjoying every aspect of ubuntu and i think it is far better than windows.. i just wish i could run two monitors :)

Thanks

---

### Post by norwoods on 2009-03-08
i update to the latest nvidia proprietary releases, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager. i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev
for a fresh install, you might also want or need:
jockey-common
jockey-gtk or jockey-kde
nvidia-settings
nvidia-xconfig

open System--Administration--Hardware Drivers.
click on the NVIDIA 180 driver
click Activate.
clock Close.

reboot

get a command line by starting Applications--Accessories--Terminal
type gksu nvidia-settings
enter password
when the nvidia gui interface is running, click X Server Display Configuration
click Configure...  
click the TwinView radio button
click OK
set up anything you want
click Save to X Configuration File
click Quit.

---

