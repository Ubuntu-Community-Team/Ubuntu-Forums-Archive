---
title: "No DVD access"
date: 2008-07-24
forum: Multimedia Software
---

### Post by slink on 2008-07-24
Hi, 

after upgrading to Ubuntu Hardy I cannot access one DVD I already could with Feisty.

The players output:

MPLAYER:
No stream found to handle url dvd://1

TOTEM:
Can't show folder contents
Operation not impemented.

VLC:
Unable to open 'dvd:///dev/hdd'

And Nautilus can't show DVD's VIDEO_TS contents so I did:

```
slink@ubuntu:/media/MYDVD12$ ls -a -l
total 10
2 drwxrwxrwx 4 slink  136 2005-04-13 11:26 ./
4 drwxr-xr-x 6 root 4096 2008-07-22 15:48 ../
2 drwxrwxrwx 2 slink   40 2005-04-13 11:26 AUDIO_TS/
2 dr--r--r-- 2 slink  768 2005-04-13 11:43 VIDEO_TS/

slink@ubuntu:/media/MYDVD12$ cd VIDEO_TS/
**[COLOR="Red"]bash: cd: VIDEO_TS/: Permission denied[/COLOR]**

slink@ubuntu:/media/MYDVD12$ sudo -s -H

root@ubuntu:/media/MYDVD12# cd VIDEO_TS/

root@ubuntu:/media/MYDVD12/VIDEO_TS# ls -al
total 4378898
dr--r--r-- 2 slink 4294967295        768 2005-04-13 11:43 .
drwxrwxrwx 4 slink 4294967295        136 2005-04-13 11:26 ..
-r--r--r-- 1 slink 4294967295      12288 2005-04-13 11:43 VIDEO_TS.BUP
-r--r--r-- 1 slink 4294967295      12288 2005-04-13 11:43 VIDEO_TS.IFO
-r--r--r-- 1 slink 4294967295    2254848 2005-04-13 11:26 VIDEO_TS.VOB
-r--r--r-- 1 slink 4294967295      83968 2005-04-13 11:43 VTS_01_0.BUP
-r--r--r-- 1 slink 4294967295      83968 2005-04-13 11:43 VTS_01_0.IFO
-r--r--r-- 1 slink 4294967295  280569856 2005-04-13 11:27 VTS_01_0.VOB
-r--r--r-- 1 slink 4294967295 1073739776 2005-04-13 11:44 VTS_01_1.VOB
-r--r--r-- 1 slink 4294967295 1073739776 2005-04-13 11:44 VTS_01_2.VOB
-r--r--r-- 1 slink 4294967295 1073739776 2005-04-13 11:44 VTS_01_3.VOB
-r--r--r-- 1 slink 4294967295  962013184 2005-04-13 11:43 VTS_01_4.VOB
-r--r--r-- 1 slink 4294967295      18432 2005-04-13 11:43 VTS_02_0.BUP
-r--r--r-- 1 slink 4294967295      18432 2005-04-13 11:43 VTS_02_0.IFO
-r--r--r-- 1 slink 4294967295      38912 2005-04-13 11:43 VTS_02_0.VOB
-r--r--r-- 1 slink 4294967295   17661952 2005-04-13 11:43 VTS_02_1.VOB


```

At this point I can open the folder and see the contents while being root. 
This, obviously, should not have to be necessary.
```
root@ubuntu:/media/MYDVD12/VIDEO_TS# nautilus .
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:14902): WARNING **: Unable to add monitor: Operation not implemented.

** (totem:14983): WARNING **: Failed to create dbus proxy for org.gnome.SettingsDaemon: Could not get owner of name 'org.gnome.SettingsDaemon': no such name
gnome-video-thumbnailer couldn't process file: 'file:///media/MYDVD12/VIDEO_TS/VTS_01_3.VOB'
Reason: Took too much time to process.
seahorse nautilus module shutdown
```

So my user has no access to DVD media.

What should I check now?

---

