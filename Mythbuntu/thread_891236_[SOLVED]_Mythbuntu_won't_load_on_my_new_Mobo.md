---
title: "[SOLVED] Mythbuntu won't load on my new Mobo"
date: 2008-08-15
forum: Mythbuntu
---

### Post by bmwman on 2008-08-15
I finally got all the parts for my new HTPC and of coarse I am so excited. I put it all together real quick. Then I tried to load Mythbuntu but it hangs 20 sec after I start it. I tried Live environment or Install - same thing. It gets to a shell and it just says BusyBox v1.1.3 Built in Shell(ash) then on next line it says "(initramfs)_" and a blinking cursor!

What do I need to do to make it load? Is the problem with the Ram since it fails at initramfs? I know the system works because i booted from Vista disk and works fine.

Here're the specs GIGABYTE GA-EG43M-S2H LGA 775 Intel G43 HDMI Micro ATX Intel Motherboard -, 
Intel Core 2 Duo E8400 Wolfdale 3.0GHz 6MB L2 Cache LGA 775 65W Dual-Core Processor
G.SKILL 2GB (2 x 1GB) 240-Pin DDR2 SDRAM DDR2 800 (PC2 6400) Dual Channel Kit Desktop Memory .

PLS HELP!

---

### Post by Liquidtricity on 2008-08-15
I know you just built and loaded stuff on the box for the first time but have you tried making sure that the BIOS is set to factory defaults or whatever it lists as defaults? I have had problems similar to this with Debian and that was the issue.

---

### Post by bmwman on 2008-08-15
I know that everything works because i'm currently loading XP on it :(

At least M$ OS works, as much as I hate it.
:(

---

### Post by tamoneya on 2008-08-15
first run RAM test for a couple of hours (at least 2 runs).  Then try using the alternate install CD.  Also give safe graphics mode a try.  You can access this from the boot options menu which i believe is F4 at the CD boot prompt.

---

### Post by bmwman on 2008-08-15
But the RAM works tho. XP just finished loading. I'm trying the standard Mythbuntu CD, I guess i need to try the alternate too. Whats the difference anyway?

---

### Post by tamoneya on 2008-08-15
> **bmwman said:**
> But the RAM works tho. XP just finished loading. I'm trying the standard Mythbuntu CD, I guess i need to try the alternate too. Whats the difference anyway?

It has a non graphical installer.  It is less error prone.  Also you should always do a memtest on a new computer.  While it may be possible to get an OS up and running on bad ram you can get stability issues down the line.

---

### Post by bmwman on 2008-08-15
I guess I'll run the memory test. I just tried Mythbuntu 8.04, 8.04.1 and a regular Ubuntu 8.04 and all get to the same error.

---

### Post by bmwman on 2008-08-15
I updated the BIOS from XP and  then rebooted. Now the damn thing doesn't even turn on. I push the power button, light comes on, checks the CD and HDD and goes off again. Keeps cycling. WTF.

:((

---

### Post by tamoneya on 2008-08-15
did xp give any errors while flashing.  An improperly flashed bios is more or less unrecoverable.  If this is the case you are best of trying to get a return.

---

### Post by bmwman on 2008-08-16
No errors, it loaded fine and then ask to reboot. I guess I need to return the mobo now.

---

### Post by ian dobson on 2008-08-16
Hi,

Try shorting the CMOS battery before sending it back. 
In the future don't try flashing the bios from XP it doesn't work that well. GigaByte have the Q-BIOS function in the bios that lets you flash the bios saved on a Floppy/USB stick.

Regards
Ian Dobson

---

### Post by bmwman on 2008-08-16
I already tried that, didn't work. Well, back in the box and have to wait again for the replacement :(

---

### Post by bmwman on 2008-08-22
I'm supposed to receive my replacement motherboard today. I was looking online and found some posts that the Intel GMA X4500 video chipset might have issues with Linux, since it's so new. Does anybody have one of these or do you know if there're issues with that?

I really hope it'll work, gonna find out tonight.

---

### Post by bmwman on 2008-08-22
Well I got the replacement and it's doing the same thing. I tried the new Mythbuntu 8.10 disk and didn't crash but it just gets black screen after finish loading. What should I do?

:(:(

---

### Post by bmwman on 2008-08-22
Is there a way to install in text mode or whatever, with no GUI, and then install the video drivers after?? That might be the way to go?

---

### Post by ozybushwalker on 2008-08-22
Your problems sound similar to those reported in [https://bugs.launchpad.net/mythbuntu/+bug/205849]("https://bugs.launchpad.net/mythbuntu/+bug/205849")
and [https://bugs.launchpad.net/mythbuntu/+bug/204057]("https://bugs.launchpad.net/mythbuntu/+bug/204057")

I went back to Mythbuntu 7.10 because I couldn't ever get 8.04 to work and got too tired of trying to figure out why. Because your hardware is so new that might not be an option for you.

---

### Post by bmwman on 2008-08-23
My new nice motherboard is going back to NewEgg. I already ordered another one which should work out of the box but it's not as nice as this one and supposebly can't really handle BlueRay which i was planning to use sometime in the future.

For now I need a working machine.
:(

---

