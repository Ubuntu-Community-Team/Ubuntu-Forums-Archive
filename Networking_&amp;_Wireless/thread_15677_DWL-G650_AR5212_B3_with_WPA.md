---
title: "DWL-G650 AR5212 B3 with WPA"
date: 2005-02-16
forum: Networking &amp; Wireless
---

### Post by jmather on 2005-02-16
I'm trying to get my DWL-G650 working with WPA. I have gotten it on the wireless network but not with WPA.  I used ndiswrapper to install the card.  I have tried several differen wpa_supplicant.conf setups (simple to complex) but I always seem to get this from my output (note I replaced the network names and lengths with x's and *'s):

$ sudo ./wpa_supplicant -Dndiswrapper -iath0 -dddd
Initializing interface 'ath0' conf '(null)' driver 'ndiswrapper'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
eapol_version=1
Line: 2 - start of a new network block
ssid - hexdump_ascii(len=*):
     52 4f 53 43 4f 45                                 XXXXXX
scan_ssid=1 (0x1)
PSK (ASCII p***phrase) - hexdump_ascii(len=*): [REMOVED]
priority=5 (0x5)
PSK (from p***phrase) - hexdump(len=*): [REMOVED]
Priority group 5
   id=0 ssid='XXXXXX'
Initializing interface (2) 'ath0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Own MAC address: 00:11:95:2e:fb:14
Failed to enable WPA in the driver.
Failed to disable WPA in the driver.
rmdir[ctrl_interface]: Bad address

Does anyone have any clue what is going on here?  Perhaps I need to use madwifi?

Has anyone else done similar setups?

Thanx

---

### Post by sunscape on 2005-02-18
I don't think ndiswrapper supports WPA, yet. I used it for my old laptop with WEP and it worked perfectly. Maybe you should use WEP, if only, for testing.

---

### Post by jmather on 2005-02-22
Ok, so I finally got this working on my laptop, I currently have a D-Link router and a D-Link DWL-G650 AR512 B3. This was simple once I got it but the troubleshooting steps were a PITA.  Lets pray that this gets easier in future versions.....  Below are the steps:

1) I udated my kernel image and headers to (I don't know if this is necessary but I was having trouble prior to this): 
linux-image-2.6.8.1-5
linux-headers-2.6.81-5

2) After upgrading I rebooted (make sure you have not configured your card yet, if you have I'm not sure about what steps you should take next, but I'm sure someone around here does:)

3) I then modified the scripts from the wpa-howto on the wiki [wpahowto](http://www.ubuntulinux.org/wiki/WPAHowto) to be one simpler script, something like below (I did this not because the scripts are no good but because I wanted something a bit simpler) I placed this in my /etc folder, I'm sure you could put it wherever you like:

```
#!/bin/bash

PATH=/sbin:/bin:/usr/sbin:/usr/bin
WPA=/usr/sbin/wpa_supplicant
NAME=wpa_supplicant
DESC="WPA Supplicant"
CONF=/etc/wpa_supplicant.conf
DEVICE=$2
DRIVER=$3
STATUS=1
TIME=0
INTERVAL=5

case "$1" in
	start)
		if [[ -z $DEVICE ]]
		then
			echo "No device specified."
			exit 1
		fi
			
		echo "Starting $DESC on $DEVICE"
		if [[ -n $DRIVER  ]]
		then
			$WPA -i $DEVICE  -D$DRIVER -B
		else
			$WPA -i$DEVICE -Dmadwifi -B
		fi

		while [[ $STATUS == 1 && $TIME -lt 25 ]]
		do
			echo "Statusing wpa time left: $TIME status=$STATUS"
			wpa_cli status | grep AUTHENTICATED 
			STATUS=$?
			TIME=$(($TIME + $INTERVAL))
			sleep $INTERVAL
		done
		
		if [[ $STATUS -ne 1 ]]
		then
			echo "Started $DESC and Authenticated"
			dhclient3 -pf /var/run/dhclient.ath0.pid -lf /var/run/dhclient.ath0.leases ath0
		else
			echo "COULD NOT AUTHENTICATE"
			exit1
		fi
		;;
	stop)
		echo "Stopping $DESC: "
		if [[ ! -z `pidof $WPA` ]]
		then
			killall $WPA
		fi
		;;
	*)
		echo "Usage: configWPA {start|stop}" >&2
		exit 1
		;;
esac
exit 0

``` 

I then added something like this to my /etc/network/interfaces file:

```

iface ath0 inet manual
pre-up ifconfig ath0 up
up /etc/configWPA start ath0
post-down /etc/configWPA stop
name DWL-G650 interface type

```

4) After I boot I can generally do an ifup ath0 and when I'm done do an ifdown ath0 and everything works (I'm even running at 54 MBPS).  I have had a few issues....

If anyone cares to comment:

a) How can I make this always work on startup?

b) How can I ensure that my settings will not be taken over by one of the network management tools?

Anyways....back to  ](*,)

---

### Post by jmather on 2005-02-22
I just wanted to mention, in case anyone was confused by my previous post...that I used madwifi (installed from ubuntu) and I grabbed wpa_supplicant from synaptic.....

Anyways...I just realized I didn't mention this above.....

---

