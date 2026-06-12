---
title: "Mandriva grub install"
date: 2008-06-17
forum: Mandriva/Mageia
---

### Post by logos34 on 2008-06-17
I'm dual-booting a test install of MandrivaOne 2008.1 alongside Ubuntu Studio 8.04, and after a bit of a fuss getting Ubuntu grub to boot the mandriva kernel selection everything seems to be working fine. (luckily in the meantime I was able to boot Mandriva because I had made a grub boot floppy during installation).  I have no idea what I did to solve the issue, but I can now boot Mandriva from ubuntu grub using any method (configfile, symlink, direct).

However I am having a problem trying to boot Mandriva in a dual-boot setup with XP Home on another pc. The machine has two disks, XP is on the Sata drive, Mandriva on the backup IDE drive (as slave, root on hdb2).  During installation I wrote grub to the IDE drive's MBR, and I can boot to it directly just fine if I toggle the Bios boot drive.  However, I want to also be able to get to it from windows bootloader.  

I got grldr from the grub4dos pkg, added entry to boot.ini, and copied menu.lst to c:\boot\grub.  That part works fine--done it a zillion times.  The problem is when I select the Mandriva entry from the menu.lst: I get bad file type error.  Neither 'root (hd0,1)' or (hd1,1) works.  I've tried all the entry formats mentioned above.  Mandriva refuses to start.  Do I need to write mandriva grub to the bootsector of the root partition also?  (I would have done so already but the keyboard suddenly stopped working that last time I was in mandriva, so couldn't type anything in the terminal!)

Or will it be impossible to chainload mandriva from windows because of the switch to 256 byte inodes, as discussed [here]("http://wiki.mandriva.com/en/Docs/SysAdmin/GrubInodeTransition")?  But then why am I able to do so on ubuntu?

Sorry for the long-winded post.

---

### Post by meierfra. on 2008-06-18
>  because of the switch to 256 byte inodes 

Yes, this is the problem.   Ubuntu 8.04 can see Mandriva, since it uses  a modified stage2 file. I'm not familiar enough with grub4dos to tell you how to solve the problem. Does it come with its own stage 2 file? Could you just replace  it with the ubuntu or mandriva stage2 file? (Edit: Sorry, this was stupid. Grub4Dos does not use the stage2 file.)


> Do I need to write mandriva grub to the bootsector of the root partition also?

That should solve the problem. Although this is a little tricky to do, since Mandriva and Windows are on different drives.

---

### Post by meierfra. on 2008-06-18
Here is the easiest solution. I just tried it out on my own computer, so I hope it will work for you too: Chainload the MBR of the IDE drive from Grub4dos:


```

root (hd0)
map (hd1) (hd0)
chainloader +1
```


I have Grub on my internal drive, and not Grub4Dos, but I hope that won't make a difference.

---

### Post by meierfra. on 2008-06-21
I tried out my suggestion from post 3 with Grub4Dos on the internal drive and Mandriva on the MBR of the External drive. 
At first I did not want to overwrite Grub in the MBR, so I loaded "Grub4Dos" via

root (hd0,0)
kernel /grub.exe

from the Grub Menu.

Then in Grub4Dos I was able to chainload Mandriva via

rootnoverify (hd0)
map (hd1) (hd0)
chainloader +1

But booting was painfully slow.

So I installed Grub4Dos to the MBR of the internal drive. Using the same code as above I got "Missing MBR-helper". I then tried


```
rootnoverify (hd1)
map (hd1) (hd0)
chainloader +1
```
and  it worked perfectly.
(Edit:  These commands also work, when Grub4Dos is loaded from the Windows boot menu)


So  with grub one needs to use "(hd0)" but with  Grub4Dos  one needs "(hd1)".

---

