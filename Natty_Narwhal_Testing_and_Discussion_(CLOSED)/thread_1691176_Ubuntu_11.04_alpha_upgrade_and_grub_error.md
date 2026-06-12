---
title: "Ubuntu 11.04 alpha upgrade and grub error"
date: 2011-02-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by recep on 2011-02-19
Hi. I have upgraded 11.04 from 10.10. I was using with dual boot, windows 7 and ubuntu. After upgrade windows 7 was disappered in grub menu and adding menu manually then I get &quot;invalid signature&quot;. When I look disk utilty my windows disk seems unknown file system. How can I mount windows volume?  Sorry about bad English. Thanks.

---

### Post by hatien on 2011-03-12
Please don't install any alpha linux distro because it make destroy your data. I installed ubuntu 11.04 alpha3 to test but i'm unlucky. After three times updates have grub three times destroy windows xp on partition 1. I'm borred to try ubuntu again.

---

### Post by kimokimkm on 2011-03-16
i tried to install ubuntu 11.04 from usb stick but everytime i was getting input/output error
i can't understand why was this happening but i hope they can fix the bug (of course if it is a bug, i maybe mistaken as well)

---

### Post by mörgæs on 2011-03-16
Alpha releases has lots of bugs. In fact the sole purpose of releasing an alpha is to find bugs.

By all means, please download the alpha releases and help the developers find the errors, but don't let an alpha get close to important data.

---

### Post by drs305 on 2011-03-16
I have moved this thread into the Natty forum for two reasons. First, Natty is still in testing. Secondly, Natty is using a version of Grub [noparse]1.99[/noparse], which has some differences from the version of Grub (1.98) used in Maverick.

To avoid confusion, it's best to keep the development issues separated from official releases.

If you just want to mount your Windows partition to view/access the files via Ubuntu, these commands should help. Change XY to the proper values (sd[COLOR="Red"]a1[/COLOR], sd[COLOR="Red"]a2[/COLOR], etc). Change it if necessary:
```

sudo mkdir /mnt/windows
sudo mount /dev/sd[COLOR="Red"]XY[/COLOR] /mnt/windows
gksu nautilus /mnt/windows
```

If you want help restoring the boot, please download the boot info script from the following link. Run it and post the contents of RESULTS.txt
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by jerrylamos on 2011-03-17
> **drs305 said:**
>  Natty is using a version of Grub 1.99, which has some differences from the version of Grub (1.98) used in Maverick.


What I do is have a Maverick (or Lucid) dual (or multi) booted on the same hard drive as Natty.

After a Natty update that gets into grub the boot menu is always all screwed up.  Natty Grub menu entries point to the wrong partition, several entries appear for different Ubuntu's pointing to the same partition, you name it.  All screwed up.

Now some of my hard drives have as many as 10 partitions.  Maverick has no trouble with this, Natty can't handle it.

With effort so far I've been able to get Maverick or Lucid booted, run update-grub and grub install /dev/sda 

No I don't have a launchpad bug entered on this.  Basically almost all daily Natty Daily Builds won't install anyway.  

Jerry

---

### Post by drs305 on 2011-03-17
What I do anytime there is a Natty grub update and I don't want to use it is to reboot into Maverick and immediately run "sudo grub-install /dev/sda" to revert control back to Maverick.

I also use different backgrounds on my Grub screen so I know immediately whether I'm booting from Natty's or Maverick's Grub.  Of course, I could always look at the version number at the top of the screen or see which kernel is listed as the first entry, but the background is even more obvious to me...  

Since I have multiple versions of the same release (and therefore same Grub2) on my system, each background has the partition number in the lower corner as well so I can immediately determine which OS is controlling Grub2.

---

### Post by billbear on 2011-03-17
There was a bug in natty alpha that under particular circumstances grub corrupts first ntfs partition:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/730225](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/730225)

---

