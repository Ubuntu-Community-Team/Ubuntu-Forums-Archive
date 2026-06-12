---
title: "install natty on USB HDD"
date: 2011-04-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jipbuntu on 2011-04-05
Hi
I have installed Natty Beta on my 320 GB external hard drive . The hard drive has 3 partitions and the Ubuntu is installed in the third partition. At the time of installation I chose the location for bootloader installation as /dec/sdc5 (which is the partition i chose for my ubuntu installation). /dev/sdc being my external hard disk

I am able to boot my ubuntu installation in the laptop where I created the installation-lenovo T400 but I cannot boot it in other PCs though I choose the USB boot option from the BIOS. I just get a blank screen.

Should I have chosen the site for bootloader installation as /dev/sdc instead of /dec/sdc5?
Will that solve the problem. If I do so will my HDD still be readbale by windows?

Help

---

### Post by oldfred on 2011-04-05
Welcome to the forums. 

If you only have the Natty on the external you should have installed the grub2 boot loader to the MBR of sdc. What code is in the MBR will not change whether windows can read the first partition.

You can install it easily just by booting into your Natty install, then install to sdc.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdc"  then just run:
sudo grub-install /dev/sdc
#If that returns any errors run:
sudo grub-install --recheck /dev/sdc
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by jipbuntu on 2011-04-05
Hi oldfred
Thanks for your reply
I moved over to my PC which did not boot from the USB HDD. So I did a fresh install of Natty on the same partition after formatting and repartioning. In this PC it was /dev/sdb3.
I chose the bootloader installation on /dev/sdb
After reboot, still after chosing the USB HDD from the boot menu, itshowed the black screen with the blinking cursor on left corner
What do I do?

---

### Post by uRock on 2011-04-05
Moved to NNT&D

---

### Post by jipbuntu on 2011-04-05
Hi urock
I didnt quite understand your reply. Could you elaborate.
PS: IM a newbie to the forums and to Ubuntu.

---

### Post by uRock on 2011-04-05
> **jipbuntu said:**
> Hi urock
I didnt quite understand your reply. Could you elaborate.
PS: IM a newbie to the forums and to Ubuntu.
I moved your thread to the proper sub-forum. Natty Narwhal threads belong in the Natty Narwhal Testing and Discussion sub-forum as it has not yet been officially released.

---

### Post by kansasnoob on 2011-04-05
You ask a lot of questions, some are difficult to understand. Certainly you should install grub to the MBR of the USB drive, but the drive designation may change for a number of reasons: 

[http://ubuntuforums.org/showthread.php?t=1659542](http://ubuntuforums.org/showthread.php?t=1659542)

But it even sounds like you're moving the USB drive from one machine to another. Generally a "hard-install" will not work from one machine to another (unless the hardware is incredibly similar). That's what "live-installs" are for.

So, the first thing to do is slow down and explain completely what you're doing, and what you're trying to accomplish :)

---

### Post by beew on 2011-04-05
> **jipbuntu said:**
> Hi
I have installed Natty Beta on my 320 GB external hard drive . The hard drive has 3 partitions and the Ubuntu is installed in the third partition. At the time of installation I chose the location for bootloader installation as /dec/sdc5 (which is the partition i chose for my ubuntu installation). /dev/sdc being my external hard disk

I am able to boot my ubuntu installation in the laptop where I created the installation-lenovo T400 but I cannot boot it in other PCs though I choose the USB boot option from the BIOS. I just get a blank screen.

Should I have chosen the site for bootloader installation as /dev/sdc instead of /dec/sdc5?
Will that solve the problem. If I do so will my HDD still be readbale by windows?

Help

I think the way you install your bootloader is correct. If you put it in sdc instead Natty will control grub, I take it is not what you want .

I have the same setup, I am able to boot it everywhere. So maybe there is some problem with your other PC. Can you test it on a third one somehow (like ask your friend)?

[B]
EDITED: [/B]OK, I assume that you have a multiboot system, but I realized that you haven't told us what are in the other partitions. Now if you are only booting from Natty (the other two partitions are not bootable) then you should indeed put the bootloader in sdc (at least I know that would work, I don't know about putting it in sdcX, I use that as a way to prevent Natty from taking grub control from Maverick installed on the same drive)

---

### Post by oldfred on 2011-04-05
If you get the cursor on the left you may have booted. Try holding shift down from BIOS until grub menu appears, if you have only one system or grub's os-prober has only found one on initial install.

Video issues have been an issue lately.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by beew on 2011-04-05
> **kansasnoob said:**
> 
  Generally a "hard-install" will not work from one machine to another (unless the hardware is incredibly similar). That's what "live-installs" are for.

No, no no and a final empathical NO! :)

That would be correct for Windows. But with Linux you can do a full install in an external drive and pretty much plug it in any PC and it just works. I have an external drive with 4 Linux OS's (Ubuntu 10.10, 11.04 beta, Fedora 14 and something called qomo. Have tried it on at least 6 or 7 machines with completely different specs (labtops, desktops, Nvidia , Intel or ATI graphic cards, you name it) It just works.

The live -install has a lot of limitations in terms of speed and system level upgrade, installing proprietary graphic drivers, etc (even though I don't install those in the external to keep it portable, but I could if I want to test a graphic card)

> So, the first thing to do is slow down and explain completely what you're doing, and what you're trying to accomplish :)I know exactly what he is doing cause that is what I do. :)  

**Edited **Opps probably not exactly, see edited on my last post.

---

### Post by kansasnoob on 2011-04-05
> **beew said:**
> No, no no and a final empathical NO! :)

That would be correct for Windows. But with Linux you can do a full install in an external drive and pretty much plug it in any PC and it just works. I have an external drive with 4 Linux OS's (Ubuntu 10.10, 11.04 beta, Fedora 14 and something called qomo. Have tried it on at least 6 or 7 machines with completely different specs (labtops, desktops, Nvidia , Intel or ATI graphic cards, you name it) It just works.

The live -install has a lot of limitations in terms of speed and system level upgrade, installing proprietary graphic drivers, etc (even though I don't install those in the external to keep it portable, but I could if I want to test a graphic card)

I know exactly what he is doing cause that is what I do. :)  

**Edited **Opps probably not exactly, see edited on my last post.

Really :confused:

Your edit aside I simply can NOT see how an installed OS is going to adapt from VIA graphics to Intel graphics to ATI and then to Nvidia, and back and forth with no issues whatsoever. That's not been my experience.

---

### Post by beew on 2011-04-05
> **kansasnoob said:**
> Really :confused:

Your edit aside I simply can NOT see how an installed OS is going to adapt from VIA graphics to Intel graphics to ATI and then to Nvidia, and back and forth with no issues whatsoever. That's not been my experience.

Use the FOSS drivers. :)

---

### Post by jipbuntu on 2011-04-06
Hi beew,
I think you can understand my problem.
I have a PC and a laptop.
I booted a live USB Natty and used it to perform a full installation in my external USB HDD. When I reboot, I selected USB boot option but I just got a blank screen with a blinking cursor on left to corner.
PS-I tried it with Bootloader on the main USB HDD as well as on the partiton containg my ubuntu installation. Neither worked
I booted the same external HDD on my laptop and Lo! It booted up to a full ubuntu system.
I think there is something that needs tweaking in my PC, though it has USB boot capability
Please help?

---

### Post by jipbuntu on 2011-04-06
Hi 
I want to let you know that my PC can boot into a live USB installation without any problem.
May be its a problem with the bootloader????
 
Urgent help needed????

---

### Post by oldfred on 2011-04-06
That still may be a video driver issue. The laptop works as the default driver works for it, but then does not work for the desktop.

What video card do you have.

sudo lshw | grep -A 11 display
or 
lspci -nn|grep VGA


One user who did have different graphics did this little script. ( have been trying to help another but his is even more complex and it does not seem to work for him). Ways to change Video:
Boot using recovery mode & 'Reconfigure graphics' or
Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.
[http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/](http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/)

---

