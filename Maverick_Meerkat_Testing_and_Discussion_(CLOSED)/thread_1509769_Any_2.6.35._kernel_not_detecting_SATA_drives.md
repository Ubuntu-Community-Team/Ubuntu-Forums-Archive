---
title: "Any 2.6.35.* kernel not detecting SATA drives"
date: 2010-06-14
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by arpanaut on 2010-06-14
Only my ide/ata drives are being found by any .35 kernel?

From boot with installed on sata drive  2.6.35.2, or 2.6.35.rc3 it drops me to initramfs cursor. (I can boot to .34 kernel)
ls /dev only shows my pre-sata drives.

From the alt. iso daily/current (which I've never had problems with before) at the partitioning phase it only shows ide/ata available.
Same with daily live desktop CD.  Will boot to live desktop but again fdisk -l and ls /dev only show my 2 ide/ata drives, not my 2 sata drives.

Only clue I have is that from (initramfs)_ cat /proc/modules shows different sata module number loaded than from same command from booted .34 kernel.

All uuid's are correct, grub.cfg seems correct, I can boot 3 other Ubuntu installs JJ, KK & LL and my XP. KK & MM on sata drives. I do have one of the wacky motherboards/bios that has the IDE/SATA problem with identifying sda, sdb, etc. correctly so I have to manually install grub to what "I know" is my primary boot drive.

Sorry for long post, but this has me ](*,)

Thanks for any assistance.

[COLOR="Red"]This Has been Partially Solved![/COLOR]  
* Reverted ata_wait_idle performace patch to fix problems with SiI 3114
     - LP: #595321
A patched kernel is available from: [https://launchpad.net/~andrew-betts/+archive/ppa-patches](https://launchpad.net/~andrew-betts/+archive/ppa-patches)
See bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595321](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595321)

Now if it can be patched on the main kernel I will be able to install on my SATA drives again.
Will mark thread solved when that happens.

---

### Post by ronacc on 2010-06-14
my install started out as lucid and then upgraded and I am showing all my drives with the 35.2 kernel 2 ide 4 sata , I'll burn a live cd later and see if it finds them all .

---

### Post by arpanaut on 2010-06-14
> **ronacc said:**
> my install started out as lucid and then upgraded 

Same here... All was well until updating to .35 kernel, and .34 is running very well.  I feel it has to do with my silicon image 3114 sata controller. Motherboard dates back to '03 so IDK, maybe support in newer kernels is waning.

Thanks for the reply, I tried the live CD on my laptop that has only a sata drive, and it detected the drive. So I presume it has to do with my desk-top's sata controller. I'll keep updating my isos and see if it works itself out.

Thanks again!

---

### Post by ronacc on 2010-06-14
burned and checked todays daily live , all my drives were detected ok . You need to bug it as a regression since earlier versions worked with your sata controller .

---

### Post by ranch hand on 2010-06-14
Yup, I just did an install with todays ISO for UNE and it has no problems and my other 5 installs all have no problem.  Some are upgrades from 9.04, 9.10 and 10.04 and some clean installs of 10.10.  All are 64 bit except the UNE which is only available in 32.

Congratulations, you have a bug.

---

### Post by arpanaut on 2010-06-14
> **ronacc said:**
> burned and checked todays daily live , all my drives were detected ok . You need to bug it as a regression since earlier versions worked with your sata controller .

HA!  I was afraid that was going to be the answer, was hoping there was a magic pill...  

<takes deep breath->exhales>  I guess if I'm really going to be part of this testing thing, I better get myself "learned-up" on reporting bugs.
(and over my fears of appearing stupid)

Thanks for the feedback.

Off to do some learnin'

---

### Post by ronacc on 2010-06-15
see this link about reporting bugs 

[ https://help.ubuntu.com/community/ReportingBugs ]( https://help.ubuntu.com/community/ReportingBugs )

and this one to check to see if it has already been reported .

[ https://bugs.launchpad.net/ubuntu/ ]( https://bugs.launchpad.net/ubuntu/ )

if it has been reported be sure to mark that it affects you too .

---

### Post by arpanaut on 2010-06-15
> **ranch hand said:**
> Congratulations, you have a bug.

Thanks, I think?

You know, in 5+ years of running Ubuntu on this old rig I've been very lucky not having any serious compatibility issues (except for dumping an ATI vid-card that I got tired of wrestling with).  

I just remembered that I have another almost identical build of this box that I think I will dust off and see how the isos work to rule out user error and config. issues. I still think I did something to hose this install being impatient with all the held-back packages the past week or so. Installing the rc3 kernel and all.

Still doesn't explain the behavior with the daily isos.

testing 1,2,3, testing 1,2,3
WooHoo! Got something "impotent" to do!

---

### Post by ranch hand on 2010-06-15
You need to feel comfortable feeling stupid.  It would help if you just realize that you are stupid.  If you weren't you would not be running an A1 version of an OS.

This is a sign of being adventurous and mentally unstable but not a real sign of being real bright.

Welcome to the crowd.  At least we are kind of FUN.

---

### Post by arpanaut on 2010-06-15
@ronacc

Much Appreciated!

---

### Post by arpanaut on 2010-06-15
> **ranch hand said:**
> You need to feel comfortable feeling stupid.  It would help if you just realize that you are stupid.  If you weren't you would not be running an A1 version of an OS.

This is a sign of being adventurous and mentally unstable but not a real sign of being real bright.

Welcome to the crowd.  At least we are kind of FUN.

Oh, Kinda like what I tell my friends that question my appearance, "When you begin with ugly, It ain't hard to present yourself as buttugly"

Your post did truly cause me to LOL, thanks for that.

---

### Post by dino99 on 2010-06-15
i've reported a bug about SATA detection, some chipset issues i guess, mine is detected but often fail, ahci set into bios

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/590727](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/590727)

---

### Post by ranch hand on 2010-06-15
I think this might be another time it would be good to try a symbolic menu entry.  As it is just calling for a Debian based kernel to boot in the defined partition it may behave differently.  This may give some indication of what the problem really entails.
```

echo "Adding What ever you want on sda8" >&2 
cat << EOF
menuentry "What ever you want on sda8" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro quiet
        initrd /initrd.img
}
EOF

```
Add to etc/grub.d/40_custom and run "sudo update-grub".

Replace the "whatever you want" with your title of choice.

Note the partition number and edit to your box.

Do not worry about what you do to the portions outside the {}s, as long as the form is preserved.  Between them is the stuff that does the work.

---

### Post by arpanaut on 2010-06-15
Thanks for that template it will come in handy in the future, alas it's not working today.

same result on boot: drive does not exist; doping to shell blah blah initramfs_
neither sata drive detected.

Must Sleep

```
sudo go_to_bed_fool
command not found
```

figures...

---

### Post by ranch hand on 2010-06-15
Well, even that is good to know.  I would say that this is not a grub problem anyway if both common menu entries are not getting it.

Have you played with Disk Utility to see if it turns the bugger up from the Live CD?  You can run fsck from Disk Utility on that partition and see what it comes up with.  You could run it from terminal too but I think that DU is a neat app that everyone should take a look at.

---

### Post by arpanaut on 2010-06-16
wOOt!  First bug report.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595321](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595321)

Now awaiting for Gibbs to appear and slap me up-side the head,
and to be banned from Launchpad.:biggrin:

Thanks for the encouragement guys!

---

### Post by tghe-retford on 2010-06-16
For some reason, when my system updated to 2.6.35.3, my SATA hard drive will no longer be detected, it goes straight to a busybox prompt. However, 2.6.35.2 boots fine.

Slightly different circumstances, same result.

---

### Post by arpanaut on 2010-06-16
Interesting... I thought I was the Lone Ranger on this.

If you would, please, go to the bug page and add a comment about your issue and hit: "This bug affects you"

Maybe someone of importance will notice and hopefully something will be done.

---

### Post by BwackNinja on 2010-06-16
This happens to me too sometimes, not all the time and not always all my sata drives. Something like that makes it sound like a timing issue.

---

### Post by arpanaut on 2010-06-16
I have had multiple releases of Ubuntu continually on this box since Dec.'04 and never had issues with sata being detected. Looking at the logs the sata_sil module tries to detect the drives 2-3 times during boot at different stages. so IDK about the timing, could be.

Since it began to affect me with the onset of the 2.6.35-* kernels I presumed the issue was there, and the controller module. I could be wrong, probably am, but I had to bug it best I saw.  Hopefully there will be some resolution, one way or another.

Thanks for the feedback

---

