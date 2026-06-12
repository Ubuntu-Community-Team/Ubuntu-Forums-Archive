---
title: "Skype  Ubuntu 11.04 Natty Narwhal"
date: 2011-01-21
forum: Multimedia Software
---

### Post by ismaelteodoro on 2011-01-21
hi
on ubuntu 10.10. I use skype with:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

but 
on ubuntu 11.04 it doesn't work.

I have libqt4-dbus, libqt4-network, libqt4-xml
my cam:
ID 04fc:2001 Sunplus Technology Co., Ltd

the problem:
when I start test webcam... Segmentation fault

I need your help
thanks

---

### Post by gnuts on 2011-05-03
I also have natty 64 bit, skype audio works but no video. That is I can receive video but not send any. I have skype installed from the software center and have also tried starting it with the command posted above with no improvement. cheese currently works with my webcam.
Thanks for any input.

---

### Post by m30w on 2011-05-04
Looks like a buggy implementation from Skype. That new Skype version seems to use 32 bit GTK instead of qt. This is what is getting spat upon console startup:

```

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:13519): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:13519): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:13519): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:13519): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:13519): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:13519): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:13519): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:13519): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:13519): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:13519): Gtk-WARNING **: Loading IM context type 'ibus' failed

```

There seems to be a ia32-lib-gtk package installed on my system but it does not include the needed modules. Looks to me that either Skype must release a 64 bit version or the ia32-libs-gtk must be modified to contain those. Until then there is not much hope for us 64 bit users. Would welcome suggestions though on how to get this fixed though..

---

### Post by jakelute on 2011-05-04
I find my webcam not recognised at all since upgrade from 10.10 -- not in Skype, not in Cheese......

---

### Post by moshebagelfresser on 2011-05-04
> **jakelute said:**
> I find my webcam not recognised at all since upgrade from 10.10 -- not in Skype, not in Cheese......
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 

This works in Natty terminal you can even make a Desktop Launcher.

Moshe

---

### Post by jakelute on 2011-05-04
Thanks for that. Nope. Still no recognition of the webcam in Skype (or Cheese, of course).

But I've just discovered that both Cheese and Skype now think that my webcam is a "Venus USB2.0 Camera (/dev/video0)", which it's not!

It's a built-in webcam in my netbook (sorry, I don't know how to get more information about the webcam on my netbook, but maybe someone can tell me where to look?).

Just to repeat, both Cheese and Skype worked excellently in 10.10 on this same machine

---

### Post by rwsmith61 on 2011-05-06
> **jakelute said:**
> It's a built-in webcam in my netbook (sorry, I don't know how to get more information about the webcam on my netbook, but maybe someone can tell me where to look?).


Open up a terminal and then type:

> sudo lspci
> sudo lsusb

In one of the outputs you will see a line for your camera. Just tell us which one.

--bs

---

### Post by jakelute on 2011-05-06
Thank you. Output below. I don't see any reference at all to a webcam. Do you?

As I say, in 10.10, Cheese and Skype just worked, and the machine had no trouble finding the built-in webcam.

Any further thoughts, or is it best to reinstall 10.10? Of course, if it's a matter of filing a bug report, I'm happy to have a go, though I've little experience of doing such things.

```
****@netbook:~$ sudo lspci
[sudo] password for ****: 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
****@netbook:~$ sudo lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:3430 Z-Star Microelectronics Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Jefferythewind on 2011-05-07
Hi Everyone,

  I have the same problem here.  Before in 32 bit ubuntu 10.10, i used the common "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" command to get my USB webcam to work with skype.  Now I am on a 64 bit version of Ubuntu 11.04, and I haven't been able to figure out how to get the camera to work.

  I followed instructions [here]("http://ubuntuforums.org/showthread.php?t=432295") for 64 bit video for skype, but there was no success.  Any help would be greatly appreciated...

---

### Post by rbrick49 on 2011-05-10
> **Jefferythewind said:**
> Hi Everyone,

  I have the same problem here.  Before in 32 bit ubuntu 10.10, i used the common "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" command to get my USB webcam to work with skype.  Now I am on a 64 bit version of Ubuntu 11.04, and I haven't been able to figure out how to get the camera to work.

  I followed instructions [here]("http://ubuntuforums.org/showthread.php?t=432295") for 64 bit video for skype, but there was no success.  Any help would be greatly appreciated...
well here is some news for skype on ubuntu it has just been sold to microsft

---

### Post by jakelute on 2011-05-10
Yes. What's the future for Skype on Linux and Skype on Mac?

---

### Post by luapub on 2011-05-19
Hi,
I have the same problem (upside-down camera) as everybody here (Ubuntu 11.04 on Asus U31F - architecture x86-64).

I tried the now famous solution involving libv4l, developed by Hans de Goede, and it didn't work. I suspected it migh be a problem of updating the library, so contacted Hans and he instructed me what to do. I installed the new library with success but got the following error:

> 
make -C libv4lconvert all
make[1]: Entering directory `/home/.../v4l-utils-0.8.4-test/lib/libv4lconvert'
cc -Wp,-MMD,"libv4lconvert.d",-MQ,"libv4lconvert.o",-MP  -c -I../include -fvisibility=hidden -fPIC -DLIBDIR=\"/usr/lib\"  -DLIBSUBDIR=\"libv4l\" -I../../include -I../../lib/include -D_GNU_SOURCE  -DV4L_UTILS_VERSION='"0.8.4-test"' -g -O1 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -o libv4lconvert.o libv4lconvert.c
In file included from libv4lconvert.c:26:0:
libv4lconvert-priv.h:25:21: fatal error: jpeglib.h: No such file or directory
compilation terminated.
make[1]: *** [libv4lconvert.o] Error 1
make[1]: Leaving directory `/home/.../Downloads/v4l-utils-0.8.4-test/lib/libv4lconvert'
make: *** [all] Error 2
Hans suggested I install the dev- library for **jpeglib**, apparently the culprit - but apparently **it doesn't exist for Ubuntu 11.04 on x86 architecture**.

Any suggestion? That has the potential to help lots of other people, I believe.

Paul

---

### Post by taylorg273 on 2011-05-25
Try this command which uses 32 bit libraries instead of the one listed in a previous post:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype


Found it here: [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/784887]("https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/784887")

---

### Post by ElToro on 2011-07-14
> **taylorg273 said:**
> Try this command which uses 32 bit libraries instead of the one listed in a previous post:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype


Found it here: [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/784887](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/784887)

It works. But it generates a bunch of errors in terminal:[I]

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:6580): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:6580): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:6580): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6580): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:6580): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6580): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:6580): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:6580): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:6580): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:6580): Gtk-WARNING **: Loading IM context type 'ibus' failed[/I]

---

### Post by luapub on 2011-07-17
> **taylorg273 said:**
> Try this command which uses 32 bit libraries instead of the one listed in a previous post:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype


Found it here: [https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/784887](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/784887)

It doesn't work for me. I think I tried everything offered on (accessible) forums, and that is why I contacted Hans de Goede at the first place - he's the one who put all this methods on the web at the first place I believe! Surprised by the lack of interest in this topic by the community...

---

### Post by malucao on 2011-07-22
/edit

Works now, I did the following:

sudo apt-get install libc6-dev-i386

See [here]("http://hansdegoede.livejournal.com/7622.html") under Ubuntu Multilib instructions.

After this, you can start skype with:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

Has anyone any idea how to flip the image in flash with firefox? Command doesnt work with firefox.

---

### Post by luapub on 2011-07-23
Great ! it works for me too. Thanks Malucao!

---

### Post by gordintoronto on 2011-07-23
Jakelute: your webcam is this line:
Bus 001 Device 002: ID 0ac8:3430 Z-Star Microelectronics Corp. 

If you Google: 0ac8:3430 usb
you can get more information.

As it happens, I have a different Z-Star webcam, and mine works fine in Cheese.

---

### Post by sasabgd84 on 2011-08-06
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype


When Im in Skype Options-video-test, tested webcam and works perfect, but in video  call conversation permanent loading, and people can not see me...My  upload is 512 kb/sec :sad:  Please people help me...

---

### Post by Hansoff on 2012-01-17
thanks for your posts - used the lib32 version of preload and it works now. Using Sony Playstation2 Eye Toy - good camera.:)

---

