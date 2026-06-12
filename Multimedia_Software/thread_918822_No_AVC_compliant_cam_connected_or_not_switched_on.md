---
title: "No AV/C compliant cam connected or not switched on"
date: 2008-09-13
forum: Multimedia Software
---

### Post by nbartusi on 2008-09-13
I am trying to capture video in Kino from my digital camcorder but I am getting this message.  I added permissions with:

> sudo mknod /dev/raw1394 c 171 0
sudo chmod a+rw /dev/raw1394


I think my firewire card is working:

> 
nbartusi@endor:~$ modprobe -l *1394*
/lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/video1394.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/eth1394.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/dv1394.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ieee1394.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/ohci1394.ko
/lib/modules/2.6.24-19-generic/kernel/drivers/ieee1394/raw1394.ko

nbartusi@endor:~$ sudo lspci
...
01:00.0 FireWire (IEEE 1394): NEC Corporation uPD72874 IEEE1394 OHCI 1.1 3-port PHY-Link Ctrlr (rev 01)
...


I have tried re-plugging the device in and manually pressing play on the camcorder.  The camcorder does work on a different Windows machine.  Any ideas I can try?

---

### Post by nbartusi on 2008-09-16
Is there someplace else I should have asked this?

---

### Post by remeeraz on 2008-10-13
Those commands are wrong.

should be

**sudo modprobe raw1394**
**sudo chown** username **/dev/raw1394**

If you don't want to have to do this every time you restart your computer...

do this

```
**sudo gedit /etc/rc.local**
```
and add the following line to it
> [COLOR="Red"]/sbin/modprobe raw1394[/COLOR]
now save and quit.
:guitar:

---

### Post by marpola on 2008-10-17
> **nbartusi said:**
> Is there someplace else I should have asked this?

I get one step further:
Capture seems to start recording but does not get anything from the camera.
It times out.
Edit>Preferences>IEEE1394
AV/C Device field is blank.

What do I enter?

---

### Post by remeeraz on 2008-10-23
> **marpola said:**
> I get one step further:
Capture seems to start recording but does not get anything from the camera.
It times out.
Edit>Preferences>IEEE1394
AV/C Device field is blank.

What do I enter?

I would start from scratch with configuring your firewire. Go to Step 9 in Post #1 of [this]("http://www.backports.ubuntuforums.org/showthread.php?t=946708") thread.

[http://www.backports.ubuntuforums.org/showthread.php?t=946708](http://www.backports.ubuntuforums.org/showthread.php?t=946708)

---

### Post by DuncanNZ on 2009-02-23
Hi there, since you're having trouble with capture over Firewire to Kino you might want to look at my recent update of the [https://help.ubuntu.com/community/Firewire](https://help.ubuntu.com/community/Firewire) page. Please let me know if there are any problems with that guide.

---

