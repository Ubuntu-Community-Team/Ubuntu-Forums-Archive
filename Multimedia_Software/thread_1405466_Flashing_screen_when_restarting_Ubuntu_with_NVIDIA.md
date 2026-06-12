---
title: "Flashing screen when restarting Ubuntu with NVIDIA GeForce"
date: 2010-02-12
forum: Multimedia Software
---

### Post by northd_tech on 2010-02-12
Has anyone else noticed that when they restart Ubuntu, there is a colorful flashing on the screen when exiting the X server?   I first noticed this with the NVIDIA graphics adapter in my HP DV9xxx laptop after the 1st updates after I installed a 64-bit version of Jaunty Jackalope 9.04.

During the restarting, it seems like the text-only  display is trying to draw letters about 2+ inches high on the video display (but gets confused in the process, like something is out of synchronization).  I have disabled both "splash" and "quiet" in my GRUB configuration so that I can see the diagnostic messages when booting (and the startup and running the X server are completely normal).  It seems like this "text" flashing occurs when/where the exit messages would normally be displayed on the screen.

I have tried both the 173 and the [recommended] 180 versions of the proprietary NVIDIA graphics driver, and they both have the problem (but it might not last quite as long with the 173 version).  I do not remember ever seeing this problem using the standard [low-resolution] Linux VESA driver though.

**lspci **identifies my graphics adapter as:

00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)

I am currently running NVIDIA Driver Version: 173.14.16

Does anyone know of any X configuration settings that I can change to make this irritating flashing go away (while hopefully being able to read the verbose diagnostic messages at restart)?

Thanks in advance.

---

### Post by northd_tech on 2010-02-14
Bump for anyone's thoughts/experience with NVIDIA laptops and weirdness restarting video display.

Anyone?  Bueller?

---

### Post by northd_tech on 2010-09-26
Here is an update on this old thread.  I recently had a Live DVD of Ultimate Ubuntu 2.7 (based on Ubuntu 10.04?) in my DVD drive and when I restarted the system, I did not observe this flashing screen problem that I saw repeatedly with ver. 9.04.  I am fairly sure that both 10.04 and 9.04 used the same version of the proprietary NVIDIA driver under Administration > Hardware Drivers, so this appears to be a problem specific to the 9.04 version of Ubuntu and its kernel(s).

I haven't done an upgrade to 10.04 yet though.

---

### Post by northd_tech on 2011-05-01
Bump, and this problem seems less noticeable under the Ubuntu 10.04.2 LTS that I'm currently running than it once was, but it is still more pronounced with my NVIDIA chipset than under Ubuntu 10.04.2 LTS on other [Toshiba] laptops with the integrated Intel? video.

I think it is mostly an NVIDIA driver/X server shutdown issue.

---

### Post by northd_tech on 2011-05-02
Here is a movie that I took of this flashing when restarting my HP laptop with the 'problematic' NVIDIA video interface:

[http://www.filefactory.com/file/cb1ad18/n/HP_Ubuntu10_04shutdownNvidia_4041.MOV](http://www.filefactory.com/file/cb1ad18/n/HP_Ubuntu10_04shutdownNvidia_4041.MOV)

This is in contrast to the same version of Ubuntu (10.04.2 LTS) on a Toshiba laptop with what I believe is an integrated Intel video interface which also shows a flashing at restart (but it is much less colorful than on the HP with NVIDIA):

[http://www.filefactory.com/file/cb1ad38/n/SergioTosh_Intel_UnbuntuShutdown_4042.MOV](http://www.filefactory.com/file/cb1ad38/n/SergioTosh_Intel_UnbuntuShutdown_4042.MOV)

:confused:

EDIT:  Post #3 was probably due to me running off the Live DVD with the Ubuntu VESA video driver.  The problem seems to have resurfaced once I installed Ubuntu 10.04.2 LTS running the NVIDIA proprietary drivers.

---

### Post by northd_tech on 2011-12-06
> **northd_tech said:**
> 
I think it is mostly an NVIDIA driver/X server shutdown issue.

After trying several flavors of Linux while archiving/organizing/converting my Ubuntu stuff from the last 3 years or so, I can state this is DEFINITELY a problem in the NVIDIA graphics driver module shutdown sequence.  I've observed it with the NVIDIA 173, 186, 285, and now 290 driver versions.

I did NOT observe it on the several LiveDVD distros that I tried which used the **nouveau** graphics driver module.

So basically, it appears to be a choice between low resolution and 'proper' shutdown/runlevel 2-4 behavior, or else 'pretty' high-resolution graphics and text with the 'flashing MEGA-text'/text mode synchronization at shutdown problem I have described and observed here for months and on several versions of Linux now.  Both drivers work pretty well within their native resolutions though as far as stability and function, but the NVIDIA is hands-down the 'prettiest.'

I don't recall seeing this problem on my new install of multilib (32- AND 64-bit) Scientific Linux 6.1 running the same NVIDIA hardware on the same laptop with the newest 290 NVIDIA driver though- I'll need to watch closer at shutdown.

This problem has only been observable on those Linuxen which briefly flash the NVIDIA logo at startup (indicating the use of the **nvidia** module rather than the **nouveau** driver), likely excepting the m32/m64-bit SL 6.1 290 driver which I don't have much experience with yet.  (It was just installed this morning).

I'll probably post some of the video that I took this morning of this on different Linux versions here and alert someone from NVIDIA tech support to this thread.

---

### Post by northd_tech on 2011-12-06
> **northd_tech said:**
> Here is an update on this old thread.  I recently had a Live DVD of Ultimate Ubuntu 2.7 (based on Ubuntu 10.04?) in my DVD drive and when I restarted the system, I did not observe this flashing screen problem that I saw repeatedly with ver. 9.04.  I am fairly sure that both 10.04 and 9.04 used the same version of the proprietary NVIDIA driver under Administration > Hardware Drivers, so this appears to be a problem specific to the 9.04 version of Ubuntu and its kernel(s).

I haven't done an upgrade to 10.04 yet though.

That would have been the **nouveau** driver running from the LiveDVD when I didn't observe this problem.  The **nvidia **module showed "shutdown flashing" with all flavors of Ubuntu 10.04 that I tried.

---

