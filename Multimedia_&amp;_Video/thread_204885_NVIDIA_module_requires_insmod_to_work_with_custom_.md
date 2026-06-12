---
title: "NVIDIA module requires insmod to work with custom kernel"
date: 2006-06-27
forum: Multimedia &amp; Video
---

### Post by ashyanbhog on 2006-06-27
Hi

I recompiled the kernel from ubuntu sources and nvidia-kernel-source using this [guide]("http://www.ubuntuforums.org/showthread.php?t=85064")

Now, when booting the custom kernel, the screen goes blank (no splash screen, no boot msgs either) and dumps into to login console with the error message "module not found nvidia" in xserver output. After logging in, I manually insert the module using the command

$ sudo insmod /lib/modules/2.6.15.7-ubuntu1-athlon/nvidia/nvidia.ko

running "startx" brings up nvidia splash screen and gnome.

There were no errors when compiling the kernel and as indicated in the guide, I got three deb files as ouput, and they installed smoothly 

/usr/src/kernel-headers-2.6.15.7-ubuntu1-athlon_10.00.Custom_i386.deb
/usr/src/kernel-image-2.6.15.7-ubuntu1-athlon_10.00.Custom_i386.deb
/usr/src/nvidia-kernel-2.6.15.7-ubuntu1-athlon_1.0.8762-0ubuntu3+10.00.Custom_i386.deb

Except for FAT error (iso8859-1 not compiled), everything else works fine with the custom kernel

I tried coping nvidia.ko to /lib/modules/2.6.15.7-ubuntu1-athlon/kernel/drivers/video/ and nvidia folder inside video dir,

But X still fails to load the module and I have to use "insmod" and "startx" after every reboot, 

am I missing some step that is required to load the nvidia driver during bootup? :-k

---

### Post by Ptero-4 on 2006-06-27
Do you have the module in /etc/modules? Have you run modprobe -d on it?

---

### Post by tseliot on 2006-06-27
Can you try my script?

[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by ashyanbhog on 2006-06-27
[QUOTE=Ptero-4]Do you have the module in /etc/modules? Have you run modprobe -d on it?[/QUOTE]

I inserted "nvidia" into /etc/modules and rebooted. It made no diff, 

tried

[I]$ sudo modprobe --d nvidia
FATAL: Module nvidia not found.[/I]

[I]$ sudo modprobe --d /lib/modules/2.6.15.7-ubuntu1-athlon/nvidia/nvidia.ko
FATAL: Module /lib/modules/2.6.15.7_ubuntu1_athlon/nvidia/nvidia.ko not found.[/I]

*$ sudo modprobe -l nvidia  # returns to prompt without any output*

after insmod and startx 

[I]lsmod | grep nvidia
nvidia               4542740  12
i2c_core               16592  2 nvidia,i2c_viapro
agpgart                27464  2 nvidia,via_agp[/I]

modprobe outputs do not change

---

### Post by ashyanbhog on 2006-06-27
[QUOTE=tseliot]Can you try my script?

[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")[/QUOTE]

Working :) 

I used [http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_8762_32](http://www.albertomilone.eu/ubuntu/nvidia/scripts/envy_8762_32) 

**thanks tseliot** 

had to make one small change though

nvidia installer used to exit with the error 

[I]/usr/
   src/kernel-headers-2.6.15.7-ubuntu1-athlon/arch/i386/Makefile.cpu: No such f
   ile or directory
   make[2]: *** No rule to make target `/usr/src/kernel-headers-2.6.15.7-ubuntu
   1-athlon/arch/i386/Makefile.cpu'.  Stop.[/I]

I had to manually download the file and comment out line 76 in your script

*sudo wget [www.albertomilone.eu/ubuntu/nvidia/scripts/Makefile.cpu](www.albertomilone.eu/ubuntu/nvidia/scripts/Makefile.cpu)*

the script fetched the driver from Nvidia site but failed on this one, maybe wget failed in sudo mode, You can try downloding the file to a diff dir without a sudo and then do a "sudo mv"

there was also a warning on the screen for line 72,  something like "envy_8762_32 error in line 72 [: argument required". 

everything else worked like breeze

**PS: Thanks Ptero-4 for responding**

---

### Post by tseliot on 2006-06-28
[QUOTE=ashyanbhog]nvidia installer used to exit with the error 

[I]/usr/
   src/kernel-headers-2.6.15.7-ubuntu1-athlon/arch/i386/Makefile.cpu: No such f
   ile or directory
   make[2]: *** No rule to make target `/usr/src/kernel-headers-2.6.15.7-ubuntu
   1-athlon/arch/i386/Makefile.cpu'.  Stop.[/I][/QUOTE]
Perhaps the folder to which the file should have been copied didn't exist. Did you create the folder or installed the kernel headers after the script failed?

---

