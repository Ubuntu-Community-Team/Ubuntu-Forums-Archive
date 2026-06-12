---
title: "1366x768 Nvidia 8600GT in Ubuntu 7.10"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by Cirion75 on 2007-10-22
Ubuntu 7.10 and Kubuntu 7.10 Live CD's boot directly in 1366x768@66 but after install Ubuntu and Kubuntu boots with 1024x768@60?!?

When I try to change resolution I only get to chose 800x600 or 1024x768.
When trying the new Screens and Resolutions program, I do not find any 1366x768@66 monitors, and I can not set it manually. I can see that it is using the latest Nvidia driver.

When trying to add the resolution to xorg.conf it boots into safemode with vesadriver and 640x480@51 resolution.

When using the new Screens and Resolution program in LiveCD mode, I can se that it is using the NV driver and not NVIDIA.

Anyone know how to get the latest Nvidia driver that is shipping with Ubuntu/Kubuntu 7.10 set up with 1366x768@66? The display is a 40" Video7 TV.

---

### Post by pbcartwright on 2007-10-22
did you enable all the repositories?  you might want to install envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

it will detect and install the correct NVIDIA drivers for you..

---

### Post by kolors on 2007-10-22
I am having a similar issue (GeForce 6150 integrated) with a widescreen monitor (Acer AL1916W, native resolution 1440x900)

The nv driver works fine, but the nvidia driver (even when built with Envy) does not allow me to select the proper resolution... closest I can come is 1400x1050 (distorted and weird) or 1280x800 (non-native, therefore blurry).

I know it's a restricted driver and in this case the open source driver works like a charm, but has anyone been able to get the nvidia driver to work properly with widescreen resolutions?

---

### Post by pointzero on 2007-10-22
I'm having same problem.  NV works but as soon as the Restricted Driver is installed everything is caput.  I have a max of 640x480 on my AL2032W (acer) monitor which does 1680x1050 with NV.  Any suggestions?

---

### Post by Cirion75 on 2007-10-23
Nothing wrong with the driver.... It's the screen detection that is not working.

I tried with a 212" LCD with 1600x1200 works great :)
But it is not working at all with 1366x768 :(

---

### Post by kolors on 2007-10-23
> tried with a 212" LCD with 1600x1200 works great

wow, at 212 inches, wouldn't that be really blocky? ;)

---

### Post by Cirion75 on 2007-10-24
ups... 21.2" :) Not blocky at all :)

---

### Post by akarimco on 2007-10-24
I was having similar problems which went away once I installed the final release of Gutsy, BUT.... when I play a video file, the screen somehow reverts to a 4:3 aspect ratio.  My screen's resolution is 1320x768, and the output matched, but as soon as I ran the video, it apparently reverted to 1024x768, but everything is horizontally squished.  This is seriously the last major hurdle keeping me from using Ubuntu full time on my computer... it probably wouldn't be an issue except that I'm using my 37" Olevia TV in my living room as my monitor, but it should be detected as a Plug and Play monitor (using the TV's VGA input), but selecting Plug and Play in Ubuntu gives me no option to change the resolution at all... no choices whatsoever.  I'd be happy to explain better if necessary, but it's late and I'm tired and having trouble forming a coherent sentence, so for now I'll just hope that you all can make sense out of me, haha.

---

### Post by daveknight on 2007-12-04
Hi,
I'm having a similar problem - i've followed the advice in here, but still cannot select 1320x768 for my 32" BenQ LCD, and thats the resolution that I need.  Help would really, really be appreciated.

Regards,
David

---

### Post by stjomi on 2007-12-04
Nothing wrong with the driver.... It's the screen detection that is not working.

I tried with a 212" LCD with 1600x1200 works great 
But it is not working at all with 1366x768 


I'm having a problem when enable my nvidia driver.....could it be my monitor detection and not the driver?

---

