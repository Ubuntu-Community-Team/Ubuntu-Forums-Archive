---
title: "Unable to install Mythbuntu onto 3ware 9650SE-controlled RAID 5"
date: 2008-03-08
forum: Mythbuntu
---

### Post by bwish on 2008-03-08
Hi everyone.  A complete Linux newbie here, in desperate need of some help...

I'm trying to set up a new server/NAS using Mythbuntu 7.10, with a RAID 5 thru a 3ware 9650SE card.  I'm able to boot into Mythbuntu with the LiveCD, and then when I finish entering all of my install choices and actually begin the install, the install APPEARS to freeze during creation of the file system.  I come back to it a few hours later and it says it's done, and ready for Step 15 of 15 (MythTV configuration).  Upon reboot, my BIOS apparently can't find the OS, and I just get a black screen.  This has happened twice.

My system details:
ASUS M2A-VM motherboard
AMD Athlon 64x2 4800+
4GB of Crucial DDR2 800
3ware 9650SE controller card
4 x Samsung HD501LJ (500GB) HDDs

After assembling all the hardware, I was able to get into the 3ware 3BM, and configure the RAID 5 successfully.  I booted into the LiveCD and attempted to load the 3ware driver from [COLOR="RoyalBlue"][http://www.3ware.com/kb/article.aspx?id=14546]("http://www.3ware.com/kb/article.aspx?id=14546")[/COLOR], to no avail (Linux newbie, remember?).  Then I read on the 3ware website that 2.6.14 kernels and newer have native support for the 9650SE, so I went ahead and tried the install, resulting in the problem described above.

After scouring the forums, it turns out that there might be an issue with the ATI SB600 southbridge on my motherboard, when using 4GB of RAM or greater, so I removed one of the DIMMs, repeated the install, and repeated the problem above.

I've sifted through the forums, but haven't had much luck on finding a way to fix my particular problem.  I've also tried to go back and reread the 3ware user's manual (which is more helpful for RedHat and Fedora installations).  I'm just not wise enough to know how to proceed.

I guess I'm pleading for help here, my wife is ready to hang me for all the time I've been spending trying to get this new computer working!

---

### Post by uopjohnson on 2008-03-08
I'm not familiar with that card but I imagine that it is a hardware raid card.  If that is the case you probably don't need to mess with drivers at all as these cards often appear to the OS as a single drive at /dev/sda1.
When you are looking at the partition portion of the installer are you seeing your raid5 array as a single disk?  Is it the size you expect?
Your problem may be far simpler.  I often find that a bad CD burn will cause just this type of installation problems.  Have you run the disk check on the CD?

---

### Post by bwish on 2008-03-08
Yeah, it's a hardware RAID controller.

The installer seems to view the RAID as one device, and it's the appropriate size.  I did check the CD w/ the utility on the CD, it checked out OK.

My real frustration right now is that I can't even figure out if it's a Mythbuntu problem, or a problem with my hardware.  I was having a problem a few nights ago when I was trying to boot off of the LiveCD, and my BIOS couldn't find the CD, and it would give me the same blank screen after starting up the controller card in the BIOS.  I fixed that problem by swapping out the CDRW drive (that's what I get for pulling one out of my "spares" supply).  This blank screen is the same, and I don't even know how to validate that Mythbuntu was actually installed properly.

When I tried the install the 2nd time, the installer gave me the option to use the "existing partition" to install to, versus just erasing and using the whole disk.  This makes me think that it doesn't "really" hang at 5% during filesystem creation.

---

### Post by bwish on 2008-03-08
Let me clarify that last post... I've booted into an Ubuntu LiveCD, there appear to be several files related to Mythbuntu on the RAID, but I'm unable to verify that everything's actually there.  If it's true that everything is in place for Mythbuntu, then I really have more of a "boot" problem, than an "install" problem... Anyone have any ideas?

---

### Post by uopjohnson on 2008-03-10
Hmm.  sounds like you at least have a boot problem, maybe with an install problem as well.  I would start by checking your boot priority in your bios to see what devices are being booted.  Try disabling everything and see what you get (hopefully a message saying 'No Boot Device' or 'Unable to boot device, press enter to try again' then enable just the raid drive as the first boot device and see what happens.  We're testing here to see if your raid card is being recognized as a valid boot device and that something else isn't getting in the way of the boot. 
Let us know what you get here.
Also try booting the livd cd again and opening a terminal window (in Accessories I think) then type
```
df -h
```
and try:
DANGEROUS, be carefull
```
sudo cfdisk /dev/sda
``` 
this will open up the partitioner and you should be able to see how your drives are partitioned (or not partitioned) 
Let us know what you see.

---

### Post by inkblot on 2008-03-11
I have HW raid as well and had a 3 drive raid 5 setup. After I loaded the live version of myth 7.10 and poked around I lost the array. Oh well.

---

### Post by bwish on 2008-03-11
OK Jon:

1.  Check BIOS for boot priority, result:  "Hard Disk" was present, right behind "CD Rom".  Under the "Hard Disk Drives" menu (on the "Boot" tab), was "SCSI-0: 3ware Storage Controller".  This sounds like good news in the compatibility arena!

2.  Disable all boot devices, result:  same blank screen, with and without the 3ware card installed.  Is it possible that my BIOS is trying to display "No boot devices", or something to that effect, but that it just isn't visible on the screen because of overscan?  How does one fix that?  Could the motherboard suddenly decide to change it's mind and display on the DVI output instead of theVGA?

3.  A funny thing happened on the way to 4, while booting into the LiveCD... If the "Hard Disk" is before "CD Rom" in the boot priority, I get the same blank screen as before.  It never made it to booting from the CD Rom. Hmmm... I dunno what that means, but surely it means something...

4.  View free disk space, result:  successfully viewed disk information for the CD... Oh, I need to change my target and df sda -h? OK, that should work... Nope.  df sda -h (along with sda1, sda2, and sda5) gives udev filesystem, 1.9G size, 68k used, 1.9G avail, 1% use, and mounted on /dev.  I should be seeing about 1.36 to 1.5 TB here, like I've seen other places, right?

5.  View disk partioning with sudo cfdisk /dev/sda, result:  "FATAL ERROR: Cannot seek on disk drive, Press any key to exit cfdisk".  That doesn't sound good.  

Hey wait! What about sudo cfdisk /dev/sda1?  (I browsed to the /dev folder to poke around...)  Result:  size: 1494.1 GB, Heads: 255, Sectors per track: 63, Cylinders: 181655, Part Type: Pri/Log, FS Type: Free Space, Size (MB): 1494163.24 ... Now we're talking!

What about sudo cfdisk /dev/sda2?  "FATAL ERROR: Bad primary partition 0: Partition begins after end-of-disk"

And sudo cfdisk /dev/sda5?  Size: 5790 MB, Heads: 255, Sectors per track: 63, Cylinders: 703, Part Type: Pri/Log, FS Type: Free Space, Size (MB) 5782.38 ... Good, at least it's not a FATAL ERROR, but what's sda5?

Thanks for the help so far Jon, I'm sure this gets me closer to fixing my 'puter, I think.

---

### Post by uopjohnson on 2008-03-11
Ok so I think your AhHa was correct.  When you put the hard disk in front of the CD you must be booting to the disk which, for some reason, is failing to respond.  
I think it is good news that you are seeing the 3ward card in the bios, maybe the issue is with the raid setup on the card.  When the computer boots do you have the option to enter a setup mode for the hardware raid card?  You may need to look at your manual but usually you press a key (just like getting into your bios) when the summary is showing.  
Have you setup your raid here.  Maybe you can wipe and rebuild the array, or reformat everything, I don't know what options you have  without seeing the screen, but a reset of the raid array and all the devices may be what is in order.

I'm really unsure what cfdisk /dev/sda1 would work and /dev/sda wouldn't work, that is weird and probalby a sympton of something I don't understand.

I think the problem is that the bios is trying to boot from the raid array, but for some reason the master boot sector on the raid array is missing or unwritten and so the bios is hanging.  Or the 3ward card is hanging.  Either way, something needs to be shook a bit. 

If resetting your raid card and drives doesn't work we can try booting into the live CD and re-installing grub onto the mbr of /dev/sda, that may be what is wrong. (just thinking out loud here, and for anyone else who wants to offer some advice.)

---

### Post by ian dobson on 2008-03-12
Hi,

Check in your BIOS for a option to boot from an adapter card. I had a box with a SCSI controller that I couldn't boot from until I "told" the bios to boot from Adaptor Boards. 

Regards
Ian Dobson

---

### Post by bwish on 2008-03-12
Could it be that I need to manually edit the partition table?  Maybe the "default" partitioning doesn't work for some reason?

---

### Post by bwish on 2008-03-12
SOLVED!!  I went and manually edited the partition table during install, making sure to divvy out some space for swap, /boot, and /, and upon reboot, IT WORKED!! YAHOO!! Now I'll get busy on the other setup items... Hopefully I don't hit anymore snafus.  Thanks for the help guys.

---

