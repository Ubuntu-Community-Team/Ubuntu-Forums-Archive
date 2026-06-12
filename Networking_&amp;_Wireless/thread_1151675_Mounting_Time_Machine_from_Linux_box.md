---
title: "Mounting Time Machine from Linux box"
date: 2009-05-07
forum: Networking &amp; Wireless
---

### Post by MacUsers on 2009-05-07
Greetings guys!!!

I'm not an ubuntu user (but mostly RedHat based) but I found this forum is very active and a number of knowledgeable guys in here, so I decided give a try here.
Can anyone tell me if it's possible to [auto]("http://discussions.apple.com/")mount my newly purchased TC on Linux (any RedHat based system) using AFP? I can mount the using samba/CIFS like this:[INDENT]***mount.cifs //10.0.11.10/Data /your-mount-point -o password=YourPassWord***
[/INDENT]but I rather like it using AFP. I'm running NetaTalk on the Linux box and afpd is already configured. Or should I stick to CIFS only?  Any one out here with such experience? you are most welcome with any comment, tips or your thoughts. Thanks in advance though. Cheers!!!

---

### Post by Kobalt on 2009-05-07
This post might help you : [http://ubuntuforums.org/showpost.php?p=6590922&postcount=12](http://ubuntuforums.org/showpost.php?p=6590922&postcount=12)

I also own a Time Capsule and an Ubuntu laptop, I've tried the above method and others in order to use AFP... But to be honest I've finally decided to stick with samba access and no auto-mount. The auto mount would launch the Time Capsule HDD from sleep with random effects.

---

### Post by MacUsers on 2009-05-07
> **Kobalt said:**
> This post might help you : [http://ubuntuforums.org/showpost.php?p=6590922&postcount=12](http://ubuntuforums.org/showpost.php?p=6590922&postcount=12)Many thanks Kobalt for your quick reply and the link; checking that out. 

> But to be honest I've finally decided to stick with samba access and no auto-mount.What made you chose samba over AFP - performance, speed, stability issues? 

> The auto mount would launch the Time Capsule HDD from sleep with random effects.What exactly did you mean by this? I plan to use TC as shared storage as well and to serve as file server (kind of) for my website. Cheers!!!

---

### Post by Kobalt on 2009-05-07
I chose smaba and not AFP because AFP wouldn't mount reliabily, sometimes it wouldn't mount at all.

A Time Capsule as a file server? Watch out, a Time Capsule is not regular NAS which you can access through FTP for instance... I would advise you to check out Apple forums for the precise use you want to do out of the Time Capsule.

---

### Post by MacUsers on 2009-05-07
Not really a file server of that sense, rather like a local disk when mounted. My plan is to use autofs, so that mount operation can be done on-demand for accessing files. And also the same way take backup (of the webserver) by cron jobs running in the back ground. Do you think that would cause any serious problem? Cheers!!!

---

### Post by Kobalt on 2009-05-07
I honnestly don't know if that's going to be possible or not with the Time Capsule, but I'm pretty sure it would be easier with a regular NAS (such as the Netgear ReadyNas) with which you could combine Time Machine, backup, file server, etc.
The Time Capsule does what it is designed for really well, but it's not really a modular NAS (yet a very good and modular router though).

---

### Post by MacUsers on 2009-05-07
The "data backup" part is working, so far. I wrote a little shell-script to test with:

```
#!/bin/bash

mkdir -p /tmpMnt
mount -t cifs //10.0.11.53/DataCenter/nVault /tmpMnt -o credentials=/root/.cifs_passwd

TARGET="/tmpMnt/Linux/"

## archive
cd ~sans
tar -czf san_Scripts.tgz Scripts/
mv -f san_Scripts.tgz ${TARGET}

## unmount
ZZ=`mount | grep tmpMnt | wc -l`

for ix in `seq ${ZZ}`; do
        umount /tmpMnt
done
sleep 1
rm -rf /tmpMnt/
```The script simply mount the drive, zip a directory move the zipped file on to the TC and then unmount the drive again when done. I set it up as a cron-job and so far it's working good. Still need to figure out the "auto-mount" part, most importantly if I really wanna do this or not. Cheers!!!

---

