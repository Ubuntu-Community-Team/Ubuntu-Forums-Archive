---
title: "gspca_stv0680 Loadable Kernel Module Not Working."
date: 2012-03-27
forum: Multimedia Software
---

### Post by gazza_11 on 2012-03-27
Using Ubuntu 11.04;  2.6.38-13-generic.

My previous installation of Ubuntu, 9.10; 2.6.31-14-generic, had no problem with my Oregon Scientific V C@m (pencam) using the good ol' stv680 loadable kernel module.  Now, having upgraded to my current Ubuntu version and kernel, this module has been deprecated in favour of one called gspca_stv0680, which is supposed to be better.  Problem is: despite unmouting the camera in Nautilus then doing a (as Root):

```
modprobe gspca_stv0680
```,

although the module loads, no /dev/video device is created and I can't, therefore, use Cheese or Camorama apps.

lsusb output for camera:

```
Bus 001 Device 007: ID 0553:0202 STMicroelectronics Imaging Division (VLSI Vision) Aiptek PenCam 1
```.

/dev/video?:

```
crw-rw----+ 1 root video 81, 0 2012-03-26 22:11 /dev/video0
```.

*That* device is my PCI TV tuner card, BTW.

I've had been using the old stv680 module, as I said, fine (for years, in fact, through umpteen Mandrake/Mandriva distros).

Any suggestions?

---

### Post by 71vhiw on 2012-06-09
Same here on 12.04 upgraded to 12.10

The device is recognized and the module (gspca_stv0680) is loaded, but there is no entry for the cam in /dev/

Suggestions anyone?

---

### Post by gazza_11 on 2012-12-04
Still not working (upgraded OS to Ubuntu 12.10; 3.2.0-34-generic).:(

---

### Post by gazza_11 on 2013-07-13
> **gazza_11 said:**
> Still not working (upgraded OS to Ubuntu 12.10; 3.2.0-34-generic).:(

Still no joy.

---

### Post by charles13 on 2013-09-20
I think I know a little bit about what is happening. It also explains why it's been progressing from 12.04 all the way up to 13.04 (my version).  There's a conflict going on. The device can operate in one of two modes: still mode and video mode. Ubuntu invokes the gphoto2 filesystem to probe the camera's still picture memory, while gspca_stv0680 handles its video mode.  Trouble is, only ONE of them can be in use at a time, and currently Ubuntu gives preference to gphoto2, mounting the camera as a device and locking in still mode.  That's why, in the past, people were told to kill a process named "gvfs-gphoto2-volume-monitor". If I'm not mistaken is the gphoto2 link to gvfs, so I'm a little leery to kill this process, especially since I have other digital cameras that thiis program could link.  What we need is a way to tell the system when it encounters the device to mount it as a video device (and use gspca_stv0680) rather than as a still device. This kind of still is currently beyond me, so some help would be greatly appreciated.

---

