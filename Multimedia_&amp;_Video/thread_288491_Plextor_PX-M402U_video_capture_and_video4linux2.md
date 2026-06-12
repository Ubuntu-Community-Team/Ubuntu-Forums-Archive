---
title: "Plextor PX-M402U video capture and video4linux2"
date: 2006-10-29
forum: Multimedia &amp; Video
---

### Post by cosmolee on 2006-10-29
I'm trying to get my Plextor PX-M402U USB video capture device to work with Ubuntu.  As far as I can tell, various applications such as mythtv & dvr can work with any device that is supported by video4linux2.

This device is supposed to be supported natively according to [http://www.mythtv.org/wiki/index.php/Plextor_ConvertX](http://www.mythtv.org/wiki/index.php/Plextor_ConvertX) 

"The Plextor ConvertX is an external PVR that connects to your computer through USB2 and has native support for Linux through GPL kernel drivers. The PVR also has onboard hardware encoding for mjpeg, MPEG1 (VCD), MPEG2 (SVCD, DVD) and MPEG4 (DivX) with PCM (uncompressed) audio, and uses the kernel's V4L2 (video4linux) modules."


I'm using the new Ubuntu Edgy, which I understand has the new v4l2 drivers built into the kernel to support this Plextor device.

Whenever I try to run `dvr` or `mythtv-setup` I get the exact same message about not being able to find a video device.  Because the message is identical from both programs, I'm guessing it is from the v4l source:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


`lsusb` results in the following info, showing that the Plextor device has been recognized:

Bus 005 Device 004: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 005 Device 003: ID 093b:a002 Plextor Corp. 
Bus 005 Device 002: ID 2001:f103 D-Link Corp. [hex] 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  



I guess that I need to troubleshoot/setup via video4linux.  Can anyone give me some advice on how to do this?  I can't seem to find much information on v4l2 troubleshooting or setup...

Thanks,
Cosmo ](*,)

---

### Post by superm1 on 2006-10-30
> **cosmolee said:**
> I'm trying to get my Plextor PX-M402U USB video capture device to work with Ubuntu.  As far as I can tell, various applications such as mythtv & dvr can work with any device that is supported by video4linux2.

This device is supposed to be supported natively according to [http://www.mythtv.org/wiki/index.php/Plextor_ConvertX](http://www.mythtv.org/wiki/index.php/Plextor_ConvertX) 

"The Plextor ConvertX is an external PVR that connects to your computer through USB2 and has native support for Linux through GPL kernel drivers. The PVR also has onboard hardware encoding for mjpeg, MPEG1 (VCD), MPEG2 (SVCD, DVD) and MPEG4 (DivX) with PCM (uncompressed) audio, and uses the kernel's V4L2 (video4linux) modules."


I'm using the new Ubuntu Edgy, which I understand has the new v4l2 drivers built into the kernel to support this Plextor device.

Whenever I try to run `dvr` or `mythtv-setup` I get the exact same message about not being able to find a video device.  Because the message is identical from both programs, I'm guessing it is from the v4l source:

X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


`lsusb` results in the following info, showing that the Plextor device has been recognized:

Bus 005 Device 004: ID 04b8:0005 Seiko Epson Corp. Stylus Printer
Bus 005 Device 003: ID 093b:a002 Plextor Corp. 
Bus 005 Device 002: ID 2001:f103 D-Link Corp. [hex] 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  



I guess that I need to troubleshoot/setup via video4linux.  Can anyone give me some advice on how to do this?  I can't seem to find much information on v4l2 troubleshooting or setup...

Thanks,
Cosmo ](*,)

If this is anything like how other video4linux devices work, you should be able do diagnose with mplayer /dev/video0 (or whatever device node is created by your USB device).  If you'd like to make sure the drivers have loaded, query them by dmesg.  Device nodes should be made in /dev/video*.

When you get that X error, does mythtv-setup crash?  Or does it hang?  Or what happens?  Does the error occur if you run mythtv-setup without the device connected?

---

### Post by cosmolee on 2006-10-30
Dmesg doesn't show any trace of devices being setup for this unit:

/var/log$ 
/var/log$ grep -i plextor dmesg
/var/log$ 

Running `myth-setup` responds that it can't open up the device....

---

### Post by ZioLupo on 2006-10-30
Are you sure that the kernel loaded the driver?

I had a Plexttor TV402U working on Dapper after compiling the driver by OSS ([http://oss.wischip.com/)](http://oss.wischip.com/)).

Starting from Edgy I cannot let it works again.

The original driver by OSS don't compile against 2.6.17 kernel, but there is a patch around in internet ( [http://files.zoeloelip.be/wis-go-0.9.8-2.6.17.patch](http://files.zoeloelip.be/wis-go-0.9.8-2.6.17.patch) )

But after compiling I couldn't force the kernel to load the module. 

Really I don't know how to let this equipment work in Ubuntu Edge.
I'm thinking to switch back to Dapper or better to go back to Gentoo!

---

### Post by ZioLupo on 2006-10-31
Cosmolee I was able to let the ConvertX device to work under edgy.

You can find a mini-guide [here]("http://www.ubuntuforums.org/showthread.php?t=288830")

Ciao!

---

### Post by cosmolee on 2006-11-14
Update:

I was finally able to get some video capture using the rudimentary `gorecord` program, following the above-referenced mini-guide.

However, I've found out that there's another thing to watch out for:  Video4Linux2 support.  

The package `dvr` only supports the original Video4Linux (non-2) devices.  The Plextor PX-M402U is supported by the go7007 ([http://oss.wischip.com/](http://oss.wischip.com/)) driver, which provides video by the Video4Linux2 API.  

So, that's another wrinkle you have to watch out for when getting video devices to work.  You must make sure that whatever software you wish to use supports whatever Video4Linux version that supports your hardware.  V4L != V4L2.

HTH...

---

