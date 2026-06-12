---
title: "How to share a linux dvd drive with a windows computer"
date: 2009-11-26
forum: Mythbuntu
---

### Post by williammanda on 2009-11-26
I have a windows laptop with a broken dvd drive. I need to load some software (outlook...I remember why I switched to linux now!). I would like to use one of the linux computers dvd drive to do this. Right now samba is setup via mythbuntu so that the windows laptop can access the videos, etc... Can I add something to the existing smb.conf to do this? I found some help by googling but it hasn't worked yet. This is what I found:

[dvd]
comment = dvd drive on linux boxen
writable = No
locking = No
path = /mnt/cdrom2

I tried this info is many other ways. Here is my current smb.conf, the entry in bold is what I added:

```
[global]
workgroup = MSHOME
server string = %h server (Samba, Mythbuntu)
log file = /var/log/samba/log.%m
max log size = 1000
syslog = 0
panic action = /usr/share/samba/panic-action %d
dns proxy = no
security = share

[recordings]
comment = TV Recordings
path = /var/lib/mythtv/recordings
public = yes
writable = no
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup

[videos]
comment = Videos
path = /var/lib/mythtv/videos
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

[music]
comment = Music
path = /var/lib/mythtv/music
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

[pictures]
comment = Pictures
path = /var/lib/mythtv/pictures
public = yes
writable = yes
create mask = 0660
directory mask = 0770
force user = mythtv
force group = mythtv

[B][DVD]
comment = DVD Drive
path = /media/OC_VOLUME
writable = no
locking = no
force user = mythtv
force group = mythtv
[/B]

```

---

### Post by nickrout on 2009-11-26
```
[DVD]
comment = DVD Drive
path = /media/OC_VOLUME
writable = no
locking = no
force user = mythtv
force group = mythtv

```

First question - where does your system mount your cd/dvd? Put one in, let it mount then run the mount command ```
mount
```

That will tell you where it is mounted. Its probably /media/cdrom

When you have the answer insert that into the smb.conf file in the ```
path =
```line.

Restart samba to make sure it has read the new config file. You should then be able see the DVD share.

---

### Post by williammanda on 2009-11-27
This is the info from the mount command:

/dev/sr0 on /media/OC_VOLUME        type iso9660 (ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500)

This is what I have already in the path statement - /media/OC_VOLUME and the windows laptop asks for username and password. I enter mythtv for the user name and password and I get "DVD not accessible you may not have permission".

---

### Post by dannyboy79 on 2009-11-27
try using your credentials that you use to log into your ubuntu machine when you're in windows. the mythtv force user and force group just makes anything written to that mount point owned by mythtv user and group. you have the uid and gid being the first user on your machine so that's who you need to enter the credentials for.

i happened to find this, might help: [http://www.google.com/imgres?imgurl=http://www.pbj-design.dk/images/Mythtv-setup.png&imgrefurl=http://www.pbj-design.dk/myth_system.jsp&h=702&w=725&sz=96&tbnid=BjmCmn2pjLN0uM:&tbnh=136&tbnw=140&prev=/images%3Fq%3Dmythtv-setup%2Bpictures&hl=en&usg=__Ao_qIndT77xW-y9pQo2SuLI73pI=&ei=u_8PS67sGIewML-u7DM&sa=X&oi=image_result&resnum=1&ct=image&ved=0CAcQ9QEwAA](http://www.google.com/imgres?imgurl=http://www.pbj-design.dk/images/Mythtv-setup.png&imgrefurl=http://www.pbj-design.dk/myth_system.jsp&h=702&w=725&sz=96&tbnid=BjmCmn2pjLN0uM:&tbnh=136&tbnw=140&prev=/images%3Fq%3Dmythtv-setup%2Bpictures&hl=en&usg=__Ao_qIndT77xW-y9pQo2SuLI73pI=&ei=u_8PS67sGIewML-u7DM&sa=X&oi=image_result&resnum=1&ct=image&ved=0CAcQ9QEwAA)

and there's a tab on the left side called Myth Extra, that shows how he shared a dvd-drive for mythtv

---

### Post by williammanda on 2009-11-27
Well I've tried my username and password as well as mythtv but the same result.

---

