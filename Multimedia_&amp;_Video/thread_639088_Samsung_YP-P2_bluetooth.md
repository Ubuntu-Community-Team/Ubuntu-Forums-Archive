---
title: "Samsung YP-P2 bluetooth"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by samknowsnufn on 2007-12-12
hi.
So I got this P2 and it's brilliant and all. But I'm stuck with it on gutsy for second night in a row, which says I need help. 
First of all, it's an MTP device. I tried every possible solution for MTP devices around and none of it worked. P2 didn't even blink. Gutsy knows nothing about it. Theeeen, I found out about Korean firmware upgrade, that should have magically changed it to UMS, but it obviously didn't, still nothing. 
What the upgrade did though, is enabled bluetooth file transfering IN SOME KIND OF WAY (which is promised to be enabled by samsung in "late december upgrade". for us and eu officially. Well, I don't have that time, I don't want to have anything to do with WIndows). I got myself the instructions  on bluetooth and now I'm perfectly able to upload anything to/from ubuntu to any bluetooth device at the house. Not this one, though. The problem here is, that I AM a newb and I have no idea how to crack the device myself. Here's all I know about it:

Browsing 00:16:6C:0D:98:21 ...
Service RecHandle: 0x10000
Service Class ID List:
  "PnP Information" (0x1200)

Service Name: Object Push
Service RecHandle: 0x10001
Service Class ID List:
  "OBEX Object Push" (0x1105 )
Protocol Descriptor List:
  "L2CAP" (0x0100)
  "RFCOMM" (0x0003)
    Channel: 1
  "OBEX" (0x0008)
Profile Descriptor List:
  "OBEX Object Push" (0x1105)
    Version: 0x0100

Service RecHandle: 0x10002
Service Class ID List:
  "AV Remote Target" (0x110c)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 23
  "AVCTP" (0x0017)
    uint16: 0x100
Profile Descriptor List:
  "AV Remote" (0x110e)
    Version: 0x0100

Service Name: Advanced audio source
Service RecHandle: 0x10003
Service Class ID List:
  "Audio Source" (0x110a)
Protocol Descriptor List:
  "L2CAP" (0x0100)
    PSM: 25
  "AVDTP" (0x0019)
    uint16: 0x100
Profile Descriptor List:
  "Advanced Audio" (0x110d)
    Version: 0x0100

How do I connect to it?
Sorry, that this is all I came up with for my first post, but I'd really appreciate any comments on this one. :) Thanks

---

### Post by Keenan-Windel on 2007-12-20
I had no success with MTP either, so I successfully switched my P2 over to UMS by following the instructions and firmware in this post:

[http://www.yjzone.net/showthread.php?t=1897](http://www.yjzone.net/showthread.php?t=1897)

Be sure to change the configuration file to EU EU UMS or it probably will remain MTP. I'm assuming you've already compiled the latest libmtp in order to communicate with the P2, but, if you haven't, this is absolutely necessary if you don't have a windows system. It has to be a newer build of libmtp, as the one in the repos doesn't seem to work.

Hope this helps.

Keenan

---

### Post by Keenan-Windel on 2007-12-20
A bit more of an explanation of using libmtp:

1.  Compile it from the latest sourcecode, making sure also that libusb-dev and build-essentials are installed from synaptic.

cd to directory
./configure
make
make install

2. At the command line, sudo (as root) send the files to the connected p2 with this command:

cd to where you unzipped the firmware.
mtp-sendfile <case-sensitive filename> /

This should start a transfer of the file, which will take a minute. Transfer all three files, including the MODIFIED configuration file (remember, it's EU EU UMS, not FR FR MTP).

This ought to work. Reboot your Samsung twice and you'll be good to go.

Keenan

---

### Post by Keenan-Windel on 2007-12-25
Sorry, the command is:

sudo mtp-sendfile YPP2.rom /

and so on for each of the three files.

Keenan

---

### Post by mmac on 2007-12-29
I'm sorry, but this is really confusing me.  I was able to install usbdev and build-essentials in synaptic.  The issue I'm having is that I can't seem to find where to get libtmp, it's really frustrating me, so any help would be greatly appreciated.

---

### Post by mmac on 2007-12-29
I'm having issues getting libtmp updated.  I have tried to follow the walkthrough, but it keeps failing out.

```
======================== Installation successful ==========================

Copying documentation directory...
./
./doc/
./doc/Makefile.in
./doc/Doxyfile.in
./doc/examples.h
./doc/Doxyfile
./doc/mainpage.h
./doc/Makefile
./doc/Makefile.am
./COPYING
./TODO
./README.windows.txt
./INSTALL
./AUTHORS
./README
./ChangeLog
grep: /var/tmp/iHkOBbrrqROoDNlGWZGMl/newfile: No such file or directory

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]: 

```

---

### Post by Keenan-Windel on 2007-12-29
Go here to download the newest version of libmtp (not libtmp):

[http://libmtp.sourceforge.net/index.php?page=download](http://libmtp.sourceforge.net/index.php?page=download)

Then unzip and compile it (you may want to uninstall the old version of libmtp in Synaptic...it might not be necessary, but I'm not sure):

cd to libmtp directory
./configure
make
make install (as root)

If it doesn't compile, you haven't installed libusb-dev or build-essential from Synaptic.

Then issue this command in the terminal to your connected P2 from the firmware directory (download the firmware from [http://www.yjzone.net/showthread.php?t=1897](http://www.yjzone.net/showthread.php?t=1897) ):

sudo mtp-sendfile YPP2.rom /

and so on with the RCS and data configuration file.  Remember to first edit the configuration file in a text editor and change it to:

EU EU UMS

That's all there is to it. Your P2 will now play ogg and connect in Ubuntu as a regular UMS device.

---

### Post by mmac on 2007-12-29
I ended up having to do it on a friends PC to get it working.  

I updated to the new firmware, with an old config.dat file to switch it over, and it seems to be working great now.

Have you been able to get the datacasts to work?  I would really like to be able to use them to catch my RSS feeds.

---

### Post by marc_paquin on 2008-01-01
Been following this thread with interest since I have a P2 as well (and think it's the bomb) but I'd like to know a few things before launching into it:

1. will reverting to a previous firmware affect other functions like bluetooth (I have a headset and Motorola phone three-way thing going)?
2. which software would best suited under Gutsy?
2. how can video/picture files be best sync'd?

Thanks

---

### Post by Keenan-Windel on 2008-01-02
I would actually try the 2.08 firmware (the newest version) with Bluetooth support, but I would edit a configuration file to change it to UMS if possible. I've heard the Korean version of 2.08 (this DEFINITELY has UMS) supports Bluetooth, but I haven't gotten Bluetooth file transfer working with the Korean version that I just flashed so I'm not sure (I haven't tried it with a Bluetooth headset). If you're really set on Bluetooth, you might stick with your current firmware and try using a configuration file to change it over to UMS. I don't think this would cause any malfunction with Bluetooth.  I don't know, honestly, what would happen if you changed your firmware or if you can change your United States (I assume) firmware. You might be stuck with MTP. I'm more concerned about having it work as a normal USB device on my Linux machine than in having Bluetooth, but your needs might be different. It won't break your Samsung to mess around with the firmware, though. Firmware upgrades for the Samsung are all from the Samsung company and all work, though Samsung won't support your P2 if you switch to another country in your data configuration file (just switch it back??). Flashing the firmware is actually encouraged by Samsung, I think, because they're promising at least three firmware upgrades. Anyway, sorry I can't help you much, but let me know if you've had any success with the US firmware and UMS should you give it a try.

Besides the Bluetooth issue, flashing to European or Korean actually ADDS a function: my P2 plays ogg files, and it didn't out of the box. I don't know if even the latest United States version supports the ogg format.

You don't need any special Linux software if your Samsung is UMS. It just pops up on the desktop as USB storage and you sync it by placing your media files in the various folders (Music, Video, Datacasts, etc.), then eject or unmount volume.

Video: I was able to get a video I ripped to work. Samsung seems to think they've come up with a new format altogether, but it's actually just a normal old avi file with very strict specifications that you save with a special file extension. I'll post the commands I used in mencoder as soon as I find them (give me an hour or two). Edit: go here and scroll down about halfway, as there's a good explanation of converting movies to svi format. [http://ubuntuforums.org/showthread.php?t=651894](http://ubuntuforums.org/showthread.php?t=651894) I tried this using a vob file and it worked perfectly, and it probably works for converting any kind of video file into svi.

Keenan

---

### Post by marcus2004 on 2008-01-02
I just got my P2 yesterday and am loving it so far. I have been playing with the bluetooth. My cell connected no problem. The bluetooth on the computer was harder. I tried using bluetooth analyser, but couldn't seem to get it to connect. I then ran:

```
sudo apt-get install gnome-vfs-obexftp
``` 

And installed a obex bluetooth server and I am able to send files to the P2. 
Keenan-Windel how do you find the quality of the svi files? I have converted some xvid avi's and the seemed a bit choppy.

---

