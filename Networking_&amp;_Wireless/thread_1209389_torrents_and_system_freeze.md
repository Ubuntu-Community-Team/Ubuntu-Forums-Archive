---
title: "torrents and system freeze"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by doomsword2001 on 2009-07-10
while downloading torrents ubuntu freezes.
i know this has allready been posted in foroums without any specific solution

what i realized is that my system was freezing at about 20 mins which was my screen saver starting as well. So i disabled screen saver, and this time ubuntu didnt freeze.

the bad thing is that on the torrent client (deluge) there was an error on both 2 torrents i've been downloading and download stopped.

i have also tried bittorrent, windwos apps with wine, vuze, qtorrent ...
using wireless.
i had a limit to connections to 80 instead of 200.

1) any1 knows why screen saver with torrents causes system freeze? 
2) any other way to download torrents ? 

i also have to mention i used to download lots of torrents with no errors or freezes, and then just torrents started to cause sys freeze wtf  ](*,)

---

### Post by pelmenept on 2009-07-10
Interesting. 

What do you mean by freezes ? Like a complete freeze, with no reaction to the clicks presses and anything, while screen is static (frozen). Or are you able to recover ?

I have started to experience the first type of freezes on my machines, and thought there was no relation to anything. But I was downloading torrents, not sure about screen saver. My machine could have operated for the whole day with no issues or only 5 minutes....

regards

---

### Post by doomsword2001 on 2009-07-12
by freezes i mean mouse keyboard hard disk are not working and the only solution is unplug / restart

---

### Post by superprash2003 on 2009-07-12
where is all this torrent data being stored?? is it on a drive with an NTFS filesystem?

---

### Post by doomsword2001 on 2009-07-15
on external hard disk, FAT

---

### Post by martinbaselier on 2009-07-15
What happens when you use a linux partition on your internal HDD?

---

### Post by doomsword2001 on 2009-07-15
i didnt try that cause i manualy set my partitions and dont have much space for downloads.
my home was 2gb so far.
i think my prob is gone, i repartitioned today, and installed virtualbox, to download from windows -_-
i have been searching for too much time on google, lot of people seem to have that problem but i found no solution, so might be a bug

---

### Post by martinbaselier on 2009-07-15
I use transmission for my torrents and my system never freezes while doing so.

---

### Post by doomsword2001 on 2009-07-16
if u are on 9.04 too, i guess prob is getting caused by wireless
the weird thing is if i am workin on pc it wont crash, it crashes when its idle o.O

---

### Post by martinbaselier on 2009-07-16
I'm on 9.04 too and it's on my laptop, using a wireless network.
It's probably either some energy setting, or a driver problem with your wireless card.

---

### Post by doomsword2001 on 2009-07-16
most possible to be a power setting, it only happens when pc is iddle, but still what, i also tried a new fresh install, didnt change anything

---

### Post by doomsword2001 on 2009-07-17
forgot to tell u, before i install ubuntu i have checked hardware compatibility for my laptob.
my wireless card was in the list of compatible hardware.

i also didnt tell you, when i boot i get this error : [SIZE=1][B]PCI unsupported PM CAP regs Version (7)

[/B]i am almost sure that means a peace of hardware doesnt work right.

i will give my pc some time today to download 5gb on my hd rather than the external without any screen savers and post my results. thats the only way to figure it out.
[/SIZE]

---

### Post by doomsword2001 on 2009-07-17
its not a wireless problem, i have managed to download over 5 hours from torrents with no screen saver directly to internal HDD

---

### Post by martinbaselier on 2009-07-17
As it seems, it's probably the usb-hdd, that's causing it. You could test if this is the problem, by copying large amounts of data to it. Also **dmesg** might shed some light on the problem. 

If the usb connection is the problem, try
dmesg | grep usb
to check if there are error messages on it. 

To get more info about the hdd, type **lsusb** to list all usb-devices.
Then **sudo lsusb -d xxxx:xxxx -v** to show some more verbose information, replace xxxx:xxxx with the device ID of your hdd. This can help your google search.

---

### Post by doomsword2001 on 2009-07-17
the  prob the hdd has now is that when the system crashed, some files have been conflicted and i am unable to remove them. always after a crash it happens, and then all files getting set to read only as well, sudo chmod and sudo rm -rf  wont solve the problem.in the past i deleted those files when i had same prob but i cant remember how. 

as for pasting big amount of data, i pasted 55gb's 4 days ago

[B]dmesg: 
[/B]
[ 7408.798018] FAT: Filesystem panic (dev sdc1)
[ 7408.798027]     invalid access to FAT (entry 0x0a228706)
[ 7408.798035]     File system has been set read-only
[ 7415.618324] FAT: Filesystem panic (dev sdc1)
[ 7415.618328]     invalid access to FAT (entry 0x0a228706)
[ 7421.132747] FAT: Filesystem panic (dev sdc1)
[ 7421.132751]     invalid access to FAT (entry 0x0a228706)
[40441.098940] FAT: Filesystem panic (dev sdc1)
[40441.098951]     invalid access to FAT (entry 0x0a228706)
[40456.054729] FAT: Filesystem panic (dev sdc1)
[40456.054739]     invalid access to FAT (entry 0x0a228706)
[40456.054746]     File system has been set read-only

the bad thing is that i cant format cause the disk is 500 gb with only 40 free, no way to backup. dosfsk doesnt seem to fix anything btw. is there any other solution except format?

---

### Post by martinbaselier on 2009-07-17
**dosfsck** would be the tool for that, see **man dosfsck** for more info. Hmm a corrupt filesystem could of course also cause problems. Before using it, you would need to unmount the drive, but it will tell you so if you try to do it without that.

edit: oops, just saw you already tried that.

The output from dmesg suggests the allocation table has some errors on it. 
Which repair option did you use for dosfsck, -a or -r?

It would help if you tell what happens when you use sudo **rm -rf** on the corrupted files.

---

### Post by doomsword2001 on 2009-07-19
dosfsck -a /... and dosfsck /.....

when i try rm -rf it says that it cannot delete the files cause they are read only, when i mount the disk everything becomes read only.

now i have managed to delete half of the files with just right click and delete, what i have done is mount/unmount disk lot of times, and some files got deleted. weird thing is sometimes files get delete but dont leave the bin. i also cant delete them with rm -rf /..../.trash

i dont know why when i mount my external it gets mounted as read only, probaply cause of corrupted files

---

### Post by martinbaselier on 2009-07-19
It sounds like you have a seriously corrupted filesystem:
dosfsck -r will give you more control. 
from **man dosfck**:
> Interactively repair the file system. The user is  asked  for  advice  whenever there is more than one approach to fix an inconsistency.

from **man mount**:
> 
If the msdos file  system  detects  an inconsistency,  it reports  an  error  and  sets  the  file system read-only. The file system can be made writeable again by remounting it.


```

mount -o remount,rw -t vfat /dev/**devicename** /**mountpoint**

```
replace devicename for the devicename of you hdd and mountpoint, for the point where you want to mount it.

If you type mount, it will show you all mounted drives and their mountpoints. Find your hdd in it, and use those values for the mount command.

---

### Post by doomsword2001 on 2009-07-20
thx everyone now the corrupted files are deleted[COLOR=Black][]("http://ubuntuforums.org/member.php?u=578534")
i guess now i will be available to download torrents again directly to my external
[/COLOR]

---

