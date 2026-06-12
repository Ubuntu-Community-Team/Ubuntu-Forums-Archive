---
title: "camera not mounting"
date: 2011-07-20
forum: Multimedia Software
---

### Post by duncombe on 2011-07-20
I have an Olympus  D-560 ZOOM. I used to be able to download pictures from the camera with: SuSE, Fedora, early Ubuntu, etc. (I still can mount and download from my camera on these systems.)  I now have Ubuntu 10.04LTS  and no longer is my camera recognised. I cannot make sense of the forum threads on this topic, dating back to Ubuntu 8.0-something, that generally ramble on for endless pages without reaching a sensible conclusion (it's a bug, it's not a bug, it's because of gphoto2, it's a gvfs problem, etc.). So maybe there is a definitive answer why my camera that works on other linux will not work on Ubuntu, and maybe by now there is a real fix that does not involve me rebooting my laptop into an old linux distro. 

`mount' shows the camera never gets automounted. Manually `mount /dev/sdb1 /media/camera' sometimes hangs and never completes, or sometimes answers immediately `mount: /dev/sdb1 is not a valid block device'.  Output in /var/log is below.

What's going on, and how can I fix it? I do not use, and I do not want to use, fstop, gphoto, gimp or any other specific software to access my camera (I have tried to download using these anyway and nothing works), I  just want to mount the camera as though it were a flash drive in the  same manner I have always done. Remember, this does not happen on other distros or early Ubuntu.

Here is the relevant output notations in /var/log/messages and /var/log/syslog.

Jul 20 14:34:17 grace kernel: [12402.825779] usb 5-1: new full speed USB device using uhci_hcd and address 11
Jul 20 14:34:18 grace kernel: [12403.013923] usb 5-1: configuration #1 chosen from 1 choice
Jul 20 14:34:18 grace kernel: [12403.016967] scsi13 : SCSI emulation for USB Mass Storage devices
Jul 20 14:34:17 grace kernel: [12402.825779] usb 5-1: new full speed USB device using uhci_hcd and address 11
Jul 20 14:34:18 grace kernel: [12403.013923] usb 5-1: configuration #1 chosen from 1 choice
Jul 20 14:34:18 grace kernel: [12403.016967] scsi13 : SCSI emulation for USB Mass Storage devices
Jul 20 14:34:18 grace kernel: [12403.017282] usb-storage: device found at 11
Jul 20 14:34:18 grace kernel: [12403.017287] usb-storage: waiting for device to settle before scanning
Jul 20 14:34:23 grace kernel: [12408.016803] scsi 13:0:0:0: Direct-Access     OLYMPUS  X200,D560Z,C350Z 1.00 PQ: 0 ANSI: 2
Jul 20 14:34:23 grace kernel: [12408.018159] sd 13:0:0:0: Attached scsi generic sg2 type 0
Jul 20 14:34:23 grace kernel: [12408.036786] sd 13:0:0:0: [sdb] 16777216 512-byte logical blocks: (8.58 GB/8.00 GiB)
Jul 20 14:34:23 grace kernel: [12408.045774] sd 13:0:0:0: [sdb] Write Protect is off
Jul 20 14:34:23 grace kernel: [12408.013874] usb-storage: device scan complete
Jul 20 14:34:23 grace kernel: [12408.016803] scsi 13:0:0:0: Direct-Access     OLYMPUS  X200,D560Z,C350Z 1.00 PQ: 0 ANSI: 2
Jul 20 14:34:23 grace kernel: [12408.018159] sd 13:0:0:0: Attached scsi generic sg2 type 0
Jul 20 14:34:23 grace kernel: [12408.036786] sd 13:0:0:0: [sdb] 16777216 512-byte logical blocks: (8.58 GB/8.00 GiB)
Jul 20 14:34:23 grace kernel: [12408.045774] sd 13:0:0:0: [sdb] Write Protect is off
Jul 20 14:34:23 grace kernel: [12408.045781] sd 13:0:0:0: [sdb] Mode Sense: 18 00 00 08
Jul 20 14:34:23 grace kernel: [12408.045787] sd 13:0:0:0: [sdb] Assuming drive cache: write through
Jul 20 14:34:23 grace kernel: [12408.091773]  sdb: sdb1
Jul 20 14:34:23 grace kernel: [12408.162771] sd 13:0:0:0: [sdb] Attached SCSI removable disk
Jul 20 14:34:23 grace kernel: [12408.310054] usb 5-1: reset full speed USB device using uhci_hcd and address 11
Jul 20 14:34:23 grace kernel: [12408.091764] sd 13:0:0:0: [sdb] Assuming drive cache: write through
Jul 20 14:34:23 grace kernel: [12408.091773]  sdb: sdb1
Jul 20 14:34:23 grace kernel: [12408.162759] sd 13:0:0:0: [sdb] Assuming drive cache: write through
Jul 20 14:34:23 grace kernel: [12408.162771] sd 13:0:0:0: [sdb] Attached SCSI removable disk
Jul 20 14:34:23 grace kernel: [12408.310054] usb 5-1: reset full speed USB device using uhci_hcd and address 11
Jul 20 14:34:56 grace kernel: [12441.130648] usb 5-1: reset full speed USB device using uhci_hcd and address 11

  [repeated 10 or more times]

Jul 20 14:35:33 grace kernel: [12478.255444] usb 5-1: reset full speed USB device using uhci_hcd and address 11
Jul 20 14:35:33 grace kernel: [12478.417249] sd 13:0:0:0: Device offlined - not ready after error recovery
Jul 20 14:35:33 grace kernel: [12478.417268] sd 13:0:0:0: [sdb] Unhandled error code
Jul 20 14:35:33 grace kernel: [12478.417273] sd 13:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Jul 20 14:35:33 grace kernel: [12478.417282] sd 13:0:0:0: [sdb] CDB: Read(10): 28 00 00 ff ff 80 00 00 08 00
Jul 20 14:35:33 grace kernel: [12478.255444] usb 5-1: reset full speed USB device using uhci_hcd and address 11
Jul 20 14:35:33 grace kernel: [12478.417249] sd 13:0:0:0: Device offlined - not ready after error recovery
Jul 20 14:35:33 grace kernel: [12478.417268] sd 13:0:0:0: [sdb] Unhandled error code
Jul 20 14:35:33 grace kernel: [12478.417273] sd 13:0:0:0: [sdb] Result: hostbyte=DID_ABORT driverbyte=DRIVER_OK
Jul 20 14:35:33 grace kernel: [12478.417282] sd 13:0:0:0: [sdb] CDB: Read(10): 28 00 00 ff ff 80 00 00 08 00
Jul 20 14:35:33 grace kernel: [12478.417303] end_request: I/O error, dev sdb, sector 16777088
Jul 20 14:35:33 grace kernel: [12478.417313] Buffer I/O error on device sdb, logical block 2097136
Jul 20 14:35:33 grace kernel: [12478.417383] sd 13:0:0:0: rejecting I/O to offline device
Jul 20 14:35:33 grace kernel: [12478.417459] sd 13:0:0:0: rejecting I/O to offline device

  [repeated endlessly until finally:]

Jul 20 14:40:41 grace kernel: [12786.790161] usb 5-1: USB disconnect, address 11
Jul 20 14:40:41 grace kernel: [12786.790161] usb 5-1: USB disconnect, address 11

---

### Post by no2498 on 2011-07-20
10.04 does not use fspot any more
so if you see any thing at all just click open
you drag and drop

take the memory card out plug the cam in turn it on see what happens 
turn the cam off put the card back in turn cam on

---

### Post by handy on 2011-07-21
Stick the card in a $10- USB attached multi card reader & access your photos that way.

It is not advisable to connect cameras with sophisticated internal software to computers anyway as occasionally it causes the ***_camera_*** software to have a melt down = become corrupt.

I will never connect my Nikon to a computer for this very reason.

---

### Post by duncombe on 2011-07-21
Please pay attention. I do not want to buy additional hardware. Fspot or other intermediate software does not work, and I do not wish to use it. The camera mounts as mass storage on this hardware with other linux distros. Why does it not mount with UBUNTU 10.04? How can I get it to work on UBUNTU 10.04?

---

### Post by no2498 on 2011-07-21
with the cam plugged in and turned on
in a terminal type  dmesg click enter
after it stops type lsusb click enter
did lsusb see the cam

---

### Post by duncombe on 2011-07-21
Yes, lsusb sees the device (bus 5 device 7). The output of dmesg duplicates the entries in syslog and messages.

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 007: ID 07b4:0105 Olympus Optical Co., Ltd Camedia C-310Z/C-700/C-750UZ/C-755/C-765UZ/C-3040/C-4000/C-5050Z/D-560/C-3020Z Zoom Camera
Bus 005 Device 002: ID 046d:c510 Logitech, Inc. Cordless Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by no2498 on 2011-07-21
is the cam seen in places, computer

---

### Post by duncombe on 2011-07-21
No, it does not appear in  Places>Computer

---

### Post by duncombe on 2011-07-21
Ah! I did something I should have done earlier, which is log in from a terminal and try the camera without anyone logged in under gdm. The camera mounts as per normal and is totally accessible as usual. So I surmise that something is started when a user logs in under a desktop environment which grabs or subverts control of the device, rendering it invisible to normal mount. Further tests will follow and and I hope I will be able to identify the culprit and UNINSTALL or otherwise DEFEAT it.

---

### Post by handy on 2011-07-21
Read my previous post again, I fixed the inexcusable typo. :oops:

If for some obsessive compulsive reason you can't see or accept what I'm saying, then good luck to you, hopefully you will find a way.

You could of course (if you must connect your camera to your computer, even though you have been advised against it & have other ways to access your photos) use a later kernel & see if that solves the problem.


Go to [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
& pick the version of the kernel you want to use, (I use a fairly current 2.6.39-rc6-ARCH-54949-g2a9e586-dirty with no problems). 

Download and execute the following (in this order, switch to 64 if need be)
- linux-headers...all.deb
- linux-headers..generic..i386.deb
- linux-image....i386.deb

Then restart your computer.

Then you might like to do this to get later versions of software to match:

Add the xorg-edgers PPA ([https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa))

update & upgrade:

```
sudo apt-get update
sudo apt-get dist-upgrade

```
Reboot.

---

### Post by handy on 2011-07-21
> **duncombe said:**
> Please pay attention. I do not want to buy additional hardware. Fspot or other intermediate software does not work, and I do not wish to use it. The camera mounts as mass storage on this hardware with other linux distros. Why does it not mount with UBUNTU 10.04? How can I get it to work on UBUNTU 10.04?

Regressions happen every time Ubuntu releases another version. They ultimately caused me to move to another distro (which I am now grateful for. :)).

---

### Post by duncombe on 2011-07-21
No, Handy, it's not that I cannot see or accept your position on cameras and computers, it's that you appear not to understand what I am asking. I have a camera, it used to work on the computer, now it does not, why? This is not a philosophical discussion but a technical one. How to make camera work with computer. Noise about whether this is advisable or detrimental to the camera or computer is not helpful at the stage I am now at. I know that it causes damage to neither the camera nor the computer; both still work, just not together with the operating system now on the computer.

---

### Post by duncombe on 2011-07-21
Further investigation ensued. One set of programs that was running when the desktop was operational was gvfs-related. I killed all gvfs processes and now the camera will mount even while the desktop is running. Now to find out if gvfs is useful for anything and if not UNINSTALL it.

---

### Post by duncombe on 2011-07-21
Thanks to all for helping me figure out that gvfs interferes with the mount process and renders the camera inaccessible. The solution I have found is to kill all gvfs processes before attempting to mount the camera.

---

### Post by duncombe on 2011-07-21
I cover myself in ordure and beat myself mercilessly with a limp noodle. The problem turns out to have been a very old, well-known, Unix problem: permissions and ownership. Somehow, I don't know how, my $HOME/.gvfs directory had acquired an owner who was not the owner of $HOME. Resetting the ownership of $HOME/.gvfs now makes the problem go away. The camera mounts and is accessible as expected and gvfs gets to remain installed on my system.

---

### Post by Condor Cluster on 2012-01-15
I'm gonna have to resurrect this old thread.

Acquired an old Olympus D560, which won't mount on Lucid.

With regards to the above post, how do I reset the ownership of the .gvfs folder?

Thanks.

---

### Post by duncombe on 2012-01-17
ls -ld .gvfs 
will tell you who owns .gvfs directory
chown newowner:newgroup .gvfs
will change ownership of .gvfs

---

