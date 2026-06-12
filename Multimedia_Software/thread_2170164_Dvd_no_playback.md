---
title: "Dvd no playback"
date: 2013-08-25
forum: Multimedia Software
---

### Post by arranskye on 2013-08-25
Tried for the first time today to watch a movie on my desktop pc ,only to find there is no playback on the dvd.      VLC & Gnome player recognise the DVD but cant play 


sudo /usr/share/doc/libdvdread4/install-css.sh 

```
maggie@margaret-VS273AA-ABU-CQ5226UK:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for maggie: 
--2013-08-25 09:18:42--  http://packages.medibuntu.org/dists/raring/free/binary-amd64/Packages
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7941 (7.8K) [application/octet-stream]
Saving to: ‘/tmp/dvdcss-h3i95B/Packages’

100%[======================================>] 7,941       --.-K/s   in 0.03s   

2013-08-25 09:18:43 (252 KB/s) - ‘/tmp/dvdcss-h3i95B/Packages’ saved [7941/7941]

--2013-08-25 09:18:43--  http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.12-0.0medibuntu1_amd64.deb
Resolving packages.medibuntu.org (packages.medibuntu.org)... 88.191.127.22
Connecting to packages.medibuntu.org (packages.medibuntu.org)|88.191.127.22|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 40506 (40K) [application/octet-stream]
Saving to: ‘/tmp/dvdcss-h3i95B/libdvdcss.deb’

100%[======================================>] 40,506       220KB/s   in 0.2s   

2013-08-25 09:18:43 (220 KB/s) - ‘/tmp/dvdcss-h3i95B/libdvdcss.deb’ saved [40506/40506]

(Reading database ... 290953 files and directories currently installed.)
Preparing to replace libdvdcss2 1.2.12-0.0medibuntu1 (using .../dvdcss-h3i95B/libdvdcss.deb) ...
Unpacking replacement libdvdcss2 ...
Setting up libdvdcss2 (1.2.12-0.0medibuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
maggie@margaret-VS273AA-ABU-CQ5226UK:~$ 



```         No joy still cant play the dvd.  please help thanks

---

### Post by arranskye on 2013-08-25
Update   I have continued trying and got an error message:  Looks like the dvd is not mounted.  It plays  Cd's ok so being new to Linux I thought that the DVD would automatically play video.

I think this is the problem as opposed to codecs.  I will continue my search on the forums and tutorials but would appreciate any help.  thanks

---

### Post by arranskye on 2013-08-25
OOps sorry  wrong again.  It is mounted and ready to work as CLI output  so look like region or codecs. Please help.  thanks

 *-c```
drom
             description: DVD-RAM writer
             product: CDDVDW TS-H653R
             vendor: hp
             physical id: 0.1.0
             bus info: scsi@2:0.1.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/dvdrw
             logical name: /dev/sr0
             logical name: /media/maggie/OFFICER_AND_GENTLEMAN
             version: 0E00
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1001,gid=1001,umask=77,iocharset=utf8 state=mounted status=ready

```

---

### Post by coldraven on 2013-08-25
Have you tried cleaning the lens?
DVD movies are dual layer and won't play even when a CD will.
I had three brand new DVDs that would not play. I cleaned the lens and two would play. I had to clean it again to get all three working.
Pets and cigarette smoke are bad news for optical drives.
Put a bit of spit on a cotton bud and **very gently** stroke the lens. It is mounted on **very delicate** springs, if you put any pressure on it it will go out of alignment.

---

### Post by arranskye on 2013-08-26
Thanks for your reply.  sorry to be such a noobi but what lens, where?????????? please

---

### Post by arranskye on 2013-08-26
Thanks for your help.  found apt-get install regionset and that sorted it.   thanks

---

### Post by hg-knight on 2013-08-26
the lens is the optical part that reads the disc.
run a dvd cleaner.

---

