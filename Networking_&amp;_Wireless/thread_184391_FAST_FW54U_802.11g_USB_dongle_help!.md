---
title: "FAST FW54U 802.11g USB dongle help!?"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by bulwynkl on 2006-05-29
Hi,

I have a FAST FW54U USB 802.11g dongle. Have not been able to get it working so far. ](*,) 

plug in the usb device and you get someting like this.

# dmesg
[4303262.101000] usb 1-2: new full speed USB device using uhci_hcd and address 5
[4303262.254000] usb 1-2: device descriptor read/64, error -71
# lsusb
Bus 001 Device 005: ID 148f:2573
Bus 001 Device 001: ID 0000:0000

Now, according to the ubuntu network device list, 148f:2570 corresponds to one of the rt2500 chipsets.

the nightly CVS builds of the RT2x00 includes an rt73 driver. this corresponds with the drivers on the windows disk
but the readme for the rt2x00 states kernel 2.6.13 required.
# uname -r
2.6.12-10-386
therefore have not tried building it yet. 

tried ndiswrapper with included windows drivers.
installed ndiswrapper-utils and ndisgtk
# ndiswrapper -i /path/to/winXP/drivers/rt73.inf
Installing rt73
#ndiswrapper -l
Installed ndis drivers:
rt73    invalid driver!

sometimes get a line 
fw54u    invalid driver!
too. not sure what causes that variability to occur

ndiswrapper module is loaded.
l# modinfo ndiswrapper
filename:       /lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.1
license:        GPL
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:        usbcore
srcversion:     E21E28A177890611AE46391
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           if_name:Network interface name or template (default: wlan%d) (charp)

lshw output includes...
              *-usb UNCLAIMED
                   description: Generic USB device
                   product: 54M.USB.......
                   vendor: Ralink
                   physical id: 2
                   bus info: usb@1:2
                   version: 0.01
                   capabilities: usb-2.00
                   configuration: maxpower=300mA speed=12.0MB/s

anything else? 
there is no wlan0 in the ifconfig -a output, nor any iwconfig recognised devices. Not surprised.

one other thing... the box has an ethernet port that, AFAIK, is flaky and not really working.  Had some luck connecting to it spasmodically but essentially it does not work.  could hardware failure elsewhere be the problem (usb dongle was the workaround for this hw problem)?

---

