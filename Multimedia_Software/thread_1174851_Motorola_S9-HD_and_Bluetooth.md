---
title: "Motorola S9-HD and Bluetooth"
date: 2009-05-31
forum: Multimedia Software
---

### Post by |Eric| on 2009-05-31
hi im having dificulties connecting my new Motorola S9-HD with my bluetooth dongle (desktop) 
im running Xubuntu core 2 duo 2g ram etc... 

the dongle is a belkin 

```
lsusb
Bus 003 Device 010: ID 050d:016a Belkin Components 
Bus 003 Device 009: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 008: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 007: ID 0a5c:4500 Broadcom Corp. 

```

here is what i get when i scan the device

```

root@eric-desktop:~# hcitool scan
Scanning ...
	00:0D:FD:2C:4C:09	Motorola S9-HD
root@eric-desktop:~# hcitool cc 00:0D:FD:2C:4C:09
Can't create connection: Input/output error

```


here is my hcid.conf
```
# hcid options
options {
	autoinit yes;
	# Security Manager mode - get passkey from dbus or pin_helper pgm
	security user;

	# Pairing mode - multi = allow re-pairing even if already paired.
	pairing multi;
       # passkey "0000";
}

# Default settings for HCI devices (dongles)
device {
	# Name that we advertise to others.  %h = hostname, %d = device ID
	name "%h";

	# What we claim to be able to do.  010c = laptop, 0104 = desktop, 
	# 0108 = server.  Leftmost 10 = OBEX; "or" with 02 for networking, 
	# etc.  See "man hcid.conf" for more codes.
	class 0x100104;

	# Allow others to detect our presence [enable or disable]
	#iscan enable;
	# Allow others to attempt to connect.
	pscan enable;

	# Default link mode (role): accept either role
	lm master;

	# Default link policy, which modes to allow
	lp rswitch,hold,sniff,park;
}

```

anybody got a clue ?

---

### Post by log2g on 2009-09-08
Hi Eric,

Surely you found a solution, but it may help somebody else..

Replace "00:01:02:23:04:89" by your bluetooth headset mac address: command ```
 hcitool scan 
```

[INDENT] * configuration
```

sudo apt-get install bluez-alsa
echo 'pcm.bluetooth {
	type bluetooth
        device "00:01:02:23:04:89" #optional, connects to specific device instead the default one
        profile "auto"             #optional, supported profiles are: auto, hifi and voice 
}' | tee ~/.asoundrc
# test with mplayer
mplayer -ao alsa:device=bluetooth  video.wmv

```
[/INDENT]

[INDENT] * use with Banshee, Rhythmbox or Totem
```

# for Bluetooth mode
gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "alsasink device=bluetooth"
# for Normal Speakers mode
gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink"

```
[/INDENT]
[INDENT] * use with Skype
```

echo 'pcm.headset {
       type bluetooth
       device "00:01:02:23:04:89"
       profile "voice"
}' | tee -a ~/.asoundrc

```
and Skype sound configuration with "headset"
[/INDENT]

BR,

Laurent.

---

### Post by |Eric| on 2011-04-05
i figured i would give an update : 

i got it paired with blueman 
works ok 
or with hcitool too 

i still have a bit of a problem i cant find the audio device 
to output to alsa 

os is 9.10  

pulse audio seams to find it in headset mode but i cant do anything with it 

root@eric-desktop:~# hcitool con
Connections:
	< ACL 00:0D:FD:2C:4C:09 handle 11 state 1 lm SLAVE AUTH ENCRYPT 
root@eric-desktop:~# 


Requesting information ...
	BD Address:  00:0D:FD:2C:4C:09
	Device Name: Motorola S9-HD
	LMP Version: 2.0 (0x3) LMP Subversion: 0xe90
	Manufacturer: Cambridge Silicon Radio (10)
	Features: 0xff 0xff 0x8b 0xf8 0x1b 0x18 0x00 0x80
		<3-slot packets> <5-slot packets> <encryption> <slot offset> 
		<timing accuracy> <role switch> <hold mode> <sniff mode> 
		<park state> <RSSI> <channel quality> <SCO link> <HV2 packets> 
		<HV3 packets> <u-law log> <A-law log> <CVSD> <paging scheme> 
		<transparent SCO> <broadcast encrypt> <enhanced iscan> 
		<interlaced iscan> <interlaced pscan> <inquiry with RSSI> 
		<extended SCO> <EV4 packets> <EV5 packets> <AFH cap. slave> 
		<AFH class. slave> <AFH cap. master> <AFH class. master> 
		<extended features> 
root@eric-desktop:~# dmesg 
...
[ 6422.772814] btusb_isoc_complete: hci0 corrupted SCO packet
[ 6422.772846] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[ 6422.772852] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[ 6422.772856] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[ 6422.772860] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
[ 6422.772864] hci_scodata_packet: hci0 SCO packet for unknown connection handle 0
root@eric-desktop:~#

---

