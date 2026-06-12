---
title: "Appropriate nvidia-glx-new missing from server?"
date: 2008-10-01
forum: Multimedia Software
---

### Post by vitreoushumours on 2008-10-01
I am new to Ubuntu and Linux in general.  I installed 8.04 on my laptop recently (an HP TX2000z convertible tablet PC.)  When I first got into Gnome it told me that I needed to install Nvidia-glx-new in order for my video hardware to work properly.  The download failed, so later I went into the Synaptic Package manager, clicked it, selected to install, then hit apply and download and I get this error:

"W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb)
  404 Not Found"

I get the same error if I go to System -> Administration -> Hardware drivers and attempt to install the nvidia-glx-new there.

I am connected to the internet via ethernet because I have not yet got my Wireless card working.

If I navigate to [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/) I find that indeed there is no "nvidia-glx-new_169.12+2.6.24.13-18.41_i386.deb" listed there.  (Though there is a "nvidia-glx-new_169.12+2.6.24.12-16.34_i386.deb  " and a "nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb"

Is there any way to update this so that it is looking for a current file location?

Can I download "nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb" and intall it to resolve the problems with my hardware?

Any advice?  Thanks. :)

---

### Post by lian1238 on 2008-10-01
IMO, I think you should go to [nvidia.com]("http://www.nvidia.com/object/unix.html") and download the driver for unix and install it manually.[]("http://www.nvidia.com/object/unix.html")

---

### Post by vitreoushumours on 2008-10-02
I downloaded the driver from Nvidia, but unfortunately I fail at following the directions provided by Nvidia.  (i figured out that I need to use "sh /filepath/filename" from terminal to extract the driver, but it says that it has to be done as root, and if I use "su root" it prompts for a password, I only set up one password when setting up the OS and it is not working.  (I did not even attempt to figure out how to "exit the X server and terminate all OpenGL applications" as the instructions suggested.  I would have to know what the X server is to do that.)  

Does anyone know if there is somewhere specific that I can go to report a problem with the missing file listed in Synaptic Program Manager?

---

### Post by lian1238 on 2008-10-02
> **vitreoushumours said:**
> I downloaded the driver from Nvidia, but unfortunately I fail at following the directions provided by Nvidia.  (i figured out that I need to use "sh /filepath/filename" from terminal to extract the driver, but it says that it has to be done as root, and if I use "su root" it prompts for a password, I only set up one password when setting up the OS and it is not working.  (I did not even attempt to figure out how to "exit the X server and terminate all OpenGL applications" as the instructions suggested.  I would have to know what the X server is to do that.)  

Does anyone know if there is somewhere specific that I can go to report a problem with the missing file listed in Synaptic Program Manager?

Don't give up just yet. Here are the steps you need to do to install that driver you downloaded from Nvidia.


[LIST=1]
[*]Assume your driver file is on the desktop. (You can put it on your desktop for simplicity)
[*]Go to the commandline: (Ctrl+Alt+F1); and log in
[*]Stop X server: sudo /etc/init.d/gdm stop
[*]Install Nvidia driver: sudo sh ~/Desktop/NV <press tab to auto complete>
[*]Let the installer configure your X configuration file.
[*]After installation, restart X server: sudo /etc/init.d/gdm start
[/LIST]
If the installer says you need to uninstall the exisiting driver, run the installer with " --uninstall" after the install command. Then run normally to install. Hope that helps

---

### Post by vitreoushumours on 2008-10-02
Thank you very much for the followup with the step by step, I had to leave it for a few hours because I was so disheartened.  LOL, it led to a string of errors inside the installer.  Maybe I got the wrong driver...I feel so lost.  I haven't spent this much time at a command prompt since my Apple IIe and my Commodore 64.

After I accept it's install on the first prompt it tells me that no precompiled interface was found to match my kernel;" I click yes for it to attempt to download a kernel from [ftp://download.nvidia.com](ftp://download.nvidia.com).  Then it tells me that no matching precompiled interface was found, and that it will need to compile a kernel interface for my kernel. I hit OK and then receive "error: You do not appear to have libc header files installed on your system.  Please install your ditrobutions libc development package" OK again, then "Installation has failed, see the file /var/log/nvidia-installer.log' for details.  You may find suggestions in the Readme available..."  When I acknowledge that, it dumps me back to the command prompt.

I checked the Synaptic Package Manager for that and found nothing, (since I have no idea where else to look. :) )

---

### Post by lian1238 on 2008-10-02
I unknowingly assumed you had build-essential.
```
sudo apt-get install build-essential

```

Note: you can skip the attempt to download a kernel from Nvidia. It'll ask you to compile. Hope you get it this time!

---

### Post by gali98 on 2008-10-02
sudo apt-get install envy-gtk
envy-gtk

simple nice gui that does all that mess for you.
Kory

---

### Post by vitreoushumours on 2008-10-25
Thanks everybody who tried to help me, I dropped my laptop, and grub loader started getting an error 22 and then I ended up restoring my MBR, and now I am waiting for Intrepid Ibex.  (To get my USB wacom digitizer, touch screen, wireless internet, Sound device, and a few other vital parts of my system working took several hours of downloading and recompiling drivers, and such.  I am hoping my hardware will be better supported in the new release.)

---

### Post by gali98 on 2008-10-25
Well that kind of stinks... At least the hardware is still working though :)
Kory

---

