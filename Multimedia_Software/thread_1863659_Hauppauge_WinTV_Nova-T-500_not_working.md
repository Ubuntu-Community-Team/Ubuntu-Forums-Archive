---
title: "Hauppauge WinTV Nova-T-500 not working"
date: 2011-10-18
forum: Multimedia Software
---

### Post by Catroaster on 2011-10-18
After twelve hours of fiddling, I have finally managed to get my Hauppauge WinTV Nova-T-500 to the point where the system recognizes the card. However, I get the following error messages in kern.log: 

Oct 18 07:37:17 edward-athlon-dualcore kernel: [  138.471133] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in cold state, will try to load a firmware
Oct 18 07:37:17 edward-athlon-dualcore kernel: [  138.477174] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'
Oct 18 07:37:17 edward-athlon-dualcore kernel: [  138.680643] dib0700: firmware started successfully.
Oct 18 07:37:18 edward-athlon-dualcore kernel: [  139.184259] dvb-usb: found a 'Hauppauge Nova-T 500 Dual DVB-T' in warm state.
Oct 18 07:37:18 edward-athlon-dualcore kernel: [  139.184406] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Oct 18 07:37:18 edward-athlon-dualcore kernel: [  139.184506] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
Oct 18 07:37:18 edward-athlon-dualcore kernel: [  139.297710] DVB: registering adapter 0 frontend 0 (DiBcom 3000MC/P)...
Oct 18 07:37:18 edward-athlon-dualcore kernel: [  139.346373] MT2060: successfully identified (IF1 = 1247)
Oct 18 07:37:19 edward-athlon-dualcore kernel: [  139.823071] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Oct 18 07:37:19 edward-athlon-dualcore kernel: [  139.823228] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
Oct 18 07:37:19 edward-athlon-dualcore kernel: [  139.832072] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
Oct 18 07:37:19 edward-athlon-dualcore kernel: [  139.837106] MT2060: successfully identified (IF1 = 1239)
Oct 18 07:37:19 edward-athlon-dualcore kernel: [  140.432042] Registered IR keymap rc-dib0700-rc5
Oct 18 07:37:19 edward-athlon-dualcore kernel: [  140.432356] input: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:02:01.2/usb2/2-1/rc/rc0/input5
Oct 18 07:37:19 edward-athlon-dualcore kernel: [  140.432507] rc0: IR-receiver inside an USB DVB receiver as /devices/pci0000:00/0000:00:14.4/0000:02:01.2/usb2/2-1/rc/rc0
Oct 18 07:37:19 edward-athlon-dualcore kernel: [  140.432808] dvb-usb: schedule remote query interval to 50 msecs.
Oct 18 07:37:19 edward-athlon-dualcore kernel: [  140.432823] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
Oct 18 07:37:19 edward-athlon-dualcore kernel: [  140.433131] usbcore: registered new interface driver dvb_usb_dib0700
Oct 18 07:37:50 edward-athlon-dualcore kernel: [  171.316395] dvb-usb: error while enabling fifo.
Oct 18 07:40:01 edward-athlon-dualcore kernel: [  302.312072] mt2060 I2C write failed (len=2)
Oct 18 07:40:06 edward-athlon-dualcore kernel: [  307.312125] mt2060 I2C write failed (len=6)
Oct 18 07:40:11 edward-athlon-dualcore kernel: [  312.312136] mt2060 I2C read failed
Oct 18 07:40:16 edward-athlon-dualcore kernel: [  317.320121] mt2060 I2C read failed
Oct 18 07:40:21 edward-athlon-dualcore kernel: [  322.328188] mt2060 I2C read failed
Oct 18 07:40:26 edward-athlon-dualcore kernel: [  327.336226] mt2060 I2C read failed
Oct 18 07:40:31 edward-athlon-dualcore kernel: [  332.344098] mt2060 I2C read failed
Oct 18 07:40:36 edward-athlon-dualcore kernel: [  337.352184] mt2060 I2C read failed
Oct 18 07:40:41 edward-athlon-dualcore kernel: [  342.360116] mt2060 I2C read failed
Oct 18 07:40:46 edward-athlon-dualcore kernel: [  347.368142] mt2060 I2C read failed
Oct 18 07:40:51 edward-athlon-dualcore kernel: [  352.376146] mt2060 I2C read failed
Oct 18 07:40:56 edward-athlon-dualcore kernel: [  357.384111] mt2060 I2C read failed
Oct 18 07:52:21 edward-athlon-dualcore kernel: [ 1042.532099] mt2060 I2C write failed

The card adamantly refuses to work.

Any ideas?

Thanks in advance.

---

### Post by BicyclerBoy on 2011-10-18
LinuxTV.org nova-t-500 page suggests there is more than one version of this card.
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-NOVA-T-500)

Your dmesg/kernel message do not match mine..(ubu11.04 2.6.38-11) but it looks like the example on the above webpage.

What kernel are you running ?

lsusb
Bus 003 Device 002: ID 2040:8400 Hauppauge 
dmesg
[    9.989844] dib0700: loaded with support for 15 different device-types
[    9.989972] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   10.027606] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.20.fw'

[   10.234698] dib0700: firmware started successfully.
[   10.738367] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   10.738467] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   10.738561] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   10.995031] DVB: registering adapter 0 frontend 0 (DiBcom 7000PC)...
[   11.215361] DiB0070: successfully identified
[   11.215365] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   11.215505] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   11.374623] DVB: registering adapter 1 frontend 0 (DiBcom 7000PC)...
[   11.595238] DiB0070: successfully identified
[   11.595248] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   11.595560] usbcore: registered new interface driver dvb_usb_dib0700

You can try to disable the IR remote (& activate LNB):
/etc/modprobe.d/dvb-options.conf
options dvb_usb_dib0700 force_lna_activation=1
options dvb_usb disable_rc_polling=1

How come your kernel timestamp is so high at firmware load ?

---

### Post by Catroaster on 2011-10-18
I am running Ubuntu 11.10, with the default kernel.
The timestamp is so high because the firmware fails to load the first time, while the system is booting, so I have to manually reload it.
I have tried passing the options dvb_usb_dib0700 force_lna_activation=1 and dvb_usb disable_rc_polling=1 - force_lna_activation gets the system to see the card, but there is no other effect.

---

### Post by BicyclerBoy on 2011-10-18
Maybe you have another version with different/new usb device id..(doubtful)

But there must be a reason why the firmware is not loaded by the driver being automagically loaded..

post your
lsusb

& then check if your usb id matches the info on LinuxTV..

Another nova-t-500 model:
The nova-t-500 in my main HTPC matches your kernel messages except the IR receiver/keymap does not exist.

Has the dmesg output changed now you have used modprobe options ?

---

### Post by tsh on 2011-10-18
Maybe the wrong firmware is being loaded. I have
ID 2040:7060 Hauppauge Nova-T Stick 2
and when it was new there were a couple of differnet versions of firmware floating about, one worked OK, the other seemed to load, but didn't really work

Another thing to check, try powering off the machine and re-starting. This is an internal USB on a card? I know mine frequently locks up the USB subsystem in some way.

---

### Post by BicyclerBoy on 2011-10-18
Where did the firmware come from ?
My nova-t-500 firmware came as part of the linux non-free firmware package.
The card in the HTPC box is the same as OP & has worked very well for >3 yrs.


The USB nova-stick is not the same as the PCI card ? or is it ?

One point I have never proved either way:
Changes to /etc/modprobe.d/*.conf files do not take effect unless you rebuild the boot image with update-initramfs -u.

Of course if you rmmod & modprobe the modules with options from terminal, the effects are immediate.

---

### Post by Catroaster on 2011-10-19
I got myself in such a mess I had to do a reinstall.

Here's the logfile after I reinstalled (only changes made were running the updates, enabling the DVB card firmware, and copying back /etc/modprobe.d/dvb-options.conf to pass the necessary options to the module).

I have tried cold restarting.

lsusb identifies the card as:

Bus 002 Device 002: ID 2040:9950 Hauppauge WinTV Nova-T-500

Here's the logfile:

Oct 19 15:53:00 Edward-athlon-dualcore kernel: [   16.335045] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
Oct 19 15:53:00 Edward-athlon-dualcore kernel: [   16.335357] DVB: registering new adapter (Hauppauge Nova-T 500 Dual DVB-T)
Oct 19 15:53:00 Edward-athlon-dualcore kernel: [   16.341301] DVB: registering adapter 1 frontend 0 (DiBcom 3000MC/P)...
Oct 19 15:53:00 Edward-athlon-dualcore kernel: [   16.346173] MT2060: successfully identified (IF1 = 1239)
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.496363] Bluetooth: Core ver 2.16
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.496515] NET: Registered protocol family 31
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.496517] Bluetooth: HCI device and connection manager initialized
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.496522] Bluetooth: HCI socket layer initialized
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.496524] Bluetooth: L2CAP socket layer initialized
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.497003] Bluetooth: SCO socket layer initialized
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.499592] Bluetooth: RFCOMM TTY layer initialized
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.499601] Bluetooth: RFCOMM socket layer initialized
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.499603] Bluetooth: RFCOMM ver 1.11
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.519082] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.519087] Bluetooth: BNEP filters: protocol multicast
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.896888] dvb-usb: Hauppauge Nova-T 500 Dual DVB-T successfully initialized and connected.
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.897003] dib0700: rc submit urb failed
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.897004] 
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   16.897062] usbcore: registered new interface driver dvb_usb_dib0700
Oct 19 15:53:01 Edward-athlon-dualcore kernel: [   17.315323] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Oct 19 15:53:02 Edward-athlon-dualcore kernel: [   17.566990] init: plymouth-stop pre-start process (1234) terminated with status 1
Oct 19 15:53:03 Edward-athlon-dualcore kernel: [   18.513462] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro,commit=0
Oct 19 15:53:03 Edward-athlon-dualcore kernel: [   18.988097] wlan0: authenticate with 94:44:52:50:f1:ca (try 1)
Oct 19 15:53:03 Edward-athlon-dualcore kernel: [   18.989542] wlan0: authenticated
Oct 19 15:53:03 Edward-athlon-dualcore kernel: [   19.004079] wlan0: associate with 94:44:52:50:f1:ca (try 1)
Oct 19 15:53:03 Edward-athlon-dualcore kernel: [   19.006400] wlan0: RX AssocResp from 94:44:52:50:f1:ca (capab=0x411 status=0 aid=2)
Oct 19 15:53:03 Edward-athlon-dualcore kernel: [   19.006406] wlan0: associated
Oct 19 15:53:03 Edward-athlon-dualcore kernel: [   19.006971] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Oct 19 15:53:13 Edward-athlon-dualcore kernel: [   29.936034] wlan0: no IPv6 routers present
Oct 19 15:54:02 Edward-athlon-dualcore kernel: [   78.552117] dvb-usb: error while enabling fifo.
Oct 19 15:56:13 Edward-athlon-dualcore kernel: [  209.352131] mt2060 I2C write failed (len=2)
Oct 19 15:56:18 Edward-athlon-dualcore kernel: [  214.352173] mt2060 I2C write failed (len=6)
Oct 19 15:56:23 Edward-athlon-dualcore kernel: [  219.352209] mt2060 I2C read failed
Oct 19 15:56:28 Edward-athlon-dualcore kernel: [  224.360123] mt2060 I2C read failed
Oct 19 15:56:33 Edward-athlon-dualcore kernel: [  229.368159] mt2060 I2C read failed
Oct 19 15:56:38 Edward-athlon-dualcore kernel: [  234.376203] mt2060 I2C read failed
Oct 19 15:56:43 Edward-athlon-dualcore kernel: [  239.384122] mt2060 I2C read failed
Oct 19 15:56:48 Edward-athlon-dualcore kernel: [  244.392174] mt2060 I2C read failed
Oct 19 15:56:53 Edward-athlon-dualcore kernel: [  249.400202] mt2060 I2C read failed
Oct 19 15:56:58 Edward-athlon-dualcore kernel: [  254.408238] mt2060 I2C read failed
Oct 19 15:57:03 Edward-athlon-dualcore kernel: [  259.416158] mt2060 I2C read failed
Oct 19 15:57:08 Edward-athlon-dualcore kernel: [  264.424199] mt2060 I2C read failed

---

### Post by BicyclerBoy on 2011-10-19
The delay to the mt2060 i2c is cause by a backend process trying to do a EIT scan ??

The workaround recommended for nova-t-500 is EIT scan enabled on (1) tuner only & this tuner must have a 1000ms tuning delay.

If you are using a internet grapper for EPG or mheg5 EPG script then disable EIT scans on both tuners.

You can check the modprobe options worked:
cat /sys/modules/dvb-usb/parameters/disable_rc_polling
etc..

---

