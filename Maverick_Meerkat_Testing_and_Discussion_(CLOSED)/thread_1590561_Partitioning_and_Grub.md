---
title: "Partitioning and Grub"
date: 2010-10-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by rooski15 on 2010-10-08
So i am running 2 500gb drives, the first (/dev/sda) has Win-7 64 bit (sda2) and the Windows 7 Loader (sda1). 

My second drive, completely unallocated and lacking format (/dev/sdb), is where i am at. I see there are quite a few discussions about the not-so-user-friendly qualities of the partition program in maverick and as such, this is where i've stopped. I plan on making a 20gig Ubuntu patition, a couple gigs of swap, and leave the vast majority for moving all my files to and running a backup. 

The only thing holding me back is the boot loader. I've spent the last hour looking for threads, guides, ect, for installing grub when dual booting. I found there is very little middle ground, not telling me where to install it,  just that I need to. If anyone here could guide me a little I'd really appreciate it, I'm really looking forward to getting this new version up and running.

Thanks,
Andrew

---

### Post by 23dornot23d on 2010-10-08
For each of the drives I have ..... 4 in all .... there is a separate boot loader on each

and all work 100 % ....... but I do not use MS ..... only LINUX .....

You may be safer putting the boot loader on sdb and switching between the drives using the BIOS .....

But maybe someone that uses Windows ...... would be able to tell you how to set it up safely on sda .........

---

### Post by rooski15 on 2010-10-08
Yeah, i popped an old 9.10 disk in and got it to the end of the install, right before i OK it and went to advanced to see where it specifies the Boot Loader install and it is hd0. However that's not an option on 10.10 so im searching the forums as we speak to see what hd0 translates into in my case. Ordinarily i would just install straight to sda but i dont want to run the risk of harming the windows install. It will be a long night at this pace, brewing some coffee. :)

---

### Post by garvinrick4 on 2010-10-08
If your install is in sdb drive the bootloader go's in sdb not sdb1 or sdb2 or sdb5 just straight sdb
Even if you had a seperate /boot partition in sdb1 you still put grub in sdb not sdb1
If your install is in sda grub go's in sda.
In previous to 10.10 the grub is installed in advanced tab in page 8 of install.
In 10.10 Maverick it is at the start of install where no one can miss it. Seems to always
be biggest problem at install is grub placement.
```
sudo update-grub
```
After install in sdb and grub2 will pick up Windows and add it to your sdb grub menu.

---

### Post by rooski15 on 2010-10-08
Will give it a shot. Thank you. :)

---

### Post by jaycee23 on 2010-10-08
If you install Grub on sdb then you will need to use your BIOS setting to switch between your HDD.

If you boot to the first HDD with Windows then it will not show your Ubuntu install at all. It will boot as usual straight into Windows 7.

If you change the boot in BIOS to your second HDD then Grub should give you the option of both Windows and Ubuntu.

This way of installing is safest if you have 2 HDD and want to leave the Windows installation untouched.

However bit of faff switching the boot order in BIOS all the time.

---

### Post by fedexnman on 2010-10-08
i have 2 drives windows7 and ubuntu and i ALWAYS unhook my windows hardrive before installing ubuntu , then i sudo update-grub , i make my bios to give the ubuntu drive 1st hd priority.

---

### Post by jaycee23 on 2010-10-08
> **fedexnman said:**
> i have 2 drives windows7 and ubuntu and i ALWAYS unhook my windows hardrive before installing ubuntu , then i sudo update-grub , i make my bios to give the ubuntu drive 1st hd priority.
 
Wow - that is super cautious!!

However better safe than sorry

---

### Post by fatman65535 on 2010-10-08
I have a multi boot system*, consisting of two 500 GB drives with Ubuntu on them, and one 20GB windows drive.

I too second the idea of **not** putting GRUB on your windows drive. *If you are **not able to choose the boot drive through BIOS**, then I suggest the following.*

1) Disconnect your windows drive (for now).
2) Make your second unformatted drive bootable, and install Ubuntu on it.
3) After the installation is complete, re-connect the windows drive as the **secondary** drive.  _You want the Ubuntu disk to be the one system boots from._
4) When you boot the system after re-connecting the windows drive, re-run `sudo update-grub` to have it recognize the windows drive, and create a menu entry for it.
5) After that, you will be able to select which O/S you want to boot from the GRUB menu.

**What ever you do, do not put GRUB on a solely windows drive,** it will complicate things in the event you need to remove the Ubuntu drives from the system, and restore windows only as an O/S for that system.

HTH



* My system allows me to boot Karmic, Lucid, Maverick, it has a placeholder for Natty, and allows me to boot windows _when I must_.

---

### Post by fedexnman on 2010-10-08
> **jaycee23 said:**
> Wow - that is super cautious!!

However better safe than sorry

yup, i know ! ive fudged my windows and ubuntu before, so thats how i do it now. its easy to mess it all up. i love ubuntu and am looking forward to oct 10th .

---

### Post by Quackers on 2010-10-08
I have two hard drives in a laptop and Sony don't allow me to choose which drive it boots from. I have Windows on sda and Ubuntu on sdb. The only way I can get a grub menu where both OSes will boot from it is to install grub2 in the mbr of both sda and sdb. This has worked well for me.

---

### Post by philinux on 2010-10-08
On a machine with 2 HD's I did the following. Installed grub to sdb1 using the advanced settings at the last instal stage. I then used easybcd in windows to pick up grub.

---

### Post by garvinrick4 on 2010-10-08
Any which way anyone chooses to install this is a good site to bookmark!!!
How to's on replacing XP,Vista,7 and all versions of Ubuntu linux and other Linux distro's
Grub's in a few key strokes. 
 With any Operating System keep your personal's backed-up. Enjoy your Linux!!

[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

---

