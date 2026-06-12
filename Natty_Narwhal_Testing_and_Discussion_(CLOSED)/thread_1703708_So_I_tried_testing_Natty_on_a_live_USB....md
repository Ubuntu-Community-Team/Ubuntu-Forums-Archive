---
title: "So I tried testing Natty on a live USB..."
date: 2011-03-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quadunit404 on 2011-03-09
Using [this]("https://wiki.ubuntu.com/Unity/InstallUSBKey") guide I decided to try testing out Natty on physical hardware as Unity under VirtualBox is really, really slow.

The installation to my selected USB - a 16GB Corsair Voyager - went fine and the persistence file was created without problem. When I booted the USB drive, I installed the proprietary Broadcom driver so I can use wireless Internet, then connected to my wireless router. Then I noticed Jockey wouldn't let me install the nVIDIA driver. I tried installing nvidia-current through Synaptic, and then Natty slapped me in the face, saying I had no free space left on the device (aka the persistence file.) And that was all because I installed the Broadcom driver.

*Wonderful.*

If anyone knows how to make a live Natty USB and use all 16GB available on that drive (possibly through installing it) please tell me. I want to know how Unity will perform on my physical machine before I upgrade to Natty in April.

---

### Post by cariboo on 2011-03-09
There's a whole thread on your exact problem [here]("http://ubuntuforums.org/showthread.php?t=1636650&highlight=usb+install")

---

### Post by Quadunit404 on 2011-03-09
Looking through that thread, I stumbled upon [this post]("http://ubuntuforums.org/showpost.php?p=10201288&postcount=29") and it had EXACTLY what I needed to do :D

Now I have a 9GB casper-rw partition thanks to that. Awesome. Just gotta wait for my custom kernel to finish compiling and I'm good to go.

---

### Post by beew on 2011-03-09
I don't think live usb supports installation of proprietary graphic cards. Neither does a live usb supports kernel updates. So, no, you can't install the Nvidia driver in a live usb via jockey.

To really test Natty on your hardware you need a full installation. Find an external hard drive and install it into it just as you would an internal drive but make sure you install it in the correct target disk and also the bootloader has to be installed in the target as well. Choose partition manually. (you can do this with an usb but you would face with the same size limitation and also it is slow to run from an usb, an external hard drive is much faster)

---

### Post by fabricator4 on 2011-03-10
> **Quadunit404 said:**
> 
If anyone knows how to make a live Natty USB and use all 16GB available on that drive (possibly through installing it) please tell me. I want to know how Unity will perform on my physical machine before I upgrade to Natty in April.

I installed Natty onto an 8 GB drive, with a 3 GB home partition and a small swap.  Of course it boots slowly, but it's not horrendous, and some operations (such as searching applications) are unnecessarily sluggish.  Overall though, it's quite usable, and sometimes I boot it up to play and finish up doing quite a bit of work on it.  I'm finding the alpha3 quite stable on my 900SD, but it throws a curve ball to mess me up occasionally.

Updates are very slow, as USB drives write at only a small fraction of their read speeds, so unpacking and installing updates is best done when I can go and do something else for a while. 

Basically, just do the install as you would for any hard drive, partitioning and all. You can put grub on the MBR of the USB drive if you wish, for booting off USB on any machine.  On the main machine I test on however, I ran update-grub so it appears in the grub boot menu off the hard drive and I don't have to worry with USB booting.  I've installed all three alphas this way, and it was great having a portable drive to move from machine to machine, and having a separate /home partition made upgrading to each new release quite painless.

Chris

---

### Post by Quadunit404 on 2011-03-11
Well using the casper-rw partition I made and Synaptic, I managed to get both the Broadcom drivers and NVIDIA drivers installed on the live Natty USB. Well now that I experienced both GNOME Shell and Unity on real hardware, I can say that I like GS better.

There never really was a doubt.

---

### Post by beew on 2011-03-11
> **Quadunit404 said:**
> Well using the casper-rw partition I made and Synaptic, I managed to get both the Broadcom drivers and NVIDIA drivers installed on the live Natty USB. Well now that I experienced both GNOME Shell and Unity on real hardware, I can say that I like GS better.

There never really was a doubt.

Then it must be a new feature that I am not aware of because my understanding is that you can't install Nvidia driver (or any proprietary graphic card) on a live system (I have tried with 10.04 and 10.10 and it broke my live usb everytime, then I found out it is not supported) On the other hand, installing broadcom WIFI card in a live usb has always been ok. So does live usb support kernel updates too now?

---

### Post by ktp on 2011-03-12
There were some issue with installing proprietary graphic drivers, there is/was bug report on this.  But if you have space and your USB is setup with persistence and casper-rw partition, you can manually install them ok (using synaptic or apt-get or your fav package tools).  If you boot with live USB, jockey will not show any proprietary drivers because people try to install it didn't understand why it failed.

---

### Post by beew on 2011-03-12
> **ktp said:**
> There were some issue with installing proprietary graphic drivers, there is/was bug report on this.  But if you have space and your USB is setup with persistence and casper-rw partition, you can manually install them ok (using synaptic or apt-get or your fav package tools).  If you boot with live USB, jockey will not show any proprietary drivers because people try to install it didn't understand why it failed.

Actually jockey did show proprietary drivers and offered to install them, but it would hang during installation and at that point the liveusb broke (10.04 and 10.10).(If there was no persistence the live usb would survive on reboot but there would be no point in installing anything without persistence, if the usb was persistent then the OS was destroyed) 

Does a Ubuntu live usb support kernel updates now?

I have since found that a better way to test drive a Linux OS would be to do a full install in an external hard drive. Then it won't be subjected to the size and speed limitation of usb flash drives and casper (Also some Linux distros don't support persistence and it may be possible, but not worthing the troubles to add them manually)

---

### Post by ktp on 2011-03-12
The jockey change is new to 11.04.  There were other bugs fixed, along with not offering proprietary drivers when on live usb/cd mode, but can't remember what they were.  

I have never tried upgrading kernal in live usb since i only really use it for temporary/quick boot in to specific version or I don't really want to upgrade my dev install.  Installing into external or large usb drive is best option, I think, if you really want to "keep up" with dev builds and going to use it frequently.  It will be also little faster, as far as boot time goes.

---

