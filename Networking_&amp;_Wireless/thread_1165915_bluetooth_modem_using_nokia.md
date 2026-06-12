---
title: "bluetooth modem using nokia"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by Ameoba on 2009-05-21
Hi,

I'm trying to setup my EEEPC 1000H to use my Nokia 500 as a modem, but using Bluetooth instead of the USB cable.
I'm running Ubuntu 9.04 net-book edition.

Can anyone tell me how to set this up, or point me in the direction of a site that will work with 9.04 and Nokia 5800?

Regards,

---

### Post by tbscmc on 2009-05-28
first, scan the bluetooth address of your phone with:

```
$sudo hcitool scan
```

it will output something like this 

	```
00:15:DE:DB:D9:5B	Tracemonkey
```

the 12 digit hex number is is phone bluetooth address
now edit your rfcomm0 file using 

```
$sudo gedit /etc/bluetooth/rfcomm0
```

This file should look like this:

```
#
# RFCOMM configuration file.
#

rfcomm0 {
	# Automatically bind the device at startup
	bind yes;
#
#	# Bluetooth address of the device
	device 00:15:DE:DB:D9:5B;
#
#	# RFCOMM channel for the connection
	channel	1;
#
#	# Description of the connection
	comment "Example Bluetooth device";
}
```

make the necessary changes in your file and uncomment the lines as shown above.

Now edit your wvdial.conf file using

```
$sudo gedit /etc/wvdial.conf
```

make it look like this:

```
[Dialer Defaults]
Phone = *99#
Modem = /dev/rfcomm0
Username =username
Password =password 
New PPPD = yes
```

save the file.
type

```
$sudo wvdial
```

you should be able to connect

---

### Post by Ameoba on 2009-06-01
Thanks very much that has got the device connecting and dialing.

However it's comming up with:

```
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Waiting for prompt.
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> PPP negotiation detected.
--> Starting pppd at Mon Jun  1 21:40:04 2009
--> Pid of pppd: 7177
--> Using interface ppp0
--> pppd: x&#65533;&#65533; x&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: x&#65533;&#65533; x&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: x&#65533;&#65533; x&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: x&#65533;&#65533; x&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: x&#65533;&#65533; x&#65533;&#65533; &#65533;&#65533;&#65533; 
--> pppd: x&#65533;&#65533; x&#65533;&#65533; &#65533;&#65533;&#65533; 
--> Disconnecting at Mon Jun  1 21:40:08 2009
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
--> Cannot get information for serial port.
--> Cannot open /dev/rfcomm0: Transport endpoint is not connected
--> Cannot get information for serial port.


```

Error code 16 is apparently "The link was terminated by the modem hanging up."

Why would my modem be hanging up, any ideas?

---

### Post by Ameoba on 2009-06-12
A bit of further information:

The listing in the /var/logs/messages file is as follows:

```
Jun 12 23:30:19 EVE pppd[3717]: pppd 2.4.5 started by root, uid 0
Jun 12 23:30:19 EVE pppd[3717]: Using interface ppp0
Jun 12 23:30:19 EVE pppd[3717]: Connect: ppp0 <--> /dev/rfcomm0
Jun 12 23:30:19 EVE pppd[3717]: PAP authentication succeeded
Jun 12 23:30:19 EVE kernel: [  562.827775] PPP BSD Compression module registered
Jun 12 23:30:19 EVE kernel: [  562.861116] PPP Deflate Compression module registered
Jun 12 23:30:19 EVE pppd[3717]: LCP terminated by peer
Jun 12 23:30:22 EVE pppd[3717]: Connection terminated.
Jun 12 23:30:22 EVE pppd[3717]: Modem hangup
Jun 12 23:30:22 EVE pppd[3717]: Exit.
Jun 12 23:30:29 EVE kernel: [  572.398940] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 118

```

Anyone got an idea as to what setting i may have incorrect or what section isn't working correctly?

---

### Post by tbscmc on 2009-07-02
You may need to set some init strings specific to your data service provider, contact their service personnel. However i had success on these occasions setting a "stupid mode" in "wvdial.conf" file

```
[Dialer Defaults]
Phone = *99#
Modem = /dev/rfcomm0
Username =username
Password =password 
New PPPD = yes
Stupid Mode =yes
```

---

### Post by Ameoba on 2009-07-09
I've got it working with the help of a friend,

I've used GnomePPP, and found the key config part i needed to work out was the Init string.

I think this is probably the same problem i'm having with wvdial.

I needed to enter AT+CGDCONT=,"IP","VIRGININTERNET"

Now i'd like to find where i can enter the same details into wvdial's config.

---

### Post by tbscmc on 2009-09-16
> **Ameoba said:**
> I've got it working with the help of a friend,

I've used GnomePPP, and found the key config part i needed to work out was the Init string.

I think this is probably the same problem i'm having with wvdial.

I needed to enter AT+CGDCONT=,"IP","VIRGININTERNET"

Now i'd like to find where i can enter the same details into wvdial's config.


You need to enter these lines as Init3, like:

```


Init 3 = AT+CGDCONT=,"IP","VIRGININTERNET"
```

Init 1 and Init 2 should be present if ```
$ sudo wvdialconf
``` found your modem.

Im sorry i take this long to reply, i had been busy for academic schedule

---

