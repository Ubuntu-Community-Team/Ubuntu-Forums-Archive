---
title: "Unable to create /var/lib/mythtv/* folders"
date: 2010-10-05
forum: Mythbuntu
---

### Post by joshoekstra on 2010-10-05
Got this error on trunk-builds:

E: /var/cache/apt/archives/mythgallery_0.24.0~trunk26644-0ubuntu0~mythbuntu1_i386.deb: error creating directory `./var/lib/mythtv/pictures'
E: /var/cache/apt/archives/mythvideo_0.24.0~trunk26644-0ubuntu0~mythbuntu1_i386.deb: error creating directory `./var/lib/mythtv/videos'
E: /var/cache/apt/archives/mythtv-backend_0.24.0~trunk26644-0ubuntu0~mythbuntu1_i386.deb: error creating directory `./var/lib/mythtv/fanart'

Was a stock mythbuntu-frontend with trunk-autobuilds, the weird thing is that the same update on the backend went without any problem...
I tried to uninstall and install via synaptic, but the error stays the same. Any pointers?
Unfortunately going back just one revision doesn't seem possible?

---

### Post by tgm4883 on 2010-10-05
> **joshoekstra said:**
> Got this error on trunk-builds:

E: /var/cache/apt/archives/mythgallery_0.24.0~trunk26644-0ubuntu0~mythbuntu1_i386.deb: error creating directory `./var/lib/mythtv/pictures'
E: /var/cache/apt/archives/mythvideo_0.24.0~trunk26644-0ubuntu0~mythbuntu1_i386.deb: error creating directory `./var/lib/mythtv/videos'
E: /var/cache/apt/archives/mythtv-backend_0.24.0~trunk26644-0ubuntu0~mythbuntu1_i386.deb: error creating directory `./var/lib/mythtv/fanart'

Was a stock mythbuntu-frontend with trunk-autobuilds, the weird thing is that the same update on the backend went without any problem...
I tried to uninstall and install via synaptic, but the error stays the same. Any pointers?
Unfortunately going back just one revision doesn't seem possible?

If the same update on another machine worked fine, must be an issue with the machine. Are those on a different mount?

---

### Post by joshoekstra on 2010-10-05
> **tgm4883 said:**
> If the same update on another machine worked fine, must be an issue with the machine. Are those on a different mount?
Nope stock, got everything on a single 250GB-disk and didn't tinker with it. If I manually try to
```
sudo mkdir /var/lib/mythtv/fanart
 or videos or pictures
```
I'm not allowed to do that.
I'll try my laptop frontend to see if that goes well....
BTW: I don't even know where it should be created, it just says: erro creating directory ./var/lib/mythtv/pictures, which would be relative to where apt works, where would that be?
I also checked if I got enough space, 14 GB left...

---

### Post by tgm4883 on 2010-10-05
That is the correct location (/var/lib/mythtv/*) If you aren't even able to sudo mkdir, then that is an issue.  What is the output of 

```
mount
```

---

### Post by joshoekstra on 2010-10-05
> **tgm4883 said:**
> That is the correct location (/var/lib/mythtv/*) If you aren't even able to sudo mkdir, then that is an issue.  What is the output of 

```
mount
```

```
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
``` and ls -la /var/lib/myth* shows:
```
/var/lib/mytharchive:
total 12
drwxr-xr-x  3 root   root   4096 2010-10-05 20:19 .
drwxr-xr-x 67 root   root   4096 2010-10-05 20:19 ..
drwxrwsr-x  2 mythtv mythtv 4096 2010-10-05 03:58 temp

/var/lib/mythtv:
total 4
drwxr-xr-x  2 root root    0 2010-10-05 21:31 .
drwxr-xr-x 67 root root 4096 2010-10-05 20:19 ..

```
Which is weird, my laptop which updated ok without a hitch has this:
```
/var/lib/mythdvd:
totaal 4
4 drwxrwsr-x 2 mythtv mythtv 4096 2009-04-24 07:26 temp

/var/lib/mythtv:
totaal 44
4 drwxrwsr-x 2 mythtv mythtv 4096 2009-10-26 08:34 banners
4 drwxrwsr-x 2 mythtv mythtv 4096 2009-10-26 08:34 coverart
4 drwxrwsr-x 2 mythtv mythtv 4096 2009-10-26 08:34 db_backups
4 drwxrwsr-x 2 mythtv mythtv 4096 2009-10-26 08:34 fanart
4 drwxrwsr-x 2 mythtv mythtv 4096 2009-10-26 08:34 livetv
4 drwxrwsr-x 2 mythtv mythtv 4096 2008-03-30 11:10 music
4 drwxrwxr-x 3 mythtv mythtv 4096 2008-08-15 22:59 pictures
4 drwxrwsr-x 2 mythtv mythtv 4096 2009-01-09 22:09 recordings
4 drwxrwsr-x 2 mythtv mythtv 4096 2009-10-26 08:34 screenshots
4 drwxrwsr-x 2 mythtv mythtv 4096 2009-10-26 08:34 trailers
4 drwxrwsr-x 2 mythtv mythtv 4096 2009-04-24 07:26 videos

```
The annoying this is that I left the frontend stock(except for trunk right now) to avoid this, but it's the only one presenting troubles...
The frontend and the laptop are both slave backends, the laptop doesn't have a tuner right now and the frontend does.

---

### Post by tgm4883 on 2010-10-05
I've moved this into it's own thread as it doesn't seem to be an issue with auto-builds and it will get more eyes this way.

---

### Post by tgm4883 on 2010-10-05
Are you able to make any directories anywhere? It appears the filesystem might be mounted read only

---

### Post by joshoekstra on 2010-10-05
> **tgm4883 said:**
> Are you able to make any directories anywhere? It appears the filesystem might be mounted read only
yup in homefolder:
```

mkdir bla
ls -la:
drwxr-xr-x  2 frontend frontend  4096 2010-10-05 22:54 bla

sudo mkdir /var/lib/test
frontend@frontend:~$ ls -la /var/lib/test/
total 8
drwxr-xr-x  2 root root 4096 2010-10-05 22:56 .
drwxr-xr-x 68 root root 4096 2010-10-05 22:56 ..

```

If I make a dir in /var/lib/test this happens, which is to be expected:
```
frontend@frontend:~$ mkdir /var/lib/test/test2
mkdir: cannot create directory `/var/lib/test/test2': Permission denied

frontend@frontend:~$ mkdir /var/lib/mythtv/fanart
mkdir: cannot create directory `/var/lib/mythtv/fanart': No such file or directory
frontend@frontend:~$ sudo mkdir /var/lib/mythtv/fanart
mkdir: cannot create directory `/var/lib/mythtv/fanart': No such file or directory

```

I made a copy of the the dir and tried to remove it: 
```
frontend@frontend:~$ sudo rm -rf /var/lib/mythtv
rm: cannot remove directory `/var/lib/mythtv': Device or resource busy

```
Which made me think what that was:
```
sudo lsof /var/lib/mythtv
automount 2056 root   12r   DIR   0,20        0 10055 /var/lib/mythtv
```

And now I understand, I used automount to mount a NFS-shared dir with pictures. Switching it off made everything install again, weird thing is that I made the link as /var/lib/mythtv/pictures as so only gallery should have failed and not mythvideo and backend.

Nevermind, thanks for the help and sorry for the fuss.... :)

---

