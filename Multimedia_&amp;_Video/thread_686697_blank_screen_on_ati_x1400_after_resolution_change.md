---
title: "blank screen on ati x1400 after resolution change"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by thepieguy on 2008-02-03
This has been a problem that made me almost uninstall Ubuntu. But I decided that I will not give up on Ubuntu just yet. I have a Dell Inspiron e1505 (also known as Inspiron 6400) with an ATI Mobility Radeon X1400. I tried to change the res from 1024x768 to 1280x800, and after I did, the screen went blank and whenever I boot into Ubuntu, I get a blank screen. How do I change the res back? I already know ctrl+alt+f7 and ctrl+alt+f3.

:confused:

---

### Post by ajgreeny on 2008-02-03
Firstly, how did you change the resolution?  If you simply changed the /etc/X11/xorg.conf file using text editor as root, you should have a backup of the file as it was before the change.  Try to reinstate that with a terminal comand ```
sudo mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf
``` or whatever the file was renamed to.  This should get you back where you were.  If you're not sure of the backup's name navigate to the folder and check file names with ```
cd /etc/X11
ls -l
```This will list all the files in that folder with permissions and dates etc etc, and could help you find the backup file name.

If you did a reconfigure of xorg, however, with ```
sudo dpkg-reconfigure xserver-xorg
```you will not have a backup, and will have to run this again and chose the old resolution when you get to that bit of the system configuration.

Good luck.

---

### Post by thepieguy on 2008-02-03
I ran a code in the Terminal that brought me to this menu of resolutions. I cannot get to the terminal though, because I have a blank screen. I can run a command in the Ctrl+alt+f3 menu, so I'm trying to find out what that code was.

---

### Post by ajgreeny on 2008-02-04
Was it perhaps ```
sudo dpkg-reconfigure -phigh xserver-xorg
```that you ran.  This is the command that configures just the resolutions of your screen, without all the other parts of xorg.  If so I think there will be no backup of your original xorg.conf.

In future, before you do anything like this backup, backup, backup.  You know it makes sense.

---

### Post by thepieguy on 2008-02-10
Yes, that was it. I ran it again and pressed space to select 1024x768, the last known working resolution. I rebooted and I still got a blank screen. I seriously considered uninstalling ubuntu because of this. I have decided to stick with it.

---

### Post by ajgreeny on 2008-02-11
I can only suggest you boot the live CD and then copy its /etc/X11/xorg.conf file to a usb flash drive and try restoring that version to your hard disk installed version, but as I said in a previous post, before you do anything, backup, backup, backup.  I'm assuming you get a display from the live CD; if not then I am not sure I can give you any further clues as to where to go now.

---

### Post by thepieguy on 2008-03-07
Alright, I am on the Live cd currently. Can you give me details on how to do this? By the way, thank you for your help.

---

### Post by ajgreeny on 2008-03-08
Ok, get the live ubuntu CD up and running, plug in a usb drive and then copy the live CD's /etc/X11/xorg.conf to the usb.  The usb will be mounted somewhere in /media, so have a look in nautilus to find what the mount point is, possibly /media/disk or something similar.  You can try to copy the file using nautilus but I'm not sure if it will work, though it should, (click and drag holding down Ctrl).  If it does, great, but if not do it with terminal ```
cp /etc/X11/xorg.conf /media/disk/
```
You should rename your old xorg.conf with sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak which will keep the file under that backup name just in case you need to use it again.
Now in your ubuntu install you will need to copy the file from the usb drive to the installed system with ```
sudo cp /media/disk/xorg.conf /etc/X11/
```

Good luck,  I hope it works.

---

