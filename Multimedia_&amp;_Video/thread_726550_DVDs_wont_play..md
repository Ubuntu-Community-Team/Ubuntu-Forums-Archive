---
title: "DVDs wont play."
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by gamer4lyf3 on 2008-03-16
I can't get them to play I keep getting errors. I was reading another post and it said to try and put this into the terminal and see what I get "mplayer dvd://".
When I did that command I got this.

Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
Couldn't open DVD device: /dev/dvd
[file] No filename
Failed to open dvd://.


Exiting... (End of file)

I think this means that it's not looking at the proper drive? I have a DVD in the drive too.
any help please?

---

### Post by Ptero-4 on 2008-03-16
type this at the console:
```
sudo ln /dev/<yourdvddrive> /dev/dvd
```
replacing <yourdvddrive> with the block device for your dvd drive. This command will create a symlink called /dev/dvd (which is what mplayer seems to expect to find) that points to the actual block device assigned to your dvd drive. It will need admin permissions to put the symlink in the /dev folder where mplayer expects to find it.
As for lirc support. Open synaptic and install lirc and lirc-X.

---

### Post by gamer4lyf3 on 2008-03-16
Thanks for the reply,
but one question. How do I figure out what my "block device" is?

---

### Post by GTvulse on 2008-03-16
> **gamer4lyf3 said:**
> Thanks for the reply,
but one question. How do I figure out what my "block device" is?


That's done automatically by the udev daemon when the machine boots, so you don't have to resort to symlinking hackery. Just browse the contents of the /dev directory in your machine. The files called dvd and dvdrw will be it.

---

### Post by gamer4lyf3 on 2008-03-16
Sorry but I'm really new to Linux. I know some of the basics.
But I went to my /dev folder and I found 2 files one that says "dvd1" and another that says "dvdrw1".
What do I do with them now?

---

### Post by GTvulse on 2008-03-16
Hmmm.... You will have to edit the file

/etc/udev/rules.d/70-persistent-cd.rules

and make sure that the devices are called dvd and dvdrw (assuming there is no other dvd player/burner that gets detected first, you haven't stated what hardware you have...). Else you'll have to swap the ordering by changing names in that file.

To edit it. "gksudo gedit" or "sudo nano" in a terminal will do, depending on your preference for a text editor. Then you can use "sudo udevtrigger" to rebuild the device files.

---

### Post by gamer4lyf3 on 2008-03-16
```
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# _NEC_DVD_RW_ND-3550A (pci-0000:00:0c.0-ide-0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0c.0-ide-0:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0c.0-ide-0:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0c.0-ide-0:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0c.0-ide-0:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
# DVD_RW_ND-3550A (pci-0000:03:09.0-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:09.0-scsi-0:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:09.0-scsi-0:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:09.0-scsi-0:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:03:09.0-scsi-0:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
```

This is what I got when I went to that destination.
and my hardware is the "_NEC_DVD_RW_ND-3550A".
I think everything looks good right?

---

### Post by GTvulse on 2008-03-17
Hmmm... Did you upgrade your system in the past so that you went through the transition from the old IDE drivers to the new libata-based ones that show PATA devices as SCSI?

---

### Post by gamer4lyf3 on 2008-03-17
Umm I don't think so. Unless it did so when I put my Pci --> IDE card in?
My mobo can only support 2 IDE ports and those two are taken up by my HDDs so my DVD drive is being supported by a PCI card that allows me to have four more IDE connections. Could it be this?

---

### Post by gamer4lyf3 on 2008-03-18
I think I somewhat solved the problem.
I just changed the path from /dev/dvd in acidRip to /dev/dvd1.
I got it to work for AcidRip at least.

---

### Post by GTvulse on 2008-03-19
My apologies for the late reply.

Changing the settings in the application is one way to do it. The cleanest, global,  way is to delete the entries in /etc/udev/rules.d/70-persistent-cd.rules or simply move the file out of the way (don't leave it in that directory or it will be read even if renamed) and then run udevtrigger to regenerate the configuration. You'll notice that both sets of entries point to the same device but the first set uses an old IDE ATA pci address while the second (the one that points to "1" devices) uses a PATA pci address (libata presents PATA and SATA devices to the system as scsi devices)

---

