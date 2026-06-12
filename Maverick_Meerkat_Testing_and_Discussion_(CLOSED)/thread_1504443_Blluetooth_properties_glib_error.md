---
title: "Blluetooth properties glib error"
date: 2010-06-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by youoh on 2010-06-08
i could not connect my keyboard so i'm writing with *onboard*

```
bluetooth-properties
** Message: adding killswitch idx 0 state 1
** Message: killswitch 0 is 1
** Message: killswitches state 1

(bluetooth-properties:4184): GLib-GObject-WARNING **: cannot register existing type `BluetoothClient'

(bluetooth-properties:4184): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

```

some terminal guru's the who can help me to connect my keyboard there

---

### Post by Kevbert on 2010-06-08
Looks like bluetooth is non-responsive. If I plug in my bluetooth USB dongle the Applet stays greyed out and yet I can turn bluetooth on and off. Clicking on Preferences and Set up new device do nothing. PC can see phone though:

 ```
~$ hcitool scan
Scanning ...
	00:1E:DC:86:44:2D	K800i
~$ sudo hcitool info 00:1E:DC:86:44:2D
Requesting information ...
	BD Address:  00:1E:DC:86:44:2D
	Device Name: K800i
	LMP Version: 2.0 (0x3) LMP Subversion: 0x520
	Manufacturer: ST Microelectronics (48)
	Features: 0xff 0xe9 0x8d 0xfe 0x9b 0xe9 0x00 0x00
		<3-slot packets> <5-slot packets> <encryption> <slot offset> 
		<timing accuracy> <role switch> <hold mode> <sniff mode> 
		<park state> <SCO link> <HV3 packets> <u-law log> <A-law log> 
		<CVSD> <power control> <transparent SCO> <broadcast encrypt> 
		<EDR ACL 2 Mbps> <EDR ACL 3 Mbps> <enhanced iscan> 
		<interlaced iscan> <interlaced pscan> <inquiry with RSSI> 
		<extended SCO> <EV4 packets> <EV5 packets> <AFH cap. slave> 
		<AFH class. slave> <3-slot EDR ACL> <5-slot EDR ACL> 
		<AFH cap. master> <EDR eSCO 2 Mbps> <EDR eSCO 3 Mbps> 
		<3-slot EDR eSCO> 
~$ 

```I read somewhere the one or two old bluetooth packages were no longer supported. It may be that we need to wait for new packages.
Xsession-errors:
```
(bluetooth-properties:2043): GLib-GObject-WARNING **: cannot register existing type `BluetoothClient'

(bluetooth-properties:2043): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed

(bluetooth-properties:2045): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(bluetooth-properties:2047): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(bluetooth-wizard:2050): GLib-GObject-WARNING **: cannot register existing type `BluetoothClient'

(bluetooth-wizard:2050): GLib-CRITICAL **: g_once_init_leave: assertion `initialization_value != 0' failed
** Message: RFKILL event: idx 1 type 2 op 2 soft 1 hard 0

** Message: updating killswitch status 1
** Message: killswitch 1 is 0
** Message: killswitches state 0
** Message: killswitch 1 is 0
** Message: killswitches state 0
** Message: RFKILL event: idx 1 type 2 op 2 soft 0 hard 0

** Message: updating killswitch status 1
** Message: killswitch 1 is 1
** Message: killswitches state 1
** Message: killswitch 1 is 1
** Message: killswitches state 1

(bluetooth-wizard:2052): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

---

