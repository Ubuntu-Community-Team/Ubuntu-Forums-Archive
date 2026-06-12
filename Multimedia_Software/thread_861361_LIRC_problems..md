---
title: "LIRC problems."
date: 2008-07-16
forum: Multimedia Software
---

### Post by kenmiles on 2008-07-16
I am trying to get my remote to work on Ubuntu 8.04 but need some help.
This is the output from the system log when I try to start lirc-

16/07/08 18:57:27	kmiles	lircd-0.8.3pre1[16743]	accepted new client on /dev/lircd
16/07/08 18:57:27	kmiles	lircd-0.8.3pre1[16743]	caught signal
16/07/08 18:57:27	kmiles	lircd-0.8.3pre1[16743]	check if /dev/input/event6 is a LIRC device
16/07/08 18:57:27	kmiles	lircd-0.8.3pre1[16743]	could not get hardware features
16/07/08 18:57:27	kmiles	lircd-0.8.3pre1[16743]	lircd(userspace) ready
16/07/08 18:57:27	kmiles	lircd-0.8.3pre1[16743]	LIRC major number is 61
16/07/08 18:57:27	kmiles	lircd-0.8.3pre1[16743]	major number of /dev/input/event6 is 13
16/07/08 18:57:27	kmiles	lircd-0.8.3pre1[16743]	this device driver does not support the new LIRC interface

This is where I am getting the event number from-

cat /proc/bus/input/devices
I: Bus=0001 Vendor=0070 Product=9002 Version=0001
N: Name="cx88 IR (Hauppauge Nova-T DVB-T"
P: Phys=pci-0000:00:08.0/ir0
S: Sysfs=/devices/pci0000:00/0000:00:08.0/input/input6
U: Uniq=
H: Handlers=kbd event6
B: EV=100003
B: KEY=100fc312 214a802 0 0 0 0 18000 41a8 4801 9e1680 0 0 10000ffc

This is my hardware.conf file -
REMOTE="hauppauge_nova_t_uk"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/input/event6"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

Can anyone please help me with this, on Edgy I had no problems with the remote.

Regards, Kenneth.

---

### Post by kenmiles on 2008-07-16
Found the problem, remote driver.

REMOTE="hauppauge_nova_t_uk"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER="dev/input"
REMOTE_DEVICE="/dev/input/event6"
REMOTE_LIRCD_CONF="/etc/lirc/lircd.conf"
REMOTE_LIRCD_ARGS=""
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
START_LIRCD="true"
START_LIRCMD=""
LOAD_MODULES=""
LIRCMD_CONF=""
FORCE_NONINTERACTIVE_RECONFIGURATION="false"

---

