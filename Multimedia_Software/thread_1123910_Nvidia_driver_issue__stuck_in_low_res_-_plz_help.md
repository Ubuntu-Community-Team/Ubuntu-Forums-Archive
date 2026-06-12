---
title: "Nvidia driver issue / stuck in low res - plz help"
date: 2009-04-12
forum: Multimedia Software
---

### Post by thelastunavail on 2009-04-12
I recently got the newest nvidia driver for my pc directly from nvidias website. I got it to install correctly by doing the cntrl-alt-F1 then sudo gdm stop then install the driver package, and it installed ok. 

Except everytime i boot my pc, it goes to low res mode, 800x600 and has the generic video/screen resolution menu instead of the old one i used to have which allowed me to get high resolutions. I think previous i had the generic "new" ubuntu nvidia driver. When i goto System > preferences > Nvidia X server settings it says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." and I allready ran sudo nvidia-xconfig after the new drivers install .. still not working..wtf

Any help is appreciated, thanks!

---

### Post by thelastunavail on 2009-04-13
plz help?
any relevent info at all plz?

---

### Post by norwoods on 2009-04-14
what version of ubuntu?
what video card?
what version of nvidia driver?

---

### Post by andrea000 on 2009-04-14
your driver may not be the right one try envy website [here]("http://albertomilone.com/nvidia_scripts1.html")
i have used it on 8.04 and 8.10 works great its  in
synaptic if your running 8.10 i do not know about 8.04
i downloaded it and installed it.

Goodluck

---

### Post by thelastunavail on 2009-04-17
I am useing Ubuntu Hardy heron version. Im not exactly sure which version number that is since im a complete linux noob, recently switched from windows.

The video card is a geforce 6 series 256MB built into the motherboard

The driver i installed from nvidias site is "NVIDIA-Linux-x86-180.44-pkg1.run", i tryed to reinstall it but it was showing allready installed, but not being recongnized. 

post from earlier , explaining details

"I recently got the game Savage 2, which looked pretty cool. I played WoW before on this same pc, it is duo core / 2 gb ram / nvidia geforce 6 series video card. I have always used the generic nvidia "new" driver from ubuntus repositorys, but Savage 2 seems to be on a permenant lag, i turned the settings down and it was still pretty slow but helped a little bit.

So I went to nvidia's site and got the official driver, thinking it would give better performance. I had some problems installing but eventually got it by hitting control-alt-f, stopping gdm, then running a "sudo sh NVIDIA-thedriver-pkg.run" and installed it. I know is installed because i rebooted the pc (had a video problem it was stuck in 800x600 and did not recognize the new driver) then went back and tried to install the driver again but it said the new version nvidia driver i installed was current now, so i exited since it appears to be installed.

Now in system > preferences > nvidia x server settings, it gives me this message everytime i try and open it , it gives me the error "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. " - so i did what the screen told me several times allready and seen in the terminal where it says it created a new one, and backed up the old one, ect.. then rebooted the pc and still it started at some menu asking if i wanted to select my monitor and graphics card, ect.. so I did but did not see the graphics card driver i just installed .. then it booted to lowres 800x600..

So finally I got pissed off and said im done for tonight and this morning when i turned on the pc it booted to the correct screen resolution, but my compiz-cube is not working, Savage 2 wont even load because i dont think my pc has a video driver now, or is selecting one at boot or something and when i goto the screen resolution screen it does not look like how it used to before i tried to install the new nvidia driver (it has less options).. has anyone here had this problem?
Or does anyone know what to do to fix this? I would really appriciate some insight, thanks!! "

and Andrea000: beautiful and intelligent.. a rare thing now ;-) I've tried the envy version but it did not work, I've tried all of the nvidia drivers in ubuntus repository, but hear the ones directly from nvidia are the best. I beleive it only supports up to driver 1.79something (envy).. the driver for my card is i beleive 1.8something
maybe this is the error?

---

### Post by norwoods on 2009-04-17
i suggest you run the following to get rid of old installations:
sudo envy --uninstall-all 
sudo dpkg -P envy 
sudo apt-get remove --purge nvidia*
sudo rm /lib/restricted-modules/.nvidia*
sudo nvidia-installer --uninstall
i suggest you run the following to set things up:
sudo apt-get install build-essential linux-headers-`uname -r`
i suggest you install from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by VotaVader on 2009-04-17
> **norwoods said:**
> i suggest you run the following to get rid of old installations:
sudo envy --uninstall-all 
sudo dpkg -P envy 
sudo apt-get remove --purge nvidia*
sudo rm /lib/restricted-modules/.nvidia*
sudo nvidia-installer --uninstall
i suggest you run the following to set things up:
sudo apt-get install build-essential linux-headers-`uname -r`
i suggest you install from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

Of the packages mentioned above, you should only need the nvidia-180-kernel-source, the nvidia-glx-180, and the nvidia-settings (which isn't mentioned). Anyway, if you still have problems doing the above, take a look at this thread [http://ubuntuforums.org/showthread.php?t=1120326](http://ubuntuforums.org/showthread.php?t=1120326)
I had a similar problem a few days back, so if you get the same error messages, it should help. Cheers!

---

### Post by dinub1 on 2009-04-20
> **andrea000 said:**
> your driver may not be the right one try envy website [here]("http://albertomilone.com/nvidia_scripts1.html")
i have used it on 8.04 and 8.10 works great its  in
synaptic if your running 8.10 i do not know about 8.04
i downloaded it and installed it.

Goodluck

Hi Andrea,

This should generally be fine. I have the same issue as the initiator. With nVidia graphics card, the Ubuntu 8.10 either GDM or KDE suddenly, out of the blue (it ran OK earlier) runs in 800 x 600 low resolution mode. No way to make it detect higher.
$ sudo dpkg-reconfigure xserver-xorg
command used to work in the past, it does not work anymore... that is, it is unable to reconfigure the graphics (it did before). Upgrading to 9.04 beta did not solve the problem.
FYI, it used to be that no special nVidia driver needs to be installed. But with Ubuntu version 8.xx and above this is happening more and more.
Mint ver 4 does not have this issue. It runs at 1680 x 1050 my screen native resolution without problems. And without the nVidia restricted driver. Why not Ubuntu?
The following is not intended to be an offense, however what I noticed is that with each newer version of Ubuntu being released, OS becomes more buggy and less efficient. Do the folks at Canonical intend to copy MS ways :) ?
Thanks for your input.

---

### Post by dinub1 on 2009-04-22
> **VotaVader said:**
> Of the packages mentioned above, you should only need the nvidia-180-kernel-source, the nvidia-glx-180, and the nvidia-settings (which isn't mentioned). Anyway, if you still have problems doing the above, take a look at this thread [http://ubuntuforums.org/showthread.php?t=1120326](http://ubuntuforums.org/showthread.php?t=1120326)
I had a similar problem a few days back, so if you get the same error messages, it should help. Cheers!

My (past) Ubuntu 8.10 OS did not have nVidia drivers activated while I am using an nVidia graphics card. I updated to ver 9.04 beta, same thing... runs in 800 x 600 mode with a Viewsonic 1680 x 1050 LCD display. Mint Darina ver 4 does not suffer from this problem (on the same machine, different partition and with same harware configuration).
I copied the xorg.conf file from the Mint's /etc/X11/ folder into the corresponding Ubuntu's folder and rebooted.
It seems that OS auto configures and overwrites the existing xorg. conf file, by wiping out the video settings, while using the same hardware :) Resolution then remains low (800x600).
I tried to implement suggested commands from another poster, it says envy not installed. Anyway... I guess a clean install of ver 9.04 will solve the issue. I am waiting for the released ediiton of 9.04.

---

