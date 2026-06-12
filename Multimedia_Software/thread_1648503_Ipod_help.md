---
title: "Ipod help"
date: 2010-12-18
forum: Multimedia Software
---

### Post by Redbrix on 2010-12-18
Hi all, new user first post.  Running 10.04 for about a week now and things have been going ok for the most part.

My problem is that when I plug my ipod into a usb port nothing happens.  It doesn't show up in Rhythmbox or gtkpod, I get nothing. When I use the terminal under ls usb this is what I get:

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:3012 Dell Computer Corp. Optical Wheel Mouse
Bus 004 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 05ac:1293 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 roo

So it looks like it's there.  But I don't know where to go from here.  Any help would be greatly appreciated.

---

### Post by Wobblybob on 2010-12-20
have you done a jailbreak on your iPod?

In a Terminal;
sudo apt-get install libgpod4 

Now connect your iPod using the USB cable provided and it should auto mount, you now need to navigate to /media to determine the mount point of your iPod [mine show up as /media/MY_IPOD. your iPod needs a SysInfo file adding to it so that it is identified by your system, I found this option to created worked first time. type or copy and paste the following into a Terminal after the prompt

sudo lsusb -v | grep -i Serial

this should give you a result similar to this;
```

  iSerial                 3 000D27002446H699
  iSerial                 1 0000:00:13.2
  iSerial                 0 
  iSerial                 1 0000:00:13.1
  iSerial                 1 0000:00:13.0
```
The 16 digit number is the iPod's FirewireID, now type or copy and paste the following into a Terminal after the prompt

sudo gedit /media/MY_IPOD/iPod_Control/Device/SysInfo

replacing /media/MY_IPOD with the path and name of your iPod. My iPod had one entry already of ModelNumStr: xB147 so I added a new line as follows;
ModelNumStr: xB147
FirewireGuid: 000D27002446H699
and re-saved it to the iPod. This allows it to be identified by linux programs and should now allow your music player to find it [fingers crossed].

---

### Post by nternalk on 2010-12-21
Took me awhile but I got my Ipod shuffle working. This for 10.10, install Gtkpod and run it with the Ipod plug in, this will setup your device. Make sure you close Gtkpod remove device and plug it back. Then install Banshee that the one that work for me and it's pretty fast. Open your music library in Banshee and just drag and drop the album you want on the Ipod Icon showing in the Banshee side menu. Good luck.

---

### Post by Dale61 on 2011-01-07
I do the
sudo lsusb -v | grep -i Serial

and get this:

```
 iSerial                 0 
  iSerial                 0 
  iSerial                 1 0000:00:1d.0
  iSerial                 3 
can't get device qualifier: Connection timed out
can't get debug descriptor: Connection timed out
cannot read device status, Connection timed out (110)
  iSerial                 3 HF1315-S32B-OV01-VA-R02.01.05
  iSerial                 0 
  iSerial                 1 0000:00:1a.0

```

I have three spare USB ports to work with, and when I change to a different port, the only change is where it indicates the connection time out.

The above code is the same when ipod is both on and off.

---

### Post by nothingspecial on 2011-01-07
Is the ipod mac formatted?

---

### Post by Dale61 on 2011-01-07
If it is mac formatted, it has done so on it's own as the first thing I did when I was gifted it was wipe it so as it was just a mass storage device, and has been that way for over 18 months.

If it helps, mine is a 1st gen shuffle, similar in shape to a cigarette lighter.

---

