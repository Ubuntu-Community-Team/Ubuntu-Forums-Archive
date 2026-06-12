---
title: "Cannot connect to unencrypted wireless networks"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by Richard_Clement on 2010-03-23
Hello, I have a machine running Xubuntu [2.6.22-14-generic]. I have been trying to get this machine connected to wireless for ages, and I'm having another stab at it.

So far I have install ndiswrapper and loaded the driver for a Linksys wireless adapter. The output of 'ndiswrapper -l' reports:

```

wusb11v4 : driver installed
        devoce (13B1: 000B) present

```

So as far as my newbie knowledge goes, I believe that step to be completed, correct?

When I turn on the machine is type in

```
sudo sh
modprobe ndiswrapper
```

to get the card running to where it will appear in the iwconfig dialog.

The commands 'iwlist wlan0 scan' will list all the wireless networks around me, but I have been un-able to connect to any network, even unencrypted ones. I have tried to connect both through Wicd and command-line to no avail. 

For command-line I have used:

```

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "linksys"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

```

With the final 'dhclient wlan0' commands, the following is returned:

```
There is already a pid file /var/run/dhclient.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:0f:66:ef:b0:14
Sending on LPF/wlan0/00:0f:66:ef:b0:14
Sending on Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

I have attempted to go ahead a step further and connect to an encrypted wireless network, however, I receive the same message, as well as another error message upon trying to enter the key, with the following code:

```

iwconfig wlan0 key s:"thekey"

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.

```

Am I using the correct syntax for this step?


Anyways, I would be incredibly appreciative of any help, and hopefully I have provided enough info, thank you very much for your time!


Sincerely, Richard

---

### Post by Richard_Clement on 2010-03-23
More information:

Below is the print out of iwconfig:

```

lo      no wireless extensions.

eth1    no wireless extensions.

wlan0   IEEE 802.11b  ESSID: off/any
        Mode: Managed Frequency:2.437 GHz  Access Point: Not-Associated
        Bit Rate:11MB/s
        RTS thr=2432 B  Fragment thr=2342 B
        Power Management: off
        Link Quality: 0 Signal level:0 Noise level:0
        Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
        Tx excessive retries:- Invalid misc:0 Missed beacon:0

```

---

### Post by Richard_Clement on 2010-03-23
[SIZE=2]Well, somehow I have managed to fix the issue myself, but I will try to describe what I have done so that if there is ever anyone who has the same issue, they might find this of some help.[/SIZE]
        [LEFT][SIZE=2]1.) I installed wpa_supplicant.[/SIZE][/LEFT]
        [LEFT][SIZE=2]2.) I edited /etc/network/interfaces to reflect the following:[/SIZE]
[SIZE=2]
[/SIZE][/LEFT]
        ```
        [LEFT][SIZE=2]auto lo[/SIZE]       

[SIZE=2]iface lo inet loopback[/SIZE]       

[SIZE=2]iface eth0 inet dhcp[/SIZE]       

[SIZE=2]auto wlan0[/SIZE]       

[SIZE=2]iface wlan0 inet dhcp[/SIZE]       

[SIZE=2]wpa-conf /etc/wpa_supplicant.conf[/SIZE]       

[SIZE=2]iface eth1 inet dhcp[/SIZE]       

[SIZE=2]auto eth1[/SIZE][/LEFT]

```[LEFT]
[SIZE=2]
[/SIZE][/LEFT]
        [LEFT][SIZE=2]3.) I edited /etc/wpa_supplicant.conf to reflect: I believe this is specifically for WPA-PSK.[/SIZE]
[SIZE=2]
[/SIZE][/LEFT]
        ```
        [LEFT][SIZE=2]ctrl_interface=/var/run/wpa_supplicant[/SIZE]       

[SIZE=2]ctrl_interface_group=0[/SIZE]       

[SIZE=2]eapol_version=1[/SIZE]       

[SIZE=2]# ap_scan=2 was the one for me you may try 0 or 1 instead of 2[/SIZE]       

[SIZE=2]ap_scan=2[/SIZE]       

[SIZE=2]fast_reauth=1[/SIZE]       

[SIZE=2]network={[/SIZE][/LEFT]
      [SIZE=2]ssid="SSID_goes_here"[/SIZE]        [LEFT][SIZE=2]       proto=WPA[/SIZE]       

[SIZE=2]       key_mgmt=WPA-PSK[/SIZE]       

[SIZE=2]       pairwise=TKIP[/SIZE]       

[SIZE=2]       group=TKIP[/SIZE]       

[SIZE=2]       psk="password_goes_here"[/SIZE]       

[SIZE=2]}[/SIZE][/LEFT]

```[LEFT]
[SIZE=2]
[/SIZE][/LEFT]
        [LEFT][SIZE=2]4.) I Ran 'ndiswrapper -m'[/SIZE][/LEFT]
    [LEFT][SIZE=2]5) I added 'ndiswrapper' to the bottom of /etc/modules (#4 wasn't working entirely how I expected it too, but this fixed it.)[/SIZE][/LEFT]
        [LEFT][SIZE=2]And this has left me very happy with a WPA encrypted wireless connection. Hope this helps someone else. :)[/SIZE][/LEFT]

---

### Post by Fritsl on 2011-01-08
I am happy the problem is solved.. But not for me, as I do not have a clue to al the strange codes you guys write :)

I am a USER, and I have installed Ubuntu 10.10. it finds all encryoted networks fine. If I take an unprotected network and protect it, it finds it fine. But I really need to connect to unprotected networks.. And they just do not appear on the list.

It appears strange to me, that I can "invent" any name of "hidden networks" that do not exist, and it will tell me that it is connected. 

So basically; if the network does not exist, or is unprotected, same-same: I can tell it to connect.. and it tells me that all is fine.. but no connection at all.

So.. For a low-tech-mouse-click-user; How the f*** do I connect to unencrypted networks? Should be possible, no? :)

Thanks, peace and loads of male bonding!

---

