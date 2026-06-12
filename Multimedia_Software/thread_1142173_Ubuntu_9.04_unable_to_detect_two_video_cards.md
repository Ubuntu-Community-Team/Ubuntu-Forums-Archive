---
title: "Ubuntu 9.04 unable to detect two video cards"
date: 2009-04-28
forum: Multimedia Software
---

### Post by agp on 2009-04-28
Hi,

I have HP xw9300 machine (AMD Operon 64-bit).
I am trying to install two video cards ( NVidia Quadro NVS 290) but Ubuntu 9.04 is detecting only one. I tried with a cople of different cards but it is recognixing only one.
(Tried two same cards, two diffrent cards)

With the same hardware, RHEL 5.3 and Fedora 10 are recongnizing both cards properly.

Thanks,

---

### Post by inzpektor on 2009-05-04
> **agp said:**
> ...but Ubuntu 9.04 is detecting only one. I tried with a cople of different cards but it is recognixing only one.

I also have two Nvidia Quadro NVS 290 cards plus 3 screens attached.  I am facing some severe XServer errors.  I first noticed the errors when rebooting into a fresh wubi disk-image.  When that failed with some "ubuquity-dm, line 280, in <module>" and subsequent "XStartupError", I tried to boot into the 9.04 liveCD, and that failed as well (also on trying to start X).

Weirdest thing is that I've actually been running 9.04 for a couple of days on this machine without any problems, but that was an 8.10 installation that I upgraded to 9.04.  So it's clearly related to the setup on the liveCD/Wubi default profile.

I'm back in Windows now, so I won't be able to give you an lshw/lspci/xorg.conf, but I can report that I saw some rather odd things in the Xorg.0.log; it seemed like it was unable to detect the pointer-device, although I saw the mouse being properly detected during boot.  In the bottom of the log it says that it did find screens (Screen sections in xorg.conf), but none of them were properly configured.

Despite what agp says, I can see that Xorg does detect both video-cards (2xNVS 290) properly.

I also tried to enable all repos in sources.list and do an apt-get install --reinstall xserver-xorg to no avail.

I also tried to do a dpkg-reconfigure xserver-xorg to no avail.

I've tried with the new trimmed down xorg.conf, and one where I use the nv-driver (the nv-driver gives a black screen and complete system freeze-up - dead getty)

---

### Post by pgilmon on 2009-05-04
Hi,

same problem here with a Dell Precision T3400. Could you boot with 8.10 live-cd? Do you think we could add some parameter at boot time so that it works?


Regards,

Pablo

---

### Post by unf on 2009-05-04
I have 8400GS + 8600GT working without problem.

---

### Post by pgilmon on 2009-05-05
The machine I'm having problems with has two nvs 290.

---

### Post by inzpektor on 2009-05-05
> **pgilmon said:**
> Could you boot with 8.10 live-cd? Do you think we could add some parameter at boot time so that it works?

I just tried to boot the 8.10 LiveCD, and that fails too.  I was previously running Ubuntu off of a USB-stick (which I had installed Linux on on another computer, why I didn't see this problem).

So this is a problem that has been around for some time.  As I mentioned previously, booting into an already installed Ubuntu works fine (No X-problems) - it is specifically something with the LiveCD (9.04 as well as 8.10, apparently) that causes it to fail.

I'm thinking - does HAL work differently on LiveCDs than on installed systems, cause it smells a bit like a device-problem of some sort (remember the pointer-device error I mentioned in a previous post).  Does modern operating systems still have issues with interrupt-allocation (something I remembered from the floppy-era), or what?

---

### Post by pgilmon on 2009-05-05
I have booted successfully with a 8.04 live-CD. Not a single problem.

Is there any way to install a complete 9.04 without a GUI installer with the Live-CD or do I have to dowload the alternate install CD?

---

### Post by pgilmon on 2009-05-06
OK, I have finally been able to make 9.04 work. The system came with two NVS 290 dual cards. I have removed one and now everything works. I don't need 4 screens (for now ;) ) so it is not a big issue.

---

### Post by pgilmon on 2009-05-07
Another thing: I wasn't able to boot the live-CD with two screens attached to the same card. After installing with the alternate CD I had the same problem with the installed system: X wouldn't start. I disconnected one of the screens and it worked. After installing NVIDIA proprietary drivers I was finally able to start X with two screens and do DualView (i.e.: extend the desktop across both screens).

---

### Post by inzpektor on 2009-06-15
Still no solution? :-)  I forgot to mention that I'm installing Ubuntu on a work machine, so I can't / mustn't open the casing (in order to remove one of the NVS 290 cards).

Furthermore, I have to install Ubuntu via Wubi, so that I don't change the partions on the HDD and so that I don't delete the existing operating system.  That's why I can't use the alternate install CD and do a text-install.

I can see that the installation fails after the reboot into the newly created Ubuntu-image when it's trying to start X, which is launched from a program called ubiquity-dm.  Is there something I can install (like the Nvidia proprietary drivers) and then re-run this ubiquity-dm program in order to have it finalize the installation?

---

### Post by pgilmon on 2009-06-16
Well, my experience is that X won't start even with the nvidia drivers if you have both cards attached. Thus, if you cannot open the case then my solution is not an option for you. Sorry.

---

### Post by pgilmon on 2009-06-16
BTW, you know that you can resize you existing OS's partition so that you can create a partition for Ubuntu without deleting you current operating system, don't you? It's easy and it can be done both with the alternate and the normal installation CD. Just ensure that you have defrag the drive using windows before proceeding.

---

### Post by markbuntu on 2009-06-16
You need to use the safe graphics option in the installer. F4 when you get the first installation screen. This will use the VESA driver on your first card and ignore the other one. Once you get everything up and running with that you can install the nvidia driver and set it up for two cards.

---

### Post by inzpektor on 2009-06-24
> **markbuntu said:**
> You need to use the safe graphics option in the installer. F4 when you get the first installation screen. 

Sounds good, but how do I specify the safe graphics option when installing through Wubi?  AFAIK, you can't install Ubuntu as a disk-image on an NTFS partition through the normal installer.?.

---

