---
title: "Please help me!!"
date: 2009-02-25
forum: Networking &amp; Wireless
---

### Post by moiss25 on 2009-02-25
Im a new person to Ubuntu and im having issues with my wirelless connectivity. So i would like to tell me who can i fix it??

---

### Post by albandy on 2009-02-25
what kind of issues?

---

### Post by moiss25 on 2009-02-25
it just doesnt show any available wirelless connections? At the other hand i dont have a problem with that on windows.. i think it's more about the drivers ...

---

### Post by albandy on 2009-02-25
What wireless card if attached or wireless chip is installed on your computer ?

do "sudo lspci"  in the console and paste the result here:

sudo lspci

---

### Post by moiss25 on 2009-02-25
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
alexandros@ubuntu:~$

---

### Post by albandy on 2009-02-25
first type
sudo aptitude install b43-fwcutter

If ask for somethink press ok
then type
sudo modprobe bcm43xx

now reboot

---

### Post by moiss25 on 2009-02-25
and that means???

---

### Post by albandy on 2009-02-25
This is what you should type to install your wifi card driver

---

### Post by moiss25 on 2009-02-25
it says "Module bcm43xx not found"

---

### Post by albandy on 2009-02-25
simply reboot

---

### Post by moiss25 on 2009-02-25
which is the next step?

---

### Post by albandy on 2009-02-25
now your wifi should work

---

### Post by moiss25 on 2009-02-25
which is the next step?

---

### Post by moiss25 on 2009-02-25
like i said  before something wasnt found that you said to me to type.. and it looks like the same situation..Unless i dont do it properly?? i go to network configuration and wireless  networks and it doesnt show any wirelless connections

---

### Post by albandy on 2009-02-25
try this again:
sudo modprobe bcm43xx

---

### Post by moiss25 on 2009-02-25
it says "FATAL: Module bcm43xx not found."

---

### Post by moiss25 on 2009-02-25
what should i do now??

---

### Post by deltaiscain on 2009-02-25
Are you sure it isn't linked to a restricted driver? go to system, administration, and then Hardware Drivers. if you see something wireless, click on it and hit activate. When that's done, reboot.

---

### Post by albandy on 2009-02-25
the module installs in 2.6.24-17-generic instead of 2.6.27-11-generic
so I think the package is outdated
I'll search for a solution

---

### Post by moiss25 on 2009-02-25
well.it is now activated. But still the same. I think i dont do it properly. Am i supposed to go to wireless connections and see my wireless conne and connect to it???

---

### Post by moiss25 on 2009-02-25
thank you albandy!

---

### Post by moiss25 on 2009-02-26
Any other ideas?? I need to fix this, please..

---

### Post by albandy on 2009-02-26
use 2.6.27-9 kernel instead of 2.6.27-11 (select it on grub menu), The 2.6.27-11 kernel module for your wifi is not ready yet

---

### Post by moiss25 on 2009-02-26
sorry i didnt get that. could you be more specific??please

---

### Post by albandy on 2009-02-26
When you boot te computer a menu is diplayed, there you can select between different kernel versions and os.

If you can't see it, a message will appear saying that pressing esc key you will be able to enter de grub menu.

---

### Post by moiss25 on 2009-03-25
I wonder if The 2.6.27-11 kernel module for my wifi is ready? Please answer me???

---

### Post by blausand on 2009-03-25
Man, when i spotted this thread in the main Forums page, i was pretty sure it was meant to be a bad example announced with 
_"Please avoid meaningless headers when posting"! _
To my surprise, it was just the newest post.

Please, man, never ever title a post with something like "Please help me!!".
I don't want to be offensive, but will you please as anybody else here

[B]-=- Take your time to make your post, and read some standard forum rules at least once in your lifetime! -=-
[/B]
You will find more help then.
Thanks a lot, 
blausand

---

### Post by moiss25 on 2009-03-25
can anybody answer me??

---

### Post by moiss25 on 2009-04-12
Can anybody tell me if the program for my wifi is ready to download? please answer me...

---

### Post by moiss25 on 2009-04-12
Does an expert do me a favour and answer me a question?????? The funny part is that the forum is very helpful..

---

