---
title: "Bluetooth keyboard help"
date: 2008-12-04
forum: Networking &amp; Wireless
---

### Post by wolftousen on 2008-12-04
First off, I'm on kubuntu 8.04 64bit..

Ok, I have a Rocketfish Bluetooth Keyboard (not the combo with mouse, just keyboard) and a Kensington Bluetooth Dongle.  I have managed to get it so that once i get logged into kubuntu I can run this set of commands to get my keyboard connected:

sudo hciconfig hci0 up
sudo hciconfig hci0 piscan
sudo hciconfig hci0 noauth
sudo hciconfig hci0 nosecmgr
sudo hcitool inq
sudo hcitool scan
sudo hcitool info 00:18:A3:00:49:7F
sudo hcitool con
sudo hidd --search

I don't know that all those commands are necessary, but it works and I put it into a script and added it to /etc/init.d/ and rc.d.  Shortly after the sound daemon starts up my keyboard stops blinking and is connected.

Where I need help is getting my keyboard to work at the boot screen and grub and the password entry screen of kubuntu.  (Though I can modify grub to default boot kubuntu, I still require winxp for some things until march next year and virtualbox doesn't cut it...)

I tried using hid2hci -0 and -1 but both tell me there are not such devices in such modes... does the command: hciconfig hci0 down, set the dongle to hid mode?

My /etc/init.d/hcid.conf file:
```
# HCId options
options {
	# Automatically initialize new devices
	autoinit yes;

	# Security Manager mode
	#   none - Security manager disabled
	#   auto - Use local PIN for incoming connections
	#   user - Always ask user for a PIN
	#
	security none;

	# Pairing mode
	#   none  - Pairing disabled
	#   multi - Allow pairing with already paired devices
	#   once  - Pair once and deny successive attempts
	pairing none;

	# Default PIN code for incoming connections
	passkey "1234";
}
	
device {
	# Local device name
	#   %d - device id
	#   %h - host name
	name "%h-%d";

	# Local device class
	class 0x000100;

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

device 00:18:A3:00:49:7F {
	name "Rocketfish Bluetooth Keyboard"
	class 0x002540
	discovto 0;
	lm accept;
	lp rswitch,sniff;
	auth enable;
	encrypt enable;
	iscan enable;
	pscan enable;
}
```

In my /etc/init.d/bluetooth file I have changed:
HID2HCI_ENABLED=0

HIDD_OPTIONS="--master --connect 00:18:A3:00:49:7F --server"

start_hid()
{
	if test "$HIDD_ENABLED" != "0"; then
		start-stop-daemon --start --quiet --exec $HIDD_DAEMON -- $HIDD_OPTIONS
		[ "$VERBOSE" != no ] && log_progress_msg "hidd"
		sudo hciconfig hci0 down
		sudo hciconfig hci0 up	
		sudo hciconfig hci0 piscan
		sudo hciconfig noauth
		sudo hciconfig nosecmgr
	fi
}

Can anyone guide me to get my keyboard working a boot/grub?

~Wolftousen

---

### Post by BrooksOfSheffield on 2008-12-10
The keyboard/mouse combo actually has a hardware means to associate prior to drivers loading (by means of pushing a button on the adapter).  But that adapter has been, at best, problematic under Linux.  Historically the only way I could make that adapter work at all was by physically hooking up a keyboard and issuing terminal commands to connect on every boot.

That's why I use an IOGear adapter I picked up on the cheap...  I lost the ability to have a wireless keyboard from POST to drivers being loaded, but for the occasions when I need a keyboard I'll just plug one in temporarily.  And it's far more convenient to have the keyboard and mouse work in the OS by default.

Without a means of hardware association, you're probably outta luck with your Kensington adapter.

---

### Post by IQRules on 2008-12-10
Have you tried to turn on BT keyborad first before reboot / turn on Ubuntu?
I do this trick with Rocketfish BT mouse, I am on 8.10 though.

I have this in /etc/init.d/bluetooth script.

# add by xxx 12/6/2008
        [B][COLOR="Red"]hciconfig hci0 pscan
[/COLOR][/B]
        log_end_msg 0
    ;;
  stop)

---

