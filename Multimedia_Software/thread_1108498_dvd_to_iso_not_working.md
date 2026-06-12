---
title: "dvd to iso not working"
date: 2009-03-27
forum: Multimedia Software
---

### Post by jonny75904 on 2009-03-27
I am attempting to make ISOs of my baby einstein DVDs (kids tear up stuff you know) using ubuntu 8.10.  When I right click DVD volume and select copy to ISO file, it only images the menu software and none of the video content.

I don't want avi or mpeg because I don't care about watching them on my computer.  I only care about being able to reburn DVDs as my son tears them up. 

Please help!

---

### Post by kruegger on 2009-03-27
If you are confident at command line, it can be done this way:

sudo umount /dev/your-drive-name

dd if=/dev/your-drive-name of=file.iso bs=1024

Ubuntu mounts optical drives at boot and "dd" dd only works with unmounted devices.

"/dev/your-drive-name" refers to your device path name. "/dev" remains the same. "/your-drive-name" can be obtained by typing this:

:~$ dmesg | grep dvd

[   31.473945]  sda:[COLOR="Red"][COLOR="#ff0000"]sr0[/COLOR][/COLOR]: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   61.139612] pktcdvd: writer pktcdvd0 mapped to sr0

Figures in red show "your-device-name". Don't forget the "/" when writing the full path. In this case it'd be /dev/sr0. 
"file.iso" can be renamed if you want to. Just type your film's title and add the .iso ending.

So, first step: dmesg | grep dvd

Second: sudo umount /dev/your-drive-name (sr0 in my case).

Third:dd if=/dev/your-drive-name of=file.iso bs=1024

dd if=/dev/sr0 of=Pirates-of-the-Caribean.iso bs=1024 in my case.
      
If you want your image to be stored in some particular directory, you have to indicate a path to it: of=/home/videos/Pirates-of-the-Caribean.iso. Otherwise it will go to the current directory: your user directory if you've just opened a terminal.

And that's it.
Hope you enjoy it.):P

---

### Post by kruegger on 2009-03-27
Can do this, as well . Change where aplies.

cat /dev/"scd0" > /home/"user-directory"/test.iso.

---

