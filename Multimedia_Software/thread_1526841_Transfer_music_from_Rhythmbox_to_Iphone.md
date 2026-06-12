---
title: "Transfer music from Rhythmbox to Iphone"
date: 2010-07-08
forum: Multimedia Software
---

### Post by Flyboy712 on 2010-07-08
Using Lucid have Iphone 3G 3.1.3 OS Rhythmbox recognizes the device when I go to drag and drop music files to my Iphone I get the following error message:

Error while getting peer-to-peer dbus connection: The name :1.1719 was not provided by any .service files

Any Ideas/help would be greatly appreciated.

Thanks,
Mike

---

### Post by Flyboy712 on 2010-07-08
Ok so I got it working and here is what I did....

Went to libimobiledevice.org and downloaded & installed the latest version 1.0.2.  Turned off the phone lock and re-started my IPhone.  Plugged in the USB went to Rhythmbox and did the drag and drop to the IPhone icon on the left under devices.  It said it was copying the file.  When it finished you have to wait about 30-45 seconds and then your phone will do a sync.  Rhythmbox is a little slow at this so be patient.  If you unplug before it syncs then it won't show up on the IPhone.

Any questions let me know,
Mike

---

### Post by JackMohr on 2011-05-15
So I've been having this same problem and still can't seem to get the transfer to work. Now that I've turned the key lock off I can drag and drop music onto the iphone w/o getting the dbus connection error message, but the phone never displays any synch messages and the music doesnt show up in the iPod app. Rhythmbox displays the music on the iPhone, but I can't remove it through Rhythmbox. 

I'm pretty sure I have all the proper PPA files installed. I'm a bit hesitant to go mucking around installing things because I already had this issue when I did that: [http://ubuntuforums.org/showthread.php?t=1748878](http://ubuntuforums.org/showthread.php?t=1748878).

Any thoughts about what I might need to do?

---

### Post by hayhursm on 2011-08-11
> **JackMohr said:**
> So I've been having this same problem and still can't seem to get the transfer to work. Now that I've turned the key lock off I can drag and drop music onto the iphone w/o getting the dbus connection error message, but the phone never displays any synch messages and the music doesnt show up in the iPod app. Rhythmbox displays the music on the iPhone, but I can't remove it through Rhythmbox. 

I'm pretty sure I have all the proper PPA files installed. I'm a bit hesitant to go mucking around installing things because I already had this issue when I did that: [http://ubuntuforums.org/showthread.php?t=1748878](http://ubuntuforums.org/showthread.php?t=1748878).

Any thoughts about what I might need to do?

I'm having the same problem on a jailbroken iPhone 4 using IOS 4.3.5.  The music will transfer to the phone through Rhythmbox but the iPod app doesn't show any music.  The music folder (iPhone/iTunes_Control/Music) shows the songs are on the phone.

---

### Post by hayhursm on 2011-08-13
I found this from a bug report: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/711355](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/711355)

The following steps works for me:
1. Jaibreak the phone (via [http://jailbreakme.com]("http://jailbreakme.com/"))
2. Install openssh from cydia
3. ssh to the phone
4. change DBVersion to 4 in the /system/library/lockdown/Checkpoint.xml
5. Generated HashInfo following the link [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/)
6. copy HashInfo to the folder /var/mobile/Media/iTunes_Control/Device/
7. Reboot the phone
8. Mounted device automatically using Ubuntu Natty (libmobiledevice, ifuse and so on already installed)
9. Sync using Banshee


I'm going to try it here shortly and I will post my results...please post if you have success with this solution.

---

### Post by hayhursm on 2011-08-14
> **hayhursm said:**
> I found this from a bug report: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/711355](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/711355)

The following steps works for me:
1. Jaibreak the phone (via [http://jailbreakme.com]("http://jailbreakme.com/"))
2. Install openssh from cydia
3. ssh to the phone
4. change DBVersion to 4 in the /system/library/lockdown/Checkpoint.xml
5. Generated HashInfo following the link [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/)
6. copy HashInfo to the folder /var/mobile/Media/iTunes_Control/Device/
7. Reboot the phone
8. Mounted device automatically using Ubuntu Natty (libmobiledevice, ifuse and so on already installed)
9. Sync using Banshee


I'm going to try it here shortly and I will post my results...please post if you have success with this solution.

No success following this procedure...Rhythmbox still transfers the music to my iPhone 4 but the iPod app shows nothing.  Is there a solution to this problem?

---

