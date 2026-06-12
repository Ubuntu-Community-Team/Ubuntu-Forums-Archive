---
title: "[SOLVED] CDROM/DVD will not play"
date: 2008-06-07
forum: Multimedia Software
---

### Post by JohnMac on 2008-06-07
I cannot get my DVD to play Cds or DVDs. A summary:

1. I have Hardy running as a virtual file on a XP host.
2. Cds and DVDs play OK in Windows although they do not autorun, I have to start them using the player,
3. I had the same fault with Gutsy
4. I followed Reassuringlyoffensive's guides and everything seemed to load without errors.
5. I tried gxine first. When I run the DVD I get a message "xine engine fails to start" then "read error from /dev/dvd"
6. I get sound when I log on and I am able to play videos, with sound,from Youtube.
7. I installed Hardy from a download, I was able to check for errors.

Can anyone help?

---

### Post by soxs on 2008-06-07
Does the dvd any encryption/is it a commercial videodvd?
sudo apt-get install lsdvd libdvdread3 libdvdread
migth help.

If not you will require to setup the medibuntu repos ([http://www.medibuntu.org/](http://www.medibuntu.org/))
follow the howto, how to add the repo and get some additional dvd reading utilities
sudo apt-get install libdvdcss2 non-free-codecs

---

### Post by JohnMac on 2008-06-07
Thanks soxs, but I have loaded this stuff all before. I did it again just because it is a wet weekend and I have nothing else to do.

All I get when when I run VLC is a bit of hissing out the speakers.
Do these apps conflict with each other?  I mean VLC and xine. Some on this forum swear by VLC.

By the way I am trying to play a DVD when has been copied, so it should not have any encryption on it.

I might try and put a bug report in through Launchpad.

---

### Post by Sinkingships7 on 2008-06-07
Try this:
```
sudo /usr/share/doc/libdvdread3/install-css.sh
```
That will give you DVD playback. If that does not work, then from the sound of things, you may have a problem with your CDROM drive.

---

### Post by JohnMac on 2008-06-08
Thanks, but no that doesn't work.

---

### Post by soxs on 2008-06-08
Does it get mounted? I mean the dvd? Does this happen with any video dvds or just with some special ones?
Do you have another linux os on your PC? soyou can check if it works there (do not install a second os just to test)

---

### Post by JohnMac on 2008-06-09
I think my DVD is mounted this is what I get when I enter lshw:

           *-cdrom
                description: DVD reader
                product: FNF246V
                vendor: CT6543D
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                logical name: /media/cdrom0
                version: 2.0B
                serial: NECVMWarVMware IDE CDR101.00
                capabilities: removable audio dvd
                configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
              *-medium
                   physical id: 0
                   logical name: /dev/cdrom
                   logical name: /media/cdrom0
                   configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,relatime state=mounted

The description seems wrong however as it is actually a DVDRAM/DVD burner/CDR.

I don't understand all that "logical name stuff"

Any thoughts?

---

### Post by soxs on 2008-06-09
plx post the output from
```
mount
``` (when your cd is in the drive and yopu hear it spinning + 5s, then check the output from mount)

---

### Post by JohnMac on 2008-06-10
When I type "mount" I get the following:

john@john-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/john/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=john)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=john)
john@john-desktop:~$ 

When I do insert a disk into the drive, and it is mounted, should I not get an icon come up in my file directory? Well I don't.

Thanks for you persistence soxs

---

### Post by soxs on 2008-06-11
```
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,utf8,user=john)
```
Your cd ism ounted correctly. you my try VLC and select [open medium] and select  /dev/scd0 as source

---

### Post by JohnMac on 2008-06-14
Thanks soxs but I have tried that and it did not work. I'll have to think about it.

---

### Post by soxs on 2008-06-14
open a terminal and type
```
cd /media/cdrom0; ls -Al
```

open another terminal and type
```
vlc
``` and try again to open the mounted cd and give pots everyting you got so far.

---

### Post by Draylorre on 2008-06-15
Thanks soxs!

I had the same problems, and when I used your last post, everything worked. What was the reasoning for this?

---

### Post by soxs on 2008-06-16
> **Draylorre said:**
> Thanks soxs!

I had the same problems, and when I used your last post, everything worked. What was the reasoning for this?
lol, that's pretty impossible as it only reads the content from your cd (if it is mounted, otherwise you will get "allinall 0")

---

### Post by JohnMac on 2008-10-11
Will not open I get "Unable to open 'dvdsimple:///dev/scd0"

Can anyone help?

---

