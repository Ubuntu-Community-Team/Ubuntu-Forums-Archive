---
title: "Can not activate nvidia-driver (whatever version)?"
date: 2009-03-05
forum: Multimedia Software
---

### Post by ngduonglam on 2009-03-05
Dear all,

I'm getting problem while upgrading to ubuntu 8.10.

In my 8.0.4, the nvidia driver is ok, 173 version I think. And the combiz worked as well as its effects.

Then I decided to upgrade to 8.10, and installed the latest driver (177, right?), then tried to active it. After restarted, ubuntu said that not correct driver installed and config, need to back to the default config with no nvidia driver installed, and of course, can not get the combiz effects :(

Did any of you face this problem? Please help me. Thanks.

Hardware information:
Laptop Lenovo 3000 N200 with NVIDIA card 7300Go
Dual OS: Vista Ultimate and Ubuntu
CPU: Dual 2.2 with 3GB RAM.

---

### Post by kestrel1 on 2009-03-05
Have you activated the prorietary drivers in System -> Administration -> Hardware Drivers?

---

### Post by ngduonglam on 2009-03-05
> **kestrel1 said:**
> Have you activated the prorietary drivers in System -> Administration -> Hardware Drivers?
Yes, I did. Go to System -> Administration -> Hardware Drivers, then select the recommended driver (v.177, right?), and click Active, and restart. But after that, when ubuntu start GDM, it notified that wrong xconfig, and ask me to use default xconfig, or create a new xconfig, or use the backup config. I tried all options, but just only the default xconfig work. And then go to Hardware Drivers again, no driver was actived :).

---

### Post by kestrel1 on 2009-03-06
Do you have the 173 drivers available? & have you tried using it?

---

### Post by ngduonglam on 2009-03-12
> **kestrel1 said:**
> Do you have the 173 drivers available? & have you tried using it?
Yes, I did all avaiable version of NVIDIA driver (96, 173, 177, and 180-beta), but still get the same problem :(

---

### Post by norwoods on 2009-03-13
i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
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

---

### Post by ngduonglam on 2009-03-13
> **norwoods said:**
> i update to the latest nvidia proprietary releases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.37 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using synaptic package manager.  i am not sure which programs are needed so i install all six provided:
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
still not work :(

---

### Post by norwoods on 2009-03-13
> **ngduonglam said:**
> still not work :(

at what point in the install sequence do you decide it does not work?

---

### Post by a2z on 2009-03-17
I also have a nvidia driver problem. System> Admin> Hardware drivers. 
I have never been able to activate either driver. It seems to stall. 
I hoped to get it to install eventually after updating. But now my updater is stalling also. The both start downloading with gui but it is usually shaded, and stuck on 0% 
Can anyone help with these processes hanging?
Thanks

---

### Post by ngduonglam on 2009-03-30
> **norwoods said:**
> at what point in the install sequence do you decide it does not work?
The installation was successful, but after restart to complete the installation, then error happened.

---

### Post by peepingtom on 2009-03-30
I've run into an issue where the activation stalls, it's always been solved by either installing the drivers through apt-get (synaptic) or running 'sudo jockey-gtk' in terminal to run to run the hardware driver manager (jockey) as root.

---

### Post by norwoods on 2009-03-30
i would try to delete all of the nvidia video drivers to get rid of any old files and then reinstall 180.
i would rename /etc/X11/xorg.conf  and generate a new /etc/X11/xorg.conf by running sudo nvidia-xconfig

---

### Post by Neobuntu on 2009-05-28
Apparently there is a distinct LACK of the dialog to simply tell newbies, they have to install the nvidia driver and the correctly numbered one.

Mine, for example, noted correctly the "96" driver. 

Therefore, I went to the add/remove programs (Where you can't click OK or it will close!) and typed in nvidia. 

Then you have to KNOW that Nvidia-glx-96...., for example will load everything you need along with it. You have to click the confusing plus/minus thing (something that you'd think would be hard to make confusing) and click "Apply" (after rebooting perhaps).

Sorry newbies(MOST important new users that we'd like to NOT "peave"-off). I hope that helps.

---

### Post by jimp180 on 2009-05-31
well I am having this same problem, somehow I have managed to overcome it and get the driver working on a couple of occasions but then after its working if I reboot the computer I am back to the same crap. "running in low graphics mode-bla bla bla" if I remove the proprietary drivers and reinstall them I can get it working again but then at next reboot it's fubared once more.

---

### Post by Neobuntu on 2009-06-03
Try running nvidia-settings (As root, I think) and setting your screen resolution that way. Then you have to save it in there AND it has to not give error messages.

---

