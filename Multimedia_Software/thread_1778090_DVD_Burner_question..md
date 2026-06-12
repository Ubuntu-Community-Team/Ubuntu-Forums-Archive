---
title: "DVD Burner question."
date: 2011-06-08
forum: Multimedia Software
---

### Post by medphys on 2011-06-08
Hi All,

I am trying to get my Sony DVD burner to recognize any medium.  I have tried gnome burner and K3B and with the same results. 

:-( /dev/sr0: media is not recognized as recordable DVD: 0

System recognizes the drive but the drive does not recognize the media.  Tried another drive and got the same results. Removed and replaced the drive, reloaded K3B and Gnomeburner.

I am at a loss as to what is happening.

My fstab file looks ok.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults               0  0  
# / was on /dev/sda1 during installation
# Commented out by Dropbox
# UUID=e69b7417-cba8-433f-913b-45e63902bf1d  /              ext4         errors=remount-ro      0  1  
# swap was on /dev/sda5 during installation
UUID=b459d0d7-d3d2-4d48-bae3-c517792f8723  none           swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sdb1                                  /media/sdb1    ext4         users,user,owner       0  0  
UUID=e69b7417-cba8-433f-913b-45e63902bf1d / ext4 errors=remount-ro,user_xattr 0 1

Can anyone help?

---

### Post by jerrrys on 2011-06-08
is this a multi-setup?  on mine, my burner will only work in slot two.  i had to keep my cd in slot one.

---

### Post by medphys on 2011-06-08
No, it is the only burner I have.  It is a SATA Sony Optiarc DVD RW  AD7240S.  Worked fine last week.  Now it can't find the medium.

---

### Post by jerrrys on 2011-06-08
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8  0  0

i would think this should read sata0 instead of cdrom0

---

### Post by medphys on 2011-06-08
Seemed to work last week.  Checked the backup Fstab file and it is the same.
Could try it.  Wonder if the laser burned out?

---

### Post by jerrrys on 2011-06-08
you said that you swapped it out and still no go.  i also wonder about a corrupt driver or maybe even bios?

---

### Post by medphys on 2011-06-09
I'm asking a dumb question, how could I reinstall the driver for the DVD burner.  Where would I find it?

Thanks for your help.

---

### Post by syoung27 on 2011-06-09
just google your make and the company should source drivers. might be harder getting it updated onto your linux distro though.

---

### Post by jerrrys on 2011-06-09
i have skimmed through the below links and have found other suggestions to try.  the cdrom0 entry has been used by others, so guess thats ok. 

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=corrupt+cd+dvd+driver&sa=Search&cof=FORID:9#1016](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=corrupt+cd+dvd+driver&sa=Search&cof=FORID:9#1016)
[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=SATA+dvd&as_qdr=all&sa=Google+Search&lang=en#956]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=SATA+dvd&as_qdr=all&sa=Google+Search&lang=en#956")
[http://www.google.com/search?client=ubuntu&channel=fs&q=SATA+Sony+Optiarc+DVD+RW+AD7240S+linux&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=SATA+Sony+Optiarc+DVD+RW+AD7240S+linux&ie=utf-8&oe=utf-8)

EDIT: took a look for drivers at sony site and only found window drivers.

---

### Post by syoung27 on 2011-06-09
Jerry's i can't PM you, are you familiar with USB audio devices in linux? Ubuntu specifically. im having issues which recently came up.

[http://ubuntuforums.org/showthread.php?t=1778092](http://ubuntuforums.org/showthread.php?t=1778092)

---

