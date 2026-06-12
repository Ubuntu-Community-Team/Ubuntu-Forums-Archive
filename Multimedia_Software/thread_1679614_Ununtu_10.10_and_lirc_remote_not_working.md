---
title: "Ununtu 10.10 and lirc remote not working"
date: 2011-02-01
forum: Multimedia Software
---

### Post by cave_man() on 2011-02-01
Hello,

I am running Ubuntu 10.10 and am trying to get lirc to recognize my pcusa mce remote control. I have been working on this for a week and have not had any success. Please note that I am very new to Linux. I am comfortable moving around in the terminal but most of anything else that I do in the terminal is just following instructions.

This is the remote that I am using:
[http://www.ncix.com/products/?sku=25972&vpn=HA-IR-01SV&manufacture=I-Rocks%20Technology](http://www.ncix.com/products/?sku=25972&vpn=HA-IR-01SV&manufacture=I-Rocks%20Technology)

When I run 
cat /proc/bus/input/devices

I do not see anything that could be the remote. I have tried plugging the USB receiver into my Ubuntu 10.10 net book but it doesn't see the receiver either. I do not have a windows machine that I can test the remote on but I plugged the receiver into my iMac and I did get a red LED lit that I haven't seen on the Ubuntu machines.

When I run irw and press buttons on the remote I see nothing on the terminal.

When I run:
sudo mode2

I get:
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory

I have tried mode2 both with lirc running and stopped and I get the same response either way.

I have confirmed that there is no /dev/lirc but there is a lircd in /dev (it's not a directory).

I'd appreciate any help that anyone could provide.

Also I had read somewhere that lirc doesn't work under Ubuntu 10.10. Is that the case? If any one has a windows mce remote and lirc working under Ubuntu 10.10 could please post.

Thank you.

---

### Post by laceration on 2011-02-01
LIRC does indeed work in 10.10.  I have a MCE remote working with it.  Even if your remote was not supported, which it is, + lirc was not installed, the light in the receiver would still blink and some identifying info would show up with the cat /proc... or lsusb.  This would suggest you have a mechanical issue such as a bad wire or connection on the unit.  You eliminated this by seeing the light when connecting to the apple, but maybe the contacts just happened to come together while you were doing that.  Test on the apple again.

---

### Post by cave_man() on 2011-02-01
Hi laceration,

I plugged the usb receiver into the mac again. The LED lights. I used os x system profiler to investigate usb devices and learned that my receiver is an eHome Infrared Transceiver.

eHome Infrared Transceiver
  Product ID:    0x0008
  Vendor ID:    0x1784  (TopSeed Technology Corp.)
  Version:    1.01
  Serial Number:    TS000Fta
  Speed:    Up to 12 Mb/sec
  Manufacturer:    Topseed Technology Corp.
  Location ID:    0x04100000
  Current Available (mA):    500
  Current Required (mA):    100

I plugged the eHome Transceiver back into my Ubuntu box (LED did not light). I know the usb port is good because my mouse works when connected to that usb port.

Ran cat /proc ...

don@HTPC:~$ cat /proc/bus/input/devices
I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0003 Vendor=06a3 Product=8000 Version=0111
N: Name="Chicony USB Gaming Keyboard Pro"
P: Phys=usb-0000:00:16.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:16.0/usb7/7-1/7-1:1.0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: EV=120013
B: KEY=1000000000007 ff9f207ac14057ff febeffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=06a3 Product=8000 Version=0111
N: Name="Chicony USB Gaming Keyboard Pro"
P: Phys=usb-0000:00:16.0-1/input1
S: Sysfs=/devices/pci0000:00/0000:00:16.0/usb7/7-1/7-1:1.1/input/input5
U: Uniq=
H: Handlers=kbd event5 
B: EV=13
B: KEY=2000000 3078d800d001 1e000000000000 0
B: MSC=10

I: Bus=0003 Vendor=06a3 Product=8000 Version=0111
N: Name="Chicony USB Gaming Keyboard Pro"
P: Phys=usb-0000:00:16.0-1/input2
S: Sysfs=/devices/pci0000:00/0000:00:16.0/usb7/7-1/7-1:1.2/input/input6
U: Uniq=
H: Handlers=event6 js0 
B: EV=13
B: KEY=7ff000000000000 0 0 0 0
B: MSC=10

I: Bus=0003 Vendor=046d Product=c404 Version=0110
N: Name="Logitech Trackball"
P: Phys=usb-0000:00:16.0-2/input0
S: Sysfs=/devices/pci0000:00/0000:00:16.0/usb7/7-2/7-2:1.0/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10

- no eHome receiver

I also ran lsusb

don@HTPC:~$ lsusb
Bus 007 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 007 Device 002: ID 06a3:8000 Saitek PLC Gamers' Keyboard
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 058f:6364 Alcor Micro Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Still no eHome receiver.

Any idea what else I should try?

Thanks

---

### Post by vidtek on 2011-02-01
> **cave_man() said:**
> Hello,

I am running Ubuntu 10.10 and am trying to get lirc to recognize my pcusa mce remote control. I have been working on this for a week and have not had any success. Please note that I am very new to Linux. I am comfortable moving around in the terminal but most of anything else that I do in the terminal is just following instructions.

This is the remote that I am using:
[http://www.ncix.com/products/?sku=25972&vpn=HA-IR-01SV&manufacture=I-Rocks%20Technology](http://www.ncix.com/products/?sku=25972&vpn=HA-IR-01SV&manufacture=I-Rocks%20Technology)

When I run 
cat /proc/bus/input/devices

I do not see anything that could be the remote. I have tried plugging the USB receiver into my Ubuntu 10.10 net book but it doesn't see the receiver either. I do not have a windows machine that I can test the remote on but I plugged the receiver into my iMac and I did get a red LED lit that I haven't seen on the Ubuntu machines.

When I run irw and press buttons on the remote I see nothing on the terminal.

When I run:
sudo mode2

I get:
mode2: could not get file information for /dev/lirc
mode2: default_init(): No such file or directory

I have tried mode2 both with lirc running and stopped and I get the same response either way.

I have confirmed that there is no /dev/lirc but there is a lircd in /dev (it's not a directory).

I'd appreciate any help that anyone could provide.

Also I had read somewhere that lirc doesn't work under Ubuntu 10.10. Is that the case? If any one has a windows mce remote and lirc working under Ubuntu 10.10 could please post.

Thank you.

Cave_man,
I have a Topseed ir reciever working through a port connected to a powered hub which has a 20mtr extension 
into my theatre from the garage where the HTPC is  (many fans and drives too noisy for theatre)
I posted my settings on the topseed to the LIRC repository (at work now can't remember site address).
There are 2 main files to edit on LIRC;

(For Mythtv)
~/.mythtv/lircrc which is the main configuration file that looks at /etc/lirc/lircd and maps buttons to operations.

When editing lircrc, examine lircd (and do a printout).  Then check the button NAMES in lircrc correspond to the same ones in the lircd file.

But first you need to get IRW to work.
Move the topseed reciever to various USB ports on the machine until you find one that works.  

Some are more equal than others, motherboards (particularly cheapies)have issues with USB ports, some work better than others. 
Chances are one will be ok for the Topseed reciever.

At work aI t the moment so when I get home will look up my notes and see what else I did to get it going.

Don't give up, these forums are very helpful.
Tony.

If you can run KDE4 as it has a great little utility for IR remotes, with support for various programmes if you don't use Mythtv. It puts an IR icon on the toolbar and this flashes when a button is mashed.  Tony

---

### Post by laceration on 2011-02-01
maybe I'm just stabbing in the dark but maybe its a marginal usb port + the voltage to run a mouse isn't the same needed for the receiver.  Try different usb ports.  Or maybe there is some weird interrupt conflict.  Try unplugging some of those other usb devices you have.  This apparently is a hardware problem, the system is not connecting to the receiver.

---

### Post by cave_man() on 2011-02-02
Hello laceration and vidtek,

I cannot believe it. I have been working on this for hours and hours (this evening alone). I tried your advice on plugging into different ports and had no success. Then because of the comments about not all usb ports being equal and voltage required for mouse vs. receiver I plugged in a powered usb hub and plugged the receiver in to that. I now get a response from irw and the remote is controlling the volume on my PC.

Thank you both very much. Now all I have to do is program the buttons. Not all of them give me a response on irw.

vidtek,

I found your config file on sourceforge ([http://lirc.sourceforge.net/remotes/topseed/RM-VR1](http://lirc.sourceforge.net/remotes/topseed/RM-VR1))

I've had enough for tonight so I'll poke away at it again tomorrow. Thanks again.

---

### Post by vidtek on 2011-02-02
> **cave_man() said:**
> Hello laceration and vidtek,

I cannot believe it. I have been working on this for hours and hours (this evening alone). I tried your advice on plugging into different ports and had no success. Then because of the comments about not all usb ports being equal and voltage required for mouse vs. receiver I plugged in a powered usb hub and plugged the receiver in to that. I now get a response from irw and the remote is controlling the volume on my PC.

Thank you both very much. Now all I have to do is program the buttons. Not all of them give me a response on irw.

vidtek,

I found your config file on sourceforge ([http://lirc.sourceforge.net/remotes/topseed/RM-VR1](http://lirc.sourceforge.net/remotes/topseed/RM-VR1))

I've had enough for tonight so I'll poke away at it again tomorrow. Thanks again.

You haven't said which programme you will be using, Mythtv? or some other media util?  It makes a difference with remote settings.  Are you using KDE4?

Tony.

---

### Post by cave_man() on 2011-02-02
Hi vidtek,

At present I am using XBMC as my media center although this HTPC project is still in its infancy so I am willing to give other things a try. On the list of things to try is LinuxMCE and Enna. Do you have any recommendations?

At present I'm running Ubuntu 10.10 which would be gnome. As far as I can tell unity is the default interface for the netbook edition only. I have not installed KDE4 but I'm not opposed to it.

I don't watch/record TV so I was planning to skip MythTV.

---

### Post by vidtek on 2011-02-02
> **cave_man() said:**
> Hi vidtek,

At present I am using XBMC as my media center although this HTPC project is still in its infancy so I am willing to give other things a try. On the list of things to try is LinuxMCE and Enna. Do you have any recommendations?

At present I'm running Ubuntu 10.10 which would be gnome. As far as I can tell unity is the default interface for the netbook edition only. I have not installed KDE4 but I'm not opposed to it.

I don't watch/record TV so I was planning to skip MythTV.

cave_man-I would probably be looking at just using VLC.  It's a well supported and mature app.  
For music you can't go past Rythmbox.   VLC is supported by the KDE4 ir interface natively, so it performs well there.
I can't remember whether Rythmbox is or not.
Tony.

---

### Post by vidtek on 2011-02-09
> **cave_man() said:**
> Hi vidtek,

At present I am using XBMC as my media center although this HTPC project is still in its infancy so I am willing to give other things a try. On the list of things to try is LinuxMCE and Enna. Do you have any recommendations?

At present I'm running Ubuntu 10.10 which would be gnome. As far as I can tell unity is the default interface for the netbook edition only. I have not installed KDE4 but I'm not opposed to it.

I don't watch/record TV so I was planning to skip MythTV.

Cave_man-
If you don't need mythtv avoid it like the plague--it's great but very time-consuming.  The only thing you may find of interest is the remote side is ultra-configurable, you can do anything with any button very simply with editing the lircrc file directly.  

VLC is supported natively in KDE but only with a few commands as you've already learned.  I have just installed a version of ubuntu with Gnome to see what support there is, but only had time to install and do updates before the wife took over the theatre (and my HTPC)with her mates.  

Now work has intervened and so I won't get another chance to further investigate for a few days.  Once I have LIRC up and running on that version (ultimate 2.8 because it has many multimedia proggies) I'll report back on my findings.
Tony

---

