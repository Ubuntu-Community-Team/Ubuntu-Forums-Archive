---
title: "Verizon svcs using GOBI 2000/Sierra Wireless card on Ubuntu 9.1??"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by edpare on 2010-04-15
I bought a Toshiba NB305-410BN-G and it has an internal Sierra Wireless GOBI`2000 HS - USB Mobile Broadband Device 9001.  This works fine providing wireless internet over Verizon's cellular service using Windoze 7 Starter os.
I installed Ubuntu 9.1 (canonical) on the NB305 and I found a network device GUI that allowed me to configure "Mobile Broadband" for Verizon and allowed me to check a little box to automatically start the service.
This action does not provide me with Verizon on Ubuntu.  When I looked at the devices, I cannot see the gobi 2000.
How do I get the gobi to work on 9.1?
:popcorn:

---

### Post by pdc on 2010-04-15
if you open a terminal and type in 

> lspci -v

and copy and paste the results back here

---

### Post by edpare on 2010-04-15
Here ya go:
lspci -v
00:00.0 Host bridge: Intel Corporation Pineview DMI Bridge
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Pineview Integrated Graphics Controller
	Subsystem: Toshiba America Info Systems Device ff30
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 18d0 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Pineview Integrated Graphics Controller
	Subsystem: Toshiba America Info Systems Device ff30
	Flags: bus master, fast devsel, latency 0
	Memory at f0280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at 40100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
	Memory behind bridge: f0100000-f01fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=09, subordinate=09, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: 40000000-400fffff
	Prefetchable memory behind bridge: 00000000f0500000-00000000f05fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at 40104000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=11, subordinate=11, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation Tigerpoint LPC Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>

00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 27
	I/O ports at 18e8 [size=8]
	I/O ports at 18dc [size=4]
	I/O ports at 18e0 [size=8]
	I/O ports at 18d8 [size=4]
	I/O ports at 18c0 [size=16]
	Memory at 40104400 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff00
	Flags: medium devsel, IRQ 10
	I/O ports at 18a0 [size=32]
	Kernel modules: i2c-i801

07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Accton Technology Corporation Device e811
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at f0100000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath9k
	Kernel modules: ath9k

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff30
	Flags: bus master, fast devsel, latency 0, IRQ 29
	I/O ports at 2000 [size=256]
	Memory at f0520000 (64-bit, prefetchable) [size=4K]
	Memory at f0510000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at f0540000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

---

### Post by edpare on 2010-04-15
but lsusb shows:
lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0830:010ot1 Palm, Inc. 
Bus 001 Device 005: ID 064e:c211 Suyin Corp. 
Bus 001 Device 004: ID 1199:9000 Sierra Wireless, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Stroage Device

Note Device 004 - that's the card.

So, Ubuntu can see the card?  How can I see if there is a driver for it?

---

### Post by pdc on 2010-04-16
well if one searches on the unique ID of the card

> 1199:9000

and a google search would be 

> Ubuntu 1199:9000

as the vague title like Sierra will find lots of other stuff with Sierra badge on it;

I didn't find much myself on a google search; but if you have a hunt;

thoughts
1) as it is an internal USB connection ........ does it show an icon on your desktop?
2) if not, I wonder if wvdial would help
3) > sudo apt-get install wvdial
4) then > sudo wvdialconf /etc/wvdial.conf  and this command should create a file in the /etc/ folder called wvdial.conf
5) > gedit /etc/wvdial.conf opens up a programme that shows what has been created; as a read-only file; may be if you get that far, you post it back here; whilst we sort of hunt around on more google searching
6) I think verizon is CDMA ?? so your dial number is likely to be #777

here is a link about verizon: sometimes with linux you need to read around, but you know more after

[http://www.mp3car.com/vbulletin/wireless-communications/38864-how-use-your-verizon-cell-free-internet.html](http://www.mp3car.com/vbulletin/wireless-communications/38864-how-use-your-verizon-cell-free-internet.html)

this link 

[http://www.mobilitysite.com/boards/wifi-talk/133140-cdma-settings-thread-sprint-verizon-etc.html](http://www.mobilitysite.com/boards/wifi-talk/133140-cdma-settings-thread-sprint-verizon-etc.html)

in post #5

talks of 

> Verizon Wireless EVDO access (You may need a hack for some phones):

Telephone #: #777
UserId: (**your phone number**)@vzw3g.com
Password: vzw 

so that may be helpful

---

### Post by pdc on 2010-04-16
thoughts: 

from reading this post

[http://crunchbanglinux.org/forums/topic/775/howto-set-up-sprint-evdo-usb-modem-on-crunchbang/](http://crunchbanglinux.org/forums/topic/775/howto-set-up-sprint-evdo-usb-modem-on-crunchbang/)

try this command

> sudo dmesg|grep -i ttyUSB

if you get no reponse, (ie saying ttyUSB0 etc )

then 

> sudo modprobe usbserial vendor=0x1199 product=0x9000

then repeat 

> sudo dmesg|grep -i ttyUSB

any ttyUSB0 appear ?

If so, you may be able to configure now in network manager ....

---

### Post by edpare on 2010-04-16
vdial conf produced:
[Dialer Defaults]
Phone = 
Username = 
Password = 
New PPPD = yes

The earlier command produced:

sudo wvdialconf /etc/wvdial.conf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: S0   S1   S2   S3   


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wiki/?WvDial](http://open.nit.ca/wiki/?WvDial)

If you still have problems, send mail to <wvdial-list@lists.nit.ca>.
edpare@edpare-notbook:~$ gedit /etc/wvdial.conf

(gedit:2339): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-YnpKf35VIv,guid=d11ccbea4960a295e1f8ec6d4bc2da24 failed: Failed to connect to socket /tmp/dbus-YnpKf35VIv: Connection refused.

Is this device a modem?  Isn't it a USB modem?

By the way, no icon appears anywhere for the GOBI 2000 and I had already added login and password to network manager.

There was a response to the second list of commands:
sudo dmesg|grep -i ttyUSB 
[ 1554.843522] usb 1-6: generic converter now attached to ttyUSB0

Lastly, now network manager will not accept my password.  Grrr!

---

### Post by pdc on 2010-04-16
well if you got

> generic converter now attached to ttyUSB0

after you typed

> sudo dmesg|grep -i ttyUSB 

(having just typed ..........

> sudo modprobe usbserial vendor=0x1199 product=0x9000 

that should stand a chance of being configured ......

this is what I use to configure

[http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html](http://www.pharscape.org/networkmanager-0.7.0-and-3g-wwan-modems.html)

.... half-way down .......... create a mobile broadband connection ..

I didn't know what 

> Lastly, now network manager will not accept my password. Grrr! 

.... meant . can  you expand on that?

I see the word GOBI in your title; 

here was a recent post on gobi loading; I wonder if the firmware here is needed too ..............

[http://www.codon.org.uk/~mjg59/gobi_loader/](http://www.codon.org.uk/~mjg59/gobi_loader/)

isn't life complicated?

---

### Post by 2hot6ft2 on 2010-04-16
I don't know if it will help any but I saw this post a while back that was interesting. If nothing else it may help you figure the problem out.
> **fheinsen said:**
> I have the same mobile broadband modem and use it regularly without any problems. 

The Verizon UMW190 is a so called "global ready" 3G modem, meaning that it connects to both CDMA and GSM networks.  Alas, Ubuntu 9.10's Network Manager currently identifies this modem as GSM only, so until this gets fixed, connecting over a CDMA network (such as Verizon's network in the US) requires that you use an additional application.

Install gnome-ppp -- this is the application you will use to connect, and do the following:

**Step 1.** Plug the modem in on a freshly restarted computer.
**Step 2.** Launch gnome-ppp as superuser (e.g., press Alt-F2 and type "gksu gnome-ppp"), and configure the following settings:
 
[LIST]
[*]Modem Tab
[LIST]
[*]Device: /dev/ttyACM0
[*]Type: USB Modem
[*]Speed: 460800
[*]Phone Line: Tone
[*]Volume: Off
[/LIST]
 
[/LIST]
 
[LIST]
[*]Options Tab
[LIST]
[*]Minimize: checked
[*]Dock in Notification Area: checked
[/LIST]
 
[/LIST]
 Click Close.  Fill in the fields in the main Gnome PPP window:
 
[LIST]
[*]Username: _1234567890@vzw3g.com_
[*]Password: vzw
[*]Phone Number: #777
[/LIST]
 **Step 3.** Click Connect.  That should be it.


To disconnect, click on the gnome-ppp dock notification icon.

(Hat tip: [http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/](http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/))

---

### Post by pdc on 2010-04-17
thanks 2hot6ft2 for this; I think we are converging on the same things;

I got 

> Verizon Wireless EVDO access (You may need a hack for some phones):

Telephone #: #777
UserId: (your phone number)@vzw3g.com
Password: vzw 

and your very helpful post got the same;

edpare seems to be getting 

> ttyUSB0

whereas others may report ttyACM0 as your post did

I think wvdial and gnome-ppp should end up at the same point

---

### Post by edpare on 2010-04-21
Thanks 2hot and pdc, but gnome-ppp doesn't see a modem, and neither does wvdial.  It all acts like there is no drivers for the gobi2000.  I saw files on the Windows 7 partition that look like the driver files referred to earlier but they are not identified by vendor so i can't tell which is which.

---

### Post by edpare on 2010-05-05
This is solved with the new 10.04 lucid netbook remix.  Also the NB305 wakes from sleep now!:p

---

### Post by ghepeath on 2010-05-11
Hello, i can get my toshibalaptop to connect to the 3G
 i upload the info in a text file i hope someone can help me with this. I'm running Linux Ubuntu, 10.04  2.6.32-22-generic

here is my hardware info, i'm trying to attach a text file with more detail output, i hope some one can help me. thanks

lsusb 

	Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
	Bus 007 Device 002: ID 046d:c52f Logitech, Inc. 		
	Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
	Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
	Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
	Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
	Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
	Bus 002 Device 003: ID 0930:130d Toshiba Corp. 
	Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
	Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
	Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci
	00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
	00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
	00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
	00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)	
	00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
	00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
	00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
	00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
	00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
	00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
	00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
	00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
	00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
	00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
	00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
	00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
	00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
	00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
	02:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
	02:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
	02:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
	03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)
	07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)

---

### Post by alexfish on 2010-05-11
hi the only thing I can find at present is this thread which may be of interest
[http://ubuntuforums.org/showthread.php?t=1477911](http://ubuntuforums.org/showthread.php?t=1477911)

also can you post the details of this command from the terminal

dmesg | grep -e "modem" -e "tty" 

this will give you the lines of the modem and may also indicate if which drivers have loaded

thanks in advance

alexfish

---

### Post by edpare on 2010-05-11
When I stated the issue was solved in 10.04 I forgot to mention I still needed to boot to Win 7 first to load the firmware for the Gobi 2000, then restart into Ubuntu.  It would be nice if someone else could figure out how to use Ubuntu to poke the firmware in to the Gobi but that is probably a bit much.  :)):P

---

### Post by alexfish on 2010-05-17
It should not not be a problem

the protocols are the same , so are the rules , at the end of the day , a help file would be the least they could provide {as regards linux} on the storage device ,

Sierra wireless do seem to be be responding to requests by Linux users , as for Verizon an a few others A little Training goes a long way , or is it just a lack of interest on behalf of your Employees.

---

