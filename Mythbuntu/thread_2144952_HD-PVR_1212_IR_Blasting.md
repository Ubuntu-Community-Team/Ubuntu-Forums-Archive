---
title: "HD-PVR 1212 IR Blasting"
date: 2013-05-13
forum: Mythbuntu
---

### Post by nrune on 2013-05-13
Following the guide from here: [http://www.mythtv.org/wiki/HD_PVR](http://www.mythtv.org/wiki/HD_PVR) unable to get IR blasting to work.  Any help appreciated!

On mythtv 0.26. 

firmware is in /lib/firmware and appears to load. 

```
mike@backend:/etc/lirc$ /sbin/lsmod | grep lirc
lirc_zilog             22513  0
lirc_dev               19204  1 lirc_zilog

```


Dmesg

```
[  133.368243] lirc_dev: IR Remote Control driver registered, major 249
[  133.385337] lirc_zilog: module is from the staging directory, the quality is unknown, you have been warned.
[  133.385976] lirc_zilog: Zilog/Hauppauge IR driver initializing
[  133.390031] lirc_zilog: probing IR Rx on Hauppage HD PVR I2C (i2c-14)
[  133.390200] lirc_zilog: probe of IR Rx on Hauppage HD PVR I2C (i2c-14) done. Waiting on IR Tx.
[  133.390212] lirc_zilog: probe of IR Rx on Hauppage HD PVR I2C (i2c-14) done
[  133.390235] lirc_zilog: probing IR Tx on Hauppage HD PVR I2C (i2c-14)
[  133.448298] i2c i2c-14: lirc_dev: driver lirc_zilog registered at minor = 0
[  133.448312] lirc_zilog: IR unit on Hauppage HD PVR I2C (i2c-14) registered as lirc0 and ready
[  133.448325] lirc_zilog: probe of IR Tx on Hauppage HD PVR I2C (i2c-14) done
[  133.448420] lirc_zilog: initialization complete

```

hardware.conf

```

#Chosen IR transmitter
TRANSMITTER="HD-PVR"
TRANSMITTER_MODULES="lirc_dev lirc_zilog"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE="/dev/lirc0"
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""
```

Testing script fails, but /dev/lirc0 does exist. 

```
0_1_KEY_POWER
irsend: could not connect to socket
irsend: No such file or directory
```


lsusb

```
mike@backend:/etc/lirc$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 2040:4903 Hauppauge
Bus 004 Device 002: ID 0dc6:3401 Precision Squared Technology Corp.

```

---

