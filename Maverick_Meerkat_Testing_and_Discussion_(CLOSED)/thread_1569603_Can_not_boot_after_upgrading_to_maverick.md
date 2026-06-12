---
title: "Can not boot after upgrading to maverick"
date: 2010-09-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by ameyjah on 2010-09-07
Hello,

I had 10.04 GNOME using wubi on d:/
But after upgrading to maverick, I did some changes and now I am not able to boot into ubuntu. Please help.

I did following changes:
1) Once upgrade was done, it restarted and perfectly booted to maverick .
2) But i was getting some syntax error at grub part, so i decided to update it with sudo update-grub.
3) As I found, it was not functioning, I decided to reinstall grub-pc.
4) While installing, I choose to opt of one of drive as boot (I guess i was wrong there)
5) Now, I am not able to boot into ubuntu.

What did I try:
1) I tried to run live cd of 9.10. 
2) Mounted root.disk using 
 mount -o loop path-to-root.disk /mnt
3)sudo grub-install --root-directory=/mnt/ /dev/sda1
(but sadly, above command is giving me error.)


Please guys help me. If you need any additional info. Let me know.
Thanks in advance

---

### Post by mörgæs on 2010-09-07
This forum will be a better choice:
[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by Sef on 2010-09-07
Moved to MMTnD.

---

### Post by Rasa1111 on 2010-09-07
You do know that 10.10/Maverick is not ready , right? 
It should only be used by those wanting to test it for bugs, 
of which there are still quite a few. 
 It's supposed to be for testing, not to actually upgrade your system. 

If one upgrades to a new version that is not even ready for real use yet,
they can most surely, , expect problems, like yourself. 

good luck.

---

### Post by kansasnoob on 2010-09-07
I'm somwhat guessing because I don't use Wubi but from here:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

> Important Note to Wubi (Windows Ubuntu) Users: Grub Update results in "No Such Disk":
A late July 2010 Grub 2 update is causing a "no such disk" error for some users of WUBI, resulting in an unbootable system. If the system doesn't display the original Windows menu, the most likely cause of the failure is that Grub 2 was installed in the MBR and/or on the Windows partition. To correct this, restore the Windows bootloader using this link:
How to restore the Ubuntu/XP/Vista/7 bootloader

Whether the failure is due to improper user selections or Grub 2's failure to recognize a Wubi install, it has been reported in the following bug and users can review it for status updates and recovery options when they become available:

[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

But also from the release notes:

[http://www.ubuntu.com/testing/maverick/beta#Known%20issues](http://www.ubuntu.com/testing/maverick/beta#Known%20issues)

> Upgrading Wubi systems from 10.04 LTS is known to fail, and is not recommended at this time. (610898, 617715)   

[https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898)

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/617715](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/617715)

---

### Post by cariboo on 2010-09-07
To repair grub, you need to chroot your Maverick install, boot from the Live CD and use the following steps:

[list=1]
[*] sudo mount /dev/sdX /mnt
[*] sudo mount -o bind /dev /mnt/dev
[*] sudo mount -o bind /sys /mnt/sys
[*] sudo mount -o bind /proc /mnt/sys
[*] sudo chroot /mnt
[/list]

/dev/sdX = the partition you have Ubuntu installed on. Once you are in the chrooted environment type:

```
install-grub /dev/sda
```

the above command will install grub to the mbr of the first drive. then type:

```
update-grub
```

When running the above command you should see all the OSs you have installed listed.

**Note**: if you use a 32-bit Live CD on a 64-bit install you will get a /bin/bash error.

---

### Post by bcbc on 2010-09-07
For wubi you will want the windows bootloader in the MBR. If you can still boot windows, then that's ok - you don't need to reinstall grub2. If you can't boot anything, reinstall the windows bootloader.

If you're affected by the last bug kansasnoob referred to (symptom is that you end up at a grub prompt - not grub rescue - when selecting Ubuntu from the windows boot manager) then you can manually workaround it by:
```
configfile (hd0,msdosX)/ubuntu/winboot/wubildr.cfg
``` you have to replace msdoxX with the partition that you installed wubi to. You can find it by using ls and then just searching for the ubuntu directory e.g. "ls (hd0,msdos2)/ubuntu" 

But it's strange to me that running "sudo update-grub" caused this in the first place. Especially since your upgrade was a success. Maybe it was caused by reinstalling grub-pc, but it's hard to know without you providing more details of the errors you were trying to fix and the symptoms you had/have.

---

### Post by ameyjah on 2010-09-08
> **bcbc said:**
> 
But it's strange to me that running "sudo update-grub" caused this in the first place. Especially since your upgrade was a success. Maybe it was caused by reinstalling grub-pc, but it's hard to know without you providing more details of the errors you were trying to fix and the symptoms you had/have.

Yeah that's what amusing me also. Well, I could able to boot into windows. But while trying to boot to ubuntu, my system was getting restarted.

So, as I didn't get any workaround. I have reinstalled Lucid and upgraded again to Maverick. Well this time, i didn't choose to reinstall grub-pc, just ran update-grub.

---

