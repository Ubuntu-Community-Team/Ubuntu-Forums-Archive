---
title: "Gstreamer with Firewire"
date: 2008-11-14
forum: Multimedia Software
---

### Post by Mr Rough on 2008-11-14
I'm attempting to work on getting my DV camera to work as a web cam. To start off, it's a Cannon HV30 and it functions under Kino perfectly fine. I set the udev properties of /dev/raw1394 to use the video group for permissions so I have access under a normal user account. I also use Ubuntu 8.10.

I'm looking for a way to use this device under v4l but so far nothing has worked and it doesn't detect the device. I've only tried this with gstreamer-properties under normal and sudo access.

From searching I found a post that appears to describe how to do this but I'm hoping there is a cleaner method. [http://ubuntuforums.org/showthread.php?t=664596&highlight=gstreamer+raw1394]("http://ubuntuforums.org/showthread.php?t=664596&highlight=gstreamer+raw1394")

Is there a newer way for this to happen through packages available in the repositories or will I need to compile what is suggested in the HOWTO?

Thank you for your time. Any help is appreciated.

---

