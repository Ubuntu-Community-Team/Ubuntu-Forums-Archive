---
title: "MD400g Sony Ericsson, anyone got one working?"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by rickggreen on 2009-09-26
Has anyone got a Sony Ericsson MD400g wireless moden to work? I have had to move to a location where I cannot get any cable or dsl service but can get cell coverage. The supplier is Rogers Canada and they supply a MD400g wireless modem that works with Win System 7 but I can not get it to work with Linux because it seems to need Net 2.0 to install the driver. (I have installed ndiswrapper, but can not find the .inf file)

Any help will be welcomed, I hate Windows

---

### Post by MobileTech on 2009-12-02
I tried one at a local Rogers dealer today (using kubuntu Karmic on an atom netbook). I was unable to get it to present it's TTY.

Here is how it shows up:

lsusb:
Bus 001 Device 004: ID 0fce:d103 Sony Ericsson Mobile Communications AB 

Here is kern.log from when I plugged it in:

Dec  2 11:17:22 trent-um kernel: [  245.552163] usb 1-1: new high speed USB device using ehci_hcd and address 4
Dec  2 11:17:22 trent-um kernel: [  245.688333] usb 1-1: configuration #1 chosen from 1 choice
Dec  2 11:17:22 trent-um kernel: [  245.708235] scsi3 : SCSI emulation for USB Mass Storage devices
Dec  2 11:17:22 trent-um kernel: [  245.718862] usb-storage: device found at 4
Dec  2 11:17:22 trent-um kernel: [  245.718870] usb-storage: waiting for device to settle before scanning
Dec  2 11:17:27 trent-um kernel: [  250.716684] usb-storage: device scan complete
Dec  2 11:17:27 trent-um kernel: [  250.717600] scsi 3:0:0:0: Direct-Access     SEMC     MMC Flash Card      0 PQ: 0 ANSI: 0
Dec  2 11:17:27 trent-um kernel: [  250.718211] scsi 3:0:0:1: Direct-Access     SEMC     MMC Flash Card      0 PQ: 0 ANSI: 0
Dec  2 11:17:27 trent-um kernel: [  250.719750] sd 3:0:0:0: Attached scsi generic sg1 type 0
Dec  2 11:17:27 trent-um kernel: [  250.720317] sd 3:0:0:1: Attached scsi generic sg2 type 0
Dec  2 11:17:27 trent-um kernel: [  250.745407] sd 3:0:0:0: [sdb] 348261 512-byte logical blocks: (178 MB/170 MiB)
Dec  2 11:17:27 trent-um kernel: [  250.751771] sd 3:0:0:1: [sdc] Attached SCSI removable disk
Dec  2 11:17:27 trent-um kernel: [  250.759927] sd 3:0:0:0: [sdb] Test WP failed, assume Write Enabled
Dec  2 11:17:27 trent-um kernel: [  250.759940] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Dec  2 11:17:27 trent-um kernel: [  250.781543] sd 3:0:0:0: [sdb] Test WP failed, assume Write Enabled
Dec  2 11:17:27 trent-um kernel: [  250.781557] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Dec  2 11:17:27 trent-um kernel: [  250.781571]  sdb: sdb1
Dec  2 11:17:27 trent-um kernel: [  250.820319] sd 3:0:0:0: [sdb] Test WP failed, assume Write Enabled
Dec  2 11:17:27 trent-um kernel: [  250.820333] sd 3:0:0:0: [sdb] Assuming drive cache: write through
Dec  2 11:17:27 trent-um kernel: [  250.820345] sd 3:0:0:0: [sdb] Attached SCSI removable disk


Here is the rule I tried adding to /etc/udev/rules.d/md400g.rules:

SYSFS{idVendor}=="0fce", SYSFS{idProduct}=="d103", RUN+="/usr/bin/eject %k"

also:

sudo eject /dev/sdb
sudo eject /dev/sdb1
sudo eject /dev/sdb
sudo eject /dev/sdc

appeared to have no effect. Has anyone gotten this to work?

trent@trent-um:~$ uname -a
Linux trent-um 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux

---

### Post by Craigwell on 2010-01-26
I have been able to get it to work on 9.04 with usb_modeswitch utility from the repositories, but not in 9.10. 

Here is the command line I use: 

 sudo usb_modeswitch -v 0fce -p d103 -O


In the network manager, I select Rogers (Canada) and the settings are:

Number: *99#
user: wapuser1
pass: wap
apn: internet.com

As I say, this worked for me in 9.04, but I cannot get it to work thus far in 9.10

---

### Post by Craigwell on 2010-03-14
I have been able to get this working in 9.10, but it is a messy two step process so far, or even three depending how you go. 

First, use the usb_modeswitch utility as mentioned. 
Second use wvdial with a modified wvdial.conf file that that looks like this:

Dialer Defaults]
New PPPD = yes
Stupid Mode = 1
Modem Type = USB Modem

#[Dialer PIN]
#Init1 = AT+CPIN=

[Dialer signal]
Modem = /dev/ttyACM1
Init1 = AT+CSQ
Init2 = AT+COPS?

[Dialer gps]
Modem = /dev/ttyACM0
Init1 = AT*E2GPSCTL=1,2,1
Init2 = AT*E2GPSNPD

[Dialer on]
Modem = /dev/ttyACM1
Init1 = AT+CFUN=1

[Dialer off]
Modem = /dev/ttyACM1
Init1 = AT+CFUN=4

[Dialer connect]
Modem = /dev/ttyACM1
Init1 = AT
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Baud = 460800
ISDN = 0
Phone = *99***1#
Password = wap
Username = wapuser1

Third: if you just use the command "wvdial on" in terminal, you then can use network manager to connect. 

I haven't gotten anywhere with the gps yet, but that's true of windows as well.

---

