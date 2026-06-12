---
title: "iPod doesn't mount"
date: 2013-02-18
forum: Multimedia Software
---

### Post by G_khan on 2013-02-18
Hello,

Before any of you decide to chew me out, let me say that I have searched and searched in all forums (even in, I may be wrong, Chinese [http://forum.ubuntu.org.cn/viewtopic.php?t=377858&p=2771626](http://forum.ubuntu.org.cn/viewtopic.php?t=377858&p=2771626), and I don't even know Chinese).  I have Ubuntu Gnome Remix on a Toshiba  Satellite C655.  I've installed ifuse, and all dependencies.  I even did what this link said to do [http://code.globalkeith.com/2012/04/cant-transfer-music-to-my-ipod-with.html](http://code.globalkeith.com/2012/04/cant-transfer-music-to-my-ipod-with.html), and still nothing.  

The ipod is mounting to my tmp folder and via the link above I thought I manually changed it so that it mounts to /media/iPod but it does not.  So then I run the command 
ifuse /tmp/ipodxxxxxx (changes each time I disconnect), and I get the following error message: 

usbmuxd_get_device_list: error opening socket!
No device found, is it connected?
If it is make sure that your user has permissions to access the raw usb device.
If you're still having issues try unplugging the device and reconnecting it.

I checked out a link that said to change a line in daemon/usb.h (namely from #define PID ... 0x129a to #define PID ... 0x129e).  First I couldn't find this file, and using the command *locate*, I noticed I don't have this path anywhere (assuming *locate *was thorough).  

I even followed a link that told me to go into .gconf/apps/rhythmbox/ (I forget the last path) and delete %gcong.xml, quit and restart rhythmbox.  Many have attested by all these solutions but obviously, not me.  

Running the command, and almost all different variations of the command, idevice, I basically get the same error.  In short, please help.  The ipod I am working with right now is the latest ipod nano 2 gen (yes, that's a joke).  I tried using my brother's ipod, which is mounted properly, but rhythmbox doesn't let me add music.  More specifically, it says it adds the songs, but when I unplug the ipod and check the library, nothing new appears.  His ipod, by the way, is touch screen.  Not sure which generation it is, but it can send out text messages.  That is all the info I can provide at the moment.

---

