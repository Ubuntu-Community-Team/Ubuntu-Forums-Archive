---
title: "CD mounts but DVD does not mount"
date: 2013-05-01
forum: Multimedia Software
---

### Post by deodhar on 2013-05-01
I have installed Ubuntu 12.04 LTS through .iso image on DVD drive.  
Problem:- if a CD is loaded in the drive, it mounts correctly. But DVD does not mount.  
I am SURE that it is a DVD drive.  
On WinXP, I have burned a DVD yesterday.  

dmesg | grep sr0  
   
gives output as --   

[    3.771706] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray  
[    3.772001] sr 5:0:0:0: Attached scsi CD-ROM sr0  

I also installed libdvdnav4, but no success.  
"apt-get install libdvdnav4"

Then,  
    sudo mount /dev/sr0 /cdrom 

gives output as --  
    mount: block device /dev/sr0 is write-protected, mounting read-only

Still, it is not mounted. (I mean, I can neither access it through file-manager, nor throu' terminal.  

Can anybody pl. suggest a remedy?  
Thanks.

---

