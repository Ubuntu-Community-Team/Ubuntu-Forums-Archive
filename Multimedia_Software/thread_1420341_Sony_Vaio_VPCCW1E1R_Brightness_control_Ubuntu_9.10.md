---
title: "Sony Vaio VPCCW1E1R Brightness control Ubuntu 9.10"
date: 2010-03-02
forum: Multimedia Software
---

### Post by Anton9121 on 2010-03-02
Hi! I Install Ubuntu 9.10 and I can't control Brightness, show brightness popup (Fn+F5\F6) but screen brightness don't work, I install NVIDIA Driver Linux-x86_64 version 190.53, modiffed xorg.conf. Please help!

---

### Post by speedygeo on 2010-03-03
Here the same with Linux Mint KDE 64 (based on kubuntu karmic 64bit) and NVIDIA x86_64 190.53 and xorg modified.

---

### Post by devottam on 2010-03-03
Having same problem ..:-(
posted the problem long ago ...nobody replied...
hope something comes up

---

### Post by angelsneverdie on 2010-03-23
i'm having same problem on vaio y series.  would really love a fix!

---

### Post by speedygeo on 2010-03-24
There are two italian threeds on this problem.

[Here]("http://forum.ubuntu-it.org/index.php/topic,357938.0.html") and [here]("http://forum.ubuntu-it.org/index.php/topic,352449.0.html").

Sorry, but now I don't have the time to translate.:(

---

### Post by Anton9121 on 2010-03-25
All files attached!
0. Adding in Device section of Xorg.conf file:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```My Device section:
```
Section "Device"
        Identifier     "Device0"
        VendorName     "NVIDIA Corporation"
        Option         "ConnectedMonitor" "DFP-0"
        Option         "CustomEDID"       "DFP-0:/etc/X11/sony-edid.bin"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```1. Install dkms. f.e. in Ubuntu run 
```
sudo apt-get update && sudo apt-get install dkms 
```2. Run the following command in the folder you've saved it.
```
sudo dkms ldtarball --archive=/home/xx/nvidia_bl-0.52.tar.gz 
```3. Go to [http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/README/appendix-a.html) and find your card and note the Device PCI ID f.e. GeForce GT 210M has Device PCI ID "0x0A74"

4. ```
sudo cp /home/xx/nvidia_bl.c /usr/src/nvidia_bl-0.52/nvidia_bl.c
```Edit as root the file "/usr/src/nvidia_bl-0.52/nvidia_bl.c" and in the section "static DEFINE_PCI_DEVICE_TABLE(nvidia_bl_device_table)" add the corresponding line for your card f.e. for GeForce GT 210M the following line has to be added.

Example:
```
/* NVIDIA Geforce 230M */
    { PCI_VDEVICE(NVIDIA, 0x0A2A), (kernel_ulong_t)&nv5x_driver_data },
```5. ```
sudo dkms remove -m nvidia_bl -v 0.52 --all
```6. ```
sudo dkms add build install -m nvidia_bl -v 0.52 
```7. ```
sudo modprobe nvidia_bl 
```8. Edit as root the file "/etc/modules" and add the line "nvidia_bl" so that the module is loaded every time you boot.

Active Fn+F5; Fn+F6 :
```
sudo su
cp /home/xx/acpi/events/sony-brightness-down /etc/acpi/events/
cp /home/xx/acpi/events/sony-brightness-up /etc/acpi/events/
cp /home/xx/acpi/sony-brn-down /etc/acpi/
cp /home/xx/acpi/sony-brn-up /etc/acpi/
cp /home/xx/acpi/chbrn /etc/acpi/
```9. Reboot!

---

### Post by Niej on 2010-05-11
Hi, I'm having the same problem on a brand new Sony Vaio VCPF1 with a nvidia
310M (218GT). No Fn keys working, ubuntu lucid detects the keys but there
is no brightness change.
Is there a way to revert the changes in case the steps in
this post doesn't work?
I recovered brightness control adding a line to xorg.conf and using brightness applet, after some weird
illumination effects, now it works fine.
(great tip!)
Otherwise the nvidia driver will set it to 100%.
Thanks in advance and great post.
Seba

---

### Post by donpoon on 2010-05-24
> **Anton9121 said:**
> All files attached!
0. Adding in Device section of Xorg.conf file:
```
Option "RegistryDwords" "EnableBrightnessControl=1"
```My Device section:
```
Section "Device"
        Identifier     "Device0"
        VendorName     "NVIDIA Corporation"
        Option         "ConnectedMonitor" "DFP-0"
        Option         "CustomEDID"       "DFP-0:/etc/X11/sony-edid.bin"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```1. Install dkms. f.e. in Ubuntu run 
```
sudo apt-get update && sudo apt-get install dkms 
```2. Run the following command in the folder you've saved it.
```
sudo dkms ldtarball --archive=/home/xx/nvidia_bl-0.52.tar.gz 
```3. Go to [http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/190.53/README/appendix-a.html) and find your card and note the Device PCI ID f.e. GeForce GT 210M has Device PCI ID "0x0A74"

4. ```
sudo cp /home/xx/nvidia_bl.c /usr/src/nvidia_bl-0.52/nvidia_bl.c
```Edit as root the file "/usr/src/nvidia_bl-0.52/nvidia_bl.c" and in the section "static DEFINE_PCI_DEVICE_TABLE(nvidia_bl_device_table)" add the corresponding line for your card f.e. for GeForce GT 210M the following line has to be added.

Example:
```
/* NVIDIA Geforce 230M */
    { PCI_VDEVICE(NVIDIA, 0x0A2A), (kernel_ulong_t)&nv5x_driver_data },
```5. ```
sudo dkms remove -m nvidia_bl -v 0.52 --all
```6. ```
sudo dkms add build install -m nvidia_bl -v 0.52 
```7. ```
sudo modprobe nvidia_bl 
```8. Edit as root the file "/etc/modules" and add the line "nvidia_bl" so that the module is loaded every time you boot.

Active Fn+F5; Fn+F6 :
```
sudo su
cp /home/xx/acpi/events/sony-brightness-down /etc/acpi/events/
cp /home/xx/acpi/events/sony-brightness-up /etc/acpi/events/
cp /home/xx/acpi/sony-brn-down /etc/acpi/
cp /home/xx/acpi/sony-brn-up /etc/acpi/
cp /home/xx/acpi/chbrn /etc/acpi/
```9. Reboot!

Thanks Anton9121!
Works for me.  vaio cw GT230M.

---

### Post by vchibikov on 2010-05-25
Thanks a lot Anton9121!
It works, but I've got a problem. My screen does not increase the brightness more than about 40%. When brightness indicator shows 50% my screen put in black. Please help

---

### Post by simar.mohar on 2010-05-31
I have a sony VPC CW 16FG face similar problem that brightness applet appearsand moves but cannot control it actually  ....

---

### Post by simar.mohar on 2010-05-31
Worked for VPCCW16FG ...
VPCCW16FG brightness issue solved .... ubuntu brightness issue solved for VPC CW 16FG and VPC CW series ...

---

### Post by nuovodna on 2010-06-01
it works but i cannot set the maximum brightness value. Is there a way to fix it?? Perhaps increasing maximum level up to 127..


PS After a kernel upgrade i have to recompile the module using this command ??
> sudo dkms add build install -m nvidia_bl -v 0.52
And after a nvidia driver upgrade?

---

### Post by ookami on 2010-06-09
Thank you Anton9121 for an excellent guide, worked perfectly for me on my Sony Vaio CW with a Nvidia GT230M running 10.04 Lucid Lynx.

I did however modify the sony-brn-down/up scripts that was included in your package a bit for the following reasons:
- There's a small error in the sony-brn-down where it does a "less or equal" test instead of "greater or equal". It's caught by the else-clause instead though so it's not really noticeable.
- The scripts only define seven brightness levels but, at least in Lucid, the gnome brightness control has eight levels, so I added one.
- There was a huge gap in the middle of the brightness levels so I evened it out a bit. Max brightness is 127 and min is 0, the original scripts are set to: 
[127, 100, 80, 60, 10,  3, 0] (seven levels) 
I set mine to:
[127,  90, 70, 50, 30, 10, 3, 0] (eight levels).
It's very easy to change them to whatever you want.

In case anyone wants to try the modified scripts I'll attach them to this post.

Cheers!

---

### Post by Anton9121 on 2010-06-14
> **vchibikov said:**
> Thanks a lot Anton9121!
It works, but I've got a problem. My screen does not increase the brightness more than about 40%. When brightness indicator shows 50% my screen put in black. Please help

I update NVidia drivers and get it problem too. Now my drivers version is 256.29 (update with Ubuntu Tweak).
Open /home/xx/nvidia_bl.c and find string 177 and 178
```

	.min           = 50, //6628,   //50,
	.max           = 30000, //138090, //1024,

```
and replaced:
```
	
	.min           = 500, //6628,   //50,
	.max           = 80000, //138090, //1024,

```

after 

sudo cp /home/xx/nvidia_bl.c /usr/src/nvidia_bl-0.52/nvidia_bl.c
sudo dkms remove -m nvidia_bl -v 0.52 --all && sudo dkms add build install -m nvidia_bl -v 0.52

after reboot!

and brightness fixed! 

You can experiment with these values, but after the changes have to restart (

---

### Post by vchibikov on 2010-06-17
Wow, Anton, you're our hero!

Thanks again!

---

### Post by nuovodna on 2010-06-18
the module doesn't compile with kernel .34


Version nvidia-bl-dkms 0.16.9 compiles but the value of brightness are too small and the syntax of source code is different. Any idea??

---

### Post by rlrhk1 on 2010-06-24
Thanks Anton9121. worked great, but has anyone else noticed that the brightness slider graphic that displays does not match up with the actual brightness level. For example, when I am at full brightness the slider indicates the level is only at 1/4 brightness. 
 
The workaround that I am using is to much keep maximizing the brightness 10 or so times until the graphic and the display are the same. Then I can adjust it as normal where they both match the same level.
 
Anyone else having this issue?
 
working in ubuntu 9.10 with nividia GT 230m card.

---

### Post by nuovodna on 2010-06-27
with kernel 2.6.34 version 0.16.10 for nvidial_bl.c is needed 

code here

[http://gist.github.com/451904]("http://gist.github.com/451904")

i compiled and installed this new version of module but the min and max brightness values are wrong

Anyone knows a solution???

---

### Post by sanju_bd on 2010-07-05
Anyone tried with G310M card on 9.10 64 bit. For some reason my Kernel version (2.6.31) is giving a lot of trouble and I cant compile following Anton's steps.

---

### Post by BKorts on 2010-07-06
my card is GeForce 310M and the Device ID is 0x0a75

for those who are having the same problem with Sony Vaio CW21FX in ubuntu 10.04,

just add the line

```
/* NVIDIA Geforce 310M */
    { PCI_VDEVICE(NVIDIA, 0x0A75), (kernel_ulong_t)&nv5x_driver_data }, 
```

time to edit your *nvidia_bl.c*

worked very well ^^

---

### Post by pelle.k on 2010-07-06
I've got a Vaio CW1 with a 230m, and i cant get it to work. The screen backlight just goes out on me when i try to echo a value to it. I have to switch back and forth between a VT to see something again.
I have got the latest nvidia_bl from the mactel ppa (0.16.10~lucid), and there is thus no need to add my 230m. I have checked the sources, but the .min value doesn't exist any more so i can't copy what some of you guys suggested verbatim.

---

### Post by sanju_bd on 2010-07-08
Thank you Anton and everyone.
It worked out quite well.

Vaio CW - 310M

---

### Post by ArcanjoV8 on 2010-07-25
> **Anton9121 said:**
> 

Open /home/xx/nvidia_bl.c and find string 177 and 178
```

    .min           = 50, //6628,   //50,
    .max           = 30000, //138090, //1024,

```and replaced:
```
    
    .min           = 500, //6628,   //50,
    .max           = 80000, //138090, //1024,

```(

This works on Ubuntu 10.04 (Lucid) with kernel 2.6 (x86x64) using nvidia_bl-0.16.10. Following your tutorial step-by-step and finally adding this code above in nvidia_bl.c it is perfectly functional in my VAIO VPCCW21FX - Geforce 310M. 

Thanks, Anton, my eyes really thanks you!

------

Is how I set brigthness on 40% at startup? because it is starting with 100% and i just want use 100% of brigthness when I'm watching movies.

---

### Post by nuovodna on 2010-07-26
Can you attach your working nvidia_bl.c  0.16.10 ?? 

Thanks in advance

Regards

---

### Post by ArcanjoV8 on 2010-07-26
> **nuovodna said:**
> Can you attach your working nvidia_bl.c  0.16.10 ?? 

Thanks in advance

Regards

I suggest that you follow the step by step tutorial, however, here is my nvidia_bl-0.16.10 folder.

---

### Post by nuovodna on 2010-07-27
This is the 0.52 version. It doesn't work on kernel >= 2.6.34 :(

---

### Post by simar.mohar on 2010-08-21
Thanks a lot this works for me, atleast for decreasing the brightness, though I can't find the correct settings for me, so when I decrease brightness, I can't it set full by increasing it.

Anyways I work for ubuntu ooperation clean sweep, I guess if we can soenhow patch this workaround and put it in a patch..

---

### Post by Bahr on 2010-09-18
Hi. I have the same problem with a Vaio VPCCW2S1E having a Geforce GT 330m card. 

How do I make this work and how do I find the PCI ID of my card, cause it wasn't in that document? 

I have no idea on what to do, am a completely new ubuntu user, and my eyes are burning very soon! 

I would really appreciate some fast help on this, and an easy guide on how to fix this :)

Thanks

---

### Post by Bahr on 2010-09-22
Is there no one, who has an easy fix for this? :(

---

### Post by lostfile on 2010-09-22
It's work on ubuntu 10.04 but not work on ubuntu 10.10. This output after excute command 
```
sudo dkms add build install -m nvidia_bl -v 0.52
```**Output**
```
Creating symlink /var/lib/dkms/nvidia_bl/0.52/source ->
                 /usr/src/nvidia_bl-0.52

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.35-22-generic-pae -C /lib/modules/2.6.35-22-generic-pae/build SUBDIRS=/var/lib/dkms/nvidia_bl/0.52/build modules.....(bad exit status: 2)

Error! Bad return status for module build on kernel: 2.6.35-22-generic-pae (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia_bl/0.52/build/ for more information.
0
0
ERROR: binary package for nvidia_bl: 0.52 not found
```Please help me to resolve this problem. Thanks for all!

---

### Post by bhb192 on 2010-11-15
I am having the same problem with 

sudo dkms add build install -m nvidia_bl -v 0.52 

in ubuntu 10.10 as well. Anybody know what is causing this problem? Here is my make.log file:

> DKMS make.log for nvidia_bl-0.52 for kernel 2.6.35-22-generic (i686)
Mon Nov 15 04:26:47 EST 2010
make: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /var/lib/dkms/nvidia_bl/0.52/build/nvidia_bl.o
/var/lib/dkms/nvidia_bl/0.52/build/nvidia_bl.c:34: warning: #warning USE_BACKLIGHT_SUSPEND
/var/lib/dkms/nvidia_bl/0.52/build/nvidia_bl.c: In function &#8216;nvidia_bl_init&#8217;:
/var/lib/dkms/nvidia_bl/0.52/build/nvidia_bl.c:543: error: too few arguments to function &#8216;backlight_device_register&#8217;
make[1]: *** [/var/lib/dkms/nvidia_bl/0.52/build/nvidia_bl.o] Error 1
make: *** [_module_/var/lib/dkms/nvidia_bl/0.52/build] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'

---

### Post by bhb192 on 2010-11-23
Okay, I downloaded the new nvidia_bl 0.17.3 for maverick from its project page. It works but it needs to be configured properly. I'm using a sony vaio VPCCW17FX with an nvidia G210M. 

When the laptop first boots the lcd is at full brightness like it always was before I installed nvidia_bl. If I go to a terminal and type in "/etc/acpi/chbrn get" I get a current brightness level of 2. However, if I set it to level 2, the brightness is so low I can't see it. I can set values all the way up to the max_level specified in nvidia_bl.c.

However, even if max_level is set at 10000, the chbrn script will not set the brightness to any value higher than 999, which is about 30% of the lcd's full brightness. 

I'm not sure if the problem lies in the nvidia_bl.c or the chbrn script. I don't fully understand the methodology behind either of these files and I'd appreciate it if somebody could look at these (they're attached) to see what's going on.

Thanks!

---

### Post by pierrexqw on 2010-11-24
I use a GT240M card and I downgrade to Ubuntu 10.04 now.
Hope to see the full solution for 10.10.

---

### Post by crisdeoliveira on 2011-01-19
Hi [bhb192]("http://ubuntuforums.org/member.php?u=1088087"), I have the same problem that you reported in [http://ubuntuforums.org/showthread.php?t=1420341&page=4](http://ubuntuforums.org/showthread.php?t=1420341&page=4) ...
to solve the problem?

Please, reply on [EMAIL="crisdeoliveira.si@gmail.com"]crisdeoliveira.si@gmail.com[/EMAIL]

Thanks

---

### Post by x.pinchart on 2011-01-24
Ubuntu 10.04 + NVidia GeForce 310M + Sony VPCS13M1E

I followed instructions given in post #30 and #20
+ 
I guess no error at log (make.log):
DKMS make.log for nvidia_bl-0.52 for kernel 2.6.32-27-generic (i686)
Sun Jan 23 23:05:20 CET 2011
make: Entering directory `/usr/src/linux-headers-2.6.32-27-generic'
  CC [M]  /var/lib/dkms/nvidia_bl/0.52/build/nvidia_bl.o
/var/lib/dkms/nvidia_bl/0.52/build/nvidia_bl.c:34:3: warning: #warning USE_BACKLIGHT_SUSPEND
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /var/lib/dkms/nvidia_bl/0.52/build/nvidia_bl.mod.o
  LD [M]  /var/lib/dkms/nvidia_bl/0.52/build/nvidia_bl.ko
make: Leaving directory `/usr/src/linux-headers-2.6.32-27-generic'

But no effect at all while pressing keys.

1) How can check the changes have been made properly ?
2) If working, do you see the small windows with brighness level, as you would see for e.g. sound level ?
3) Any advise ?

Vax

---

### Post by aporto on 2011-02-02
Hello, anyone maked it in 10.10???
I tried and not sucess...

THanks

---

### Post by pgw on 2011-02-17
> **aporto said:**
> Hello, anyone maked it in 10.10???
I tried and not sucess...

THanks

[http://shiba89.wordpress.com/2010/10/28/screen-backlight-on-sony-vaio-vpcs11e7e-with-ubuntu-10-04/](http://shiba89.wordpress.com/2010/10/28/screen-backlight-on-sony-vaio-vpcs11e7e-with-ubuntu-10-04/)

Works for me.

---

### Post by astawa87 on 2011-02-18
Hey dear,
 I have Sony Vaio TZ36GN, ANY ONE Can help me to make all device working.. I need yours help.

Thank you

---

### Post by bhb192 on 2011-07-08
*New Strategy*

Install the latest nvidiabl driver from [guillaumezin's github page]("https://github.com/guillaumezin/nvidiabl/downloads"). Guillaumezin has added additional support for many more Sony Vaio laptops since my last post in this thread. 

Next you will need to modify one line (yes, only one!) in the source code for the Gnome Brightness Applet so that it ignores the non-working Sony backlight driver and adjusts the nvidiabl driver instead. I've posted detailed instructions on how to do this at nV News Forums: 
[http://www.nvnews.net/vbulletin/showpost.php?p=2453584&postcount=139](http://www.nvnews.net/vbulletin/showpost.php?p=2453584&postcount=139)

Because you will be using the native Ubuntu brightness control, there is no need for any ACPI scripts and you get a working, on-screen display!

Hope this solves the backlight issue for everybody else!

---

### Post by Anton9121 on 2011-12-17
*New version for new strategy =)*
Tested in Vaio vpccw1e1r, ubuntu 11.10.

0) Download last version nvidiabl-dkms, from [https://github.com/guillaumezin/nvidiabl/downloads](https://github.com/guillaumezin/nvidiabl/downloads) 
For example 
```
wget https://github.com/downloads/guillaumezin/nvidiabl/nvidiabl-dkms_0.72_all.deb
sudo dpkg -i nvidiabl-dkms_0.72_all.deb
```

1) See you version gnome-settings-daemon in synaptic and download source from launchpad, for example in Oneiric: [https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.2.2-0ubuntu2](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.2.2-0ubuntu2) 

```
wget https://launchpad.net/ubuntu/+archive/primary/+files/gnome-settings-daemon_3.2.2.orig.tar.bz2
bzip2 -cd ~/gnome-settings-daemon_3.2.2.orig.tar.bz2 | tar xvf -
```

2) after need edit ~/gnome-settings-daemon-3.2.2/plugins/power/gsd-backlight-helper.c

```
gedit ~/gnome-settings-daemon-3.2.2/plugins/power/gsd-backlight-helper.c
```
Find &#8220;sony&#8221; and replace &#8220;nvidia_backlight&#8221;, string 60

3) after save, and

```
cd ~/gnome-settings-daemon-3.2.2
sudo apt-get install intltool
sudo apt-get build-dep gnome-settings-daemon
./configure
make
```

4) after compiling, need replace gsd-backlight-helper

```
sudo mv /usr/lib/gnome-settings-daemon/gsd-backlight-helper /usr/lib/gnome-settings-daemon/gsd-backlight-helper.old
cd ~/gnome-settings-daemon-3.2.2/plugins/power/
sudo cp gsd-backlight-helper /usr/lib/gnome-settings-daemon/.
```

and. .  DUNE!

---

### Post by xristos on 2011-12-31
Thanks Anton9121 !!!
It worked perfect for Vaio VPCCW1

---

### Post by arunize on 2012-01-08
Anton, thanks for the solution. 
However on reboot it doesn't remember the brightness level what I set earlier and on first brightness '-' operation it goes to 0 from maximum. How can I overcome this?

Thanks.

Arun

---

### Post by rfictus on 2012-04-07
Hi Anton,

Few years down the lone now, ran through all of the steps on a VPCCW16FG Vaio but didn't help adjust screen brightness. Keys are fn+F5+F6. Bar moves but no action.

Any new update on this would be kindly appreciated.
Regards

---

### Post by rfictus on 2012-04-15
This one hits it right on the head! Much gratitude.
My case: VPCCW16FG, Ubuntu 11.10. Sec. + Rec. Updates!

> **Anton9121 said:**
> *New version for new strategy =)*
Tested in Vaio vpccw1e1r, ubuntu 11.10.

0) Download last version nvidiabl-dkms, from [https://github.com/guillaumezin/nvidiabl/downloads](https://github.com/guillaumezin/nvidiabl/downloads) 
For example 
```
wget https://github.com/downloads/guillaumezin/nvidiabl/nvidiabl-dkms_0.72_all.deb
sudo dpkg -i nvidiabl-dkms_0.72_all.deb
```

1) See you version gnome-settings-daemon in synaptic and download source from launchpad, for example in Oneiric: [https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.2.2-0ubuntu2](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.2.2-0ubuntu2) 

```
wget https://launchpad.net/ubuntu/+archive/primary/+files/gnome-settings-daemon_3.2.2.orig.tar.bz2
bzip2 -cd ~/gnome-settings-daemon_3.2.2.orig.tar.bz2 | tar xvf -
```

2) after need edit ~/gnome-settings-daemon-3.2.2/plugins/power/gsd-backlight-helper.c

```
gedit ~/gnome-settings-daemon-3.2.2/plugins/power/gsd-backlight-helper.c
```
Find &#8220;sony&#8221; and replace &#8220;nvidia_backlight&#8221;, string 60

3) after save, and

```
cd ~/gnome-settings-daemon-3.2.2
sudo apt-get install intltool
sudo apt-get build-dep gnome-settings-daemon
./configure
make
```

4) after compiling, need replace gsd-backlight-helper

```
sudo mv /usr/lib/gnome-settings-daemon/gsd-backlight-helper /usr/lib/gnome-settings-daemon/gsd-backlight-helper.old
cd ~/gnome-settings-daemon-3.2.2/plugins/power/
sudo cp gsd-backlight-helper /usr/lib/gnome-settings-daemon/.
```

and. .  DUNE!

---

### Post by s20202 on 2012-04-26
It doesn't work with Ubuntu 10.04
but after upgrading to 11.10, it works!!!
thanks a lot!

> **rfictus said:**
> This one hits it right on the head! Much gratitude.
My case: VPCCW16FG, Ubuntu 11.10. Sec. + Rec. Updates!

---

### Post by Anton9121 on 2012-10-01
For ubuntu 12.04

1. Download nvidiabl last version from [hear]("https://github.com/guillaumezin/nvidiabl/downloads")
```
wget https://github.com/downloads/guillaumezin/nvidiabl/nvidiabl-dkms_0.79_all.deb
```

2. Installed it 
```
sudo dpkg -i nvidiabl-dkms_0.79_all.deb
```

4. Download oBacklight Script
```
wget http://dev.osource.se/files/oBacklight_0.3.8.tar.gz
```

5. Untar it 
```
tar -xvf oBacklight_0.3.8.tar.gz
```

6. cd to the untared directory
```
cd oBacklight_0.3.8
```

7. Give the script execution permission 
```
chmod +x oBacklight
```

8. Edit oBacklight, set string BMT="1" to BMT="2"
```
gedit oBacklight
```

9. Copy oBacklight script to the /etc/init.d directory
```
sudo cp ./oBacklight /etc/init.d/.
```

10. Add it to the start up 
```
sudo update-rc.d oBacklight defaults
```

and Dune!

---

### Post by Anton9121 on 2012-10-20
For ubuntu 12.10

1. Download nvidiabl last version from [hear]("https://github.com/guillaumezin/nvidiabl/downloads")
```
wget https://github.com/downloads/guillaumezin/nvidiabl/nvidiabl-dkms_0.79_all.deb
```

2. Installed it 
```
sudo dpkg -i nvidiabl-dkms_0.79_all.deb
```

4. Download oBacklight Script
```
wget http://dev.osource.se/files/oBacklight_0.3.8.tar.gz
```

5. Untar it 
```
tar -xvf oBacklight_0.3.8.tar.gz
```

6. cd to the untared directory
```
cd oBacklight_0.3.8
```

7. Give the script execution permission 
```
chmod +x oBacklight
```

8. Edit oBacklight, set string BMT="1" to BMT="2", and replace all "nvidia_backlight" to "nv_backlight"
```
gedit oBacklight
```

9. Copy oBacklight script to the /etc/init.d directory
```
sudo cp ./oBacklight /etc/init.d/.
```

10. Add it to the start up 
```
sudo update-rc.d oBacklight defaults
```

11. Run:
sudo gedit /etc/default/grub
Update these lines:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
... with the following arguments:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=nv_backlight"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

12. Then run sudo update-grub and reboot.

---

