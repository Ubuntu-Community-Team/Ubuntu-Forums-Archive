---
title: "bluetoothd as remote control"
date: 2009-06-12
forum: Networking &amp; Wireless
---

### Post by bryonak on 2009-06-12
Not sure if it's the right forum, but I'll try anyway ;)

I'd like to control a machine from a cell phone (Sony Ericsson K750i) via bluetooth, ideally moving the mouse with the joystick and assigning the number keys to xkbd queries.

These are the options:

**BlueZ** - the standard bluetooth stack
**hidd** - a daemon in old BlueZ releases, now deprecated
**Blueman** - a bluetooth manager that can transfer files and connect to the internet, but I couldn't figure out remote control
**LBRC** - a new tool (LIRC for bluetooth) in alpha stage. Can't get it to work.
**rfcomm** - can't get it to work with HID

Java applets: anyRemote, Bemused, RemoteJ, X-Stream Remote

Those are the main threads I found on UF:
[A hidd HowTo]("http://ubuntuforums.org/showthread.php?t=5412")
[An anyRemote HowTo]("http://ubuntuforums.org/showthread.php?t=993993")
[Another anyRemote HowTo with lots of other info]("http://ubuntuforums.org/showthread.php?t=341408")



I can't figure out how to do it with BlueZ or Blueman... On my phone, I can select the remote control -> MediaPlayer -> my computer name, but it throws an error (Failed to connect) because there's no service except default bluetoothd running.

There's a lot of old HowTos describing how to get it to work with hidd, which has been declared as deprecated in newer BlueZ releases and I don't think downgrading the whole bluetooth stack is a smart thing to do.
However, a friend of mine had it perfectly working with hidd some time ago.
BlueZ says to use the new "input service" instead of hidd, but I simply can't find any guide on this.

Also, I'd greatly prefer to use the HID instead of installing Java clients, since most SE phones and many others have built-in HID. This rules out all the Java applets mentioned, which require installation on every phone that has to control the computer (a media center with various applications)... and they're going to be quite a bunch of phones. Plus it's much less elegant.

Anyone got suggestions or useful guides for the newer BlueZ releases?

Thanks!

---

### Post by bryonak on 2009-06-12
Ok... I just figured it out.
The whole process is quite simple, but badly documented.

1. Edit the Local device class section in your /etc/bluetooth/hcid.conf to look like this***:
```

        # Local device class
        class 0x520204;

```
2. Restart the bluetooth service:
```

sudo /etc/init.d/bluetooth stop
sudo /etc/init.d/bluetooth start
("restart" didn't work for me)

```
3. Select "always visible" in the bluetooth preferences (System -> Preferences -> Bluetooth)
4. Search for your phone and connect to it in order to set a mutual passkey.
5. On your mobile phone, select the "bluetooth remote control" option (either in Organiser or Entertainment), choose the device name (which you set in the bluetooth preferences of your computer) and confirm the request on the PC.
6. You're done.

*** If you have no hcid.conf, you have to create one:
```
#
# HCI daemon configuration file.
#

# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security user;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing multi;

	# Default PIN code for incoming connections
	passkey "1234";
}

# Default settings for HCI devices
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
#	class 0x000100;
	class 0x520204;


	# Default packet type
	#pkt_type DH1,DM1,HV1;

	# Inquiry and Page scan
	iscan enable; pscan enable;
	discovto 0;

	# Default link mode
	#   none   - no specific policy 
	#   accept - always accept incoming connections
	#   master - become master on incoming connections,
	#            deny role switch on outgoing connections
	lm accept;

	# Default link policy
	#   none    - no specific policy
	#   rswitch - allow role switch
	#   hold    - allow hold mode
	#   sniff   - allow sniff mode
	#   park    - allow park mode
	lp rswitch,hold,sniff,park;
}

```

---

