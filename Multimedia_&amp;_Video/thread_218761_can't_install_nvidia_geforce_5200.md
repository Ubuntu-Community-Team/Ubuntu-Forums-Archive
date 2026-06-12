---
title: "can't install nvidia geforce 5200"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by ohmyiv on 2006-07-19
Hi,

i have a GeForce 5200 video card that Ubuntu doesn't seem to like.  I've tried the nvidia installation techniques posted here, but they just crash my xserver. ](*,)  I'm not sure what else to do.  Ubuntu runs fine off the onboard graphics, but I woujld like to do other things, like use google earth.  I should also note, WinXP works fine when I boot from the video card.  When I switch my bios to pci, Ubuntu locks up at the hardware driver loader during startup. Any help would be greatly appreciated.  I can provide as much info as possible to get my card to work.

I have:
HP 2.93GHz Celeron
Nvidia GeForce 5200 FX (pci)
1G ram
dual booting Ubuntu Dapper and XP Home SP2 

Oh, if it's any help, when I installed Dapper, I had to use the boot line: acpi=off pci=noacpi

Thanks for the time...I'm new to linux, so bear with me.

---

### Post by coffeecat on 2006-07-19
My Geforce 5200 card is working fine in Ubuntu Dapper. The only difference is that it is an AGP card, not PCI. You don't say which posted method you tried. I used [Automatix]("http://ubuntuforums.org/showthread.php?t=190025").

---

### Post by tseliot on 2006-07-19
1) Set the BIOS to use the PCI card (nvidia) and connect your monitor to it.

2) Boot in Recovery Mode (you can boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer)

3) type:
```
lspci | grep VGA
```

and write down the output on a piece of paper (there's no need to post it right now).

OR (if you don't want to use a piece of paper)
```
lspci | grep VGA > /home/your_username/videolist.txt
```

OF COURSE replace "your_username" with your username.

You will find the output of that command in /home/your_username/videolist.txt

You might need that output later

4) Type: 
```
sudo nano -w /etc/X11/xorg.conf
```

Put a # before the BUSID in the section Device
Set the driver to "vesa"

CTRL+X to exit

5) reboot:
```
sudo reboot
```

and boot as usual.

If that doesn't work (explain me what happens) please post the output you got in step 4

---

### Post by Plankman on 2006-07-19
have you tried using the nvidia-glx-legacy driver? I have a geforce 5500 and also had problems till i tried the driver. You will probably have to edit  /etc/X11/xorg.conf as when I installed it, it somehow got that it was an ATI card and the address was 0:5:0 instead of 1:0:0.

Hope you come right

---

### Post by ohmyiv on 2006-07-19
Thanks for the quick replies.

Coffeecat, I tried methods 1 and 2.  I didn't try 3 because it states that if 1 and 2 don't work, 3 is NOT going to solve my problem. I also tried easy ubuntu and automatix.  

TSEliot, I can't boot in recovery mode.  When I change the bios to pci and boot into recovery mode, it keeps rebooting the computer over and over again.  I'm not sure what to do now.


Plankman, I have tried to, but my xserver crashed, so I figured I'd just ask for help.

---

