---
title: "Nvidia Drivers not working. Nvidia 6200, Ubuntu 8.04"
date: 2008-04-27
forum: Multimedia Software
---

### Post by Zac on 2008-04-27
Hi, I've been struggling for a few days now trying to get my Nvidia drivers working for my Nvidia 6200 128mb 3d card. I am hoping that maybe someone can help me as to what I am doing wrong because I have tried every way that I have thought.

I've tried using Envyng but that doesn't work. I install the nvidia-new drivers and then I find that inside my Xorg.0.log file I have this error:

```
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
```

And that is the exact same error that I'd get if I installed the nvidia-new drivers with synaptic package manager. I have even tried downloading the .run file from nvidia's website and I've tried that. I still get the same error. After installing the drivers I reboot Ubuntu and when I get back into X I get a message saying that my card and screen could not be configured automatically and that I should do it manually. 

I will be attaching my xorg.conf file and my Xorg.0.log file to this post. I have really and truly run out of options and I hope that someone will be able to help me. 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
At the bottom of that document there is a trouble shooting section and I've followed those steps too.. alas, no success.

Xorg.0.log :
[http://rafb.net/p/L8CJZI90.html]("http://rafb.net/p/L8CJZI90.html")

Xorg.conf :
[http://rafb.net/p/fpqGaq13.html]("http://rafb.net/p/fpqGaq13.html")

I've also tried to configure my xserver-xorg using 'dpkg-reconfigure xserver-org' I get to the part where it asks for keyboard options and immediately after that I get this error:

> xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080427134838
FATAL: Error inserting battery (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/battery.ko): No such device

Very strange because I am using a desktop computer..

#nvidia-settings gives me this:
> 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

and:
#nvidia-xconfig gives me this : 

> Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

Any feedback would be greatly appreciated! Thank you for taking your time to read my post :)

---

### Post by kigango123 on 2008-06-04
I am also trying to install an Nvidia 6200 (AGP) on my old computer with very limited success. I tried it with the restricted drivers and got major resolution problems, i fell back to envyng and was initially succesful, but i ran into some video playback  problems, 

Only thing i can say to you is not to try and run restricted driver together with envy. I am still trying to find out my problem so.... . .

Cheers

---

