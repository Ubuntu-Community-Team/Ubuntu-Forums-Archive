---
title: "URGENT. Can't get my (nVidia Geforece Go 7950 GTX) Driver to work...!!!"
date: 2008-04-20
forum: Multimedia &amp; Video
---

### Post by seijiroikeda on 2008-04-20
Upfront, I would like to thanks in advance for any help.!

This is what I have:

Alienware Area-51 m9750 Laptop.
Video card: nVidia Geforce Go 7950 GTX.

Here it's my problem:

I tried almost everything to get my nVidia Driver to work.

First, I tried the "Restrictive Driver Manager" and it says "You hardware does not need any restricted drivers".

Second, I tried the "Add/Remove Application", searched for nVidia. I activated the NVidia binary X.org driver ('new' and 'legacy' drivers, and they just simple don't do anything.

Third, I went to nVidia's website, download the right Driver for my video card (Geforce Go 7950 GTX), place the file on my Desktop, then ran it from the Terminal using SUDO, and still doesn't work. I get:

- You don't appear to have NVIDIA GPU supported by the 169.12 NVIDIA Linux graphic driver installed in this system. For further details, please see appendix SUPPORTED NVIDIA GRAPHICS CHIP in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

- You appear to be running an X server; please exit X before installing. For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

- Installation has failed. Please see the file '/var/log/nvidia-installer.log' for details. You may find suggestions on fixing installation problems in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

Fourth, I went to Alberto's Milone website, downloaded his Script program, and it installed perfectly, but when I click on "Install the NVIDIA driver" and I get:

- There was an error in the installation process. You can see the log file /var/log/envy-installer.log

After all this, I've been searching for other methods, codes or any other way to make my video card's driver to work and enable the 3D effects.

Any repository sites where the may have the right driver for my video card (nVidia Gefore Go 7950 GTX "Not SLI Enable")?. Or maybe, to get the ENVY to work properly? Or any other idea other than what I've tried already?

Again, thanks in advance for any help here, its really appreciate it.

========================================================

This is what i get for the ENVY Report:

chino@chino-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371SB PIIX3 IDE [Natoma/Triton II]
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
chino@chino-laptop:~$ cat /var/log/envy-installer.log
python pulse.py nvidia 
root@chino-laptop:/usr/share/envy# python pulse.py nvidia
Envy - Version 0.9.10
ENVY ERROR: Nvidia card not found

---

### Post by chewearn on 2008-04-20
You appeared to be running linux inside virtualbox?  You will not be able to use nvidia driver inside virtualization.

---

### Post by seijiroikeda on 2008-04-20
WoW... Thanks a lot for that fast response...!!! I really appreciate it..!!!

Now, i'm not gonna ask you how you see that in my report, since it doesn't say anything about virtualbox? Or I guess thats the answer...:?:   Anyways, you are right.! I'm running ubuntu inside virtualbox... I'm gonna have to change my plans now....

Now my question is: 

If I set up a dual boot or create another partition, when instaling ubuntu what minimun size or hard disk should i provide for ubuntu in order to run perfectly using all the 3D effects and running some more applications as Beryl, etc...   I currently don't do much in Linux other than using the Terminal, but in the future i'm willing to swap from Vista to Linux... So what if I run short in memory in the future, can I extend the currently memory lets say (10GB NOW) and in the future i wanna give it (30GB EXTRA), can I do that having the Linux OS already installed? Or do i have to unistall it and reinstall it giving it more memory than before (FINAL MEMORY) in the HD?

Thanks.

---

### Post by chewearn on 2008-04-20
> **seijiroikeda said:**
> If I set up a dual boot or create another partition, when instaling ubuntu what minimun size or hard disk should i provide for ubuntu in order to run perfectly using all the 3D effects and running some more applications as Beryl, etc...   I currently don't do much in Linux other than using the Terminal, but in the future i'm willing to swap from Vista to Linux... So what if I run short in memory in the future, can I extend the currently memory lets say (10GB NOW) and in the future i wanna give it (30GB EXTRA), can I do that having the Linux OS already installed? Or do i have to unistall it and reinstall it giving it more memory than before (FINAL MEMORY) in the HD?

Thanks.

10GB for linux partition is sufficient, though I usually prefer 15GB or 20GB.  You also need about one to two times your system RAM for swap partition (e.g. if you have 2GB DDR, reserved about 2GB to 4GB swap).

If you are not sure how to allocate the partitions, let the installer automatically do this for you.  Before installing ubuntu, repartition your harddisk to free up say 20GB; leave the space unallocated (i.e. do not create another partition in the empty space).  Then choose the option "Largest continuous free space" during installation.

If later, you need more space, you can use a livecd (either the same one for ubuntu installation) or a third party livecd (e.g. [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)) to repartition your harddisk (there is no need to reinstall).

Here is a dualboot setup help page:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by seijiroikeda on 2008-04-20
> **AstalaVista said:**
> 10GB for linux partition is sufficient, though I usually prefer 15GB or 20GB.  You also need about one to two times your system RAM for swap partition (e.g. if you have 2GB DDR, reserved about 2GB to 4GB swap).

If you are not sure how to allocate the partitions, let the installer automatically do this for you.  Before installing ubuntu, repartition your harddisk to free up say 20GB; leave the space unallocated (i.e. do not create another partition in the empty space).  Then choose the option "Largest continuous free space" during installation.

If later, you need more space, you can use a livecd (either the same one for ubuntu installation) or a third party livecd (e.g. [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)) to repartition your harddisk (there is no need to reinstall).

Here is a dualboot setup help page:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

AstalaVista, thanks a lot man... I really appreciate your help.!

Now one last question, I didn't get this part: 

" You also need about one to two times your system RAM for swap partition (e.g. if you have 2GB DDR, reserved about 2GB to 4GB swap). "

I meant switching from Vista to Linux in the future, completely... Now you have to make yourself clear... lol... You confuse me with that... Sorry if I didn't make myself clear, but I think you didn't go for my question in that part, did you? Other than that, everything was clear.

Thanks...

---

### Post by chewearn on 2008-04-20
What I meant was swap partition (not swapping OS :smile:).  When you install ubuntu, you need a minimum of two partitions, one for root and one for swap.
[http://en.wikipedia.org/wiki/Swap_partition#Swapping_in_Linux](http://en.wikipedia.org/wiki/Swap_partition#Swapping_in_Linux)

---

### Post by seijiroikeda on 2008-04-21
Thanks a lot man, I really appreciate your help.! Thought I think my best option is to go with the Wubi option, and just install Ubuntu in a separate partition instead of using the VirtuaBox...!!! 

Thanks.

---

### Post by chewearn on 2008-04-21
> **seijiroikeda said:**
> Thanks a lot man, I really appreciate your help.! Thought I think my best option is to go with the Wubi option, and just install Ubuntu in a separate partition instead of using the VirtuaBox...!!! 


Wubi option allows you to install ubuntu in a file inside windows.  There is no separate partition involved. To put it another way, the linux filesystem is inside the windows filesystem.

This is good for dual boot, but if eventually you are looking for straight ubuntu only, it might be difficult to delete windows.  You have to first move the linux filesystem out of windows, before you can delete windows.

---

### Post by seijiroikeda on 2008-04-22
Thanks a lot man, it's working perfectly. Definitively the problem was the Virtual Box. I also Join the Virtual Box Forum, and for those foxes out there that are trying to runs full OpenGL or 3D effects, etc in your Linux, IT'S NOT POSSIBLE. They are currently developing a new VB, but not any time soon. Here it's the link: [http://forums.virtualbox.org/viewtopic.php?t=16](http://forums.virtualbox.org/viewtopic.php?t=16)

Thanks a lot AstalaVista, for all the help... It's really appreciate it...

P.D: I have another question now, I recently encounter a new error, I didn't want to post it here, but since you helped me out, maybe you know about this...!!!

After I install the Wubi, everything is perfectly running, except for the Sound... I've been searching all over the web, lots of results, but none of them work for me... It seems that any Linux Flavor after install, by default the SOUNDS in on "Mute", so I used:

> alsamixer

After this, I disable the "mute" ones pressing the "m". After that, went into the GUI, checked the Sound option, played around with it to see if any result, and none at all. 
Then, I went to RealTek.com, downloaded the driver for Linux, went into the Terminal and installed, but it rejected during the installation saying that it can't find Library...

It shows that the OS is recognizing the Sound Card hard drive, but for some reason there is no Sound coming from the speaker, but it does if I use the headphones... Any help here?

Thanks a lot.

---

### Post by chewearn on 2008-04-22
Good to know things are working for you.

Unfortunately, sound in one area I'm don't have much expertise.  I know very little about the existing alsa sound framework, and nothing about the new pulse audio used in hardy 8.04.

However, there are a few general things you can check.

1. Check which kernel modules related to sound are loaded:
```
lsmod | grep snd
```2. Find out the exact sound device detected:
```
lspci | grep Audio
```Other than that, I suggest you go ahead and post a new thread with a descriptive title about your sound problem.   You should add the output of the commands above in your new thread.

---

