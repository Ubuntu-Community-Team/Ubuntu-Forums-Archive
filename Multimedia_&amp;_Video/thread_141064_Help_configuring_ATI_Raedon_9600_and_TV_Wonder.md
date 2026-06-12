---
title: "Help configuring ATI Raedon 9600 and TV Wonder"
date: 2006-03-07
forum: Multimedia &amp; Video
---

### Post by ignatz42 on 2006-03-07
Hi all. 

I am trying to get my ATI Raedon 9600 and my ATI TV Wonder (seperate cards) to work together.  I am running Ubuntu 5.10 and have followed the instructions [here]("http://ubuntuforums.org/showpost.php?p=423584") for installing the latest ATI drivers.

Here is my verification output:
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 Generic
OpenGL version string: 2.0.5642 (8.22.5)

When I try to run tvtime I get this:

~$ sudo apt-get install tvtime
Reading package lists... Done
Building dependency tree... Done
tvtime is already the newest version.

~$ sudo tvtime
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/ignatz42/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

Here is some other information that might be helpful.

~$ sudo cat /var/log/syslog | grep bttv
Mar  7 13:10:02 localhost kernel: [4303566.323000] bttv: disagrees about version of symbol tveeprom_hauppauge_analog
Mar  7 13:10:02 localhost kernel: [4303566.323000] bttv: Unknown symbol tveeprom_hauppauge_analog

~$ lspci
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800 South]
0000:00:05.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)
0000:00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
0000:00:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
0000:00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
0000:00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [K8T800 South]
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
0000:00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 NorthBridge
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
0000:01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

I'm pretty sure that the card I am having problems with is:

0000:00:05.0 Multimedia video controller: Conexant Winfast TV2000 XP (rev 05)

I found this thread: [http://ubuntuforums.org/showthread.php?t=80296](http://ubuntuforums.org/showthread.php?t=80296) that suggested possible settings in the xorg.conf

Here are the parts of my  /etc/X11/xorg.conf

Section "Device"
	Identifier  "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "ATI Graphics Adapter 0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Any and all help is appreciated.

---

### Post by ignatz42 on 2006-03-07
I changed my /etc/X11/xorg.conf so the device section looks like this:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
EndSection

and now, this is the output from tvtime:

sudo tvtime
Password:
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/iggy/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory
Restarting tvtime.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/iggy/.tvtime/tvtime.xml
videoinput: Cannot open capture device /dev/video0: No such file or directory
Thank you for using tvtime.

~$ sudo modprobe videodev
~$ sudo modprobe bttv
FATAL: Error inserting bttv (/lib/modules/2.6.12-10-386/kernel/drivers/media/video/bttv.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

