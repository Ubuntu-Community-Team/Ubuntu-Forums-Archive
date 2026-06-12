---
title: "Can't install ubuntu 11.04"
date: 2011-04-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by tnorgd on 2011-04-20
Hi,

I would like to install 64-bit Ubuntu 11.04 on an Intel i7 machine. I tired to use Live CD (AMD64 ISO file) but I screwed someting up. So I burned a CD and try to do the installation from scratch.

On my first attempt I boot from CD and got an ubuntu 11.04 working from the CD but it couldn't format my /dev/sda1 prior installation as it was mounted as /cdrom and I couldn't umount it.

So I mounted /dev/sda1 from another linux and removed everything from /dev/sda1 with mkfs.

Now, when I boot from Ubuntu 11.04 cdrom, I am getting:
"grub rescue>" prompt.

How can I switch this stupid grub thing and just start ubuntu from CD and install it on a HDD?

Although I don't care about /dev/sda1, I DO care about /dev/sda2, so I can't remove partition table from this drive.

What I have is:
- clean /dev/sda1 partition where I want to install U11.04
- /dev/sdb1 with working ubuntu 10.10
- cdrom with ubuntu 11.04

---

### Post by ghostborg on 2011-04-20
I believe your Ubuntu Install cd is getting bypassed otherwise grub should not show up. It sounds like your system is trying to boot from the hard disc installation. Check your boot devices and order in the bios and look for any messages during boot to press a key to boot from the cdrom. 
See if the Ubuntu cd you made will boot on another system, maybe a funky burn or bad download.
I hate it when something simple turns into a PIA.

Maybe this tool can help with your partition problem if all else fails and hopefully you can boot it if needed.
Be very careful with it.
[http://ubuntu-rescue-remix.org/]("http://ubuntu-rescue-remix.org/")

Good Luck

---

### Post by s.fox on 2011-04-20
Thread moved to [Natty Narwhal Testing and Discussion]("http://ubuntuforums.org/forumdisplay.php?f=394")

---

### Post by IPEX-731BA5DD06 on 2011-04-20
I can only add my own experiences:

1. booting from cd, my system, the BIOS for some strange reason I don't understand, and really don't care to look into, will keep defaulting to HDD as main boot option, after I boot once with a change to cd 1st. It will boot the cd 1st time, then immediately defaults back to HDD or Floppy drive 1st, AFTER I've disabled it.

Note, maybe I'm changing too many options at once and changing back...who knows.

sorry if I'm telling you what you know or understand, but boot into live cd, choose the 'Try UBUNTU option, and then run GPARTED from the system selection. You may have to unmount the swap file if you want to amend that,but re-mount BEFORE you leave. Oh, click on the Tick to action your choices, off course I've alway's done that:(

Changing BIOS to Boot from CD as 1st option, not 2nd after HDD. That's either F2, F8, or even F10, depends on you BIOS. worst comes to worst, reset BIOS to defaults, Via the motherboard, on one of the pins.

On partitions, having a separate home and Data partition, is the best thing I've ever done.

Big Thankyou to Psychocats and their posting on how to do it. Heh heh heh, even I could follow it and do it correctly 1st time. Sorry you'll have to look for it, I think its in the tutorial's section.

Possible solution, why not set up a 3rd partition for the installation of 11.04, I assume you have enough HDD space, 30 Meg, well 10 really would be plenty. Separate swap file = to your memory or > than you memory, with a Data partition and separate home partitions for the various versions.

---

### Post by ghostborg on 2011-04-20
You might want to read this maybe your bios settings and sata ports need
to be looked at.
Everything works if I use everything as IDE in the bios.

Today I installed 11.04 B2 and changed my bios settings from IDE to AHCI and put in an SSD for the install partition and a hard drive (that I was going to use as my HOME partition) It had an old version of Ubuntu on it.
Booting:
It did not recognize my sata optical drive and went on trying to boot off the hard drive. The bios settings where set to boot cdrom first and the cdrom had 11.04 install disc in it.

This being my first attempt using AHCI I figured I had to move the port my sata cdrom drive was on. MY Gigabyte MB has a setting for Sata type and allows me to configure two ports 4/5 as IDE, As Sata or Raid. I chose IDE and plugged the optical drive into port 5 and then everything worked.

So:
Sata port 1,2 SSD and standard hardrive as type Sata. AHCI
Port 5 Optical drive as type IDE.

---

### Post by IPEX-731BA5DD06 on 2011-04-22
Found the web page, I had it bookmarked under Ubuntu software any way, enough of that. 

[ [COLOR=Lime][/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")[ Seperate home/install partitions ](http://www.psychocats.net/ubuntu/separatehome)

Excellent tutorial, even I could follow it.:popcorn:

---

