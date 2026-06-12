---
title: "[HOWTO] Install NVIDIA drivers manually on Lynx"
date: 2010-04-30
forum: Multimedia Software
---

### Post by AndyBoy_LV on 2010-04-30
Well, i am one of those users who never install Nvidia drivers from repository, but manually - by downloading from Nvidia`s website. It was never a pain in the rear on previous Linux distros (including Karmic), but i failed to do so on Lynx. Whenever i tried to install it, i got an error: ```
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
```

I read somewhere that they changed the way nvidia drivers get installed on Lynx (correct me if i`m wrong), so it took me some time to figure out how to do that. So, here is the guide:


1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin: (i use gedit for text file editing)```
sudo gedit /etc/modprobe.d/blacklist.conf
```
3) Add these lines and save: 
```

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```
4) Uninstall any previously installed Nvidia drivers: 
```
sudo apt-get --purge remove nvidia-* 
```
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
8) Install drivers ```
sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run
```
9) Start GDM ```
sudo service gdm start
```

Enjoy ;)

P.S. if you are having trouble with my method, there is an [updated one]("http://ubuntuforums.org/showpost.php?p=9211609&postcount=35"), posted by **trespuntos** - maybe it will solve your problem.

---

### Post by dino99 on 2010-04-30
nice howto

if you have the choice, prefer packages from ubuntu repo (less troubles) as they have been fine tuned by ubuntu devs.

---

### Post by AndyBoy_LV on 2010-04-30
But they aren`t always up-to-date ;)

---

### Post by pslim940 on 2010-04-30
Thanks for this.  This fixed my problems booting into "low-graphics" mode every 2 or 3 boots.

---

### Post by Linuxforall on 2010-04-30
Many thanks, I tried blacklisting nouveau and it didnt work. Your method worked out well.

---

### Post by Linuxforall on 2010-04-30
> **AndyBoy_LV said:**
> But they aren`t always up-to-date ;)


Fully agreed, specially if you have latest video cards or need latest features.

---

### Post by denali on 2010-05-01
Sadly, this did not fix mine.  I even went so far as to delete nouveau.ko and the module STILL somehow loads. :confused:

---

### Post by Linuxforall on 2010-05-01
> **denali said:**
> Sadly, this did not fix mine.  I even went so far as to delete nouveau.ko and the module STILL somehow loads. :confused:

When you blacklisted, did you give a space after the entries, thats a must.

---

### Post by peepingtom on 2010-05-01
[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)
this ppa is better for most people.

Lucid's new system for managing nvidia drivers allows muliple versions to be installed concurrently (although not run concurrently). this is why you had to remove those packages to use nvidia's .run installer.

---

### Post by Linuxforall on 2010-05-01
Unfortunately, this ppa doesn't get updated days.

---

### Post by denali on 2010-05-01
> **Linuxforall said:**
> When you blacklisted, did you give a space after the entries, thats a must.

Yes.  No joy, module still loads.

---

### Post by Linuxforall on 2010-05-01
> **denali said:**
> Yes.  No joy, module still loads.


Something seriously going wrong here, I installed on three nvidia PCs so far without any issues.

---

### Post by denali on 2010-05-01
> **Linuxforall said:**
> Something seriously going wrong here, I installed on three nvidia PCs so far without any issues.

Agreed.  I'm still not sure how the module is still loading if it's been deleted.  Only thing I can figure is I some how ended up with a version of the kernel that has it compiled inline rather than being a module.

---

### Post by Linuxforall on 2010-05-01
> **denali said:**
> Agreed.  I'm still not sure how the module is still loading if it's been deleted.  Only thing I can figure is I some how ended up with a version of the kernel that has it compiled inline rather than being a module.

Did you add the other lines along with nouveau in blacklist.conf?

---

### Post by denali on 2010-05-01
> **Linuxforall said:**
> Did you add the other lines along with nouveau in blacklist.conf?

Yes, with a space after them as well.

---

### Post by Linuxforall on 2010-05-01
> **denali said:**
> Yes, with a space after them as well.

You just need the space after the last entry.

---

### Post by denali on 2010-05-01
> **Linuxforall said:**
> You just need the space after the last entry.

If I added a space after all of them, does it make a difference?

---

### Post by Linuxforall on 2010-05-01
> **denali said:**
> If I added a space after all of them, does it make a difference?

It shouldn't but try otherwise and see if it makes any difference.

---

### Post by denali on 2010-05-01
> **Linuxforall said:**
> It shouldn't but try otherwise and see if it makes any difference.

Nope, no difference.

I'm curious as to why deleting the module didn't kill it.

---

### Post by Linuxforall on 2010-05-01
> **denali said:**
> Nope, no difference.

I'm curious as to why deleting the module didn't kill it.

I am as well, blacklisting should have been enough at this point. Did you try installing nvidia drivers via hardware appelet?

---

### Post by denali on 2010-05-01
> **Linuxforall said:**
> I am as well, blacklisting should have been enough at this point. Did you try installing nvidia drivers via hardware appelet?

I can't get that far.  The desktop doesn't come up due to these drivers, from what I can tell.

---

### Post by Linuxforall on 2010-05-01
Man that truly sucks, let me see what else I can find.

---

### Post by denali on 2010-05-01
> **Linuxforall said:**
> Man that truly sucks, let me see what else I can find.

Tell me about it!  I've never had this much trouble with video card drivers.

---

### Post by M4T1A5 on 2010-05-01
I've got it to work. you just need to go to synaptic and remove the nouveau driver from there. make sure to remove it completely. that worked for me and i had the same problem that you had

Edit:
remember to reboot and then just install  the nvidia driver normally

---

### Post by Linuxforall on 2010-05-01
> **M4T1A5 said:**
> I've got it to work. you just need to go to synaptic and remove the nouveau driver from there. make sure to remove it completely. that worked for me and i had the same problem that you had

Edit:
remember to reboot and then just install  the nvidia driver normally

Removing nouveau also removes lots of other stuff that looks real important like acpi etc. I have that installed in synaptic and yet my nvidia install went fine.

---

### Post by M4T1A5 on 2010-05-01
> **Linuxforall said:**
> Removing nouveau also removes lots of other stuff that looks real important like acpi etc. I have that installed in synaptic and yet my nvidia install went fine.
actually it only removed xserver-xorg-video-all

Edit:
oh and i updated to 10.04 from 9.10 so that might be why it won't work

---

### Post by Linuxforall on 2010-05-01
> **M4T1A5 said:**
> actually it only removed xserver-xorg-video-all

Edit:
oh and i updated to 10.04 from 9.10 so that might be why it won't work

How about libdrm nouveau?

---

### Post by M4T1A5 on 2010-05-01
> **Linuxforall said:**
> How about libdrm nouveau?
it can be installed only remove the xserver-xorg-video-nouveau
and it wont remove the libdrm noveau

---

### Post by Linuxforall on 2010-05-01
> **M4T1A5 said:**
> it can be installed only remove the xserver-xorg-video-nouveau
and it wont remove the libdrm noveau

I just tried removing nouveau xserver and the system booted in low graphics mode without nvidia drivers loaded. I did remove the blacklist entries. So even after removing the nouveau driver, blacklist entries seem to be needed.

---

### Post by M4T1A5 on 2010-05-01
> **Linuxforall said:**
> I just tried removing nouveau xserver and the system booted in low graphics mode without nvidia drivers loaded. I did remove the blacklist entries. So even after removing the nouveau driver, blacklist entries seem to be needed. well i had the blacklists still in place i just made sure it can't possibly load the nouveau driver what ever was the case by removing it and i also had the nv xserver driver installed probably because i updated from 9.10 (and when i rebooted it loaded the nv driver and then i just installed the nvidia driver like you would install it on 9.10)

---

### Post by Linuxforall on 2010-05-01
> **M4T1A5 said:**
> well i had the blacklists still in place i just made sure it can't possibly load the nouveau driver what ever was the case by removing it and i also had the nv xserver driver installed probably because i updated from 9.10 (and when i rebooted it loaded the nv driver and then i just installed the nvidia driver like you would install it on 9.10)

Yep good point, I just added the extra bit of removing nouveau thanks to you alongwith the blacklists.

---

### Post by denali on 2010-05-01
> **M4T1A5 said:**
> I've got it to work. you just need to go to synaptic and remove the nouveau driver from there. make sure to remove it completely. that worked for me and i had the same problem that you had

Edit:
remember to reboot and then just install  the nvidia driver normally

I'm using Kubuntu.  Is there a CLI version of Synaptic for Kubuntu?  I can't get to the desktop and I'm having to do everything from terminal.

---

### Post by Linuxforall on 2010-05-01
> **denali said:**
> I'm using Kubuntu.  Is there a CLI version of Synaptic for Kubuntu?  I can't get to the desktop and I'm having to do everything from terminal.

Try sudo apt-get --purge remove xserver-xorg-video-nouveau

---

### Post by denali on 2010-05-01
> **denali said:**
> I'm using Kubuntu.  Is there a CLI version of Synaptic for Kubuntu?  I can't get to the desktop and I'm having to do everything from terminal.

Found it.  Aptitude.

---

### Post by trespuntos on 2010-05-01
i was in the same situation as denali. after researching a little, this method let me install nvidia drivers. I hope it can help some of you


sudo nano /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

(remember last space)

sudo gdm-stop
sudo apt-get --purge remove nvidia-*

RESTART

(after this ubuntu boots with some graphical errors like white lines and incorrect resolution)

sudo gdm-stop
sudo apt-get --purge remove xserver-xorg-video-nouveau

RESTART

(after this, ubuntu boots  with no graphical errors BUT CANT GET INTO TERMINAL with gdm stopped so cant install nvidia drivers)

So heres the tricky part

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

and you need to comment 'blacklist vesafb' and add 'blacklist vgafb16' (both without quotes)

sudo nano /etc/initramfs-tools/modules

and add 'fbcon' and 'vesafb' (dont forget last space)

sudo update-initramfs -u

sudo nano /etc/default/grub

search for 'GRUB_CMDLINE_LINUX='  and ADD (dont delete) vga=771 or 795 (according to your resolution)

sudo update-grub

RESTART

sudo gdm-stop

now can enter terminal and install NVIDIA drivers. and they will install without errors.

---

### Post by VyacheslavS on 2010-05-01
**to trespuntos:**
Thanks, works!

---

### Post by Brain Juice on 2010-05-01
Thank you! 

Worked for me too  :guitar:

---

### Post by AndyBoy_LV on 2010-05-01
**to trespuntos**

Thanks for updating the HOWTO :)

---

### Post by swalker23 on 2010-05-01
Thanks, It worked for me and solved an issue in which I install nvidia drivers via hardware devices and afterwards Kubuntu hangs when shuttingdown/rebooting.  After doing what trespuntos suggested I came across 2 lil problems.

1.  When rebooting I hear 3 fast beeps from my mobo.

2.  I'm using kubuntu and when I boot up(before log in screen) or shutdown I get the ubuntu splash screen.  Also during the boot it also displays the text starting cups. 


I also have another question in which I don't want to start a thread.  Before the login screen I have a black screen with a flashing dash (_).  Is this normal?  It doesn't bother me just wanted to know.

---

### Post by denali on 2010-05-01
To Trespuntos:

That did it!  Thank you!

Now I just have to find my desktop folders. :P

---

### Post by Linuxforall on 2010-05-01
The GDM stop has to be done after getting into terminal and not before.

---

### Post by Kurtosis on 2010-05-01
I just did a fresh install of 10.04, and want to install the Nvidia drivers via the Software Center update icon in the top right.  

However, I can't tell what version they are - the update manager is vague on that point, and a google search for "Ubuntu 10.04 Nvidia driver version" didn't help either.

Suggestions?

---

### Post by Linuxforall on 2010-05-01
Use hardware appelet and install nvidia current, that gets you the last driver 195.36.15, current is 195.36.24

---

### Post by ibuclaw on 2010-05-01
> **AndyBoy_LV said:**
> But they aren`t always up-to-date ;)

They aren't up to date ... yes, but you never know what sort of damage you'll run into with a newer driver. ([hint]("http://www.maximumpc.com/article/news/nvidia_removes_linux_solaris_drivers_due_overheating_bug"))

---

### Post by Linuxforall on 2010-05-01
That issue affected limited cards and nvidia was prompt in removing those, that don't mean one should be prevented from using latest drivers. Since Lucid is LTS slated for next three years, I guess one goes out and gets a new card only to find that the drivers don't support it since they are three years old, with this attitude, Linux desktop is going to loose big to MS, no ifs and or buts.

---

### Post by Kurtosis on 2010-05-01
> **Linuxforall said:**
> Use hardware appelet and install nvidia current, that gets you the last driver 195.36.15, current is 195.36.24
Thanks, though I'm not familiar with 'hardware appelet'.  Are you saying to allow the Update Manager to install the recommended Nvidia driver?

---

### Post by Linuxforall on 2010-05-01
> **Kurtosis said:**
> Thanks, though I'm not familiar with 'hardware appelet'.  Are you saying to allow the Update Manager to install the recommended Nvidia driver?

system>administration>hardware drivers

---

### Post by Kurtosis on 2010-05-01
> **Linuxforall said:**
> system>administration>hardware drivers
Got it, thank you!

---

### Post by mocha on 2010-05-02
> **peepingtom said:**
> Lucid's new system for managing nvidia drivers allows muliple versions to be installed concurrently (although not run concurrently). this is why you had to remove those packages to use nvidia's .run installer.

Care to explain how this works?

---

### Post by coolcaseley67 on 2010-05-02
hi 

can one help me  ?

I've blacklist and remove the drivers . Then i download the installer and reboot . log-in the terminal .

I cant change to my home folder to run it ...

thanks

---

### Post by Linuxforall on 2010-05-02
> **coolcaseley67 said:**
> hi 

can one help me  ?

I've blacklist and remove the drivers . Then i download the installer and reboot . log-in the terminal .

I cant change to my home folder to run it ...

thanks

Did you install build-essential?

Also you don't have to be in HOME when you are in terminal, you are already there, make sure the run file is there.

---

### Post by honorshark on 2010-05-02
Coolcaseley: I used the recovery mode. Blacklist driver, boot up the recovery mode, only root login with networking. Type your root password. Type: init 5. After the login pop ups, login as root, cd into your home dir and execute the installer.

You can also use the dkms script which can be found on this forum..

[http://ubuntuforums.org/showthread.php?t=1036788](http://ubuntuforums.org/showthread.php?t=1036788)

---

### Post by Hsp192 on 2010-05-02
7) Login and cd to the directory where you saved your file
8) Install drivers ```
sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run
```9) Start GDM ```
sudo service gdm start
```Enjoy ;)[/QUOTE]

Hi! I follow all instructions, but when I tape "sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run" in the blacklist, it answer:
"sh: can't open NVIDIA-Linux-x86_64-195.36.24-pkg2.run"

What I'm supposed to do?

---

### Post by swalker23 on 2010-05-02
> **Linuxforall said:**
> Use hardware appelet and install nvidia current, that gets you the last driver 195.36.15, current is 195.36.24

Whenever I use this method my PC hangs when rebooting/shutting down and the monitors goes off in both ubuntu and kubuntu.  I have to push my reset button in order to reboot.  When I install the drivers manually I can reboot/shutdown but when I do I hear 3 or 4 fast beeps from my mobo and it shutdowns.  I also can't go into console with ctrl-alt-F2 after I install the drivers manually and I also hear 3 beeps from my mobo when pressing ctrl-alt-F2.  This makes me want to go back to 9.1.

---

### Post by ratcheer on 2010-05-02
Question: I have always used **pkg1** to do this, with complete success. Why is everyone using **pkg2**, now? What is the difference and when should one or the other be used?

Tim

---

### Post by coolcaseley67 on 2010-05-02
hi

thanks for your reply s  .

-went I run it i get an error saying : sudo : sh  NVIDIA-linux-x86-96.43.16-pkg1.run command not found

---

### Post by Linuxforall on 2010-05-02
> **ratcheer said:**
> Question: I have always used **pkg1** to do this, with complete success. Why is everyone using **pkg2**, now? What is the difference and when should one or the other be used?

Tim

pkg2 is what Nvidia recommends for our distro.

---

### Post by Linuxforall on 2010-05-02
> **coolcaseley67 said:**
> hi

thanks for your reply s  .

-went I run it i get an error saying : sudo : sh  NVIDIA-linux-x86-96.43.16-pkg1.run command not found

just type sudo sh instead of .sh

---

### Post by coolcaseley67 on 2010-05-02
hi 

now i get an error saying: sh can't open NVIDIA-linux-x86-96.43.16-pkg1.run ...

thanks for the help .........

ps i've installed build essential ..

---

### Post by ratcheer on 2010-05-02
> **Linuxforall said:**
> pkg2 is what Nvidia recommends for our distro.

Thanks. I have never seen that. Maybe I just need to look harder. :)

Tim

---

### Post by swalker23 on 2010-05-02
> **coolcaseley67 said:**
> hi 

now i get an error saying: sh can't open NVIDIA-linux-x86-96.43.16-pkg1.run ...

thanks for the help .........

did you navigate to the folder that has the nvidia driver in it?

I do that all the time, forget to $ cd Downloads when installing the drivers.

---

### Post by ratcheer on 2010-05-02
I looked harder. All I can find is this. It seems a little vague, but it supports what you said.

```
The package suffix (-pkg#) is used to distinguish between packages containing the same driver, but with different precompiled kernel interfaces. The file with the highest package number is suitable for most installations.
```

[http://us.download.nvidia.com/XFree86/Linux-x86/195.36.24/README/selectdriver.html](http://us.download.nvidia.com/XFree86/Linux-x86/195.36.24/README/selectdriver.html)

Tim

---

### Post by meediake on 2010-05-02
Hello, i have still problems with installing it.
The log messages are here:

```

-> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':
   -1 No such device
-> Kernel messages:
   [  355.012712] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on lvds
   encoder (output 0)
   [  355.012721] [drm] nouveau 0000:01:00.0: Calling LVDS script 6:
   [  355.012729] [drm] nouveau 0000:01:00.0: 0xD259: Parsing digital output
   script table
   [  355.296341] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC
   0 using output A
   [  355.296350] [drm] nouveau 0000:01:00.0: Calling LVDS script 2:
   [  355.296357] [drm] nouveau 0000:01:00.0: 0xD2BA: Parsing digital output
   script table
   [  355.448143] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on lvds
   encoder (output 0)
   [  355.448153] [drm] nouveau 0000:01:00.0: Calling LVDS script 5:
   [  355.448160] [drm] nouveau 0000:01:00.0: 0xD24A: Parsing digital output
   script table
   [  355.448177] [drm] nouveau 0000:01:00.0: Output LVDS-1 is running on CRTC
   0 using output A
   [  355.448213] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga
   encoder (output 1)
   [  355.468453] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga
   encoder (output 1)
   [  355.468462] [drm] nouveau 0000:01:00.0: Output VGA-1 is running on CRTC 1
   using output A
   [  370.521966] [drm] nouveau 0000:01:00.0: nouveau_channel_free: freeing
   fifo 1
   [  370.681066] wlan0: deauthenticating from 00:14:7f:81:76:90 by local
   choice (reason=3)
   [  577.693174] nvidia: module license 'NVIDIA' taints kernel.
   [  577.693180] Disabling lock debugging due to kernel taint
   [  579.310741] NVRM: The NVIDIA probe routine was not called for 1
   device(s).
   [  579.310751] NVRM: This can occur when a driver such as rivafb, nvidiafb
   or
   [  579.310755] NVRM: rivatv was loaded and obtained ownership of the NVIDIA
   [  579.310758] NVRM: device(s).
   [  579.310766] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel
   module
   [  579.310769] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb
   [  579.310773] NVRM: support), then try loading the NVIDIA kernel module
   again.
   [  579.310779] NVRM: No NVIDIA graphics adapter probed!
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.

```

I followed the instructions at the beginning of this topic.:(

---

### Post by VyacheslavS on 2010-05-02
> **meediake said:**
> Hello, i have still problems with installing it.
...
I followed the instructions at the beginning of this topic.:(
[http://ubuntuforums.org/showpost.php?p=9211609&postcount=35](http://ubuntuforums.org/showpost.php?p=9211609&postcount=35)

---

### Post by mothes on 2010-05-02
Thank you very much!

---

### Post by meediake on 2010-05-02
Thank you, it is working now. There is still hassle with video cards in linux but it is still worth trying, i like new ubuntu very much :):KS

---

### Post by Durayne on 2010-05-03
thx trespunto

---

### Post by coolcaseley67 on 2010-05-03
hi 

i still can not open the installer  Can any one help ?

thanks

---

### Post by fireandfuel on 2010-05-03
Why did you use vesafb (instead of uvesafb)?
uvesafb supports more resolutions than vesafb - like 1280x800.

I realized a broken framebuffer after the update to Lucid Beta2.

So I have written a tutorial in the German ubuntuusers.de forum, how you install and use uvesafb and get plymouth (new boot screen) displayed at start up correctly.

The translation:

Add or replace in /etc/default/grub for 1280x1024 @ 32bit color range (replace with your favorite resolution)
```
GRUB_GFXPAYLOAD_LINUX=1280x1024x32
GRUB_CMDLINE_LINUX="video=uvesafb:mode_option=1280x1024-32"
```. Then run
```
update-grub 
```. In /etc/modprobe.d/blacklist-framebuffer.conf you add the line
```
blacklist vga16fb
``` and add in /etc/initramfs-tools/modules the line
 ```
uvesafb 
```. Finally run
```
update-initramfs -u
```.

In some cases you need to install the package v86d from the repository.

A fix for get plymouth before the X server starts:
```

sudo su
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
exit
```Without that fix you see plymouth only a few seconds and at the longest time a black screen. 

PS: All commands needs root privileges (sudo) and
don't forget to save the changes!
Use your favorite text editor: gedit, vim, nano etc.

The changes will be activated at the next boot.

I hope you understand translation. :)

PPS: I don't know how often the nvidia-current package will be updated, but I think a stable and tested driver is better then a new and 'not tested' driver.

---

### Post by peepingtom on 2010-05-04
Word to the wise: The Ubuntu X Updates PPA regularly adds stable NVIDIA drivers within a couple days of their release.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)


Most people should use that instead of NVIDIA's .run files. It's very easy.

---

### Post by Linuxforall on 2010-05-04
> **peepingtom said:**
> Word to the wise: The Ubuntu X Updates PPA regularly adds new NVIDIA drivers within a couple days of their release.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

Not really but for Lucid this has been an exception and lets hope it stays that way so we can all be happy and not have to resort to manual ways.

---

### Post by go2arslan on 2010-05-05
> **trespuntos said:**
> i was in the same situation as denali. after researching a little, this method let me install nvidia drivers. I hope it can help some of you


sudo nano /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

(remember last space)

sudo gdm-stop
sudo apt-get --purge remove nvidia-*

RESTART

(after this ubuntu boots with some graphical errors like white lines and incorrect resolution)

sudo gdm-stop
sudo apt-get --purge remove xserver-xorg-video-nouveau

RESTART

(after this, ubuntu boots  with no graphical errors BUT CANT GET INTO TERMINAL with gdm stopped so cant install nvidia drivers)

So heres the tricky part

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

and you need to comment 'blacklist vesafb' and add 'blacklist vgafb16' (both without quotes)

sudo nano /etc/initramfs-tools/modules

and add 'fbcon' and 'vesafb' (dont forget last space)

sudo update-initramfs -u

sudo nano /etc/default/grub

search for 'GRUB_CMDLINE_LINUX='  and ADD (dont delete) vga=771 or 795 (according to your resolution)

sudo update-grub

RESTART

sudo gdm-stop

now can enter terminal and install NVIDIA drivers. and they will install without errors.

Thanks Buddy !!!

---

### Post by anamtamrin on 2010-05-08
go2arslan, please explain to me what this line means:

you need to comment 'blacklist vesafb' 

I'm a beginner

thank you

---

### Post by Linuxforall on 2010-05-08
> **anamtamrin said:**
> go2arslan, please explain to me what this line means:

you need to comment 'blacklist vesafb' 

I'm a beginner

thank you


Hi,

Since you are a beginner, its better for you to install the driver via xswat ppa which has the latest driver there.

All you do is open a terminal and type sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update 

and then go to system>administration>hardware drivers and install nvidia-current.

---

### Post by UrbenLegend on 2010-05-08
> **fireandfuel said:**
> Why did you use vesafb (instead of uvesafb)?
uvesafb supports more resolutions than vesafb - like 1280x800.

I realized a broken framebuffer after the update to Lucid Beta2.

So I have written a tutorial in the German ubuntuusers.de forum, how you install and use uvesafb and get plymouth (new boot screen) displayed at start up correctly.

The translation:

Add or replace in /etc/default/grub for 1280x1024 @ 32bit color range (replace with your favorite resolution)
```
GRUB_GFXPAYLOAD_LINUX=1280x1024x32
GRUB_CMDLINE_LINUX="video=uvesafb:mode_option=1280x1024-32"
```. Then run
```
update-grub 
```. In /etc/modprobe.d/blacklist-framebuffer.conf you add the line
```
blacklist vga16fb
``` and add in /etc/initramfs-tools/modules the line
 ```
uvesafb 
```. Finally run
```
update-initramfs -u
```.

In some cases you need to install the package v86d from the repository.

A fix for get plymouth before the X server starts:
```

sudo su
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
exit
```Without that fix you see plymouth only a few seconds and at the longest time a black screen. 

PS: All commands needs root privileges (sudo) and
don't forget to save the changes!
Use your favorite text editor: gedit, vim, nano etc.

The changes will be activated at the next boot.

I hope you understand translation. :)

PPS: I don't know how often the nvidia-current package will be updated, but I think a stable and tested driver is better then a new and 'not tested' driver.

Thanks for the tip! Seems to have fixed the offcenter splash screen issue that randomly appears at times with vga16fb.

Also if you're using video=uvesafb:mode_option=1280x1024-32, you do NOT need GRUB_GFXPAYLOAD_LINUX=1280x1024x32

EDIT: You also don't need the uvesafb line in /etc/initramfs-tools/modules. You just need to install v86d.

EDIT2: It turns out you DO NEED GRUB_GFXPAYLOAD_LINUX=1280x1024x32 only if you're not using the FRAMEBUFFER=y option.

---

### Post by Philippo.co on 2010-05-09
Thank you so much AndyBoy_LV and trespuntos!!

maybe this page would be useful for some people
[http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/](http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/)

---

### Post by AndyBoy_LV on 2010-05-09
You are welcome, **Philippo.co**


A small update for those, who are having trouble installing the driver on the latest kernel:

If you get an error saying > Error: unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernal source files for your kernel and that they are properly configured...

Than all that you should do is install the latest kernel headers (2.6.32-22 in my case)
Login into your newest kernel. Go to terminal and type ```
sudo apt-get install linux-headers-$(uname -r)
```
After installation finishes, proceed with the Nvidia driver installation as usual.
Good luck :)

---

### Post by Philippo.co on 2010-05-09
Thank you again.

I had remember some threads about installing nvidia video cards and I found these:

[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400) (previous way to install drvs)

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573) (interesting one about how can auto-install drivers with any kernel update)

I tested last one and works fine.

See you :)

---

### Post by AndyBoy_LV on 2010-05-10
> **Philippo.co said:**
> Thank you again.

I had remember some threads about installing nvidia video cards and I found these:

[http://ubuntuforums.org/showthread.php?t=1125400](http://ubuntuforums.org/showthread.php?t=1125400) (previous way to install drvs)

[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573) (interesting one about how can auto-install drivers with any kernel update)

I tested last one and works fine.

See you :)



Wow, very useful one. Thank you! I`ll have to test it out on the next kernel update.

---

### Post by coolcaseley67 on 2010-05-10
hi 
 
I am still geting errors saying i can not open it ! 
 
any thoughts :confused::confused:

---

### Post by AndyBoy_LV on 2010-05-10
> **coolcaseley67 said:**
> hi 
 
I am still geting errors saying i can not open it ! 
 
any thoughts :confused::confused:

At what point are you getting these errors?

---

### Post by coolcaseley67 on 2010-05-10
hi 

well  I break the ubuntu and then go in to the log-in Terminal  , see my other post for the error .

many thnks

---

### Post by bsyapril88 on 2010-05-11
Hi,

I am also having tons of trouble with my Nvidia GT240.  I followed "trespuntos" method but wasn't able to get back into the terminal on the last step...

I get a screen with this...
Ubuntu 10.04
. . . . * Speech-dispatcher configured for use[ OK ]i
ons
* PulseAudio configured for per-user sessionsupsd
 *Enabling additional executable binary formats binfmt
-support                            [ OK ]
*Checking battery state...          [ OK ]


I can type but otherwise it is stuck.  The upside is that this process got my monitor to have the correct resolution but I'm still not using the nvidia driver.

Thanks for the help.

---

### Post by robegue on 2010-05-14
I have an 8400M-GS (dell XPS M1330)

Following the procedure "blacklist + remove nouveau + update initrd + install nvdidia-current" I finally got it work.

BUT

now I have the fan at full speed for all the time and the gpu thermal indicator stuck to 56 degrees (celsius)!!

No problem  with the nouveau drivers!

What's going on here?

---

### Post by AndyBoy_LV on 2010-05-14
> **robegue said:**
> I have an 8400M-GS (dell XPS M1330)

Following the procedure "blacklist + remove nouveau + update initrd + install nvdidia-current" I finally got it work.

BUT

now I have the fan at full speed for all the time and the gpu thermal indicator stuck to 56 degrees (celsius)!!

No problem  with the nouveau drivers!

What's going on here?
 
Have you tried installing drivers from Synaptic? Do they work ok? If yes, than i would recommend to stay with them and not to try installing drivers manually, or at least wait until next driver version comes out.

---

### Post by robegue on 2010-05-14
> **AndyBoy_LV said:**
> Have you tried installing drivers from Synaptic? Do they work ok? If yes, than i would recommend to stay with them and not to try installing drivers manually, or at least wait until next driver version comes out.

Have you red my post?
Considering that the nvidia proprietary drivers overheat my laptop I believe they are not working well at all! I immediately switched back to nouveau drivers. Even if they are slow, I do not risk to melt the gpu:

nvidia   -> 56 degrees
nouveau  -> 32 degrees

there's something wrong for sure

---

### Post by AndyBoy_LV on 2010-05-14
> **robegue said:**
> Have you red my post?
Considering that the nvidia proprietary drivers overheat my laptop I believe they are not working well at all! I immediately switched back to nouveau drivers. Even if they are slow, I do not risk to melt the gpu:

nvidia   -> 56 degrees
nouveau  -> 32 degrees

there's something wrong for sure

If the newest Nvidia driver version works like that, it doesn`t mean all versions will overheat your card. I would recommend to try the next version when it comes out. It`s not like it will melt down your GPU in one second, you will always have a chance to rollback to nouveau :) 

Also, i have an 8600M GT and its average temperature is 59-60 Degrees with up to 75 degrees when watching Flash videos or playing Flash games :) And it has always been that way, since the first day i installed Linux on my laptop :)

---

### Post by Linuxforall on 2010-05-15
I got nvidia drivers installed on two laptops here, one a Lenovo and the other a VAIO and there is absolutely no overheating here.

---

### Post by HarshReality on 2010-05-16
Well, Im pushing an NVidia 9600 GTS and the whole thing still goes ape.. so much for limited affected cards and resolutions.

---

### Post by fowl on 2010-05-19
> **AndyBoy_LV said:**
> Well, i am one of those users who never install Nvidia drivers from repository, but manually - by downloading from Nvidia`s website. It was never a pain in the rear on previous Linux distros (including Karmic), but i failed to do so on Lynx. Whenever i tried to install it, i got an error: ```
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
       
```I read somewhere that they changed the way nvidia drivers get installed on Lynx (correct me if i`m wrong), so it took me some time to figure out how to do that. So, here is the guide:


1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin: (i use gedit for text file editing)```
sudo gedit /etc/modprobe.d/blacklist.conf
```3) Add these lines and save: 
```

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```4) Uninstall any previously installed Nvidia drivers: 
```
sudo apt-get --purge remove nvidia-* 
```5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
8) Install drivers ```
sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run
```9) Start GDM ```
sudo service gdm start
```Enjoy ;)

P.S. if you are having trouble with my method, there is an [updated one]("http://ubuntuforums.org/showpost.php?p=9211609&postcount=35"), posted by **trespuntos** - maybe it will solve your problem.

I did the following commands and i was having an issue with Ubuntu still loading into the x server. I tried several ways to stop gdm. sudo service gdm stop and sudo /etc/init.d/gdm stop without luck. It seemed that something was not being blocked from the blacklist.

I went into the software manager ~> installed software and typed nvidia into the search bar. I then removed everything from there. I restarted to a low resolution window and stopped gdm again. I then installed the driver and so far have not had any problems.

Hope this helps anyone looking around for a way to install the latest driver and had similar issues. I kinda hope myself that it works out to be a lasting fix haha!

fowl

---

### Post by wesamly on 2010-05-19
Oh! man thanks a lot, you saved my life =D>
My laptop is Sony Vaio VPCCW23FX
After installing Kubuntu for 3 times, trying many different ways to install Nvidia drivers, I got it to work.
One thing is that for those my need to install build-essential and linux-headers which are required to install the nvidia driver
```
sudo apt-get build-essential linux-headers-`uname -r`
```

Now time to check what else works :popcorn:

---

### Post by ozzyprv on 2010-05-23
Post #1 worked for me (so far 1 shutdown/reboot). But now I lost the nice initial Lucid splash screen and the booting lasts a bit longer.
I also lost the nvidia settings menu.

---

### Post by Linuxforall on 2010-05-23
nvidia settings is there in settings>preferences instead of administration. Plymouth doesn't work with any proprietary driver so boot screen is not there, thankfully it doesn't take Lucid long to boot.

---

### Post by Linuxforall on 2010-05-23
Latest 256 nvidia beta drivers updated on X Swat PPA.

---

### Post by toasted124 on 2010-05-28
Thanks for this post, it fixed my KDE issues after upgrading from 9.10 to 10.04. Now that I have my KDE back and things are working again. Do I need to remove the blacklist entries described in step 3?

---

### Post by ozzyprv on 2010-05-28
> **Linuxforall said:**
> nvidia settings is there in settings>preferences instead of administration. Plymouth doesn't work with any proprietary driver so boot screen is not there, thankfully it doesn't take Lucid long to boot.


Not here. Do you know what package I should have installed for that shortcut to show? I deleted them (nvidia packages) all before doing the manual install
Thanks.

---

### Post by phendrome on 2010-05-28
I don't seem to get this to work. I've followed every step properly and when I reboot I still get into the desktop just as nothing would've happened.

I do have a space at the very end of the blacklist thing too and I've uninstalled the drivers.

Anyone? All help is appericiated.

Edit: Oh, and I use Ubuntu 10.4!

---

### Post by Bubbet on 2010-05-29
I have tried this method twice. The first time I would get the ubuntu splash indefinately after installing the drivers. I had to reinstall ubuntu. Now I set ubuntu to boot into terminal rather than with xserver. Now when I try to start the xserver or gdm system hangs. Any thoughts?

---

### Post by phendrome on 2010-05-31
Hmm, I actually tried the second method (which is linked on the first post at the very end) and I did everything correct and I managed to install the new NVIDIA drivers (195.36.24). 

However, I still ain't able to use the desktop effects, neither am I able to check if the drivers are actually there. Which I find very weird.

One thing that might have been wrong, is that - after the installation was completed and I still was in the console, I didn't type a command to reboot, I rebooted from the reset button on the case.  

Anyone might have an idea what could be wrong?

Oh yeah by the way, I'm using PNY 8800 GTS 640MB (G80).

---

### Post by Cincinnatux on 2010-05-31
AndyBoy_LV, I am in your debt.  Last week my home server choked (nVidia GTS-240) and your instructions returned it to full functionality.  Today, for reasons I cannot fathom, my laptop suddenly decided it, too, needed to self-bork its ability to activate the nVidia card (nVidia 8400M).  The confusion on timing of the laptop's self-borking is that I spent the weekend in an area without Internet access and booted the machine and shut it down on three occasions.  On the fourth, it borked.  Go figure.

Anyhow, AndyBoy_LV's guide restored my laptop to full function as well.  

I hope someday to be able to figure this stuff out on my own.  But in the meantime, I am deeply grateful for the many out there who take the time to make the Linux experience more rewarding for mere users such as I am.

---

### Post by phendrome on 2010-05-31
> **Cincinnatux said:**
> I hope someday to be able to figure this stuff out on my own.  But in the meantime, I am deeply grateful for the many out there who take the time to make the Linux experience more rewarding for mere users such as I am.
I couldn't have written it better. Thumbs up! :)

---

### Post by wum1ng on 2010-06-10
I did like to thank all the help this thread has provided me. I would also like to add that this line

sudo apt-get --purge remove xserver-xorg-video-nouveau

was crucial for getting past the nvidia kernel not being able to run problem. I can now finally get back to doing work!

---

### Post by ^[H3ad-Tr1p]^ on 2010-06-18
> **trespuntos said:**
> i was in the same situation as denali. after researching a little, this method let me install nvidia drivers. I hope it can help some of you


sudo nano /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

(remember last space)

sudo gdm-stop
sudo apt-get --purge remove nvidia-*

RESTART

(after this ubuntu boots with some graphical errors like white lines and incorrect resolution)

sudo gdm-stop
sudo apt-get --purge remove xserver-xorg-video-nouveau

RESTART

(after this, ubuntu boots  with no graphical errors BUT CANT GET INTO TERMINAL with gdm stopped so cant install nvidia drivers)

So heres the tricky part

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

and you need to comment 'blacklist vesafb' and add 'blacklist vgafb16' (both without quotes)

sudo nano /etc/initramfs-tools/modules

and add 'fbcon' and 'vesafb' (dont forget last space)

sudo update-initramfs -u

sudo nano /etc/default/grub

search for 'GRUB_CMDLINE_LINUX='  and ADD (dont delete) vga=771 or 795 (according to your resolution)

sudo update-grub

RESTART

sudo gdm-stop

now can enter terminal and install NVIDIA drivers. and they will install without errors.



Hi 

I'm doing this metod and work . Great !

After I've finished,I have to reconfiguring these things like before?

thanks

---

### Post by birkopf on 2010-06-25
AndyBoy_LV thanks for how to. After 6hours of google search and struggle I finally installed nvidia driver on apparently-better-than-jaunty-lucid....

---

### Post by kvaju on 2010-06-28
Thank you very much this is very helpfull.
it works on my GT 8600

---

### Post by ghalebalmahdi on 2010-07-01
> **trespuntos said:**
> i was in the same situation as denali. after researching a little, this method let me install nvidia drivers. I hope it can help some of you


sudo nano /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

(remember last space)

sudo gdm-stop
sudo apt-get --purge remove nvidia-*

RESTART

(after this ubuntu boots with some graphical errors like white lines and incorrect resolution)

sudo gdm-stop
sudo apt-get --purge remove xserver-xorg-video-nouveau

RESTART

(after this, ubuntu boots  with no graphical errors BUT CANT GET INTO TERMINAL with gdm stopped so cant install nvidia drivers)

So heres the tricky part

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

and you need to comment 'blacklist vesafb' and add 'blacklist vgafb16' (both without quotes)

sudo nano /etc/initramfs-tools/modules

and add 'fbcon' and 'vesafb' (dont forget last space)

sudo update-initramfs -u

sudo nano /etc/default/grub

search for 'GRUB_CMDLINE_LINUX='  and ADD (dont delete) vga=771 or 795 (according to your resolution)

sudo update-grub

RESTART

sudo gdm-stop

now can enter terminal and install NVIDIA drivers. and they will install without errors.


Thank you for your work
but not work for me
maybe i do some mistakes
but i repeat again and again and again ...................
also not work
please can you re-explain with picture
note my pc vaio cw series and the driver display is :
NVIDIA GeForce GT 330M

please helpe

---

### Post by someitalian123 on 2010-07-01
andy-boy's first post worked for linux kernal 2.6.32-22-generic, but now that ubuntu has updated to a newer version i can't get to my desktop, i'm stuck in the terminal. please help.

---

### Post by guitardennison on 2010-07-02
"6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit  to console)
7) Login and cd to the directory where you saved your file"

I exit to console just fine but it brings me to a black screen where i log in.  from there what does cd to the directory mean. i saved the file on my desktop.  

When  i **sudo gdm- start** it sends me to the same screen as if i were to exit to console.

help!!

sudo gdm-stop does not work while in the black window

---

### Post by birkopf on 2010-07-03
> **guitardennison said:**
> "6)
When  i **sudo gdm- start** it sends me to the same screen as if i were to exit to console.


Try one of combinations:
```

sudo /etc/init.d/gdm stop (start)
sudo gdm-stop (start)
sudo service gdm stop (start) 

```
For me to stop I need tu use gdm-stop and to start I use service gdm start...


PS - **You made space** in your gdm-stop above. That's important as that might be reason (!)

---

### Post by birkopf on 2010-07-03
> **guitardennison said:**
> 
I exit to console just fine but it brings me to a black screen where i log in.  from there what does cd to the directory mean. i saved the file on my desktop.  

That's quite unclear what you write. You need to know basic linux commands (like cd, ls, sh, sudo, etc. etc. etc.) if you want to install driver that way.

Man pages and google is your friend for that.

---

### Post by birkopf on 2010-07-03
I came up with another solution which is best for me. 

**WARNING - If you want to do it that way you do it at your own responsibility**

I am following first few steps from first manual with blacklisting, but in tty when try to install driver - nothing will stop this usual error. 

I rebooted, and normally from Terminal:
```

sudo apt-get install nvidia-settings 
sudo apt-get install nvidia-185-kernel-source

```

If you want to see what's newest available try:
```

sudo apt-get install nvidia*

```
and select newest. 
There will be info during install that the problem with .ko file has been resolved. After that in System -> Administration -> you should see: NVIDIA X server settings. 
Open it and configure required resolution. 

If that wouldn't work as should, backup your xorg.conf in /etc/X11/xorg.conf
You may want to install Midnight Commander which is cool terminal manager.
```

sudo apt-get install mc

```
When in Terminal or Tty use mc to start or sudo mc to start as root.


When xorg.conf is safe press Alt+F2 and:
```

gksu gedit /etc/X11/xorg.conf

```

Erase everything whats in the file and paste that:
```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder62)  Thu Jun  3 09:42:34 PDT 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Thu Jun  3 09:41:37 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
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
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7000M / nForce 610M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

That code needs to be edited before saving, replacing your card name, required resolution, refresh rate, etc.
(Section "Device" and Section "Screen")

I have came with that solution when I noticed that all installation was going fine but than new settings from nvidia couldn't be saved. 
Once overwritten you should be fine... until next headers update :-D

---

### Post by kenkaku on 2010-07-10
I followed the original post to the letter; and it worked great for me.
Thanks Andy.

Edit: Though I did start having [this]("http://ubuntuforums.org/showthread.php?p=9573877#post9573877") problem. May or may not be related.

---

### Post by fbtb on 2010-07-15
Thank you! Finally ;)

---

### Post by jcllings on 2010-07-24
I've got the nvidia drivers working *but* I'm having a problem with my TTY's. They seem to load just fine. I can see characters fine until X loads and then when I switch to a TTY the characters are fuzzy as if being viewed through some kind of electronic interference.  I suspect this is a known issue. 

Can anyone provide me with a methodology for troubleshooting this?  

Jim C.

---

### Post by h_corey on 2010-07-29
> **Linuxforall said:**
> Hi,

Since you are a beginner, its better for you to install the driver via xswat ppa which has the latest driver there.

All you do is open a terminal and type sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update 

and then go to system>administration>hardware drivers and install nvidia-current.

I just tried this tonight.  I get the Hardware Drivers dialog box to open with no drivers to install and "No proprietary drivers are in use on this system".  Does this mean that the 256 drivers are not ready for installation on the latest kernel or is something wrong with my fresh install?

---

### Post by PreThunder on 2010-07-31
Worked like a charm \\:D/

---

### Post by WSGrant on 2010-07-31
> **M4T1A5 said:**
> it can be installed only remove the xserver-xorg-video-nouveau
and it wont remove the libdrm noveau
Im using Ubuntu 10.04 X64 and I kept getting this error until I removed the nouveau xserver from synaptic *after* following the instruction on the first post and getting the error again. 

Everything seems to be working fine now.

---

### Post by sinatosk on 2010-08-01
I've tried a fresh installation of Ubuntu 10.04 64bit and I still get the "Unable to load the kernel module 'nvidia.ko'."... I followed all of the instructions... tried it on Linux Mint (latest ) as well... same thing

---

### Post by speed32219 on 2010-08-11
> **sinatosk said:**
> I've tried a fresh installation of Ubuntu 10.04 64bit and I still get the "Unable to load the kernel module 'nvidia.ko'."... I followed all of the instructions... tried it on Linux Mint (latest ) as well... same thing

I got it to work following a post on the page before this, and I used only these steps.

sudo apt-get --purge remove nvidia-*

sudo apt-get --purge remove xserver-xorg-video-nouveau

**RESTART**

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

add to EOF 
blacklist vesafb
blacklist vgafb16

sudo nano /etc/initramfs-tools/modules

and add 'fbcon' and 'vesafb' (dont forget last space)

sudo update-initramfs -u

---

### Post by LogistiX on 2010-08-19
Followed the original post and everything was well, now the problem is screen tearing. Did  [this ]("http://www.omgubuntu.co.uk/2010/01/how-to-stop-video-tearing-vlc-nvidia.html")but its not working. HELP.

---

### Post by Linuxforall on 2010-08-21
> **h_corey said:**
> I just tried this tonight.  I get the Hardware Drivers dialog box to open with no drivers to install and "No proprietary drivers are in use on this system".  Does this mean that the 256 drivers are not ready for installation on the latest kernel or is something wrong with my fresh install?

Did you do a --purge remove nvidia ?

---

### Post by VMC on 2010-09-02
This procedure worked on both Lucid & Maverick when nothings else would. 

What started me on this path was after installing the nVidia drivers using Ubuntu method , GDM kept failing to start. 1 out of 5 times it would work.

In a last hitch effort I tried this method. It worked perfectly. It worked so well I used the same method on Maverick and it too works perfect.

As of this writing I'm current with **NVIDIA Driver Version: 256.53**

This is on a GeForce 6150SE nForce 430. Some older hardware won't work with the current version. the nVidia web site will show which ones work.

Thank you Andy!

---

### Post by kuckie on 2010-09-20
Both howto´s didnt work for me. I´m on lucid 64bit. I tried everything step by step, didnt get an error along the way, but in the end there still is the complain about the .ko
present.

I reversed all blacklisting stuff and installed the old nvidia-drivers again, but now the "hardware-drivers" app doesnt show any more drivers and claims the installed driver as "not activated" - which is definitely not true.

I really need the recent nvidia drivers for opencl features, but dont know what to try next....

p.s.: just a vage guess, could the virtualbox stuff have some to do with it? I think I saw there some error on booting about virtualbox while I did the blacklisting.
(to be clear, ubuntu runs native with virtualbox installed)

---

### Post by ratcheer on 2010-09-20
> **kuckie said:**
> 

I really need the recent nvidia drivers for opencl features, but dont know what to try next....



My suggestion is to remove the installed driver and reboot. Then, add the x-swat ppa, update your package manager, run the Hardware Devices applet and reinstall nvidia current. This should install the latest driver from the ppa (currently 260.19.04). This procedure has been working for me when nothing else would.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

If it works, then going forward you only need to update, then safe upgrade your package manager to install future updates.

I hope this helps.

Tim

---

### Post by kuckie on 2010-09-21
frak me, this worked perfectly in like under a minute!

Thanks a lot ratcheer!! :popcorn:

---

### Post by ratcheer on 2010-09-21
> **kuckie said:**
> frak me, this worked perfectly in like under a minute!

Thanks a lot ratcheer!! :popcorn:

You are welcome.

Tim

---

### Post by sdowney717 on 2010-09-21
I install Nvidia manually and ok until MM upgraded.
On reboots now refresh always falls to 60 hz.
I have to set it to auto or 85 and click apply.
I tried pasting the xorg configuration into the xorg.conf file, save it and reboot but it always boots up to 60hz again.
So what can I do to make it keep that setting?

---

### Post by rasmus91 on 2010-09-23
Hi there.

I've encountered a problem too, with my Nvidia GT 330m (i have an acer aspire 5745G with core i5)

i've posted my problem in this thread, but perhaps one of you guys can tell me what the problem is:

[http://ubuntuforums.org/showthread.php?t=1488705&page=8]("http://ubuntuforums.org/showthread.php?t=1488705&page=8")

This is what i noticed

```
[    86.662] (EE) No devices detected.
[    86.662] 
Fatal server error:
[    86.662] no screens found
[    86.662]
```

Thanks for your time.

---

### Post by Quadari on 2010-09-25
> **trespuntos said:**
> 
sudo nano /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

(remember last space)



HALLE-FREAKING-LULAH!

This was a painful process.  It wasn't until I added the following to my
/etc/modprobe.d/blacklist.conf

Ttat it worked:
blacklist intel_agp
blacklist agpgart
blacklist amd76x_edac
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

Note that this has a few more things in it than the original post.

Credit for this goes [here]("http://ubuntuforums.org/showpost.php?p=9885855&postcount=13").

Note that I had to ssh into my box in order to complete most of those steps since some of those early steps caused the screen to go black when using my built-in graphics card.  But the machine was still running so I could ssh into it and get things done.   (The problem that I was having is that if I plugged in my GeForce card the machine wouldn't even start up all the way.  So I had to do all of this without the GeForce plugged in.)

But thank you thank you for figuring this out.

---

### Post by soulitude on 2010-10-03
Thanks andyboy and all those who have contributed to this thread.

I am about to install nvidia drivers using the steps here. But before that I just need to know. 

Do we have to give 'nomodeset' to grub even if the new driver is installed and working fine? Is nomodeset anyway  related to graphics drivers?

---

### Post by Linuxforall on 2010-10-03
No need for nomodeset, blacklisting is very important, so is removing all nvidia related files and nouveau.

---

### Post by soulitude on 2010-10-04
Ty! Ty!

Got it running. Yeah did blacklisting and uninstalling nvidia drivers before proceeding with the one from nvidia.com. Its pretty annoying to see ones machine with cool graphics and processing speed having to minimize and maximize windows like peeling ur desktop off!! :) But the fix is now quite popular in the web. 

Graphics is running like Bolt now!!

Thanks a lot for keeping this forum alive. Linuxforall .. thanks for writing back. tc.

---

### Post by soulitude on 2010-10-04
Any idea on how this nomodeset work with kernel? how does it work to start with the default graphics drivers in the first place? It is worth a bit of discussion cause that was how i got into before getting the above steps working.

---

### Post by Linuxforall on 2010-10-04
If you do the blacklist, nomodeset is not really needed.

---

### Post by soulitude on 2010-10-05
Yeah dude .. I did get it running without nomodeset :) I guess i missed to mention it in my update above. You are right, it is not required when proper graphic drivers work. Its fine now, Just my curiosity on nomodeset parameter in grub menu. I guess it tells the kernel to stand back in setting graphics mode when with nVidia cards. If not nouveau will take charge. 

Thanks for the help.

---

### Post by Clive McCarthy on 2010-12-14
This method worked great for me. Then, maybe because I was installing on a virgin 10.10 system, it didn't work. After the re-boot Gnome came back up so it wasn't possible to install the Nvidia driver.

What I did was:

[INDENT][COLOR="SeaGreen"]<Ctrl><Alt><F1> which exits from the Gnome desktop
Login again.
sudo service gdm stop[/COLOR] // this _really_ exits X-Windows ;)
[/INDENT]
Now it is possible to install the Nvidia driver with:

[INDENT][COLOR="SeaGreen"]sudo sh NVIDIA-Linux-260.19.21.run[/COLOR]
[/INDENT]
The 260.19.21 driver is way, way better than nouveau. :D

---

### Post by soulitude on 2010-12-20
>  
The 260.19.21 driver is way, way better than nouveau

 
I agree Clive. That one is good, I am using it.

---

### Post by a-user on 2010-12-20
just in case you guys didn't knew:
you shouldn't isntall the nvidia drivers like this. you can avoid the whole problems with blacklisting and recompiling (reinstalling) everytime you get a kernel update if you use the x-swat repos.

they delivers ubuntu packages updates that keep you current to the official nvidia driver releases. there is a release delay of at most 3 or 4 days after a nvidia beta or official release.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by theopye on 2011-01-09
I followed this guide and it worked great!

However, I think I have FBAR'ed my ethernet card.... I have no access to my network in Linux Mint 10, Windows 7, Linux Mint 10 LiveCD, or even Express Gate.

The moment I restarted, the network connection died.

Thoughts? Any help would be appreciated.

---

### Post by telescopic on 2011-02-03
> Error: Unable to find the kernel source tree for the currently running kernel. Please make sure you have installed the kernel source files for your kernel and that they are properly configured; on Red Hat Linux systems, for example, be sure you have the 'kernel-source'or 'kerneel-devel' RPM installed. If you know the correct kernel source files are installed, you may specifiy the kernel soucrce path with the ''-kernel-soucrce-path' command line option

I did the procedure in p4 of this thread. Now when I reboot to the grub and choose to run ubuntu, ubuntu can't be loaded as expected andI come to  the prompt shell, then I cd to the folder where the driver is and type:

>sudo sh NVIDIA-Linux-x86_64-260.19.36.run

I get the installer running, later received above error about the kernel source path...What should i do? I don't know where is the kernel source path.

Any help please.

---

### Post by VyacheslavS on 2011-02-03
> **telescopic said:**
> ...What should i do? I don't know where is the kernel source path...

```
sudo apt-get install linux-headers-`uname -r` binutils pkg-config build-essential  xserver-xorg-dev
```

---

### Post by telescopic on 2011-02-03
> **VyacheslavS said:**
> ```
sudo apt-get install linux-headers-`uname -r` binutils pkg-config build-essential  xserver-xorg-dev
```

Thank you. May i ask why I need to install these files? They are related to the kernel? Aren't kernels the file inside the folder /boot under the name something likes: "2.716...generic" ?

---

### Post by sciurognathi on 2011-02-06
And one more note, as I spent much more than 3 hours on this issue for a linux pendrive and solved it thanks to [snuffmeister]("http://ubuntuforums.org/member.php?u=1195571"):
[LIST]
[*]Blacklist *nouveau* by running
[*] 	Code:
 	sudo gedit /etc/modprobe.d/blacklist.conf 
[*]Add "blacklist nouveau" at the end; save and close.
[*]Then, run this little line of code which most tutorials are missing and for the love of me I can't figure out why....
[*]Also, I'd like to thank mrpeenut24 for [saving my sanity ]("http://ubuntuforums.org/showpost.php?p=9227114&postcount=5")
[*] 	Code:
 	sudo update-initramfs -u 
[*]This is mentioned in the blacklist.conf file, I think, but idiots  like me don't read that because we're just cool that way. If we did, we  wouldn't have had spent 3 hours on this issue and that just would have  been enjoyable.
[/LIST]
Again, all credits go to [snuffmeister]("http://ubuntuforums.org/member.php?u=1195571")

And one more thing from my side for a linux pendrive - here is a nice point: [https://wiki.kubuntu.org/X/Troubleshooting/Nouveau](https://wiki.kubuntu.org/X/Troubleshooting/Nouveau)
So, just edit the menu.lst find the line with "quiet splash" and add *nouveau.modeset=0*

---

### Post by telescopic on 2011-02-08
> **VyacheslavS said:**
> ```
sudo apt-get install linux-headers-`uname -r` binutils pkg-config build-essential  xserver-xorg-dev
```

As said in my last post, I follows the Page 4 in this thread and install the driver, it gives me the error message about the whereabouts of the kernel. Thanks to tips of VyacheslavS, I install the Linux header.

>uname -r
>sudo apt-get install linux-headers-"Output from above command"

then install the Nvidia driver for 64 bit; it installs the driver. But, when I reboot, Grubs runs fine, I see the logo "Ubuntu 10.04..." ,then falls on the shell prompte asking me to login. Then I type at prompte "sudo service gdm start". Xserver is not loaded. 

Why? Do i need to undo the blacklist procedure?

---

### Post by Oathanvil on 2011-02-20
Thank you I was able to install Nvidia Drivers manually through those commands using the Terminal.
 
However be advised you will need to write down the install insructions as your computer will boot to DOS and a username: & Password: Login
 
After that use the <dir> commnd to list so you cn see everything for peace of mind.
Now type <Downloads> then <dir> my Beta driver for the Nvidia card was downloaded by Firefox to the download folder by default.
 
Now use the Sudo commands as described and replace the above info with the current NVIDIA driver found in the downloads folder.

---

### Post by enakud on 2011-03-01
> **trespuntos said:**
> i was in the same situation as denali. after researching a little, this method let me install nvidia drivers. I hope it can help some of you


sudo nano /etc/modprobe.d/blacklist.conf

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

(remember last space)

sudo gdm-stop
sudo apt-get --purge remove nvidia-*

RESTART

(after this ubuntu boots with some graphical errors like white lines and incorrect resolution)

sudo gdm-stop
sudo apt-get --purge remove xserver-xorg-video-nouveau

RESTART

(after this, ubuntu boots  with no graphical errors BUT CANT GET INTO TERMINAL with gdm stopped so cant install nvidia drivers)

So heres the tricky part

sudo nano /etc/modprobe.d/blacklist-framebuffer.conf

and you need to comment 'blacklist vesafb' and add 'blacklist vgafb16' (both without quotes)

sudo nano /etc/initramfs-tools/modules

and add 'fbcon' and 'vesafb' (dont forget last space)

sudo update-initramfs -u

sudo nano /etc/default/grub

search for 'GRUB_CMDLINE_LINUX='  and ADD (dont delete) vga=771 or 795 (according to your resolution)

sudo update-grub

RESTART

sudo gdm-stop

now can enter terminal and install NVIDIA drivers. and they will install without errors.

Wow, thanks trespuntos ... this ACTUALLY WORKED. I've tried everything & was starting to feel pain from knocking my head against a wall.

Cheers,
enakud

---

### Post by inobe on 2011-03-01
or if you have an 8 series and up card that supports vdpau, just get the avenard repo [http://avenard.com/media/Home.html](http://avenard.com/media/Home.html)

[http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html](http://avenard.com/media/Ubuntu_Repository/Ubuntu_Repository.html)

it should get you the latest nvidia drivers soon as they are out of testing.

i believe you can add the testing repo to get unstable drivers.

if you guys are into mythtv, that's also useful.

make sure you add the correct repo for your version of k/ubuntu.

---

### Post by Swashbunglar on 2011-07-02
Thank you sir! I followed the instructions in opening post to install NVIDIA-Linux-x86_64-275.09.07.run on Ubuntu 11.04 Natty x64.
Worked like a charm and now back to my desktop safe and sound!
Just wanted to say thanks!

---

### Post by TheGeorgian on 2011-07-02
Hello All,  I recently installed Ubuntu 10.04 LTS. I decided to install the latest Nvdia driver manually because sometimes when I boot my computer all I get is a black screen. I have noticed from online posts that others are having this problem too. I won't go into too much detail about that because it may not be relevant to this thread. I have a GeForce 8400 GS. Anyways, I followed the steps on page 4 suggested by trespuntos. After the last restart in the instructions, I login as usual, open a terminal (using Applications-> Accessories) and type "sudo gdm-stop".  This just causes my screen to go black and eventually the screen hibernates. I rebooted the computer using the power button, logged in, and this time tried ctrl-alt-F1 first, resulting in the same black screen. So it seems that in my case, the previous steps outlined by trespuntos (no disrespect intended!) do not allow me to stop gdm, and install the nvidia drivers from the command line.  Any advice? I have been using Ubuntu for a few years and love it, but consider myself a noob. Also, this is my first post... so go easy on me!  Thanks!

---

### Post by hoppel118 on 2011-07-25
Thanks AndyBoy_LV, good job!

---

### Post by sacchidanand on 2011-11-03
Thank you very much.
This post solved my screen resolution problem.
Recently, I have purchased a new laptop Sony Vaio E-Series VPCEH25EN and install Ubuntu 10.04 LTS i386.
After that i come to know that i can not able to change screen resolution.
But, after following your guidelines i can successfully able to change my screen resolution.
Thank you once again.

---

