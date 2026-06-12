---
title: "Driver touch screen t2250mts IIYAMA Quanta"
date: 2010-05-02
forum: Multimedia Software
---

### Post by julien_ch on 2010-05-02
Hello,
 
I got the touch screen PROLITE T2250MTS from IIYAMA 22" & tried many solution from the net or ther versions of unbuntu without any succes . I coudn't let it work not even slightly & everybody says that it should work with linux!
 
Touch screen: Prolite T2250MTS IIYAMA (Quanta computers , Inc)
OS: Lynx 10.04 or karmic
 
lsusb: BUS 005 Device 002: ID 0408:3000 Quanta computer, Inc.
 
I'm french & i've submitted this problem to the french forum without any success
 
hardware : Intel board 
 
I'm new to linux but a micro computer programmer. I'll appreciate really the community if somebody helping me resolving this problem
 
Regards,

---

### Post by mgschwan on 2010-06-29
hi julien

yesterday i got the same monitor. It is not supported out of the box but it is possible to get it working.

I roughly followed these instructions [http://ubuntuforums.org/showthread.php?t=1375047](http://ubuntuforums.org/showthread.php?t=1375047)

They have an Acer monitor but the USB HID Device is exactly the same (vendor 0408 product 3000) and it works with my monitor.

Here is a short step by step list what you need to do.

Install the xorg development files

```

sudo aptitude install xserver-xorg-dev

```

Download the hidtouch suite (you should use Version 9.04.04, otherwise the patching won't work) 

```

wget http://sourceforge.net/projects/hidtouchsuite/files/xf86-input-hidtouch/v9.04.04/xf86-input-hidtouch-9.04.04.zip/download

```

Download the patch from the debian tutorial on the touchscreen

[http://wiki.debian.org/InstallingDebianOn/PackardBell/OneTwo/Lenny](http://wiki.debian.org/InstallingDebianOn/PackardBell/OneTwo/Lenny)

the file is attached at the bottom of the page and is called hidtouch.patch

unpack the hidtouch suite, apply the patch and compile it

```

unzip xf86-input-hidtouch-9.04.04.zip
cd xf86-input-hidtouch-9.04.04
patch -p 1 < <path to your hidtouch.patch>
./configure --prefix=/usr
make
sudo make install

```

Now configure some udev rules to give the monitor a fixed name under dev (which makes configuring xorg a lot less painful)

Create a file /etc/udev/rules.d/99-touch.rules with the following content

```

SUBSYSTEM=="usb", ATTRS{idVendor}=="0408", ATTRS{idProduct}=="3000", SYMLINK+="usb/quanta_touch"
SUBSYSTEM=="input", KERNEL=="event*", ATTRS{idVendor}=="0408", ATTRS{idProduct}=="3000", SYMLINK+="input/quanta_touch"

```

Now just edit (or create /etc/X11/xorg.conf)

```

Section "InputDevice"
 Identifier      "T2250MTS"
 Driver          "hidtouch"
 Option          "SendCoreEvents"        "true"
 Option          "ReportingMode"         "Raw"
 Option          "Device"                "/dev/usb/quanta_touch"
 Option          "PacketCount"           "13"
 Option          "OpcodePressure"        "852034"
 Option          "OpcodeX"               "65584"
 Option          "OpcodeY"               "65585"
 Option          "CalibrationModel"      "1"
 Option          "CornerTopLeftX"        "0"
 Option          "CornerTopLeftY"        "0"
 Option          "CornerTopRightX"       "1920" # 1920 for 23"
 Option          "CornerTopRightY"       "0"
 Option          "CornerBottomLeftX"     "0"
 Option          "CornerBottomLeftY"     "1080"  # 1080 for 23"
 Option          "CornerBottomRightX"    "1920" # 1920 for 23"
 Option          "CornerBottomRightY"    "1080"  # 1080 for 23"
 Option          "CornerScreenWidth"     "1920" # 1920 for 23"
 Option          "CornerScreenHeight"    "1080"  # 1080 for 23"
EndSection

Section "ServerLayout"
	Identifier "Touchscreen"
	InputDevice "T2250MTS" "SendCoreEvents"
EndSection

```

If you have already a file /etc/X11/xorg.conf then just add the whole Section "Input Device" and add the line 

```
InputDevice "T2250MTS" "SendCoreEvents"
```

to the ServerLayout Section.

The tutorial says you just need to restart everything but i did reboot my computer just to be sure.

Greetings 
Michael

Btw: This should work for every monitor that uses the Quanta Touchscreen Hardware

---

### Post by victor-be on 2011-01-14
hello

when i want to compile the pateched driver i have many complaints

```
make  all-recursive
make[1]: Entering directory `/home/victor/src/xf86-input-hidtouch-9.04.04'
Making all in src
make[2]: Entering directory `/home/victor/src/xf86-input-hidtouch-9.04.04/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c -o hidtouch_drv_la-hidtouch.lo `test -f 'hidtouch.c' || echo './'`hidtouch.c
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c hidtouch.c  -fPIC -DPIC -o .libs/hidtouch_drv_la-hidtouch.o
In file included from hidtouch.c:66:
hidtouch__HdtRawData.h: In function ‘HdtRawData__fillFromInputInfo’:
hidtouch__HdtRawData.h:42: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
In file included from hidtouch.c:67:
hidtouch__HdtFishNetLocator.h: In function ‘HdtFishNetLocator__destroy’:
hidtouch__HdtFishNetLocator.h:31: warning: ‘Xfree’ is deprecated (declared at /usr/include/xorg/os.h:234)
hidtouch__HdtFishNetLocator.h:36: warning: ‘Xfree’ is deprecated (declared at /usr/include/xorg/os.h:234)
hidtouch__HdtFishNetLocator.h: In function ‘HdtFishNetLocator__instanciate’:
hidtouch__HdtFishNetLocator.h:43: warning: ‘Xcalloc’ is deprecated (declared at /usr/include/xorg/os.h:225)
hidtouch__HdtFishNetLocator.h:44: warning: ‘Xcalloc’ is deprecated (declared at /usr/include/xorg/os.h:225)
In file included from hidtouch.c:71:
hidtouch__body.h: In function ‘hdtOnDeviceInit__initButtons’:
hidtouch__body.h:146: warning: ‘Xcalloc’ is deprecated (declared at /usr/include/xorg/os.h:225)
hidtouch__body.h:153: warning: passing argument 3 of ‘InitButtonClassDeviceStruct’ from incompatible pointer type
/usr/include/xorg/input.h:297: note: expected ‘Atom *’ but argument is of type ‘CARD8 *’
hidtouch__body.h:153: error: too few arguments to function ‘InitButtonClassDeviceStruct’
hidtouch__body.h:158: warning: ‘Xfree’ is deprecated (declared at /usr/include/xorg/os.h:234)
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes’:
hidtouch__body.h:174: warning: passing argument 3 of ‘InitValuatorClassDeviceStruct’ makes pointer from integer without a cast
/usr/include/xorg/input.h:303: note: expected ‘Atom *’ but argument is of type ‘int’
hidtouch__body.h:174: error: too few arguments to function ‘InitValuatorClassDeviceStruct’
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes__MinMax’:
hidtouch__body.h:213: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
hidtouch__body.h:221: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes__FourCorners’:
hidtouch__body.h:239: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
hidtouch__body.h:247: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
In file included from hidtouch__xorg_driver.h:30,
                 from hidtouch.c:72:
hidtouch__xorg_driver__driver.h: In function ‘hdtPreInit’:
hidtouch__xorg_driver__driver.h:71: warning: ‘Xcalloc’ is deprecated (declared at /usr/include/xorg/os.h:225)
hidtouch__xorg_driver__driver.h:105: warning: ‘Xfree’ is deprecated (declared at /usr/include/xorg/os.h:234)
hidtouch__xorg_driver__driver.h:124: warning: ‘Xfree’ is deprecated (declared at /usr/include/xorg/os.h:234)
hidtouch__xorg_driver__driver.h: In function ‘hdtUnInit’:
hidtouch__xorg_driver__driver.h:157: warning: ‘Xfree’ is deprecated (declared at /usr/include/xorg/os.h:234)
hidtouch__xorg_driver__driver.h:164: warning: ‘Xfree’ is deprecated (declared at /usr/include/xorg/os.h:234)
make[2]: *** [hidtouch_drv_la-hidtouch.lo] Error 1
make[2]: Leaving directory `/home/victor/src/xf86-input-hidtouch-9.04.04/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/victor/src/xf86-input-hidtouch-9.04.04'
make: *** [all] Error 2

```

so "make" fails

regarding usb, i've checked and i have a /dev/usb directory now; it only includes quanta_usb; i didn't have before and i was able to mount any usb stick, or printer...

i found out something now : on the monitor preferences, settings, when i turn off my laptop panel (so i only have the touchsreen panel working), i can have perfectly adjusted mice, and the maximum resolution; i figured that out by re-reading the debian how-to

so i suppose that having both working together may not be possible for now

i guess it's solved now

and above all, thank you for having spend some time answering to me; i admire such things :-)

best to you

victor

---

### Post by Nikb on 2011-02-05
Hi I hope this thread is still alive,
I have Exactly the same problem as victor-be

I have got to the " ./configure --prefix=/usr
                          make
[INDENT][INDENT]sudo make install" Section & I have the following error's.
[/INDENT][/INDENT]
[COLOR=DarkRed]make  all-recursive
make[1]: Entering directory `/home/ubuntu/Downloads/xf86-input-hidtouch-9.04.04'
Making all in src
make[2]: Entering directory `/home/ubuntu/Downloads/xf86-input-hidtouch-9.04.04/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c -o hidtouch_drv_la-hidtouch.lo `test -f 'hidtouch.c' || echo './'`hidtouch.c
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -O2 -fvisibility=hidden -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c hidtouch.c  -fPIC -DPIC -o .libs/hidtouch_drv_la-hidtouch.o
In file included from hidtouch.c:66:
hidtouch__HdtRawData.h: In function ‘HdtRawData__fillFromInputInfo’:
hidtouch__HdtRawData.h:42: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
In file included from hidtouch.c:71:
hidtouch__body.h: In function ‘hdtOnDeviceInit__initButtons’:
hidtouch__body.h:153: warning: passing argument 3 of ‘InitButtonClassDeviceStruct’ from incompatible pointer type
/usr/include/xorg/input.h:290: note: expected ‘Atom *’ but argument is of type ‘CARD8 *’
hidtouch__body.h:153: error: too few arguments to function ‘InitButtonClassDeviceStruct’
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes’:
hidtouch__body.h:174: warning: passing argument 3 of ‘InitValuatorClassDeviceStruct’ makes pointer from integer without a cast
/usr/include/xorg/input.h:296: note: expected ‘Atom *’ but argument is of type ‘int’
hidtouch__body.h:174: error: too few arguments to function ‘InitValuatorClassDeviceStruct’
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes__MinMax’:
hidtouch__body.h:213: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
hidtouch__body.h:221: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes__FourCorners’:
hidtouch__body.h:239: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
hidtouch__body.h:247: error: too few arguments to function ‘xf86InitValuatorAxisStruct’
make[2]: *** [hidtouch_drv_la-hidtouch.lo] Error 1
make[2]: Leaving directory `/home/ubuntu/Downloads/xf86-input-hidtouch-9.04.04/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ubuntu/Downloads/xf86-input-hidtouch-9.04.04'
make: *** [all] Error 2[/COLOR]

[COLOR=Black]
Any help would be greatly appreciated, I am quite new to ubuntu, but have enough knowledge to get myself into a whole heap of trouble. Thanks[/COLOR]

---

### Post by lx3r on 2011-05-22
I couldn't get this to work in 10.04 or 10.11 .
So I installed 11.04 and it worked right away.

No multitouch though, just single.

---

### Post by tariqf on 2011-06-22
has anyone got mulitouch working on this screen? I am using 11.04 and get single touch only.

---

### Post by tariqf on 2011-10-14
ok if anyone's interested after upgrading to 11.10 dual touch is kind of working. I can do a two finger scroll in firefox now although it's jerky and unresponsive (unlike when I boot into windows which then works flawlessly so I know the monitor is capable of working well)

---

