---
title: "wlan DWL-G122 - no Accessponits - *-network DISABLED"
date: 2010-02-20
forum: Networking &amp; Wireless
---

### Post by unsen on 2010-02-20
i have a wlan usb stick DWL-G122, but newtwork-manager cant find an access-point.

```
lsusb
Bus 002 Device 002: ID 046a:0050 Cherry GmbH 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
seems to be identified..

iwlist:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

but i cant scan:

```
iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```

lshw is telling me:
```
...
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:22:b0:62:ab:ee
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

"DISABLED"? it's not a notebook, where i can turn off the wlan.. ;)
there doesn't seem to be a driver loaded also. 
p54usb should be the correct one, as far as i know. but it isnt loaded:

lsmod |grep p54
-> empty

after loading the driver with modprobe p54usb it's showing up in lsmod, but still not loaded with the unsb device and wlan still isnt working..

dmesg after de-/ re-attaching the usb-device:
```

[  140.845005] usb 1-1: USB disconnect, address 2
[  140.845211] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[  140.845262] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[  140.845317] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x0a failed for offset 0x0000 with error -19.
[  144.412064] usb 1-1: new high speed USB device using ehci_hcd and address 5
[  144.785555] usb 1-1: configuration #1 chosen from 1 choice
[  145.052451] phy1: Selected rate control algorithm 'minstrel'
[  145.053994] Registered led device: rt73usb-phy1::radio
[  145.054026] Registered led device: rt73usb-phy1::assoc
[  145.054059] Registered led device: rt73usb-phy1::quality
[  145.090339] rt73usb 1-1:1.0: firmware: requesting rt73.bin
[  145.101757] phy1 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.
[  145.106170] rt73usb 1-1:1.0: firmware: requesting rt73.bin
[  145.116569] phy1 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.

```
 
how should i continue?

---

### Post by chili555 on 2010-02-20
> [  145.106170] rt73usb 1-1:1.0: firmware: requesting rt73.bin
[  145.116569] phy1 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.It can't find the firmware. You are supposed to be able to run an updater and, if you are connected to the internet, it will go fetch and install the firmware for you. However, the URL in the updater is incorrect.

You can, however, go here: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and grab this: Firmware RT2501USB(RT2571W/RT2671)

Download the file to any convenient location, your desktop, perhaps. Right click the .zip file and select 'Extract Here.'
Then open a terminal and do:```
cd Desktop/RT71W_Firmware_V1.8
cp rt73.bin /lib/firmware
cd /lib/firmware
sudo chown root:root rt73.bin
```Now unplug and replug your device and see if it works as expected.

If not, please let us see:```
dmesg | grep rt73
```Thanks.

---

### Post by unsen on 2010-02-23
ok - after copying the firmware to /lib/firmware it's working, many thanks!

```
[  608.320309] Registered led device: rt73usb-phy0::radio
[  608.320344] Registered led device: rt73usb-phy0::assoc
[  608.320378] Registered led device: rt73usb-phy0::quality
[  608.321079] usbcore: registered new interface driver rt73usb
[  608.349679] rt73usb 1-10:1.0: firmware: requesting rt73.bin

```

(took me a while to remember, that i recently blacklistet rt73usb ;) but then it worked)


**Question**: why isnt the DWL-G122 recognised by karmic anymore? 
i tried a hardy live-cd, there the stick was operating "out of the box"

for that reason i have bought especially that w-lan stick to get rid of these "workarounds", for which one usually needs a connection to the internet to be able to apply them...

---

### Post by chili555 on 2010-02-23
I don't know that it is not recognized. Your pci.id is:> [COLOR="Red"]07d1:3c03[/COLOR] D-Link System DWL-G122 802.11g Adapter [ralink rt73]The module rt73usb is still in Ubuntu as far forward as Lucid beta:```
$ modinfo rt73usb | grep 3C03
alias:          usb:v[COLOR="Red"]07D1[/COLOR]p[COLOR="Red"]3C03[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```How or why did it not work?

---

### Post by unsen on 2010-02-23
> How or why did it not work?

see above.

i took a quite clean kermic installation and attached the DWL-G122 802.11g

it just didnt work. 

you're right, the device ist correcltly recoginzed:
> lsusb
Bus 001 Device 004: ID 07d1:3c03 D-Link System DWL-G122 802.11g Adapter [ralink rt73]

verdor and device are correct. 

but what's causing this error then? 
> dmesg
.....
[  145.090339] rt73usb 1-1:1.0: firmware: requesting rt73.bin
[  145.101757] phy1 -> rt2x00lib_request_firmware: Error - Failed to request Firmware.


..or better question:
why is this issue occuring only on my kermic installation? it's not too old, and i definately havent touched anything around the modules, libs.. whatever..

---

### Post by chili555 on 2010-02-23
I guess I am confused. It it working, as in post #3? Do you have a second computer in which it doesn't work? Or a Live CD?

---

### Post by unsen on 2010-02-24
ah.. in post #3 i should have said, that i copied the firmware to /lib/firmware to get the stick working on my karmic installation - as you suggested in post #2.


i tried the stick also with a earlier live cd "hardy". there it was working out of the box - as it always used to. i only have problems in my actual karmic installation, which where solved by copying the firmware from ralink to /lib/firmware

---

