---
title: "Bluetooth device manager doesn't allow for audio devices"
date: 2009-02-26
forum: Multimedia Software
---

### Post by stir-crazy on 2009-02-26
I just got a little USB Bluetooth dongle, trying to get it to connect to my bluetooth headphones.  Problem is, when I go to add device, there's the option for "input device" but the "audio device" is greyed out and unselectable.

I thought maybe I was missing some bluetooth audio packages, and tried to install bluez-gstreamer, bluez-alsa and bluez.  Here's what I got:

```
mark@Dell-erious:~$ sudo apt-get install bluez-gstreamer bluez-alsa bluez
Reading package lists... Done
Building dependency tree
Reading state information... Done
bluez-gstreamer is already the newest version.
bluez-gstreamer set to manually installed.
bluez-alsa is already the newest version.
bluez-alsa set to manually installed.
bluez is already the newest version.
bluez set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I don't know where to begin as far as the manual installs are concerned here.  Any pointers?

Thanks in advance!

---

### Post by stir-crazy on 2009-02-28
Yet another of the many things over my head in the Linux world, but found this in the README file in /usr/share/doc/bluez-alsa

```
BlueZ - Bluetooth protocol stack for Linux
******************************************

Copyright (C) 2000-2001  Qualcomm Incorporated
Copyright (C) 2002-2003  Maxim Krasnyansky <maxk@qualcomm.com>
Copyright (C) 2002-2008  Marcel Holtmann <marcel@holtmann.org>


Compilation and installation
============================

In order to compile Bluetooth utilities you need following software packages:
	- Linux Bluetooth protocol stack (BlueZ)
	- GCC compiler
	- D-Bus library
	- GLib library
	- USB library (optional)
	- Lexical Analyzer (flex, lex)
	- YACC (yacc, bison, byacc)

To configure run:
	./configure --prefix=/usr --mandir=/usr/share/man \
		--sysconfdir=/etc --localstatedir=/var --libexecdir=/lib
 
Configure automatically searches for all required components and packages. 

To compile and install run:
	make && make install


Information
===========

Mailing lists:
	linux-bluetooth@vger.kernel.org

For additional information about the project visit BlueZ web site:
	http://www.bluez.org
```

Clearly, just copying and pasting ```
./configure --prefix=/usr --mandir=/usr/share/man \
		--sysconfdir=/etc --localstatedir=/var --libexecdir=/lib
``` does nothing (didn't stop me from trying).

How do I modify this to suit my needs?  Am I on the right track?

---

### Post by TremerePuck on 2009-03-12
According to [http://lists.opensuse.org/opensuse-bugs/2009-01/msg10977.html]("http://lists.opensuse.org/opensuse-bugs/2009-01/msg10977.html")

Audio devices can't be paired with kbluetooth4 yet.  I've been trying for months. =o/  I can never get a headset to work for me.

---

### Post by inobe on 2009-03-12
[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

some stuff you can try

---

### Post by gpothier on 2009-09-13
You can use gnome's bluetooth manager:
sudo apt-get install gnome-bluetooth

Then:
bluetooth-properties

If you're on karmic, you might be hit by this bug if it has not been fixed by the time you read this: [https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/423090](https://bugs.launchpad.net/ubuntu/+source/gnome-bluetooth/+bug/423090)
In this case use the workaround in comment #3

Cheers,
g

---

### Post by luvallcomputers on 2010-10-05
I made my blue tooth headphones work.  It took install bluetooth manager in a certain order that found on the INTERNET.  Then the finial step after installing some pulseaudio-module-bluetooth-d drivers from synaptic package manager.  The main thing that I think worked was to go into my mixer and add input source 3 to the mixer and the blue tooth headphones just starting working.  I had already paired the headphones and my bluetooth dongle.  It was trusted also.

Not sure if this will help but would start at the mixer and add extra settings to see if one will work.  Using VLC as player Amorak kept crashing.

---

