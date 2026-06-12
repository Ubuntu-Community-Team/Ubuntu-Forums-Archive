---
title: "Can't share my secondary HD (Ubuntu to Windows)"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by ECPCLINUX on 2009-11-25
Hello, I recently built a System out of old Computer parts I had. I installed Ubuntu 9.10 in it. I built it for sharing all my files with my other computer at home. I'm tired of having so many external Hard Drives. So, I built this new/old system and installed an old Seagate 500GB hard drive I've just RMAed. I'm able to share all my files with Windows Vista & 7 without any issues at all. I installed Samba and it all worked without any issues at all, it was supper easy, just like I need it. 

**Here is the issue:**

Once I had the Ubuntu system sharing well I decided to Dismantled another External hard drive add as a secondary hard drive to the system. At first I could not get Ubuntu to share it. It took me a while to get windows to see it but I did it. The issue I'm having is that Windows finds it but it says "Access Denied" contact server administrator, that's some kind of Administrator I make. Nevertheless, here are a few things I've done, the most relevant:
 
**One **

Followed this, [https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)
Under "Sharing folders via the Shared Folders application"

the part which uses: shares-admin

This worked, to the extent which I was able to see my hard drive in Windows. Please remember this is only my secondary hard drive for which I'm having problems with, My primary hard drive, the one with Ubuntu installed can be seen and shared without issues. I then tried this same instruction with a folder. I thought if I can get one folder to be shared correctly, from my seconday hard drive, I could just put all the hard drive's content into that one folder. But I was not successful. I should mention that the secondary hard drive has been formated with NTFS, since it was an external hard drive.
 
**Second** I tried this:

I used Gedit and edited Samba, See here: [http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/](http://www.howtogeek.com/howto/ubuntu/share-ubuntu-home-directories-using-samba/)   
 Still the same problem. I'm really a Noobee at any kind of Networking, even Windows.  I would appreciate any help. If I'm able to share my secondary hard drive I would add my two other external to this system and tuck it way just let it do it's magic without a monitor. 
Note, just in case is important this Computer is connected to the Network Wireless.

In case anybody is curious, or in case it's relevant, here are the specs of this System:

MSI P6GM, Celeron 3200, 2.5GB ddr2 667, 400W iMicro power supply, Nvidia PCIE 6200 fanless, 2 SATA hard drive, 1 IDE Sony CD burner and Wireless USB Zonet ZEW2500P Adapter.

---

### Post by dmizer on 2009-11-25
Is your secondary hard drive connected via USB?

If so, you'll have to make an fstab entry to mount the USB drive before you can share it with samba. Take a look here for how to accomplish that: [http://solutionsandtips.blogspot.com/2009/05/uuid-fstab-and-automatically-mount-usb.html](http://solutionsandtips.blogspot.com/2009/05/uuid-fstab-and-automatically-mount-usb.html)

---

### Post by ECPCLINUX on 2009-11-25
Hi, thank you for your quick reply. This is an Internal secondary hard drive. My goal is to add all my external to this system internally, sorry I was not very clear.

---

### Post by dmizer on 2009-11-25
No problem. Where is your secondary HD mounted?

---

### Post by ECPCLINUX on 2009-11-25
Hi, it's inside the Ubuntu computer which I want to use as a personal server just to share files with my network. The Computer is situated, at the moment, very close to the wireless Router. I get 100% connectivity. Hope this answers your question. Once more thank you for your help.

---

### Post by dmizer on 2009-11-25
Sorry, I mean where in the computer system is the hard drive mounted.

In other words, what directory do you browse to when you want to access the files on the HD?

---

### Post by ECPCLINUX on 2009-11-25
Ohh, wow I feel like a total Noob. Is it as in windows? c: or d:, etc. if so, I looked under Disk Utility and it says /dev/sdb2. Is that what you were asking me? Otherwise, I just go to Places-Computer and then the hard drive which says 400 GB HARD DISK: SEAGATE400GB. Thank you for your patients.

---

### Post by ECPCLINUX on 2009-11-25
I wanted to add that I'm using 32 bit Ubuntu 9.10.

---

### Post by dmizer on 2009-11-26
Closer, but still not quite what I'm looking for. ;)

Try this. Please post the output of:
```
df -Th
```
and
```
cat /etc/fstab
```

---

### Post by ECPCLINUX on 2009-11-26
Thank you for you prompt help' Hereis the results for the first command:

ecpc@SERVER-PC:~$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    452G  7.0G  422G   2% /
udev         tmpfs    1.3G  260K  1.3G   1% /dev
none         tmpfs    1.3G  716K  1.3G   1% /dev/shm
none         tmpfs    1.3G  348K  1.3G   1% /var/run
none         tmpfs    1.3G     0  1.3G   0% /var/lock
none         tmpfs    1.3G     0  1.3G   0% /lib/init/rw


The second command result are:

ecpc@SERVER-PC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=b5b58444-f6df-49c2-b0d0-773abcd7f079 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=45df943c-cea3-4fac-9e2e-69de68d99ab0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
  

Ok, that's what I got. I will be going to my mother's for the day, Thanksgiving Holiday. Happy Holiday and thank you very much for your help. I'll back very late nevertheless, before I go to sleep I'll check for any help provided, once home.

---

### Post by dmizer on 2009-11-26
Humm ... let's try one more:
```
blkid
```

---

### Post by ECPCLINUX on 2009-11-27
Hi, I just got home. ok I did as you asked but, nothing came up. I copied it anyway:

ecpc@SERVER-PC:~$ blkid
ecpc@SERVER-PC:~$ 
 

Thanks!

---

### Post by ECPCLINUX on 2009-11-27
Hi, I believe I have solved this problem at least partially. The problem was not Ubuntu nor Samba as I suspected. I'm using Windows Vista,7 as well as a Nas storage metal Gear Galaxy. While Googling and trying to hit the problem from different angles, I found some info on NAS external storage. Seems like Windows 7 has issues accessing Samba based Nas storage. I can verify that since I can view mine in all computer but cannot access it from Windows 7. Anyway, Read some people's comments and they suggested re-mapping the Nas hard drive? I know what a Map is,lol Figure they might use it to assign a different place for the Nas storage drive? So I started poking around windows 7, since I could not find anyone telling how to re-map. I found that by right clicking the Ubuntu secondary hard drive while in Windows 7 network  I can choose "Map Network Drive" so a light bulb went on,:!:lol. I choose that and told Windows 7 to remap. It asked me for a user name and password, I entered ubuntu's user name & password and Voila!!! I'm in. Windows Vista is very similar but, proving a bit more stubborn. I'll keep working on Vista. I wanted to thank you all, Special thanks to dmizer, you've been great! :guitar:

---

