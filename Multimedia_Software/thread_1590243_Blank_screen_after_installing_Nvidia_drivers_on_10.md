---
title: "Blank screen after installing Nvidia drivers on 10.10 RC"
date: 2010-10-07
forum: Multimedia Software
---

### Post by atari130xe on 2010-10-07
Hello forum, I have installed Ubuntu Maverick 10.10 RC in my PC, everything works fine, but after install Nvidia proprietary Graphics driver it boot up on a blank screen (I can hear the login sounds, etc) but screen is absolutely black.

I try to login in recovery mode and check if something is wrong but nothing happens (even adding noveau driver to a blacklist (editing grub))
Now I have re installed Ubuntu 10.04.1 and works fine but I would like to install the 10.10 version, since I have this inconvenience, I cant do it.

My graphic card: Nvidia Gforce 8400GS 256MB Pci Express

Anyone with the same problem?
thanks!

---

### Post by krzysz00 on 2010-10-07
Same here. bump.

---

### Post by atari130xe on 2010-10-07
It's really weird, I used to have problems with the old Ubuntu versions (6.06, etc.) but never with the newest. I would love to know whats wrong in order to install Ubuntu 10.10 final.

---

### Post by guntu on 2010-10-07
I don't get a black screen after installing Nvidia drivers on Ubuntu but my second monitor (TV) turned Black and White after I installed the driver.. 

anyone had this problem?

---

### Post by atari130xe on 2010-10-08
The exact problem I face is that as soon as I install the Nvidia recommended drivers using the "Hardware Driver Manager", I restart the system but it never gets past the login splash screen. After I log in it simply goes to a black screen and sits like this indefinately.

Does anyone know of a particular fix for this problem?

---

### Post by lostfile on 2010-10-11
I have the same problem with Nvidia GForce 230M on ubuntu 10.10 release. I try to reinstall with file *.run (newest driver download from nvidia site) but it's not work.

---

### Post by bhupsi on 2010-10-11
From my understanding the latest Ubuntu does not have support for legacy Nvidia cards.  It really sucks.

---

### Post by theanswriz42 on 2010-10-11
> **lostfile said:**
> I have the same problem with Nvidia GForce 230M on ubuntu 10.10 release. I try to reinstall with file *.run (newest driver download from nvidia site) but it's not work.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/656330](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/656330)

---

### Post by miles916 on 2010-10-11
hi everyone!

im having a similar problem. after everything boots, my monitor tells me "no input" or something to that effect. 

what ive tried: 
installed newest nvidia drivers off nvidia website. 
that got x running, but unfortunately my logviewer is telling me theres a kernal mismatch.

tried to uninstall all nvidia packages, incl. modules etc. reinstalling nvidia-current. to no avail. still cant get a gdm session started. 

is there any way to completely uninstall all nvidia components and whatnot, and perhaps use nouveau instead (couldnt figure out how to reinstall it, as i had uninstalled it for compatibility reasons with the nvidia drivers)?

regards, M.

---

### Post by atari130xe on 2010-10-11
I see Im not alone with this issue. Today I have re installed (from zero) Maverick 10.10, the results: after installing Nvidia Graphics (260.XX version) from Ubuntu repositories, there is a black screen once again... I don know what to do :(

---

### Post by chris3689 on 2010-10-11
I too was having the same problems with the nvidia card.  Even after I reinstalled Maverick, the blank screen problem existed.  What I found helped, is that if I booted into Windows then restarted and booted back into Ubuntu, I could now login and such without encountering a blank screen.  I haven't tried this with the nvidia driver yet, just the fresh install.  I'm installing the driver now, I'll post if I still have the blank screen problem after.  -Chris

---

### Post by luctor on 2010-10-11
I have this problem too.
Only solution I got is to install the drivers from the nvidia website.

---

### Post by coffee412 on 2010-10-11
Ive been running 10.010rc for a little bit and have the nvidia 8400gs card on my system. Did an update just this morning and it borked my video. BLACKSCREEN of death for me too. 

Since I dual boot, I booted up off of my fedora install and mounted the Ubuntu hard drive then edited the /etc/X11/xorg.conf file and changed the driver from nvidia to nv. Then booted back into ubuntu and installed the 173 driver for Ubuntu thru Proprietary drivers.

Rebooted. Worked fine. 

Hope it helps. I havent had a problem since. But getting the updates is a real show stopper!

02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400 GS] (rev a1) (prog-if 00 [VGA controller])

---

### Post by bua882002 on 2010-10-12
Hi everyone.

I've the same problem here, when I install Ubuntu 10.10 the first time, the screen resolution is just 800x600, I've try to install nvidia driver from the Ubuntu repository, after that black screen come, and only termial are there, cannot startx also.

The second time I install, ubuntu installation said that jockey-gtk has got problem. After install done, I reinstall Jockey-gtk and install Nvidia driver 173, and it works, Nvidia driver runs correctly, but after install Vietnamese language and reboot the system, backscreen come again.

I think the problem is the jockey-gtk it's do not recognize the hardware.

My system:
Benq S41 laptop:
Core 2 duo T7250
Geforce 8600M GS

---

### Post by miles916 on 2010-10-12
well, after a fresh install of maverick i installed the 173 drivers through "additional drivers".   seems to be working so far (current drivers end in no input error)...  my problem was actually threefold. 
  

[LIST=1]
[*]grub was broken
[*]nvidia-current was installed
[*]second hdd is failing
[/LIST]

fresh install repaired 1 & 2, 3 im still working on (probably gonna get a replacement for this replacement drive - samsung hdds really suck)

---

### Post by atari130xe on 2010-10-12
Here it is a screenshot of the problem:
(in a fresh installation)

[http://img839.imageshack.us/img839/6474/pantallazok.png](http://img839.imageshack.us/img839/6474/pantallazok.png)
:(

---

### Post by atari130xe on 2010-10-14
bump...

---

### Post by ca1ig0la on 2010-10-14
Ubuntu 10.10
nvidia geforce gt 415M
Fresh install: resolution 800x600

installed: NVIDIA-Linux-x86-260.19.06 driver

after reboot blank screen.
Xorg.0.log says: (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Now I'm running in low graphic mode.

---

### Post by atari130xe on 2010-10-14
I have reported this as a bug on launchpad, I don't know if they will take it as a bug, but Im sure its a bug, untill Ubuntu Lucid Lynx, everything ran very well, now I had to go back to Lucid Lynx, there is no way to get a "normal X" with Nvidia Drivers version 260.19.06 binary (ironically suggested by Ubuntu)... so Im back to 10.04.1 till this thing is fixed.

---

### Post by ca1ig0la on 2010-10-15
Ho do you do the downgrade to the previous release?
Do you have to make a fresh reinstall of the system?
'Cause I've done a fresh install of U10.10 and not an upgrade on th 10.04.

thanks

---

### Post by ncohea on 2010-10-15
I have had difficulties installing 260.19.12 drivers (which run all your cards, by the way). However, fixed the issue, and I have a [HOWTO]("http://ubuntuforums.org/showthread.php?t=1597178") showing what I did on my machine.

---

### Post by ca1ig0la on 2010-10-15
I think that what makes the difference is:

was your nvidia already working decently with your previous driver? Did you make a plain installation of Ubuntu 10.10 or did you upgrade from 10.04?

I think that people who are having troubles and cannot work around it are of the category:
Ubuntu 10.10 plain install + can't get the card decently working with any driver.

Someone correct me if I'm wrong.

---

### Post by ncohea on 2010-10-15
> **ca1ig0la said:**
> I think that what makes the difference is:

was your nvidia already working decently with your previous driver? Did you make a plain installation of Ubuntu 10.10 or did you upgrade from 10.04?

I think that people who are having troubles and cannot work around it are of the category:
Ubuntu 10.10 plain install + can't get the card decently working with any driver.

Someone correct me if I'm wrong.

I started with 10.04 LTS and upgraded to 10.10. nVidia 260.19.06 drivers were working just fine, and I had to do the ghastly work-around I linked you to to get 260.19.12.

---

### Post by theautates on 2010-10-15
I have the same problem after installing the nvidia driver using the 'install drivers' of ubuntu 10.10 netbook remix. 

I have followed this instruction >>>  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
i run the 'install drivers' of ubuntu and activated the nvidia driver. ubuntu downloaded and installs the driver and told me to reboot. I rebooted and all went well, i can even see the splash screen but before i can login the screen went blank and there it is the no gui login. 

I tried "sudo service gdm start" and it said the service is already running i also tried "startx" to start the x server and i got the error "[EE] no screen found"
I have attached the bug report made by the nvidia-bug-report.

im using nVidia Geforce GT 330m and my other system specs are stated below .im pretty comfortable using the terminal and using basic commands. 

Any suggestions and help would be greatly appreciated!

---

### Post by ca1ig0la on 2010-10-15
Plain installation or upgrade from 10.04?

---

### Post by theautates on 2010-10-15
I did a plain installation of ubuntu netbook remix and i just want to install the driver for my gt330m.

---

### Post by ca1ig0la on 2010-10-15
Bad news...
so far I haven't heard about anybody able to get nvidia to work with a plain ubuntu 10.10 installation. If you're lucky it doesn't apply to the netbook version.

---

### Post by atari130xe on 2010-10-15
> **ca1ig0la said:**
> Ho do you do the downgrade to the previous release?
Do you have to make a fresh reinstall of the system?
'Cause I've done a fresh install of U10.10 and not an upgrade on th 10.04.

thanks

I did an Upgrade from 10.04 to 10.10 and didnt work, then I did a fresh install (10.10) the same results...

---

### Post by theautates on 2010-10-16
anyone successful with activating their nvidia driver with netbook remix?

---

### Post by atari130xe on 2010-10-16
Its a bug for sure, I have found a lot of people with the same problem...

---

### Post by lakcaj on 2010-10-16
I was having the same issue.  When the proprietary drivers option came up, it listed both the nvidia-173 and nvidia-current packages, with current being the "recommended" option.  I figured out that I would get a blank screen after reboot if I used the recommended nvidia-current package, but everything would work fine if I installed nvidia-173 instead.  This was on a fresh install of 10.10, not an upgrade.  

So, maybe try a fresh install, upgrade all packages to most recent, reboot, and then manually install the nvidia-173 package from the commandline.  Hopefully this might help someone get their machine running.  It's certainly an issue that I'm surprised made it into the final release of 10.10.

FYI - I have the nVidia Corporation G86 [GeForce 8300 GS] as listed by lspci.

---

### Post by atari130xe on 2010-10-16
Definitely a bug to fix, I wish I could install my Nvidia drivers without such a mess & bad results... it's a pity.

---

### Post by theautates on 2010-10-17
I also hope that this bug would be fix on the next update... Oh well i guess im going to be stucked with my boring/no effects desktop for now :D

---

### Post by atari130xe on 2010-10-18
Anyone lucky on the last days had any success with this issue?

---

### Post by atari130xe on 2010-10-18
Well im lucky Launchpad has taken the problem as a bug, if you are registered on Launchpad just click on the floowing link and then click on "this bug affects you and xx other people" the more people with this problem click on it the soonest will be solved. By the way im using the sugested 173.xx drivers (too old) but at least works by now till its fixed.

here it is the bug link: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/660596")

---

### Post by kabeza on 2010-10-21
Hi guys
I've read the whole thread, because i'm still having same trouble:

How can I install the nvidia driver 173 on my Maverick Meerkat?

I've tried with nvidia-260 from nvidia.com
I've tried with nvidia-current from synaptic

but I'm still getting monitor off when booting

Thanks,

---

### Post by SeePU on 2010-10-21
Install the 260 version.  Make sure all the old stuff is uninstalled and purged if necessary.

Make sure the correct headers are installed and that the glx modules are installed properly.  Follow all the instructions.  You should have a backup xorg.conf file just in case as you have to stop X Window/Server in order to carry out most of the commands.

---

### Post by kabeza on 2010-10-21
ouch.
I've installed 173 version from synaptic and now everything is working fine. I couldn't make compiz to work yet, but at least resolution problem is fixed

---

### Post by atari130xe on 2010-10-21
> **SeePU said:**
> Install the 260 version.  Make sure all the old stuff is uninstalled and purged if necessary.

Make sure the correct headers are installed and that the glx modules are installed properly.  Follow all the instructions.  You should have a backup xorg.conf file just in case as you have to stop X Window/Server in order to carry out most of the commands.

I have tried many things (erasing Nouveau drivers, all the Nvidia stuff, etc and re installing the 260 versions (260.19.06 & 12) and the problem remains, it is kinda frustrating because till 10.04 everything relating to Video worked out of the box and now it´s like going back to ubuntu 5.04 :( by the way Geforce 8400GS PCIe its only 2 years old so it should not be a hardware issue...

---

### Post by SeePU on 2010-10-21
> **atari130xe said:**
> I have tried many things (erasing Nouveau drivers, all the Nvidia stuff, etc and re installing the 260 versions (260.19.06 & 12) and the problem remains, it is kinda frustrating because till 10.04 everything relating to Video worked out of the box and now it´s like going back to ubuntu 5.04 :( by the way Geforce 8400GS PCIe its only 2 years old so it should not be a hardware issue...Nouveau drivers are the open source Nvidia driver.   They shouldn't be a problem.  It's the previous Nvidia binary drivers and associated files that would conflict or cause you problems.  Don't use the Ubuntu restricted hardware driver install method.  Install the 'Nvidia way' to get it done.   It's a bit more work but done right, it should work.  Look in synaptic and do a search for 'nvidia.'  See if there's anything still installed and remove/uninstall it.  Then check the linux headers for the nvidia files are also removed.  Reboot with VESA drivers and try again.  

Do a search for the latest install method for installing the Nvidia driver the 'Nvidia way' and add "+ Ubuntu 10.10' or 'Debian' (it's basically the same process).  I forget all the steps as I haven't done it lately but it involves having modules, glx and matched linux kernel headers with the corresponding Nvidia version files.

When starting from scratch again, with the previous version driver and associated files removed, you would download 260 (unless you have it already) and then stop X.  You are in full-screen terminal (basically) and then start the process from there - with associated linux headers and glx modules installed.  Then you run the Nvidia installer and it checks that your lib files, headers etc. are all matched together etc.  If enough criteria is met, it runs the installer and installs the latest (260) driver.

---

### Post by atari130xe on 2010-10-21
> **SeePU said:**
> Nouveau drivers are the open source Nvidia driver.   They shouldn't be a problem.  It's the previous Nvidia binary drivers and associated files that would conflict or cause you problems.  Don't use the Ubuntu restricted hardware driver install method.  Install the 'Nvidia way' to get it done.   It's a bit more work but done right, it should work.  Look in synaptic and do a search for 'nvidia.'  See if there's anything still installed and remove/uninstall it.  Then check the linux headers for the nvidia files are also removed.  Reboot with VESA drivers and try again.  

Do a search for the latest install method for installing the Nvidia driver the 'Nvidia way' and add "+ Ubuntu 10.10' or 'Debian' (it's basically the same process).  I forget all the steps as I haven't done it lately but it involves having modules, glx and matched linux kernel headers with the corresponding Nvidia version files.

When starting from scratch again, with the previous version driver and associated files removed, you would download 260 (unless you have it already) and then stop X.  You are in full-screen terminal (basically) and then start the process from there - with associated linux headers and glx modules installed.  Then you run the Nvidia installer and it checks that your lib files, headers etc. are all matched together etc.  If enough criteria is met, it runs the installer and installs the latest (260) driver.

Thanks for the advice, already know how to install Nvidia drivers "old style" but even using this mode, it does not solve the problem in my PC, everything removed related to Nvidia from my sys but still does not work. Nouveau are ok but they dont give 3D acceleration at least in my pc, I have found that we are hundred of people with the same problem, something is wrong with the latest xorg file; Im not a programmer so I can´t understand what´s wrong. Even on Ubuntu 10.04 Nvidia Driver 260.19.06 causes the same mess in my system, I hope it can be fixed soon.

---

### Post by kabeza on 2010-10-21
don't know if this helps, but I installed nvidia version 173 from synaptic and all went ok (no GL nor acceleration nor 3d) but at least desktop shows fine and not 640*480

I also own a PCIe GForce 8400GS and don't think this board is the problem because I could run everything with 3d, etc. smoothly in 10.04

---

### Post by SeePU on 2010-10-21
> **atari130xe said:**
> Thanks for the advice, already know how to install Nvidia drivers "old style" but even using this mode, it does not solve the problem in my PC, everything removed related to Nvidia from my sys but still does not work. Nouveau are ok but they dont give 3D acceleration at least in my pc, I have found that we are hundred of people with the same problem, something is wrong with the latest xorg file; Im not a programmer so I can´t understand what´s wrong. Even on Ubuntu 10.04 Nvidia Driver 260.19.06 causes the same mess in my system, I hope it can be fixed soon.Yes, the Nouveau drivers are reverse-engineered by a small group of developers so the development is slow but they do well considering they have no help.  3D acceleration is only available via the proprietary drivers so no choice but to install the binary driver.

I haven't read that ver. 260 is not working for recent cards unless it's the brand new Fermi and then it's usually something to do with Compiz or having desktop effects enabled.  Also, I read that VDPAU isn't working properly with the new driver or video cards at the moment.

I'm not sure what is going wrong on your end but you might want to check out the website NVNEWS and see if there is anything interesting there that might help.

I haven't installed the latest driver yet but I've installed Nvidia drivers on more than one distro and many times so I know how it is having that darn black screen.  It's usually a mis-step or omitted step.  It seems if there is just one step not done, the Installer will not compile everything properly and the result is the frustrating black screen.  I didn't think the newest Nvidia driver is so buggy that you would keep getting a black screen.  There would be a lot of discussions on that.  I suspect there is some command not being included so that the installer is missing required info in order to do the compile/matching.

---

### Post by atari130xe on 2010-10-21
> **kabeza said:**
> don't know if this helps, but I installed nvidia version 173 from synaptic and all went ok (no GL nor acceleration nor 3d) but at least desktop shows fine and not 640*480

I also own a PCIe GForce 8400GS and don't think this board is the problem because I could run everything with 3d, etc. smoothly in 10.04

Hola Kabeza ;) I have tried version 173 but if you try to use any dock its a pain (traling) so I prefer to find a better solution.

---

### Post by atari130xe on 2010-10-21
> **SeePU said:**
> Yes, the Nouveau drivers are reverse-engineered by a small group of developers so the development is slow but they do well considering they have no help.  3D acceleration is only available via the proprietary drivers so no choice but to install the binary driver.

I haven't read that ver. 260 is not working for recent cards unless it's the brand new Fermi and then it's usually something to do with Compiz or having desktop effects enabled.  Also, I read that VDPAU isn't working properly with the new driver or video cards at the moment.

I'm not sure what is going wrong on your end but you might want to check out the website NVNEWS and see if there is anything interesting there that might help.

I haven't installed the latest driver yet but I've installed Nvidia drivers on more than one distro and many times so I know how it is having that darn black screen.  It's usually a mis-step or omitted step.  It seems if there is just one step not done, the Installer will not compile everything properly and the result is the frustrating black screen.  I didn't think the newest Nvidia driver is so buggy that you would keep getting a black screen.  There would be a lot of discussions on that.  I suspect there is some command not being included so that the installer is missing required info in order to do the compile/matching.

You know? I totally agree, there is something missing during the install, if not it should work perfect like in the last versions.

take a look to the release highlights on Nvidia site:

Linux Display Driver - x86
 
 

Version: 260.19.12 
Certified Release Date: 2010.10.13
Operating System: Linux
Language: English (U.S.)
File Size: 27.1 MB

>     * Added support for the following GPUs:
            GeForce GTS 450
            GeForce GTX 460M
            GeForce GT 415M
            GeForce GT 425M
            GeForce GT 420M
            GeForce GT 435M
            Quadro 2000
            Quadro 600 Stopped installing OpenGL, VDPAU, CUDA, and OpenCL header files with the driver. Those interested in these files can get them from their Linux distributions' packages, where available, or upstream from:
    *
            OpenGL header files (gl.h, glext.h glx.h, glxext.h):
                        [http://www.opengl.org/registry/](http://www.opengl.org/registry/)

            VDPAU header files (vdpau.h and vdpau_x11.h):
                        [http://freedesktop.org/wiki/Software/VDPAU](http://freedesktop.org/wiki/Software/VDPAU)

            CUDA and OpenCL header files (cuda.h, cudaGL.h, cudaVDPAU.h,
                                cl.h, cl_gl.h, cl_platform.h):
                        [http://developer.nvidia.com/object/gpucomputing.html](http://developer.nvidia.com/object/gpucomputing.html)

      Note that while libvdpau.so is still included in 260.xx drivers, it will be removed from a future release series in early 2011. Distributors are encouraged to package libvdpau.so from [http://freedesktop.org/wiki/Software/VDPAU](http://freedesktop.org/wiki/Software/VDPAU)

      Note that [http://www.opengl.org/registry/](http://www.opengl.org/registry/) does not presently provide gl.h or glx.h.  Until that is resolved, NVIDIA's OpenGL " header files can still be chosen, through the “--opengl-headers” installer option.
    * Fixed the CustomEDID X configuration option so that it can handle EDID files from Linux procfs; e.g., /proc/acpi/video/IGPU/LCD0/EDID.
    * Fixed an interaction problem with a change in X server behavior that caused slow text rendering on X.Org xserver 1.9.
    * Enhanced VDPAU to support interop with CUDA and OpenGL when Xinerama is active.
    * Fixed a bug in VDPAU that prevented temporal-spatial de-interlacing from operating when temporal de-interlacing was not also enabled.
    * Added support for configuring the dithering depth used when driving a flat panel with a GeForce 8 family or Quadro 4600/5600 or
      newer GPU. See the "Dithering Controls" in the Flat Panel page in nvidia-settings.
    * Added support for the nvcuvid API.

      nvcuvid provides a mechanism for decoding video and exposing the surfaces to CUDA, allowing applications to perform custom processing of the video. nvcuvid is primarily targeted at transcoding and video- processing applications. nvcuvid was already available on other platforms.

      By default, nvidia-installer places headers in /usr/include/nvcuvid, and library in /usr/lib/libnvcuvid.so, or in the appropriate library path for your system.
    * Fixed a bug in VDPAU that could cause a "display preemption" when toggling MPlayer to full-screen the first time.
    * Added OpenGL 4.1 support for Quadro Fermi, GeForce GTX 4xx, and later GPUs.
    * Enhanced VDPAU to fully support Xinerama.
    * Fixed a bug in the X driver that prevented operation of Xinerama when using multiple NVIDIA GPUs from different major hardware generations
      on X with ABI 4 or greater.
    * Fixed a bug in the OpenGL driver's Xinerama support.

      Rendering should have ocurred to all physical X screens driven by an NVIDIA GPU compatible with the NVIDIA GPU driving physical X screen 0. However, if some physical X screen did not satisfy that requirement, then not only would that physical X screen not be rendered to (as expected), but also all physical X screens with a higher number would not be rendered to (which was unexpected).
    * Added GPU "Processor Clock" reporting to the nvidia-settings PowerMizer page.
    * Implemented support for SLI Mosaic Mode on Quadro FX 5800 and Quadro Fermi and newer Quadro GPUs.
    * Enhanced the VDPAU overlay-based presentation queue to allow it to be used when SLI is active, and in some cases when the X composite extension is enabled. See the README for further details.
    * Added support for configuring the dithering mode used when driving a flat panel with a GeForce 8 family or Quadro 4600/5600 or newer GPU.See the "Dithering Controls" in the Flat Panel page in nvidia-settings.
    * Added unofficial GLX protocol support (i.e., for GLX indirect rendering) for the following OpenGL extensions:
            GL_EXT_texture_integer
            GL_ARB_stencil_two_side
            GL_EXT_transform_feedback2
            GL_NV_transform_feedback2
            GL_NV_conditional_render Added GLX protocol support (i.e., for GLX indirect rendering) for the following OpenGL extensions:
    *
            GL_NV_point_sprite
            GL_EXT_stencil_two_side
            GL_EXT_point_parameters
            GL_ARB_transpose_matrix
            GL_EXT_framebuffer_blit
            GL_EXT_framebuffer_multisample GLX protocol for the following OpenGL extension is promoted from unofficial GLX ptotocol to ARB approved GLX protocol:
    *
            GL_EXT_geometry_shader4
            GL_ARB_shader_objects
            GL_ARB_vertex_shader
            GL_ARB_fragment_shader Added support for configuring individual displays as any eye in passive stereo mode "4" when using TwinView or SLI Mosaic through extensions to the MetaMode syntax.
  * * Added ColorSpace and ColorRange features for HDMI. These give the ability to output YUV over HDMI and select full/reduced color range on RGB over HDMI. ColorSpace and ColorRange are X Configuration options and can be changed dynamically through nvidia-settings.

Note that many Linux distributions provide their own packages of the NVIDIA Linux Graphics Driver in the distribution's native package management format. This may interact better with the rest of your distribution's framework, and you may want to use this rather than NVIDIA's official package.

Also note that SuSE users should read the SuSE NVIDIA Installer HOWTO before downloading the driver.

Installation instructions: Once you have downloaded the driver, change to the directory containing the driver package and install the driver by running, as root, sh ./NVIDIA-Linux-x86-260.19.12.run

One of the last installation steps will offer to update your X configuration file. Either accept that offer, edit your X configuration file manually so that the NVIDIA X driver will be used, or run nvidia-xconfig

Note that the list of supported GPU products is provided to indicate which GPUs are supported by a particular driver version. Some designs incorporating supported GPUs may not be compatible with the NVIDIA Linux driver: in particular, notebook and all-in-one desktop designs with switchable (hybrid) or Optimus graphics will not work if means to disable the integrated graphics in hardware are not available. Hardware designs will vary from manufacturer to manufacturer, so please consult with a system's manufacturer to determine whether that particular system is compatible.

See the README for more detailed instructions.
GeForce 400 series:
GTX 460, GTX 470, GTX 480, GTX 465, GTS 450

GeForce 400M series:
GTX 480M, GT 425M, GT 435M, GTX 460M, GT 420M, GT 415M

GeForce 300 series:
GT 330, GT 320, GT 340

GeForce 300M series:
GT 330M, GTS 350M, GT 325M, GT 320M, GTS 360M, 310M, 305M, GT 335M

GeForce 200 series:
GTS 240, G210, GTX 285, GTX 280, GT 240, GTX 260, GT 230, GTS 250, GTX 275, GT 220, GTX 295, 205

GeForce 200M series:
GTX 280M, GTS 250M, GTS 260M, GTX 285M, G210M, GT 230M, GT 220M, GT 240M, GTX 260M

GeForce 100 series:
GT 120, G 100, GT 130, GT 140

GeForce 100M series:
GTS 160M, G 103M, G 105M, G 102M, GT 120M, GT 130M, GTS 150M, G 110M

GeForce 9 series:
9800 GTX/GTX+, 9600 GT, 9400, 9800 GX2, 9400 GT, 9200, 9300 GE, 9600 GSO 512, 9100, 9300 SE, 9600 GS, 9800 GT, 9500 GS, 9300, 9600 GSO, 9300 / nForce 730i, 9500 GT, 9650 S, 9800 GTX+, 9300 GS

GeForce 9M series:
9700M GT, 9700M GTS, 9600M GT, 9650M GT, 9800M GTX, 9500M G, 9200M GS, 9800M GT, 9400M, 9300M GS, 9100M G, 9650M GS, 9400M G, 9600M GS, 9800M GTS, 9500M GS, 9300M G, 9800M GS

GeForce 8 series:
8800 GT, 8300 GS, 8800 Ultra, 8400 SE, 8300, 8100 / nForce 720a, 8800 GTX, 8800 GTS, 8800 GTS 512, 8400 GS, 8400, 8500 GT, 8800 GS, 8200, 8600 GS, 8600 GTS

GeForce 8M series:
8400M GS, 8400M G, 8600M GT, 8800M GTS, 8400M GT, 8200M G, 8700M GT, 8600M GS, 8800M GTX

GeForce 7 series:
7000M /NVIDIA nForce 610M, 7800 SLI, 7800 GT, 7300 GS, 7050 / NVIDIA nForce 610i, 7150M /NVIDIA nForce 630M, 7300 GT, 7300 LE, 7900 GS, 7900 GT/GTO, 7650 GS, 7800 GTX, 7500 LE, 7100 GS, 7900 GTX, 7350 LE, 7600 GS, 7025 / NVIDIA nForce 630a, 7300 SE / 7200 GS, 7050 / NVIDIA nForce 630i, 7150 / NVIDIA nForce 630i, 7050 / nForce 620i, 7800 GS, 7950 GX2, 7050 PV / NVIDIA nForce 630a, 7600 GT, 7100 / NVIDIA nForce 620i, 7100 / NVIDIA nForce 630i, 7600 LE, 7950 GT

GeForce Go 7 series:
Go 7200, Go 7600 GT, Go 7900 GS, Go 7300, Go 7700, Go 7800, Go 7600, Go 7950 GTX, Go 7400, Go 7800 GTX

GeForce 6 series:
6600 GT, 6100, 6800, 6600 VE, 6610 XL, 6600, 6800 GT, 6600 LE, 6200 A-LE, 6200 LE, 6800 GS, 6800 XT, 6150, 6800 Ultra, 6700 XL, 6100 nForce 400, 6800 XE, 6150SE nForce 430, 6800 LE, 6200, 6200SE TurboCache, 6250, 6100 nForce 420, 6500, 6100 nForce 405, 6200 TurboCache, 6150 LE

Quadro series:
4000, 2000, 600, 5000, 6000

Quadro FX series:
FX 5500, FX 3400/4400, FX 1800, FX 370, FX 380 LP, FX 1700, FX 370 Low Profile, FX 3800, FX 570, CX, FX 560, FX 5600, FX 580, FX 4500 X2, FX 4500, FX 1500, FX 380, FX 5800, FX 540, FX 4700 X2, FX 1400, FX Go1400, FX 4600, FX 550, FX 3450/4000 SDI, FX 3700, FX 3500, FX 4000, FX 350, FX 4800

Quadro FX Notebook series:
FX 360M, FX 380M, FX 770M, FX 3800M, FX 1800M, FX 1500M, FX 2500M, FX 1700M, FX 3700M, FX 540M, FX 3600M, FX 370M, FX 570M, FX 560M, FX 2700M, FX 2800M, FX 350M, FX 1600M, FX 880M

Quadro NVS series:
NVS 420, NVS 210S / 6150LE, NVS 285, NVS 295, NVS 450, NVS 440, NVS 290

Quadro NVS Notebook series:
NVS 110M, NVS 320M, NVS 510M, NVS 160M, NVS 130M, NVS 150M, NVS 120M, NVS 135M, NVS 140M

Quadro Plex series:
Model IV, D Series, Model II

Quadro G-Sync series:
G-Sync II

Quadro SDI series:
Quadro SDI

1U System:
Tesla M2070, Tesla S2050, T10 Processor, Tesla M1060, Tesla M2050, Tesla M2070-Q

ION series:
ION LE, ION

GPU Computing Processor series:
Tesla C2070, Tesla C2050, Tesla C870, Tesla C1060




---

### Post by SeePU on 2010-10-22
So, you tried steps like what's in this thread?:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9997642](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9997642)

[http://ubuntuforums.org/showthread.php?p=9988389](http://ubuntuforums.org/showthread.php?p=9988389)

[http://www.ubuntugeek.com/how-to-install-nvidia-260-19-12-drivers-in-ubuntu-10-1010-04-using-ppa.html](http://www.ubuntugeek.com/how-to-install-nvidia-260-19-12-drivers-in-ubuntu-10-1010-04-using-ppa.html)

P.S.  When you try to install it and get the black screen, have the Ubuntu 10.10 Live CD handy and reboot your machine with it in the burner.  When the Live version boots up, you can recover your system by copying your xorg.conf.bak (make a backup copy of the xorg.conf file that works enough to have a normal screen) or whatever it got named to the 'screwed up' current one which will get your xorg configuration file back to the previous which allows you to try again.  It's a nuisance but it is relatively straight forward and works.

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

If you didn't create a backup of a 'working' xorg.conf file, removing the 'non-working' xorg.conf file should give you VESA drivers assuming you disabled or blacklisted nouveau drivers (I think?).

---

### Post by atari130xe on 2010-10-23
> **SeePU said:**
> So, you tried steps like what's in this thread?:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9997642](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9997642)

[http://ubuntuforums.org/showthread.php?p=9988389](http://ubuntuforums.org/showthread.php?p=9988389)

[http://www.ubuntugeek.com/how-to-install-nvidia-260-19-12-drivers-in-ubuntu-10-1010-04-using-ppa.html](http://www.ubuntugeek.com/how-to-install-nvidia-260-19-12-drivers-in-ubuntu-10-1010-04-using-ppa.html)

P.S.  When you try to install it and get the black screen, have the Ubuntu 10.10 Live CD handy and reboot your machine with it in the burner.  When the Live version boots up, you can recover your system by copying your xorg.conf.bak (make a backup copy of the xorg.conf file that works enough to have a normal screen) or whatever it got named to the 'screwed up' current one which will get your xorg configuration file back to the previous which allows you to try again.  It's a nuisance but it is relatively straight forward and works.

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

If you didn't create a backup of a 'working' xorg.conf file, removing the 'non-working' xorg.conf file should give you VESA drivers assuming you disabled or blacklisted nouveau drivers (I think?).

Blacklisting Nouveau drivers didnt work to me, I gave a try even installing Debian Squeeze (not very easy as ubuntu) and I had no luck...

---

### Post by kabeza on 2010-10-25
This new driver published from nvidia on Oct. 18, solved my problems, but compiz and graphic related stuff work slower

[http://www.nvidia.es/object/linux-display-ia32-173.14.28-driver-es.html](http://www.nvidia.es/object/linux-display-ia32-173.14.28-driver-es.html)

---

### Post by atari130xe on 2010-10-25
> **kabeza said:**
> This new driver published from nvidia on Oct. 18, solved my problems, but compiz and graphic related stuff work slower

[http://www.nvidia.es/object/linux-display-ia32-173.14.28-driver-es.html](http://www.nvidia.es/object/linux-display-ia32-173.14.28-driver-es.html)

Im back to Lucid Lynx till the problem is fixed in Maverick, it's a pity...

---

### Post by jadonchristensen on 2010-11-14
I have a Geforce VGA MSI N240GT-MD1G/D5 GT240 1GB and I get a black screen or a screen that freezes and shows frozen pixels after a clean install of 10.10 32 bit version. I can't even install using the GUI, because it freezes, I had to use the Alternate CD to install, same black screen when the install finishes.

---

### Post by sdf1984 on 2010-11-23
I have not been able to run the GUI from a new install since 9.10
My Nvidia GForce 8400GS will not boot to desktop after fresh install. I can't even get to the point where i can choose the non-open drivers.
My method has been to install 9.10 install restricted drivers, upgrade to 10.04, then upgrade to 10.10, then everything works just fine. My system is Gigabyte EP45-UD3L, Intel Core 2 Duo E6850, 2GB DDR2, GForce 8400GS, LG Flatron W1952TQ 19" on DVI. This is crazy. All I can think is XORG must have broken something.
By the, running live cd works just fine, it is only at rebuilt does my screen go into power saving mode.
I am running NVIDIA Driver Version: 260.19.06 without any trouble, as long as I follow the crazy upgrade process.

---

### Post by jadonchristensen on 2010-11-24
> **jadonchristensen said:**
> I have a Geforce VGA MSI N240GT-MD1G/D5 GT240 1GB and I get a black screen or a screen that freezes and shows frozen pixels after a clean install of 10.10 32 bit version. I can't even install using the GUI, because it freezes, I had to use the Alternate CD to install, same black screen when the install finishes.

I fixed my issue by doing the following.
-select Recovery Mode from the Boot menu
-select Failsafex Graphics mode
-select ok
-I was then able to login using the GUI and installed the restricted Geforce drivers (System > Administration > Additional Drivers)
-everything works now

---

### Post by fudoki on 2010-12-04
> **krzysz00 said:**
> Same here. bump.

Same here with Official Release running a GeForce 7600GT, got "Out of Range" error on my 1600x1050 Asus LCD monitor.  Hooked up a Gateway Diamond Scan, same error, then tried a Sony Trinitron 21in. - SAME ERROR!!  Insane!  The Sony will run at amazing high configs.

The problem - faulty "auto-detect" and no xorg.conf file is generated, at least not one that is usable ("Default" everything).

Here is a complete Debian generated xorg.conf file that will fix your problem, once you edit in the values for your monitor.  I had to re-install and copy the backup from my Debian "Lenny" install I upgraded from onto a local partition, since you cannot mount a memory stick or DVD while in "Root Maintenance mode", at least I couldn't, but I only have about 28 years experience with Unix and Linux...

After you get this file copied to a handy place, whilst still running the generic "nv"driver, bring up Synaptec and search on "nvidia", select the "173" top choices, good for GeForce 5 to 8 series, inclusive.  Hit "apply"and let Synaptec build and install the driver.  Now copy the xorg.conf file to /etc/X11 and when you reboot everything will look, and run, just great.  You might want to make a backup file, or leave the original copy in place, just in case of any Windows-like "automatic" behaviour... ; ) 

-----------------------------------------

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (randy@juliet2)  Tue Jun 24 10:44:02 PDT 2008

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (randy@juliet2)  Fri Sep  5 15:03:39 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
    FontPath 	"/usr/share/fonts/truetype/ttf-larabie-uncommon"
    FontPath 	"/usr/share/fonts/truetype/ttf-larabie-straight"
    FontPath 	"/usr/share/fonts/truetype/ttf-larabie-deco"
    FontPath 	"/usr/local/share/fonts"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Asus"
    ModelName      "ACI ASUS VW223"
    DisplaySize     480    315
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"

# Removed Option "metamodes" "1280x1024_60 +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "TwinView" "0"
    Option         "metamodes" "1680x1050 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

----------------------------------------------------

*End of Message*

---

### Post by bhavesh d linux lover on 2010-12-06
i had the same problem when i installed the current version of nvidia 8400gs aftre rebooting i land up with a blank screen moniter says 'no signal'  i tried 4-5 time i tried to install ubuntu again n again everytime failed in installing the drivers 
but i got the solution after long hard work on it.....
its much simple the solution was in front of my eyes but i did nt used...
that is i tried to the 173 version...... 
and know its working fine with me with 3d effects and compiz....
love ubuntu its awsome ......
i m sure this will help....
my system;intel dual-core, nvidia 8400gs, lg flatorn w1942t 19" screen, 2gb ram, 1tb hard disk,
jus try to install 173 version..... it will work........
i garantiee.......

---

### Post by johnthei on 2010-12-09
I still cannot get nvidia to work on 10.10. I dual boot into 10.4 where it works fine.

here is what i find I have. no idea which of the numerous suggestions for nvidia will work, tried a few to no avail.

I am thinking of putting in another video card I have, to see if that helps.



02:00.0 VGA compatible controller:nVidia Corporation NV18 [GeForce4 MX - nForce GPU] {rev a3}

---

### Post by vangop on 2010-12-10
HP 8440p, nvidia 3110m. x64
1. Install from alternative CD, this will fix the installation graphics problems.
2. upon the 1st boot edit boot options. Then change grub config to have nomodeset. [More info]("http://blog.triumphovermadness.com/2010/05/ubuntu-1004-lts-on-hp-elitebook-8440p.html")

3. Install nvidia drivers from hardware drivers.

All works fine afterwards. The only problems so far:
1. a lot of NVRM: os_raise_smp_barrier(), invalid context! in syslog
2. I changed power options to  blank the screen when I close the lid to save battery. But when I open the lid, the screen is blank and nothing makes it work. I have to switch virtual terminals several times to make it work again.

---

### Post by atari130xe on 2010-12-22
> **vangop said:**
> HP 8440p, nvidia 3110m. x64
1. Install from alternative CD, this will fix the installation graphics problems.
2. upon the 1st boot edit boot options. Then change grub config to have nomodeset. [More info]("http://blog.triumphovermadness.com/2010/05/ubuntu-1004-lts-on-hp-elitebook-8440p.html")

3. Install nvidia drivers from hardware drivers.

All works fine afterwards. The only problems so far:
1. a lot of NVRM: os_raise_smp_barrier(), invalid context! in syslog
2. I changed power options to  blank the screen when I close the lid to save battery. But when I open the lid, the screen is blank and nothing makes it work. I have to switch virtual terminals several times to make it work again.

I still didnt try this one, but its really frustrating to see that a GPU not that old is having these problems.

---

### Post by malypetu on 2011-02-02
Guys
Commiserations on the problem and I'm sorry to say that I am on the same boat.  I have a NVIDIA GeForce 8500 GT (what a force) and at boot time screen goes black and never gets to splash screen for login.
I have to resort to default graphic mode and all work fine except of course that I got a GPU not in use.
I have tried pretty much all suggestions available but all fail miserably into the same black screen, forcing me back to default.
Hope somebody can produce or point us to a procedure that assess the situation and offer step by step instructions on how to fix it.

Cheers

---

### Post by bill 974 on 2011-02-03
Same problem with my nvidia 8400M GS for most than a year. After spending hours of search and compiling different answers i found a solution that worked for me in my new install of kubuntu 10.10. i think it will work also in ubuntu. 
First to begin if you are having problem installing the OS because of the black screen click F6 and check "nomodeset". This 'll allow you to install but by first booting after a fresh install, because of the black screen again, you have to edit your grub by pressing "e" when the grub list appears. You 'll see some parameters and after the the words "quit slash" add "nomodeset", press Ctrl+X and you can boot normally.

After installing the nvidia drivers, i faced again the same problem but this time nothing from above helped. So, you have to:

[LIST=1]
[*]Run the recovery mode and wait until the recovery menu appears
[*]Scroll down to the last option and choose the "root" option
[*]type "cd /etc/X11"
[*]Now you need to edit the xorg.conf file. By kubuntu type "nano xorg.conf" and if i am not mistaken in ubuntu works to.
[*]Go down in section "Device" and change the Driver from "nvidia" to "nv". This is the most critical step.
[*]Save it and then type "reboot"
[/LIST]
This solved my problem. let me know if it helped you too.
Sorry for my mistakes in English.
):P

---

### Post by malypetu on 2011-02-03
Hey Bill
Thanks for the tip I'll give it a shot and report back. 

Cheers
PS You English is quite good and your ideas are well constructed.

---

### Post by krzysz00 on 2011-02-03
Here's the solution!


[LIST=1]
[*]Remove ALL nvidia drivers
[*]Install nvidia-173
[*]It should work.
[/LIST]

---

### Post by kabeza on 2011-02-04
> **krzysz00 said:**
> Here's the solution!


[LIST=1]
[*]Remove ALL nvidia drivers
[*]Install nvidia-173
[*]It should work.
[/LIST]


You're right, but nvidia-173 doesn't work with compiz. I mean, it works, but the PC becames VERY SLOW

---

### Post by wconrad on 2011-02-09
I have been battling this problem for weeks.  Here's what finally worked for me.

First, I went to the nVidia web site and downloaded the specific driver for my hardware. This is the one that worked for me.
[http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html](http://www.nvidia.com/object/linux-display-amd64-256.53-driver.html)

Then, I rebooted my laptop and held shift to choose boot options (you may need something different to get your boot options). I then selected recovery mode. In the recovery mode menu, I chose to use the command line as root. Once I got the command line, I navigated to my downloaded driver and installed it.  here's the code I used.

cd /home/wconrad/Downloads
sudo sh NVIDIA-Linux-x86_64-256.53.run

I then followed the installation instructions (for instance it told me to switch to runlevel 3 and I did so).

After reboot I got the 3d hardware acceleration and all the other speed my graphics driver brings.

Hope that works.

Will

---

### Post by BicyclerBoy on 2011-02-10
If you read all the info & instruction so on the nvidia website you can't go wrong..

The biggest problem with the nvidia install process is the requirement for kernel headers & then the use of console login..

Using "nv" instead of "nvidia" just gives you the nouveau driver 2d no 3d driver..

The other poster with xorg.conf file attached needs to remove the modules section.
You don't normally need a modules section in the xorg.conf

Old xorg.conf files can contain entries that stop the driver loading.
Sometimes backup & deleting the existing xorg.conf & rebooting is a fix.

The best way to get the driver is a 3rd party pre-compiled package...

---

### Post by kabeza on 2011-02-10
> **BicyclerBoy said:**
> ...The other poster with xorg.conf file attached needs to remove the modules section.
You don't normally need a modules section in the xorg.conf

Old xorg.conf files can contain entries that stop the driver loading.
Sometimes backup & deleting the existing xorg.conf & rebooting is a fix.

The best way to get the driver is a 3rd party pre-compiled package...


3rdparty pre-compiled package? for example from where?

PS: I just would like to know why the same driver worked perfectly with 10.04 and why is just giving so much headaches with latest 10.10

---

### Post by marve12le on 2011-02-10
From my understanding the latest Ubuntu does not have support for legacy Nvidia cards.  It really sucks.

---

### Post by BicyclerBoy on 2011-02-11
But you can get all the old drivers from nvidia...

Anything before the 8000 series is basically useless anyway except for a server box..

The new driver still supports back to FX & 6000s..
I would prefer they dropped old GPU support if it made the driver faster..

Remember, it could be a whole lot worse like the ATI situation..

3rd party ppa's 
be very very very careful with xorg updates..stick to std *buntu repos for that.
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

The driver install uses Ubuntu scripts; something in these, including preference for nouveau driver, must be the root cause of the problems.

---

### Post by malypetu on 2011-02-22
Hi Again
I have try the NV trick, unfortunately it still doesn't work.  Not only that but now I've got a new problem. When I reconfigure th default graphics, after the computer goes to SUSPEND it can't recover from there taking back to the evil Black Screen.  I can hear the HDD spinning but nothing on the screen.

Cheers

---

### Post by malypetu on 2011-02-23
Hi Guys
Again I've try the installation by first uninstalling all NVIDIA drivers.
After that I've try the NVIDIA-Linux-x86-173.14.27-pkg1.run as somebody mentioned is a good one to try.
I have recompiled for the kernel and all seems to go ok.  Only after installation is completed, when restarting the computer it gets the Ubuntu splash screen then screen goes black.
Hope somebody is got some suggestions.

Cheers

My xorg.conf content is as follows:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder75)  Tue Jul 13 21:08:53 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
EndSection


Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
   Monitor        "Monitor0"
   DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by BicyclerBoy on 2011-02-23
The entry
Driver         "nv"

makes xorg load the nouveau driver (or may be the free vesa) not the nvidia ..

The 10.10 kernel needs the nouveau kernel module blacklisted.
The old nvidia driver installer scripts will not do the blacklisting AFAIK.

---

