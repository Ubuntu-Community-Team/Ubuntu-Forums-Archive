---
title: "CD-ROM doesn't refresh"
date: 2007-08-22
forum: Multimedia &amp; Video
---

### Post by shadowtruth on 2007-08-22
I'm sorry if a thread like this exists already but i've searched and found none.

The problem is that when I insert a new cd it doesn't recognize it but, if I restart Ubuntu it will recognize. Also, I can't open the cd-rom player unless I issue the command from Ubuntu. (the open button doesnt work... in Ubuntu) 

the cd-rom player is ATAPI CD-ROM 52x (firmware 172A, connection SCSI)

the error message it displays is "Não foi possivel montar mídia." = can't mount media.

any help is apreciated and by the way I only use linux and ubuntu for 3 days. (meaning I can't understand lots of things so try to explain as if you were explaining to a baby ;))

---

### Post by livestockPimp on 2007-08-22
have you tried mounting/unmounting it from command line? (xterm)
when a CD is in the ROM it will lock the drive so you can't open it unless it is unmounted.
when you are at command prompt you will need to become root. (the prompt will be a # instead of $) to get to a root prompt you type "sudo -s".
to unmount a CDROM you will need to know where the cdrom is physically, ie; if it is primary master then it is /dev/hda, for primary slave IDE position its /dev/hdb, secondary master is /dev/hdc, ect.
you can see what it is by typing "df" to list all mounted partitions when the cdrom is working.

Once you know where the CDROM is at the Root command prompt type "umount /dev/hdc" this will unmount the drive, you can then open it with the button and to remount it type "mount /dev/hdc /media/cdrom -t cdrom"

to break down that last command /dev/hdc is the location of the CDROM, /media/cdrom is the mount point (where you want the files to be accessed from) and "-t cdrom" is specifying that the type of media you are mounting is a CD.
Generally you dont need to specify media type since it can auto-detect.
for more info on the mount command type "man mount".

---

### Post by shadowtruth on 2007-08-22
thanks for the reply

I go to "root mod" by pressing entering "sudo -s" but, then I can't mount or dismount

is this helpfull?

[B][I]root@shadowtruth-desktop:~# mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
[/I][/B]

---

### Post by livestockPimp on 2007-08-22
when the CD drive is working can you copy/paste the output of "df -h" and "cat /proc/partitions"

---

### Post by livestockPimp on 2007-08-22
oh, wait...
I think you typed it wrong.
type "umount /dev/hdb"
there is a space between "umount" and "/dev/hdb"

---

### Post by livestockPimp on 2007-08-22
also, when you type the "mount /dev/hdb /media/cdrom" you need to ensure that the directory structure is already there (you need to have the folders /media/cdrom), if the folders dont exist then it wont be able to mount it. and there are spaces between all of the arguments. "mount<space>/dev/hdb<space>/media/cdrom<enter>"

---

### Post by shadowtruth on 2007-08-22
> **livestockPimp said:**
> also, when you type the "mount /dev/hdb /media/cdrom" you need to ensure that the directory structure is already there, if the folders dont exist then it wont be able to mount it. and there are spaces between all of the arguments. "mount<space>/dev/hdb<space>/media/cdrom<enter>"


LOL sorry... I'll try that
thanks

---

### Post by shadowtruth on 2007-08-22
no dice...

root@shadowtruth-desktop:~# mount /dev/hdb/ media/cdrom
mount: o ponto de montagem media/cdrom não existe 

you said something about "you need to ensure that the directory structure is already there (you need to have the folders /media/cdrom)" 

oh my god I'm sorry but how do I do that? (I feel so stupid... windows as to make you dumber)

also is the text in **bold** on the post above usefull?

---

### Post by livestockPimp on 2007-08-22
ok, you have a file structure in Linux, kind of like windows, think of you "/" partition as C:\
your "/home" as your "my documents", ect.
when you mount a CD-ROM you link the contents of the CD drive to a folder. if the folder you are trying to mount it to does not exist then it will not be able to mount it.
at the command prompt type "cd /"
if you type "ls" it will list all the files and folders in the "/" directory. you need to see if "media" exists. if it does you can "cd media" if not, then you will need to "mkdir media" to create the folder. once you "cd" (this stands for change directory) you can type "ls" again to see what files/folders you have here. if "cdrom" does not exist then you can type "mkdir cdrom" to create this also.
to relate it back to windows, its like trying to save a file to a location that does not exist.

The bold stuff just tells me that there is no CD-Rom mounted. (or at least that I can see)

---

