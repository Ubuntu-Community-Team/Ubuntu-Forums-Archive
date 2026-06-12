---
title: "How to install nvidia on rt-kernel &amp; switch between kernels without compiling"
date: 2009-03-07
forum: Multimedia Software
---

### Post by ticket on 2009-03-07
This has been pulled together from various sites & threads. It certainly helped me to install nvidia on the rt-kernel and the generic kernel, and switch easily between them using grub.  Also the video resolution issue is solved for me.  Note that this how-to is for installing the nvidia drivers directly as supplied by nvidia. It does not cover the .deb packages.  I am running Intrepid.

From the nvidia site:

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the files /etc/init.d/nvidia-glx and /etc/init.d/nvidia-kernel do not exist

If you use Ubuntu, please also ensure that the linux-restricted-modules or linux-restricted-modules-common packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv nvidia_new"

Additionally, delete the following file if it exists:

    /lib/linux-restricted-modules/.nvidia_new_installed

=======================================================

This is what I did to install the 177.80 drivers to the rt kernel:
(from [http://meandubuntu.wordpress.com/2008/07/17/install-nvidia-17713-drivers-on-realtime-kernel]("http://meandubuntu.wordpress.com/2008/07/17/install-nvidia-17713-drivers-on-realtime-kernel") )


1. Download the drivers, necessary build packages and Linux kernal source
[http://www.nvidia.co.uk/object/linux_display_ia32_177.80_uk.html](http://www.nvidia.co.uk/object/linux_display_ia32_177.80_uk.html)


3. Run the driver script with the “-x” (extract-only) option:
```
sudo sh NVIDIA-Linux-x86-177.80-pkg1.run -x
```


4. Make the replacements mentioned in the nvidia linux forums:
sudo gedit /usr/src/NVIDIA-Linux-x86-177.80-pkg1/usr/src/nv/nv-linux.h
Replace “__SEMAPHORE_INITIALIZER” with “__COMPAT_SEMAPHORE_INITIALIZER”
Replace “struct semaphore”        with “struct compat_semaphore”

5. Run the installer:
```
cd NVIDIA-Linux-x86-177.80-pkg1
```

Then Kill X-server using:
```
sudo /etc/init.d/gdm stop
```

Then:
```
sudo ./nvidia-installer
```

From here on out it should work just like normal!

6. Restart X-server using (or maybe re-boot at this point?)
```
sudo /etc/init.d/gdm start
```

7. To uninstall the driver: (can be done while gnome is running(?))
```
sudo sh NVIDIA-Linux-x86-177.80-pkg1.run --uninstall
```

//// Fixing the screen resolution
Try
  ```
sudo nvidia-settings
```
Use the gui to set up your resolution, apply it and when happy, save the xorg.conf.
Because you are running with sudo, nvidia-settings will be able to properly save the file.
Then using
    System->Perferences->Screen Resolution
make sure you choose the same screen resolution and save it.

//// After a kernel upgrade...
Check which kernel is being booted - a kernel upgrade usually alters the boot menu.
You can edit it at /boot/grub/menu.lst
Boot menu items are numbered starting from 0.

--------------------------------------
Finally here's the solution having with different nvidia drivers in different kernels.

The problem is that when running the nvidia installer, it wipes out the driver from other kernels and just installs for the current one.

The installer builds a nvidia.ko kernel object and places it in 
   /lib/modules/CURRENT-KERNEL-NAME/kernel/drivers/video/nvidia.ko
where CURRENT-KERNEL-NAME is that returned by ```
uname -r
```

The trick is to force the installer to just build for a user-specified kernel and do nothing else.
The following worked for me. I was running the rt-kernel with the modified nvidia driver as described in this thread.  I wanted to install the standard (unmodified) driver into my latest generic kernel (2.6.27-11-generic).  This is what I did:

stop x server: 
   ```
sudo /etc/init.d/gdm stop
```
(sometimes this hangs using the rt kernel - hitting crtl-alt-F1 afterwards can help - else reboot & try again)

Install nvidia using: 
   ```
sudo ./nvidia-installer --kernel-name=2.6.27-11-generic  -K
```

Note the two options here:
 
   --kernel-name=2.6.27-11-generic  
will install to the named kernel (as obtained from 'uname -r')

   -K   
will install the nvidia.ko object without un-installing existing drivers / kernel objects.

I found you need to use both options together!

After the install completes, you will have a new nvidia.ko in: 
   /lib/modules/2.6.27-11-generic/kernel/drivers/video/nvidia.ko
while the one in: 
   /lib/modules/2.6.27-3-rt/kernel/drivers/video/nvidia.ko
is untouched.

Restart X with:
   ```
sudo /etc/init.d/gdm start
```
(or simply re-boot if that fails)

Use grub to select 2.6.27-11-generic
The nvidia drivers you just compiled will load.

You can now switch between kernels as normal (using grub) without having to re-build the drivers!

---

### Post by kzipz on 2009-03-23
:p I managed to do what I was beginning to think IMPOSSIBLE! 

[COLOR="Sienna"][SIZE="3"]**SUCCESS: Installing Nvidia 180.41 and PulseAudio with Alsa upgrade (Rev 1.0.19) on OpenGEU on linux-2.6.27-3-rt**[/SIZE][/COLOR]:D

I had been struggling with UbuntuStudio both Jaunty & Intrepid x64 distros trying various tricks applied to older distros with no success...then out of the blue I decided to download the newest release of OpenGEU AMD64.

[OpenGEU 8.10 - Luna Serena]("http://opengeu.intilinux.com/OpenGEU_Linux_Official_Home/Download.html")


My hopes weren't too high since I hadn't read of ANYONE getting nVidia's proprietary driver working and I had tried several times with 177, 180.29, 180.32 and finally 180.41 but every-time the installer choked. 

After the initial installation of OpenGEU I didn't have sound but just proceeded to install the RT kernel package from Synaptic pkg manager...rebooted into the newly installed 2.6.27-3-rt kernel. Then I dropped into shell and killed gnome-desk-manager and launched the nVidia 180.41 installer with the "-k$(uname -r)" option and to my pleasant surprise it installed without a hickup!!! I allowed the installer to reconfigure xorg and rebooted with my nVidia working properly in linux-REAL-TIME.

Still no sound... but I was so glad to get the nV in I just laughed through the ALSA upgrade and when I rebooted had BLASTING clear audio. Much higher volume output and crisper quality immediately noticeable.:popcorn:

ALSA UPGRADE:[http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

Now I'm on my way to running patches for pulseaudio and improved latency which I'm not concerned with accomplishing now that the Major obstacles have been overcome.

PATCHING RT AUDIO:[http://proaudio.tuxfamily.org/wiki/index.php?title=Howto_RT_Kernel]("http://proaudio.tuxfamily.org/wiki/index.php?title=Howto_RT_Kernel")

Thanks for posting your results and I hope someone repeats this step and posts feedback so more people can start gettting the MAX out of their multimedia computers. Happy Jamming!

Kz

---

