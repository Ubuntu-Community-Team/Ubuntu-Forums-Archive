---
title: "Installing 9.10 using entire disk = system can't boot"
date: 2009-11-17
forum: Mythbuntu
---

### Post by DaveQB on 2009-11-17
I am trying out mythbuntu for the first time.

I did a test install on an old 10gig disk, choosing to use the whole disk. All looked good. Then on the reboot grub doesn't get going.

Didn't bother troubleshooting, figured the drive must be done. So grabbed a 320gig out of a raid and did the same thing with the same result.

I haven't had time to try booting and installing grub on the MBR or checking to see if the disks even have a menu.list or a kernel even, but just wondering if this a known bug or not.

Thanks

---

### Post by prshah on 2009-11-17
> **DaveQB said:**
> 
I did a test install on an old 10gig disk, Then on the reboot grub doesn't get going.

 but just wondering if this a known bug or not.


I haven't run across any bugs with the Mythbuntu installer; however, I have a suggestion: Make sure that "Virus protection" / "Boot sector write protect" / "Sector 0 readonly" options (or combinations thereof) are turned off in the BIOS.

You can re-enable it after installation, but it not really of much use, no matter what operating system you use.

---

### Post by DaveQB on 2009-11-17
Thanks **prshah**
It is odd.

The exact system has been running MythTV installed ontop of a very thin Ubuntu 8.04 install with the only change being the HDD.

I am about to put one of the HDD's in an eSata enclosure and take a look at its contents on my Desktop.

---

### Post by DaveQB on 2009-11-17
Well it seems like we are missing the menu.list file.

Also weird are the files found in /boot/grub, they are like drivers for FS's and all.

```


ls /media/disk/boot/grub/
915resolution.mod  bufio.mod       drivemap.mod  grubenv        linux.mod      normal.mod      probe.mod     tar.mod           vga_text.mod
acpi.mod           cat.mod         echo.mod      gzio.mod       lnxboot.img    ntfscomp.mod    pxeboot.img   terminfo.mod      video_fb.mod
affs.mod           cdboot.img      efiemu32.o    halt.mod       loadenv.mod    ntfs.mod        pxecmd.mod    test.mod          video.mod
afs_be.mod         chain.mod       efiemu64.o    handler.lst    loopback.mod   ohci.mod        pxe.mod       tga.mod           videotest.mod
afs.mod            cmp.mod         efiemu.mod    handler.mod    lsmmap.mod     part_acorn.mod  raid5rec.mod  true.mod          xfs.mod
aout.mod           command.lst     elf.mod       hdparm.mod     ls.mod         part_amiga.mod  raid6rec.mod  udf.mod           xnu.mod
ata.mod            configfile.mod  ext2.mod      hello.mod      lspci.mod      part_apple.mod  raid.mod      ufs1.mod          xnu_uuid.mod
ata_pthru.mod      core.img        extcmd.mod    help.mod       lvm.mod        part_gpt.mod    read.mod      ufs2.mod          zfsinfo.mod
at_keyboard.mod    cpio.mod        fat.mod       hexdump.mod    mdraid.mod     partmap.lst  

```


Its like it hasn't completed the setup....

I'll chroot and see if I can fix grub.

---

### Post by DaveQB on 2009-11-17
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Oh..

---

### Post by Dusilmenni on 2009-11-17
Hi.
I have exactly the same problem.
Installed Mythbuntu 9.10 on a 160Gb Sata drive and dedicated the entire drive for Mythbuntu.
Everything installs smoothly and after the configuration period I reboot. After that I only get the "Grub" prompt and the system stalls.
I have installed Mythbuntu on a old h/w with a 20Gb disk, no problems there. I even configured a VMware machine to run Mythbuntu for testing, no problems.
I found nothing in BIOS that could be messing with the drives and my knowledge on anything Linux is limited. 
I hope that you can find a solution to this which I can apply to my system, cant wait to get this roaring in my livingroom :)

Regards,
Dusilmenni.

---

### Post by DaveQB on 2009-11-18
What I did was choose manual paritioning. 
I didn't even need to use any mental resources on allocating partitions as I kept what the install made before, labelled slash and swap and ....

Oh yeah, at the end, I chose the Advanced tab and made sure the Boot loader was installed on the MBR on the right disk. Its defualt was hd(0,0) but I didn't have grubs device.map handy, so who knows which disk tha twas, so I stipulated the right disk for my system, /dev/sdc

Try that.

---

### Post by Dusilmenni on 2009-11-18
Thanks. I'll give that a try.

---

### Post by AJ1000 on 2009-11-18
If you want to reinstall grub using the live cd look here:

[http://platonic.techfiz.info/2009/11/06/reinstaling-grub-using-ubuntu-9-10/](http://platonic.techfiz.info/2009/11/06/reinstaling-grub-using-ubuntu-9-10/)

This worked for me.

---

### Post by DaveQB on 2009-11-18
Re-installing grub only was a thought, but
1) I wasn't sure if it was the only problem, I am not familiar with grub2 yet to troubleshoot it well.
2) I wanted to know if it was an issue with the install method I chose. IT seems so and I guess now I should report it as a bug.

Thanks

---

### Post by DaveQB on 2009-11-18
[https://bugs.launchpad.net/mythbuntu/+bug/485083](https://bugs.launchpad.net/mythbuntu/+bug/485083)

---

### Post by SiHa on 2009-11-19
I've installed 9.10 on two separate systems (BE/FE and FE only) unsing the 'Entire Disk' method, with no problems. The only notable difference from your install is that I pulled any other drives prior to the install. There is a fairly well-documented bug with GRUB (not sure if it affects GRUB2), where the bootloader sometimes ends up on the wrong drive, especially if you have a combination of IDE/SATA drives.
I'm just paranoid, I prefer to make sure an OS has only one drive to worry about when I install it!

---

### Post by Zimmer on 2009-12-02
Check you have the boot flag set for the install drive. Use the LiveCD and gparted...

---

### Post by DaveQB on 2009-12-04
Yes I could and did do that, but isn't that the point of the installer?

---

