---
title: "HD-PVR disappears every other reboot"
date: 2010-01-07
forum: Mythbuntu
---

### Post by yonkiman on 2010-01-07
My HD-PVR's now working amazingly well (image quality, file sizes, and playback are all much better than expected), but if I reboot, it's not there (mythtv-status just shows my ATSC tuner).  If I then reboot again, it's back and works fine.  

This isn't critical since I have a fix (always reboot an even number of times), but does anyone know how I can make it always show up?

-Fred

---

### Post by blackoper on 2010-01-07
it's changing device name aka /dev/video1 is what it was when you set it up and on reboot it is sometimes being setup as for example /dev/video2

You need to make your devs static. There is a script to do this 

[http://ubuntuforums.org/showthread.php?t=753434]("http://ubuntuforums.org/showthread.php?t=753434")
download the attachment udev-rules-jaunty.py and read the rest of the thread for usage. Basically for my hdtv I rand it as

py udev-rules-jaunty.py /dev/video1 /dev/video_hdpvr

you then manually have to enter in /dev/video_hdpvr for your hdpvr in the mythtv-setup --> capture card section. After you do that it will never disappear again

---

### Post by yonkiman on 2010-01-12
Blackoper - thanks for the advice.  I was waiting to respond until I could say "That was it, it works now!", but I haven't gotten it fixed yet.  I'm sure you're right, though - will look into it further when I have more time.

Cheers!

---

### Post by loonsailor on 2010-01-26
I'm having a similar problem, but it's not an odd-even thing.

When my system reboots, either after a power cycle or 'shutdown -r', the two hdpvr's are usually not found so that neither /dev/video0 nor /dev/video1 exists.  I can bring them back with some combination of power-cycling them and unplug-replugging their USB cords.  Merely unplug-replug usually doesn't do it, nor does just power-cycling the hdpvr's.

Prior to upgrading to 9.10, I was using the development branch of v4l to get the hdpvr drivers and all worked fine.  With 9.10, the drivers are included so I'm no longer building my own from the v4l development tree.  Makes life much easier not to need to mess with recreating the drivers after every upgrade, but perhaps the new (older?) drivers are causing the problem.

I do have udev rules set up for them, to wit:
```

# Name the usb-uirt device usb-uirt0. Also, link it to /dev/lirc

ATTR{name}=="Hauppauge HD PVR", ATTRS{serial}=="00A33660", NAME="video0", SYMLINK+="hdpvr0"
ATTR{name}=="Hauppauge HD PVR", ATTRS{serial}=="00A37178", NAME="video1", SYMLINK+="hdpvr1"
```


Anybody else seen this?  Any wisdom to shed?

---

### Post by djchandler on 2010-01-26
Have you tried just stopping the backend and restarting it without powering down? I use a single PCI based ATSC card, so this is something out of my experience.

But it sounds like the USB devices aren't initializing properly on a cold boot if they are plugged in. Do you have boot from USB (or other device) switched on in your BIOS? Check your BIOS, and if it is set that way, turn that boot option off in the BIOS. 

If that doesn't fix it, then this is what I would try next. Try unplugging the USB tuners when power is off, and do not plug them back in until you have logged into your desktop. Plug in the USB tuners, then startup the MythTV backend. You may need to reconfigure how MythTV starts up by keeping the backend from starting until you can log in, then plug in the tuners.

But before you go to all that trouble, just restart the backend by running MythTV Backend Setup [**Applications>System>MythTV Backend Setup**] which will stop the backend and restart it when exiting setup.

Let us know if that works, then we can solve the rest of the puzzle of not starting the backend until your tuners are ready.

---

### Post by loonsailor on 2010-01-26
I'm actually not running myth.  I'm running SageTV.  But I don't think that this is a Sage/Myth problem, anyway.  The device should appear in /dev, independent of any application using the device, and it simply isn't there.  So, it's either a linux or a driver problem.

---

