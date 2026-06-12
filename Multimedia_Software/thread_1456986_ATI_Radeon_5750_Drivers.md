---
title: "ATI Radeon 5750 Drivers"
date: 2010-04-18
forum: Multimedia Software
---

### Post by mitchewr on 2010-04-18
Ok, so I just installed Ubuntu 64 bit (I had 32 bit before) and I want to get my graphics card working.  I have an ATI Radeon 5750 hd card.  I tried to use the proprietary drivers from "hardware drivers" but I get a watermark in the bottom right hand corner of the screen and the resolution is terrible.  Also, the whole screen seems to be vibrating, which kills the eyes, so I got rid of that driver.

I also tried to download and install the driver from ATI website [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")  but ubuntu couldn't open the pakage.  I gave me some error message about the "encoding text" or something like that.  

So how (if it's possible) do I get my video card working so that I can use compiz and run 1080 resolution?  I have been through tons of threads but none of them helped my any.

Thanks in advance.

---

### Post by Yellow Pasque on 2010-04-18
The easiest way is to install Ubuntu 10.04/Lucid and just use the proprietary ATI driver that comes with that.

If you want to install the drivers from the ATI site on Karmic, see: [http://ubuntuforums.org/showthread.php?t=1409467](http://ubuntuforums.org/showthread.php?t=1409467)

---

### Post by mitchewr on 2010-04-18
> **Temüjin said:**
> The easiest way is to install Ubuntu 10.04/Lucid and just use the proprietary ATI driver that comes with that.

If you want to install the drivers from the ATI site on Karmic, see: [http://ubuntuforums.org/showthread.php?t=1409467](http://ubuntuforums.org/showthread.php?t=1409467)

  See I tried to install the 10.04 beta last night, but every time it it would start to load the installer and then just go to a black screen and sit there.  I had to manually reboot the computer (I tried this several times).  I know the disc is good b/c a friend of mine used the same disc and it installed perfectly on his computer.

---

### Post by Yellow Pasque on 2010-04-18
> **mitchewr said:**
> I know the disc is good b/c a friend of mine used the same disc and it installed perfectly on his computer.
Your computer may use different files on the disc, so just because it works on one computer, it does not verify the disc integrity.

At any rate, you can upgrade to Lucid with your existing Karmic install. [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by JuhaL on 2010-04-21
Ubuntu 10.04 64bit daily-2010-04-19 wont work with Ati Radeon HD 5750, Asus M4A79 Deluxe AMD Athlon 7750 MOBO/CPU.

Install start but ends with black screen/no singnal.

Have tried several builds during last weeks including Alternate-install.

Drivers downloaded directly from ATI worked several days/sertain build.

Sabayon 5 -64 works 90%, Windows 32bit 100%.

Anybody has an idea whats going on?

best,
juha

---

### Post by markbuntu on 2010-04-21
The Xserver was just upgraded but it has a major memory leak so you might want to wait until they figure out what to do about that before you try again, like maybe next week's release. By that time other stuff should be figured out also.

---

### Post by JuhaL on 2010-04-22
Ok, thanks!

Switching to good old Nvidia GF7950GT for waiting time.

/j

---

### Post by c-roc on 2010-05-05
so.... what would I look for to determine a good time to upgrade to 10.4 (being a 5750 owner)

---

### Post by Yellow Pasque on 2010-05-05
If you own a 5750, you should either install Catalyst 10.4 in your current distro or upgrade to Lucid (which has Catalyst 10.4 built-in).

> The Xserver was just upgraded but it has a major memory leak so you might want to wait until they figure out what to do about that before you try again
The glx 1.4 patches were reverted and the memory leak only affected open-source drivers using DRI2 anyway.

---

