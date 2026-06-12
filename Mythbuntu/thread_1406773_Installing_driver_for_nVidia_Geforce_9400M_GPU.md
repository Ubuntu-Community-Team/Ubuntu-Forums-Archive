---
title: "Installing driver for nVidia Geforce 9400M GPU?"
date: 2010-02-14
forum: Mythbuntu
---

### Post by hhtmp88 on 2010-02-14
Dear all,

According to:
[http://tw.download.nvidia.com/XFree86/Linux-x86/190.53/README/index.html](http://tw.download.nvidia.com/XFree86/Linux-x86/190.53/README/index.html)

Before I start to install the driver, "NVIDIA-Linux-x86-190.53-pkg1.run"  for nVidia Geforce 9400M GPU, 
(i)  I need to exit the X server and terminate all OpenGL applications 
(ii) set the default run level on my system such that it will boot to a VGA console, and not directly to X. Doing so will make it easier to recover if there is a problem during the installation process. 

-> so how to do (i) & (ii)?

Thanks for any kind of help!
Rgds,

---

### Post by nickrout on 2010-02-14
NoNoNo do not download the driver from nvidia. Use the one in the repositories.

---

### Post by hhtmp88 on 2010-02-14
Thanks nickrout for your comment!

the driver in the repositories is "nVidia accelerated graphics driver " (as detected by MythTV)
-> installed but only VGA output has signal, 
-> and max. resolution is 1024x768, video is not in proper aspect ratio and lengthened
-> while HDMI output does not has any signal!

so what next?
-> where to download the correct driver for nVidia Geforce 9400M GPU so that I can have HDMI output and play 1080p Full HD movies ?

Rgds,

---

### Post by nickrout on 2010-02-14
So is the driver actually operating? What does /var/log/Xorg.0.log tell you?

you might also want to look at nvidia-settings

---

### Post by hhtmp88 on 2010-02-15
Thanks nickrout for your instructions!

but... I've got no ideas about what they are really talking about.

However, I have attached them and hope that you know what they means and find some clues for the solution
-> /var/log/Xorg.0.log
-> and some screen captures of "nvidia-settings"

Thanks for any kind of help!
Rgds

---

### Post by Cirion75 on 2010-02-15
For the 9400M GPU you need a newer driver than the 185 that is included in the repositories.

Open a terminal and paste this:
```
sudo add-apt-repository ppa:nvidia-vdpau/ppa &&
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767 &&
sudo apt-get update && sudo apt-get install nvidia-glx-195 &&
sudo nvidia-xconfig && sudo reboot
```

---

### Post by hhtmp88 on 2010-02-15
Thanks Cirion75 for your quick advice, but...no luck! 
-> installation cannot be finished due to an error, pls. see attached file "error02.txt" for details


Actually, I am using Giada N10 (Atom N330 + nVidia ION chipset):
================================
[FONT=Arial]Processor[/FONT]: [FONT=Arial]Intel® dual-core ATOM™ N330 1.6GHz[/FONT]
                                                         [FONT=Arial]GPU: [/FONT][FONT=Arial]nVidia® Ion™, Support 1080P movie[/FONT] 
                                                         [FONT=Arial]Memory[/FONT]: [FONT=Arial]2GBDDR2 RAM (Max. 4GB)[/FONT]

[http://giada.cc/chanpinzhongxin/minipc/slim%20series/2009-10-30/1.html](http://giada.cc/chanpinzhongxin/minipc/slim%20series/2009-10-30/1.html)

================================
-> on the packaging of Giada, it states that chipset is nVidia ION and GPU is nVidia Geforce 9400M
-> so do we need to install driver for the nVidia ION chipset too?

Rgds,

---

### Post by nickrout on 2010-02-15
> **hhtmp88 said:**
> Thanks nickrout for your instructions!

but... I've got no ideas about what they are really talking about.

However, I have attached them and hope that you know what they means and find some clues for the solution
-> /var/log/Xorg.0.log
-> and some screen captures of "nvidia-settings"

Thanks for any kind of help!
Rgds

See where the nvidia-settings gui says the TV screen is disabled? Try clicking on it and enabling it!

---

### Post by hhtmp88 on 2010-02-16
Thanks nickrout for your further instructions, tried activating nVidia-version195 driver, but... still no luck!
-> SystemError: installArchives() failed
-> pls. see attached screen capture


Rgds,

---

### Post by hhtmp88 on 2010-02-17
I would like to give more detailed on what I have tried (according to your instructions, Nickout & Cirion75):

1. Installation of Mythbuntu: "mythbuntu-9.10-desktop-i386.iso"
2. do updates
3. do sudo on a terminal window:
=====================
sudo add-apt-repository ppa:nvidia-vdpau/ppa &&
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767 &&
sudo apt-get update && sudo apt-get install nvidia-glx-195 &&
sudo nvidia-xconfig && sudo reboot
=====================
   -> and get an return error as stated in " 	[Error02.txt]("http://ubuntuforums.org/attachment.php?attachmentid=147136&d=1266253597") "

4. reboot the machine
5. try to activate nVidia driver in "Applications -> System -> Hardware Drivers" menu
  -- tried activate v195 -> failed
  -- then v190              -> still failed
  -- then v185              -> [SIZE=4]**[COLOR=Red]FAILED[/COLOR]**[/SIZE]    **[COLOR=DarkRed]<--- strange as it can be activated before & can make screen of resolution 1024x768![/COLOR]**

so, are there something wrong in the sudo commands ??

Rgds,

---

### Post by nickrout on 2010-02-17
> **hhtmp88 said:**
> I would like to give more detailed on what I have tried (according to your instructions, Nickout & Cirion75):

1. Installation of Mythbuntu: "mythbuntu-9.10-desktop-i386.iso"
2. do updates
3. do sudo on a terminal window:
=====================
sudo add-apt-repository ppa:nvidia-vdpau/ppa &&
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys CEC06767 &&
sudo apt-get update && sudo apt-get install nvidia-glx-195 &&
sudo nvidia-xconfig && sudo reboot
=====================
   -> and get an return error as stated in " 	[Error02.txt]("http://ubuntuforums.org/attachment.php?attachmentid=147136&d=1266253597") "

4. reboot the machine
5. try to activate nVidia driver in "Applications -> System -> Hardware Drivers" menu
  -- tried activate v195 -> failed
  -- then v190              -> still failed
  -- then v185              -> [SIZE=4]**[COLOR=Red]FAILED[/COLOR]**[/SIZE]    **[COLOR=DarkRed]<--- strange as it can be activated before & can make screen of resolution 1024x768![/COLOR]**

so, are there something wrong in the sudo commands ??

Rgds,

*sigh* you are using the 185 drivers so thats a good start.

Have you tried activating the other display?

---

### Post by underdarkonsole on 2010-02-17
use **system > adminstrator > hardware drivers**

and install it ( Note: full internet access )

visite this page for detail :
[http://underdarkonsole.blogspot.com/2010/02/install-nvidia-on-ubuntu-910-karmic.html](http://underdarkonsole.blogspot.com/2010/02/install-nvidia-on-ubuntu-910-karmic.html)

---

### Post by hhtmp88 on 2010-02-17
Thanks all!

but... I am looking for 1920x1080 full HD, 
so are there someone to working on the functional v195 nVidia driver?


-> in addition, there should also been an audio driver for the nVidia ION chipset (or nVidia Geforce 9400M chipset?)
-> the sound output now is very small and I have to increase the volume, but then very noisy! any operations on the machine sound some annoying noise!


Rgds,

---

### Post by nickrout on 2010-02-17
> **hhtmp88 said:**
> Thanks all!

but... I am looking for 1920x1080 full HD, 
so are there someone to working on the functional v195 nVidia driver?




For heaven's sake how many times do I have to say it. Leave the 185 driver installed for the moment.

Then as I said before activate the TV screen. In your picture 03_xserver_displayconfig.png there are two screens shown, CRT-0 and QHD_QHTF42. Click on QHD_QHTF42 and then activate it.

If that doesn't work try unplugging the CRT and run it JUST with the TV.

---

### Post by hhtmp88 on 2010-02-18
> **nickrout said:**
> For heaven's sake how many times do I have to say it. Leave the 185 driver installed for the moment.

Then as I said before activate the TV screen. In your picture 03_xserver_displayconfig.png there are two screens shown, CRT-0 and QHD_QHTF42. Click on QHD_QHTF42 and then activate it.

If that doesn't work try unplugging the CRT and run it JUST with the TV.

Thanks Nickrout for your instructions!

It seems that I am going on the right track now!

There are two options when I click on "configure"
1. I tried the "TwinView" option, it does NOT works and only a blinking screen on the HDMI output

2. then I try "[COLOR=DarkRed]**[SIZE=2]separate x-screen (requires x-start)[/SIZE]**[/COLOR]" option, 
-> it requires me to save the configuration to **[COLOR=DarkGreen]/etc/x11/xorg.conf[/COLOR]** before anything can go further, I failed to do so -- access denied!
-> so how to set the access right and get the configuration be saved?
-> and how to do "x-start"?


Rgds,

---

### Post by nickrout on 2010-02-18
If you want it to change the xorg settings then run it from the command line like:

```
gksudo nvidia-settings
```

---

### Post by hhtmp88 on 2010-02-18
Thanks Nickrout!

but... I don't know what to change...
-> so how to grand the program the access right to write to the configuration file?

Rgds,

---

### Post by nickrout on 2010-02-19
are you saying ```
gksudo nvidia-settings
``` does not work?

try ```
sudo nvidia-settings
```

---

### Post by hhtmp88 on 2010-02-20
> **nickrout said:**
> are you saying ```
gksudo nvidia-settings
``` does not work?

try ```
sudo nvidia-settings
```

I can change the settings but the new configuration cannot be saved, 
-> pls. see attached screen shot "[Error_sudo_nvidia-settings_02.png]("http://ubuntuforums.org/attachment.php?attachmentid=147722&stc=1&d=1266722793")"
-> and there are some error message displayed on the terminal screen, see "	[Error_sudo_nvidia-settings_01.png]("http://ubuntuforums.org/attachment.php?attachmentid=147723&stc=1&d=1266722793")"
-> I included the configuration file "xorg.conf" for your reference

I wonder how to grand the access right to write to the configuration file?
-> or if this is not possible, what exactly should we do change to the configuration file
so that I can change it manually?

Rgds,

---

### Post by nickrout on 2010-02-21
try ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nvidia-xconfig
sudo nvidia-settings
```

---

