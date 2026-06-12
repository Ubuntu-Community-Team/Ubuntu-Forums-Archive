---
title: "F-Spot stopped working with fresh install of 9.10"
date: 2009-11-12
forum: Multimedia Software
---

### Post by Javensbukan on 2009-11-12
Hello everybody!
Upon upgrading to Ubuntu 9.10 everything works great, except for one thing. 
F-Spot!!  With 9.04 and earlier it worked fine, but now F-Spot wont even launch!  When I launch it from the menu it starts up for a few brief seconds, then crashes.  I also did a clean install of 9.10 with the identical results.

When I launch it in terminal this is what it says:

"james@Solidarity:~$ dbus-launch f-spot
[Info  22:17:31.461] Initializing DBus
[Info  22:17:31.577] Initializing Mono.Addins
[Info  22:17:31.742] Starting new FSpot server (f-spot 0.6.1.5)

** (f-spot:4346): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4346): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4346): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4346): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:4346): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  22:17:32.655] Starting BeagleService
[Info  22:17:32.674] Hack for gnome-settings-daemon engaged

(f-spot:4346): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2891 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
james@Solidarity:~$"

For trouble shooting info here is also a lspci command:

"james@Solidarity:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)
01:0e.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)


Thanks your help would be appreciated!  I tried installing openSuSE on my computer and F-Spot worked fine, so I don't know if it is a problem with my GMA945 graphics card... it worked fine before.  Thanks!

P.S. I tried reinstalling F-Spot and it did the same thing.

---

### Post by directhex on 2009-11-13
Change theme. It's caused by a bug in your GTK theme, which F-Spot exposes

---

### Post by mr_bijae on 2009-11-23
I have experienced the same bug with three different Themes, Human, Human-Clear and U-Studio. Each produces the same results:

dbus-launch f-spot
[Info  08:24:07.237] Initializing DBus
[Info  08:24:07.383] Initializing Mono.Addins
[Info  08:24:07.592] Starting new FSpot server (f-spot 0.6.1.5)

** (f-spot:10508): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:10508): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:10508): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:10508): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:10508): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  08:24:08.614] Starting DBusService
[Info  08:24:08.620] Starting BeagleService
[Info  08:24:08.642] Hack for gnome-settings-daemon engaged

(f-spot:10508): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
EOS_DIGITAL - gnome-dev-harddisk-usb - Mountpoint file:///media/EOS_DIGITAL True True Harddrive
Harddrive
looking for /media/EOS_DIGITAL
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 2333 error_code 1 request_code 135 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by directhex on 2009-11-23
> **mr_bijae said:**
> I have experienced the same bug with three different Themes, Human, Human-Clear and U-Studio. Each produces the same results:

dbus-launch f-spot
[Info  08:24:07.237] Initializing DBus
[Info  08:24:07.383] Initializing Mono.Addins
[Info  08:24:07.592] Starting new FSpot server (f-spot 0.6.1.5)

** (f-spot:10508): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:10508): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:10508): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:10508): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:10508): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  08:24:08.614] Starting DBusService
[Info  08:24:08.620] Starting BeagleService
[Info  08:24:08.642] Hack for gnome-settings-daemon engaged

(f-spot:10508): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
EOS_DIGITAL - gnome-dev-harddisk-usb - Mountpoint file:///media/EOS_DIGITAL True True Harddrive
Harddrive
looking for /media/EOS_DIGITAL
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 2333 error_code 1 request_code 135 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

ATI graphics?

---

### Post by mr_bijae on 2009-11-23
> ATI graphics?

Yes, ATI Radeon 700. Using default drivers that came with UBUNTU 9.10.

---

### Post by Charlemagne1st on 2009-11-29
I have just tried f-spot too and got the error listed here. Changing my theme fixed this, I was using the dust theme.

Here is the error:

[Info  08:08:19.368] Initializing DBus
[Info  08:08:19.499] Initializing Mono.Addins
[Info  08:08:19.688] Starting new FSpot server (f-spot 0.6.1.5)

** (f-spot:24283): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:24283): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:24283): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:24283): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:24283): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  08:08:20.647] Starting BeagleService
[Info  08:08:20.667] Hack for gnome-settings-daemon engaged

(f-spot:24283): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 2947 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by bwsmith7 on 2009-12-08
Changing my theme worked too.

Any chance this will be fixed soon? It's kind of frustrating having to change your theme each time...

---

