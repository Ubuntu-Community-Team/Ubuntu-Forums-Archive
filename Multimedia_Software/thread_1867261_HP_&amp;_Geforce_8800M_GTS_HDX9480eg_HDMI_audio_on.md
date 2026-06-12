---
title: "HP &amp; Geforce 8800M GTS HDX9480eg: HDMI audio on the Sony 72-inch NOK; HDMI Video OK,"
date: 2011-10-22
forum: Multimedia Software
---

### Post by innovativer on 2011-10-22
HI,

My computer: HP Pavilion HDX9480eg
 My Graphics Card: NVIDIA GeForce 8800M GTS 512MB HDMI
 My second "Monitor" (TV set) Sony BRAVIA KDL-40EX715 101.6 cm (40 inch) LED-backlit TV (Full HD, 100Hz, DVB-T / -C/-S2) black
 Url: [http://geizhals.at/?a=348078&t=alle&ahme&vl=at&v=e](http://geizhals.at/?a=348078&t=alle&ahme&vl=at&v=e)
 My OS: Ubuntu 11.10.  
 
The problem: HDMI audio on the Sony TV is not working, HDMI video works fine. Audio-IN (Microphone) is not working either.
 

 Analysis: In the program Pulseaudio the following is shown
 - Input Device: "Internal Audio Analogue Stereo"  
 - Output Device: "Internal Audio Analog 4.0 Surround"
 - HDMI no trace. :-(

**First Troubleshooting attempt:**
 Ubuntu 11.10 - system settings.
 Installation of additional drivers.
 Got Latest NVIDIA drivers (260.99) installed.  
 Serious mistake!  
  
 **Result:** 1 minute after I logged into the GUI (the GUI desktop), the graphics card FREEZEs !  
 I tried 4 times to install ubuntu 11.10 from scratch:
 
[LIST=1]
[*]with minimal     installation, no OS updates & after that NVIDIA Latest Driver (260.99)      ==> Freeze
[*]with minimal     installation, all OS updates & after that NVIDIA Latest Driver     (260.99) ==> Freeze
[*]with full installation,     no OS updates & after that NVIDIA Latest Driver (260.99) ==> Freeze
[*]with full     installation, all OS updates & after that NVIDIA Latest Driver (260.99)      ==> Freeze
[/LIST]
 

NVIDIA Latest Driver (260.99) installation? Unusable for my old laptop.
 However, I could see within that one minute within the Pulse Audio software that new hardware was visible, namely, the HDMI port for TV! So the driver works, but the graphics card still freezes! WTF?

Now I'm on the road with full install and all updates without Latest NVIDIA (260.99) drivers on board.
 the Sony TV doesn't feature HDMI audio tough, HDMI video gets transferred, audio-in (microphone) fails, seems to me also unsupported sound card.

(The laptop was until recently under _Windows 7_. There, too, led Latest NVIDIA driver  systematically to a graphics freeze. There, I helped myself with an old NVIDIA driver version (197.16_notebook_winvista_win7_64bit_international_whql). This was how the Win7 system got stable!)
[B]
Second Troubleshooting attempt: [/B] 
 I searched the HP.com site for suitable Linux drivers for my notebook:  
 Result: I found the HP Linux driver NVIDIA-Linux-x86-180.29-pkg1.run [http://www.nvidia.de/object](http://www.nvidia.de/object) / linux_di180.29_de.html

**The problem here: ** 
 **The install script complains about “you appear to be running an x-server, please exit x before installing!**
 [B]Whilst working on the terminal using ctrl-alt-f1. (I'm not a Linux geek and maybe this is the problem!)
[/B]
Please help! ;-)


:popcorn:

---

### Post by BicyclerBoy on 2011-10-22
There's a lot to attack so let's just start on the video driver..

It should not crash unless something is badly wrong.

some kernel bug with your h/w acpi
32 bit 

Maybe find something in the kernel logs or Xorg logs
/var/log/Xorg.0.log  var/log/*

If you must go outside of package management you should only download the driver from nVidia.
The installation instructions are in the driver documentation. nVidia documentation is 2nd to none.
Briefly...have to console login & stop X server (gdm), execute the installer..
But you need compiler tools & kernel headers packages.

You can get different versions of the nVidia driver from synaptic by using force version.
But how far back you can go in 11.10 is the question..Probably not far enough.

You could try ubuntu 10.10 64 bit (before unity)..

Note that the 8000 & 9000 series do not have real HDA HDMI audio; they support S/PDIF over HDMI via a link cable from mobo soundcard to video card.
I think you can get this working without the nVidia graphics driver.

Real HDA codec HDMI audio requires the 'right' graphics driver.

---

### Post by Galicslayer on 2011-10-23
I am experiencing the same problems with the same card: 8800m GTS 512 from my experience, the only driver that works with hdmi audio was 180 and later, but that doesnt install unless you're on jaunty or lower (i think). I had tried to install the newest driver but i had many graphical freezes like you did.

Your best bet is to go back to the older 173 driver.

---

