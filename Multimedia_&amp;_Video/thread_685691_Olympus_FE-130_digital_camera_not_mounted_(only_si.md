---
title: "Olympus FE-130 digital camera not mounted (only since gutsy)"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by agostonbejo on 2008-02-02
Hi!

I'm only having this problem since having upgraded to Gutsy. (Well, something like that - see 'Additional system info below'.)

When I connect my Olympus FE-130 digital camera, it's automatically detected as usual (I get this window popping up, see screenshot). But when I click 'Open', it tries to open the contents of the camera in Dolphin, but with no success. (See other screenshot.) The problem is not with the camera, since on another machine (with Xubuntu) it mounts completely smoothly.

Operating System: 
Kubuntu Gutsy desktop 32-bit
root@<mymachine>:/media/camera# uname -a
Linux csekiguszti 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux


The last few lines from the output of 'sudo dmesg': (I don't know from which line it is relevant.)
[23926.209638] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[23926.209712] sd 3:0:0:0: Attached scsi generic sg2 type 0
[24617.133146] usb 3-1: USB disconnect, address 3
[24625.898927] usb 3-1: new full speed USB device using uhci_hcd and address 4
[24626.095661] usb 3-1: configuration #1 chosen from 1 choice
[24626.098722] scsi4 : SCSI emulation for USB Mass Storage devices
[24626.098936] usb-storage: device found at 4
[24626.098940] usb-storage: waiting for device to settle before scanning


Additional observations:
In earlier versions for any USB device (I have this camera and a Philips mp3-player) if I clicked 'Cancel' here, it was still mounted under /media/<whatever>. Now first I have to click 'Open' in the pop-up window and wait for Dolphin to show the contents. (After that I'll find it also under /media/...) I don't know if this is by design for Gutsy or an additional symptom.


Additional system info:
I've recently reinstalled Ubuntu from an Edgy live CD, then upgraded through the internet to Feisty and then Gutsy. Earlier, while I had Edgy, it worked fine. The upgrade to Feisty was interrupted in the middle back then (and probably as a result of this, the upgrade to Gutsy then messed the system up completely, and that's why I eventually reinstalled). So I cannot be sure, but this seems to be a problem with either Feisty or more probably only Gutsy, since on Edgy there was no such problem.

Btw. I have also installed gphotofs and tried to mount the camera into a pre-created directory as root. Here's the result:

root@<mymachine>:/media# ls -ltr
total 16
drwxr-xr-x 2 root root 4096 2008-01-12 18:40 floppy0
lrwxrwxrwx 1 root root    7 2008-01-12 18:40 floppy -> floppy0
drwxr-xr-x 2 root root 4096 2008-01-12 18:40 cdrom0
lrwxrwxrwx 1 root root    6 2008-01-12 18:40 cdrom -> cdrom0
drwxrwxrwx 9 root root 4096 2008-01-13 15:07 hda1
drwxrwxrwx 2 root root 4096 2008-01-30 21:11 camera

root@<mymachine>:/media# gphotofs camera

root@<mymachine>:/media# ls camera/
ls: reading directory camera/: Input/output error

root@csekiguszti:/media# mount
[...]
gphotofs on /media/camera type fuse.gphotofs (rw,nosuid,nodev)


Thanks for any help,
Agoston

---

### Post by DorianX on 2008-05-12
Having the same problem since upgrading to Gutsy witha Kodak EasyShare V803. 

Trying to import with gthumb (after verifying that gphotofs won't let me access the camera) gave this error:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device

---

