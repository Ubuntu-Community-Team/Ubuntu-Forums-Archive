---
title: "Nvidia Geforce 4 420 Go twinview problems"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by theanswriz42 on 2006-07-04
Hello, I am having an issue with the twinview on my laptop with the aforementioned graphics card. I have all the nvidia stuff setup and working well but for some reason when I follow the instructions at [https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut) I get a horizontal line across the screen where the top half is black and the bottom half is white and I cannot access any of the other terminal screens so I have to restart and manually change my xorg.conf file in recovery mode to comment out the options I added. 

If anyone knows if there is a fix for this, I would be greatful.

Cheers

---

### Post by M4LFUNCT10N on 2006-07-04
Similar results here.  Toshiba Satellite 1415-S174.

Black screen, with white bar just south of the middle of the screen, doesn't quite span the whole width of the screen.

---

### Post by theanswriz42 on 2006-07-04
Yeah, that's the exact same issue I'm having.

---

### Post by sfink01 on 2006-07-06
Try this:

Download the nVidia driver

[http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8762.html)

Extract the nvidia driver

./NVIDIA-Linux-x86-1.0-8762-pkg1.run -x

Then 

cd NVIDIA-Linux-x86-1.0-8762-pkg1/usr/src/nv

then

vi os-registry.c

find the line 

static int NVreg_Mobile = ~0;

Change to

static int NVreg_Mobile = 0;

then

 cd ../../../

then

using the Method 2 listed here 

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Install the nVidia driver.

This is how I have to do it on several of my laptops.

Best,

Steve

---

### Post by Martinv on 2006-07-19
Hello theanswriz42,
I have a nvidia 420 GO too, but I can't get mine to
work at all. When I download the latest drivers, it
replaces 'nvidia 420 bla bla' in xorg with 'ATI radeon 7600 bla bla'!
And when 'nv' is replaced with 'nvidia' in xorg, it
either freezes on boot, or gives the error 'No screens found'.
Please, would you tell me how you got your to work?
I've tried all kinds of guides but it just wont work..

---

### Post by tseliot on 2006-07-20
> **Martinv said:**
> Hello theanswriz42,
I have a nvidia 420 GO too, but I can't get mine to
work at all. When I download the latest drivers, it
replaces 'nvidia 420 bla bla' in xorg with 'ATI radeon 7600 bla bla'!
And when 'nv' is replaced with 'nvidia' in xorg, it
either freezes on boot, or gives the error 'No screens found'.
Please, would you tell me how you got your to work?
I've tried all kinds of guides but it just wont work..

Follow Method 1 and point 7 of the Problems Section of this guide of mine:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

