---
title: "Dvd will not  burn iso"
date: 2009-05-19
forum: Multimedia Software
---

### Post by hwroth1 on 2009-05-19
I created an iso image using devede and I can't get the image to burn. The dvd writer is a hp dvd 840 lightscribe. It works fine recording cds, and data dvds. 

None of the writing programs I use will recognize the disks to burn the iso image. I have used k3b, ubuntu write program, Brasero, and gnomebaker. 


Thanks

---

### Post by physwizz on 2009-05-19
I'm having the same trouble. I just want to burn a video DVD from a .mpg file but breserio didn't work. Devede seemed to burn something to the DVD but it was unplayable on a DVD player.

Do I have to first burn the iso file to the hard disk and then use another step to make the video DVD?

---

### Post by physwizz on 2009-05-19
I've worked it out.

1. burs the image file to one of your folders on the hard disc
2. right click on the .iso file and select "write to disc"
3 wait and see if the disc plays on a normal DVD player (it works!):p

---

### Post by lisati on 2009-05-19
Burning an ISO file: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by physwizz on 2009-05-19
it even works with High Definition :p:p:p

---

### Post by hwroth1 on 2009-05-19
I tried to right click and burn to disc.  The writer will not highlight the burn button. 

The unit can burn a data dvd or a cd but not an iso file. I am going to download an iso from the internet and see if it will burn a different iso. 

BTW This happens on all of the mentioned programs. The iso goes through an itegrity check and passes. So the iso is probably good 

but no copy yet. Brasero makes a copy of everything it does so I tried to burn the copy. No such luck.

---

### Post by hwroth1 on 2009-05-19
I downloaded a small iso and try to burn it. I got the same results from trying to burn a iso on cd or dvd. 

I thought that maybe the iso was bad now I am sure it is a problem with burning an iso.

---

### Post by physwizz on 2009-05-20
Don't use Breserio at all.
Just use Devede to make the iso file on the desktop or in your home folder
close down Devede
just right click on the iso file and click "write to disk" from the box

---

### Post by hwroth1 on 2009-05-22
> **physwizz said:**
> Don't use Breserio at all.
Just use Devede to make the iso file on the desktop or in your home folder
close down Devede
just right click on the iso file and click "write to disk" from the box

Thanks. I will try that. 

Harv

---

### Post by hwroth1 on 2009-05-23
> **physwizz said:**
> Don't use Breserio at all.
Just use Devede to make the iso file on the desktop or in your home folder
close down Devede
just right click on the iso file and click "write to disk" from the box


I followed your instructions and I get more of the same the program will not recognize the that their is a  blankdvd in the burner. 

I am wondering if their is a problem with the Phillip's dvds. I had a problem with memorex one time.

---

### Post by hwroth1 on 2009-05-24
I found another post that had some information that I needed. It was a really good thread that helped me deduce it might just be the hard drive. I pulled it an replaced with another I had and it worked fine creating iso and burning using devede [http://www.rastersoft.com/programas/devede.html](http://www.rastersoft.com/programas/devede.html)





# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a4fb3547-31c7-4dd2-be61-7edd4d129a08 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=eee821b9-6006-413f-8273-b57fc4ec3fde none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0





hwroth1@hwroth1-desktop:~$ sudo lshw -C disk
[sudo] password for hwroth1: 
  *-disk                  
       description: ATA Disk
       product: WDC WD300AB-00BP
       vendor: Western Digital
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 18.2
       serial: WD-WMA6W1931041
       size: 27GiB (30GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00006a42
  *-cdrom
       description: DVD-RAM writer
       product: DVD Writer 840d
       vendor: HP
       physical id: 0.1.0
       bus info: scsi@0:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: HPD3
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
hwroth1@hwroth1-desktop:~$ 


I pulled the dvd and installed a different burner it works ok.

---

