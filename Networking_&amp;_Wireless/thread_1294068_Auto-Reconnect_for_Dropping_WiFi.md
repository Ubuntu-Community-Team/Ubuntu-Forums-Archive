---
title: "Auto-Reconnect for Dropping WiFi"
date: 2009-10-17
forum: Networking &amp; Wireless
---

### Post by Deverell on 2009-10-17
Hello, 

I have a BlackBook and naturally I used to have Leopard. I mostly use my laptop in my bedroom and in college, in both places I'm dependent on WiFi. When I had OS X my signal strength was usually full and connection was consistent. Now I have Jaunty and my signal strength is suddenly much weaker and the signal just drops at seemingly random intervals with no apparent bearing on signal strength i.e. it drops sometimes even if I have full reception.  

I was hoping someone has either heard some way to resolve this issue. Acceptable workarounds for me would include

1. An alternative driver (proprietary or open source)that improves communication between my hardware and Jaunty. 
2. Some way to auto-reconnect to the last network joined when a disconnection occurs or after a short time interval.

Thanks, 
Deverell.

---

### Post by t0mppa on 2009-10-17
> **Deverell said:**
> 1. An alternative driver (proprietary or open source)that improves communication between my hardware and Jaunty.

We're not mind readers, so you're going to have to tell us which chip & driver you're using first. :)

> **Deverell said:**
> 2. Some way to auto-reconnect to the last network joined when a disconnection occurs or after a short time interval.

If you set Network Manager to automatically connect to a network, it'll instantly begin reconnecting after a disconnection. Mine drops off every now and then as well (at times every 2 minutes, then sometimes it can last 10 hours in row without a disconnect), but since it reconnects in ~10 seconds, I haven't bothered to do anything about it.

---

### Post by Deverell on 2009-10-17
t0mppa,  

> **t0mppa said:**
> We're not mind readers, so you're going to have to tell us which chip & driver you're using first. :)

What is the command to give such information?

> **t0mppa said:**
> 
If you set Network Manager to automatically connect to a network, it'll instantly begin reconnecting after a disconnection. Mine drops off every now and then as well (at times every 2 minutes, then sometimes it can last 10 hours in row without a disconnect), but since it reconnects in ~10 seconds, I haven't bothered to do anything about it.

I'm new to Linux. How do I set up Network Manager to automatically connect to a network?
I'm off to sleep now, its very late (2:30am). Hopefully I can read your reply in the morning. 

Thanks Again, 
-Deverell.

---

### Post by RabidWeezle on 2009-10-17
Easiest way to find out is running lspci in a terminal, and looking for network, that should tell you what linux thinks your wireless card is. 


[LIST=1]
[*]alt+f2
[*]gnome-terminal [enter]
[*]then in gnome-terminal: lspci [press enter]
[*]then highlight all the output from that with the mouse
[*]ctrl+shift+c
[*]make a new reply in this thread
[*]ctrl+v or right-click paste
[/LIST]

---

### Post by Deverell on 2009-10-18
```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:07.0 Performance counters: Intel Corporation Device 27a3 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
03:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)

```

Should I be fortunate to find a better driver, how do I make a backup of the one I have so I can easily revert to the previous state because if my network card goes down. I've essentially lost communication to get help from you guys or being able to help my self without internet. 

Also Network-Manager, I found a config file called n-m-system-settings in /etc/NetworkManager/ with the following code inside it:
```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```

ifupdown is handled in /etc/NetworkManager/dispatcher.d

```
#!/bin/sh -e
# Script to dispatch NetworkManager events
#
# Runs ifupdown scripts when NetworkManager fiddles with interfaces.

if [ -z "$1" ]; then
    echo "$0: called with no interface" 1>&2
    exit 1;
fi

# Fake ifupdown environment
export IFACE="$1"
export LOGICAL="$1"
export ADDRFAM="NetworkManager"
export METHOD="NetworkManager"
export VERBOSITY="0"

# Run the right scripts
case "$2" in
    up)
	export MODE="start"
	export PHASE="up"

	if [ -d /var/run/network/ ] ; then
		tmpfile=`mktemp -t`
		if [ -e /var/run/network/ifstate ] ; then
			cat /var/run/network/ifstate | grep -v ^$IFACE= > $tmpfile || true
		fi
		echo $IFACE=$IFACE >> $tmpfile
		mv $tmpfile /var/run/network/ifstate
	fi

	exec run-parts /etc/network/if-up.d
	;;
    down)
	export MODE="stop"
	export PHASE="down"

	if [ -e /var/run/network/ifstate ] ; then
		tmpfile=`mktemp -t`
		cat /var/run/network/ifstate | grep -v ^$IFACE= > $tmpfile || true
		mv $tmpfile /var/run/network/ifstate
	fi

	exec run-parts /etc/network/if-down.d
	;;
    pre-up)
	export MODE="start"
	export PHASE="pre-up"
	exec run-parts /etc/network/if-pre-up.d
	;;
    post-down)
	export MODE="stop"
	export PHASE="post-down"
	exec run-parts /etc/network/if-post-down.d
	;;
    *)
	echo "$0: called with unknown action \`$2'" 1>&2
	exit 1
	;;
esac
```

What changes do I need to make?

---

### Post by Deverell on 2009-10-18
In the end I decided to install wicd(Wireless Interface Connection Daemon)

For Googlers this is an alternative NetworkManager to the default one supplied by Ubuntu. Apparently it stops the WiFi dropping but I'm not saying this out of experience just from what I've read from other users of the program.  

To install in Jaunty:
```
sudo apt-get install wicd
```

To start:
```
wicd-client
```

For more information including how to get .deb packages and install instructions on other distributions or versions. Visit the [website]("http://wicd.sourceforge.net/"). 

-Deverell

---

### Post by Spartachris on 2009-11-05
Deverell

wicd is working for me too. network-manager was dropping the connection like crazy, sometimes getting it again, but most of the time I would have to re-enter the wpa password, and even then it would not always reconnect. I never had a problem with this in 8.04-9.04, with the same wifi card (Linksys).

I've searched launchpad to see if there is a bug report on this, but can't seem to find it. Do you or anyone know if this is reported officially or being worked on?

Thanks!

---

### Post by sjafri on 2009-12-30
I using acer aspire 5585
it's work for me to
but I had a problem how to auto start this programs without open the console
[B]
Update[/B]
to autostart the wicd, go to system--> preference --> startup applications

---

