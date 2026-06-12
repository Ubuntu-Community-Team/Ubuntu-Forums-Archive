---
title: "Mythbuntu md5 issues?"
date: 2008-04-19
forum: Mythbuntu
---

### Post by jmw86069 on 2008-04-19
I have been trying to install 8.04 unsuccessfully, and what I found here:
[http://ubuntuforums.org/showpost.php?p=4663722&postcount=9](http://ubuntuforums.org/showpost.php?p=4663722&postcount=9)
suggested it was because I was burning to CDRW.

1) Please put "Don't burn to CDRW" on the instructions. In big red letters. :-)

I then tried to install via USB key, which by the way is very cool, or would be if the md5sum checked out.

Here's the situation:
The md5sum checked out fine on the ISO for the alternate CD. But when I unpacked the ISO, the md5 failed for 7 files. What am I missing? If the md5 of the ISO is correct, why would the files be corrupt? I unpacked the ISO with 7zip in Windows XP. Windows/Unix character differences maybe?

I just tried the same thing with the live CD, and both md5's checked out fine. Damn, should've tried that in the beginning. I'll try that now and see how it goes.

Has anyone else noticed the md5 issue with the alternate CD?

---

### Post by tgm4883 on 2008-04-19
Why are you trying to unpack the iso?  You should burn it as an image file

---

### Post by jmw86069 on 2008-04-20
Can you point to the page giving you those directions? Not to be a pain, I'd be really happy to know, since there are some different techniques people use, and not always consistent.

The one I was using was here, [InstallationUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick#head-a45f469b0b7ec2750cdedce449b76003c391416d")


And its quote was:
Copy the contents of the Ubuntu installation CD to your flash drive (i.e. all files and directories that are on the installation CD). Please do not copy an ISO image of the installation CD file to your flash drive.

On that same page, what caught me for the longest time was the
syslinux -s F:
which should be
syslinux -s -m F:
(The -m makes sure the master boot record for ISOLINUX is written, in my case replacing the GRUB loader.)

Fwiw, if one tries it, you also have to rename /dists/hardy to /dists/stable, since USB sticks don't do symbolic links (not in FAT32 anyway.)

No complaints, I'm just documenting what I'm finding so far, and will update that Wiki entry if I can later. Still doesn't work though, it got through part of the install then complained about missing a .udeb file... tracking that down now...

---

### Post by laga on 2008-04-20
CD-RW works me for so far with the alternate disk.

---

### Post by tgm4883 on 2008-04-20
> **jmw86069 said:**
> Can you point to the page giving you those directions? Not to be a pain, I'd be really happy to know, since there are some different techniques people use, and not always consistent.

The one I was using was here, [InstallationUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick#head-a45f469b0b7ec2750cdedce449b76003c391416d")


And its quote was:
Copy the contents of the Ubuntu installation CD to your flash drive (i.e. all files and directories that are on the installation CD). Please do not copy an ISO image of the installation CD file to your flash drive.



Knowledge from burning OS distributions for years.  Why not use the CDR?  

MD5SUM the ISO
burn at slow speed (4x)
Verify the burn of the CD

---

### Post by jmw86069 on 2008-04-20
tgm4883, no problems here, 'cept I don't have CDR's handy. Plus, check the board chatter on CDR's, there must be 10,000 worthless Ubuntu coasters out there. Even when people burn at 1x (ytf do burners even have 24x?) end up with coasters.

My case, I extracted direct to USB. No burner. md5 on the ISO was fine. md5 on the files failed for 8 files. During the install, these files caused the install to fail. I found the solution, to trash and burn the liveCD/alternateCD kernels (initrd and vmlinuz) and use the [Ubuntu Hardy Kernels]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/"), referenced from here:
[http://ubuntuforums.org/showpost.php?p=4102319&postcount=5](http://ubuntuforums.org/showpost.php?p=4102319&postcount=5)

I question the wisdom of having "mini" kernels in the installers. Best I can tell, it saves 1 meg (8 megs vs. 7 megs for initrd and vmlinuz, ubuntu vs mythbuntu installer, respectively) at the expense of possibly key drivers. I'm updating Wiki topics as I see them, so the information is there in the how'to's.

I do appreciate the md5s, keeping downloaded files legit and all, which is why I mentioned the original issue and md5 mismatches. I also just think one should say "Use only CDR and use it at the slowest "slower than freaking handwritten" speed you can use."

---

### Post by superm1 on 2008-04-21
You know it's possible there is a bug in the md5sum generation on the disk too.  This is our first go at alternate disks...

I know it's fine on the Live disks, fixed it some time back during 7.10's cycle.

---

