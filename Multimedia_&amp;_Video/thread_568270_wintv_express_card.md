---
title: "wintv express card"
date: 2007-10-05
forum: Multimedia &amp; Video
---

### Post by madandbad on 2007-10-05
I am a total nooob! ay linux and really need your help getting my wintv express with soft pvr working on ubuntu feisty and tvtime, it just says this

no signal

Permission denied
cannot open capture device /dev/video0

any help?
it did used to work but has just stopped,
on device manager it is listed as a bt878 video capture by haupphaugge

---

### Post by Jukkis on 2007-10-06
HI !

I have been working with many unix versions at my job. I have used Windows 3.1 -> XP in my personal computers, but started to use UBUNTU-linux couple of days ago, because my windows xp crashed totally.

Everything is working just fine (I have quite old pc, 500 Mhz CPU, Nvidia Riva TNT 64, SoundBlaster ZS, 3 different hard disks (2 x 8 GB and 1x16 GB, CD/DVD, RAM about 640 MB and Wintv Express (mono unfortunately) tv-card).

I think you should check the ownerships and permissions about your device. Open terminal and check it:

jukkis63@JPS1963PC:~$ cd /dev
jukkis63@JPS1963PC:/dev$ ls -l video*
crw-rw---- 1 root video 81, 0 2007-10-06 14:03 video0
jukkis63@JPS1963PC:/dev$ 

Check also your userid permissions as follow:

jukkis63@JPS1963PC:/dev$ id
uid=1000(jukkis63) gid=1000(jukkis63) ryhmät=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(jukkis63)
jukkis63@JPS1963PC:/dev$ 

As you see, the video0 owner is root and group is video. Both have write/read permissions to use the device. Your userid should belong at least to group "video" to have read and write permissions to use that device. (I have finnish system, so ryhmät=groups).

Check this first and if you do not have the permissions as above. I will give more information about make those settings if this is the problem.

Greetings from Finland.

Jukkis :)

---

### Post by madandbad on 2007-10-06
I did it and got this:
```
fred@fred and theos pc:~$ cd /dev
fred@fred and theos pc:/dev$ ls -l video*
crw-rw---- 1 root video 81, 0 2005-01-01 01:02 video0
fred@fred and theos pc:/dev$ id
uid=1001(fred) gid=1001(fred) groups=4(adm),20(dialout),21(fax),24(cdrom),25(floppy),26(tape),29(audio),30(dip),46(plugdev),104(scanner),117(admin),119(fuse),121(mythtv),1001(fred)
fred@fred and theos pc:/dev$ 
```

---

### Post by Jukkis on 2007-10-06
Okey... Your userid "fred" does not belong group "video" as you can see at the list. This problem can be solved many different ways. Following way is fast and should work (you must do this as a super user, so lets do it using sudo command... :

1. Open terminal
2. Enter command 
 sudo passwd
3. Enter your password (same as you use when login as fred)
4. Enter new password (twice, and that will be your superuser password when ever you open the terminal and give "su" command)
5. Enter command 
 su
6. Enter the new password you entered above for superuser (now you are in superuser mode, remember your superuser password in the future)
7. Enter command:
  chmod 666 /dev/video0

Now all users have permission to use /dev/video0 device.
8. Close terminal
9. Start the tv-software as before... it should work.
As I told, there are many ways to solve this problem... for example add video-group to your fred-userid. But anyway... try this. 

T: Jukkis:)

---

### Post by madandbad on 2007-10-09
thanks sooo much, it works

---

### Post by princemanjee on 2007-10-22
I have a wintv express with BT878 chip and before i use to use it with no problems... i formated my computer and reinstalled 7.1 and didnt like it so i switched back to 7.04... now i cant get any programs to find the TV card... yet i know its installed... 

I run ls -l video in the /dev and get :
'crw-rw-rw- 1 root video 81, 0 2007-10-09 15:03 video0'

then i ran id in /dev and get:
'uid=1000(prince) gid=1000(prince) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),120(mythtv),1000(prince)'

TVTIME Viewer crashes out and mythTV doesn't find the card...

what do i do next?

kinda new to linux here and fighting hard not to switch back to windows... but issues like this and not being able to do any decent gaming because ATI sucks at making video drivers makes me wanna go back to MicroShit cause it will eliminate SOME head aches... (small price to pay i guess...)   some one please help?

---

