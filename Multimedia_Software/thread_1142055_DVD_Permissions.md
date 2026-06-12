---
title: "DVD Permissions"
date: 2009-04-28
forum: Multimedia Software
---

### Post by AcelandineKestrel on 2009-04-28
Omg, this is really pissing me off.

I put 'Kung Fu Panda' into my DVD drive. Totem opened, and then I got an error message. It said it could not access the file because I do not have permission.

Now, I took it out and put in a data DVD I had made a while back. It loaded up fine and gave me no problems there.

I tried putting in another DVD movie, 'Tron', and got the permission error again.

Why aren't any DVD movies working? :confused: Data DVD works fine enough.

I tried commenting out the line in fstab about the /media/cdrom, but that just created an error with Hal.

Could someone please tell me how I can get permission to watch these DVDs? (and could you please explain it fully, seeing as I've only had Ubuntu for a week, and I'm still quite the noob). :(

---

### Post by AcelandineKestrel on 2009-04-28
I just now opened /etc/group to take a look at it:

```
root:x:0:
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:kestrel
tty:x:5:
disk:x:6:
lp:x:7:
mail:x:8:
news:x:9:
uucp:x:10:
man:x:12:
proxy:x:13:
kmem:x:15:
dialout:x:20:kestrel
fax:x:21:
voice:x:22:
cdrom:x:24:kestrel
floppy:x:25:
tape:x:26:
sudo:x:27:
audio:x:29:
dip:x:30:
www-data:x:33:
backup:x:34:
operator:x:37:
list:x:38:
irc:x:39:
src:x:40:
gnats:x:41:
shadow:x:42:
utmp:x:43:
video:x:44:
sasl:x:45:
plugdev:x:46:kestrel
staff:x:50:
games:x:60:
users:x:100:
nogroup:x:65534:
libuuid:x:101:
syslog:x:102:
klog:x:103:
scanner:x:104:
nvram:x:105:
fuse:x:106:
ssl-cert:x:107:
crontab:x:108:
mlocate:x:109:
ssh:x:110:
avahi-autoipd:x:111:
lpadmin:x:112:kestrel
netdev:x:113:
saned:x:114:
slocate:x:115:
messagebus:x:116:
avahi:x:117:
polkituser:x:118:
haldaemon:x:119:
admin:x:120:kestrel
gdm:x:121:
kestrel:x:1000:
sambashare:x:122:kestrel
winbindd_priv:x:123:

```

Which of those do I need to activate for it to give me permission to play the video dvd?

---

### Post by Azmaedra on 2009-06-05
I'm having the exact same problem. I installed Ubuntu a week or so ago, and out of the ten or so dvds I've tried, I always get the permission error. I tried logging in as root user, but it said the system administraor wasn't allowed to log in from the log in screen. Any ideas?

---

### Post by Azmaedra on 2009-06-07
bump

---

### Post by xc3RnbFO8P on 2009-06-07
Did you install Medibuntu
Jaunty:
[http://ubuntuforums.org/showpost.php?p=7197110&postcount=5]("http://ubuntuforums.org/showpost.php?p=7197110&postcount=5")

---

### Post by floatingpoint on 2009-06-07
Hey Ringi, 

Those instructions solved the permission problem, but the dvd playback is totally messed up. The only thing that didn't seem to work was installing the w32codec, it gave me the error 
```
E: Package w32codecs has no installation candidate
```

could this be the problem? any ideas for a solution? thanks very much for your help so far!

---

### Post by Azmaedra on 2009-06-07
That fixed it for me! On windows, just before I switched to ubuntu, every dvd I tried to play was choppy and messed up to the pint that I could no longer watch dvds, but this seems to have solved that problem as well. thank you!

---

### Post by xc3RnbFO8P on 2009-06-08
> **floatingpoint said:**
> Hey Ringi, 

Those instructions solved the permission problem, but the dvd playback is totally messed up. The only thing that didn't seem to work was installing the w32codec, it gave me the error 
```
E: Package w32codecs has no installation candidate
```

could this be the problem? any ideas for a solution? thanks very much for your help so far!
Did you install Ubuntu 64 bit, if so:
> sudo apt-get install w64codecs

---

