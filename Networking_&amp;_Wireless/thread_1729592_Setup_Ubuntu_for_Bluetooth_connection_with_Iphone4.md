---
title: "Setup Ubuntu for Bluetooth connection with Iphone4"
date: 2011-04-15
forum: Networking &amp; Wireless
---

### Post by shayno90 on 2011-04-15
Ok the aim of this thread is to network an Iphone 4 with my Ubuntu desktop via Bluetooth. I would like to be able to share my desktop Wireless connection to my Iphone 4 wifi and sync my phone with the desktop also to transfer my documents.

Based on this old thread:

[http://ubuntuforums.org/showthread.php?t=598890&page=2](http://ubuntuforums.org/showthread.php?t=598890&page=2)

1.I start off by downloading and installing these packages:

sudo apt-get install

bluetooth
bluez-gnome
bluez-utils
gnome-bluetooth
                                                                                                                                                          2. edit the /etc/network/interfaces to this:
auto lo
iface lo inet loopback
iface bnep0 inet dhcp

3. In a text editor create 2 files: panup and pandown
For panup:

#!/bin/bash
sudo pand --connect 49:A0:98:J4:89:8E -n
sleep 1
sudo ifup bnep0

For pandown:

#!/bin/bash
sudo ifdown bnep0
sudo pand -K

sudo transfer them to /etc/bluetooth/pan from your directory where you first save them
cd /home/user/Documents/
sudo cp panup /etc/bluetooth/pan/
sudo cp pandown /etc/bluetooth/pan/
cd /etc/bluetooth/pan
/etc/bluetooth/pan$ ls -a
.  ..  dev-down  dev-up  pandown panup


3. Add this to /etc/default/bluetooth
PAND_ENABLED=1
PAND_OPTIONS="--role=PANU"

4. Find the MAC address of your Iphone4
:~$ sudo hcitool scan
Scanning ...
    2B:52:I7:L4:9A:3M    Nokia X3-02
    49:A0:98:J4:89:8E    Iphone4


My Iphone address appeared with another bluetooth capable phone I have.

4. Connect to the Iphone4
[FONT=monospace]:~$ pand --connect [/FONT]49:A0:98:J4:89:8E[FONT=monospace] -n
pand[3773]: Bluetooth PAN daemon version 4.69
pand[3773]: Connecting to [/FONT]49:A0:98:J4:89:8E[FONT=monospace]
pand[3773]: Connect to [/FONT]49:A0:98:J4:89:8E[FONT=monospace] failed. Permission denied(13)

Ok so this is the problem here, the Iphone4 either doesn't support this service or doesn't allow file sharing with Ubuntu 10.10.

Any ideas on how to correct this in order to share your desktop wireless with the Iphone Wifi and also share files?
[/FONT]

---

