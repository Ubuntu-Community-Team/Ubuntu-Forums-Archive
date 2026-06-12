---
title: "Connect command line to a wifi"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by _cvt_ on 2010-08-13
Hi,

   I'm trying to connect to a AP by command line but I can't yet. Using the network manager it's possible but I need the command lines to use in my code programming.

Here it's what I tryed:

```
sudo iwconfig wlan0 mode managed channel 6 key restricted s:'12345' essid 'cassiano-PC_AP'
```

and the tail: sudo tail -f /var/log/syslog
```
Aug 13 14:05:55 cassiano-linux kernel: [13476.935795] wlan0: direct probe to AP 00:15:af:84:29:d3 (try 1)
Aug 13 14:05:55 cassiano-linux kernel: [13476.935943] wlan0: deauthenticating from 00:15:af:84:29:d3 by local choice (reason=3)
Aug 13 14:05:55 cassiano-linux kernel: [13476.936002] wlan0: direct probe to AP 00:15:af:84:29:d3 (try 1)
Aug 13 14:05:55 cassiano-linux kernel: [13476.939620] wlan0: direct probe responded
Aug 13 14:05:55 cassiano-linux kernel: [13476.939628] wlan0: authenticate with AP 00:15:af:84:29:d3 (try 1)
Aug 13 14:05:55 cassiano-linux kernel: [13476.942595] wlan0: authenticated
Aug 13 14:05:55 cassiano-linux kernel: [13476.942631] wlan0: associate with AP 00:15:af:84:29:d3 (try 1)
Aug 13 14:05:55 cassiano-linux wpa_supplicant[828]: No network configuration found for the current AP
Aug 13 14:05:55 cassiano-linux kernel: [13476.944736] wlan0: RX AssocResp from 00:15:af:84:29:d3 (capab=0x431 status=0 aid=20)
Aug 13 14:05:55 cassiano-linux kernel: [13476.944742] wlan0: associated
Aug 13 14:05:55 cassiano-linux kernel: [13476.965044] wlan0: deauthenticating from 00:15:af:84:29:d3 by local choice (reason=3)
Aug 13 14:05:55 cassiano-linux wpa_supplicant[828]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
```

I think that the error is:
```
Aug 13 14:05:55 cassiano-linux wpa_supplicant[828]: No network configuration found for the current AP
```

And when I connect with the network manager appears this on the tail:
```
 NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto cassiano-PC_AP' has security, and secrets exist.  No new secrets needed.
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'ssid' value 'cassiano-PC_AP'
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'auth_alg' value 'OPEN'
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'wep_key0' value '<omitted>'
Aug 13 14:31:31 cassiano-linux NetworkManager: <info>  Config: added 'wep_tx_keyidx' value '0'
```

and this:
```
Aug 13 14:31:32 cassiano-linux wpa_supplicant[828]: Associated with 00:15:af:84:29:d3

```

Can anyone help me ?

---

### Post by _cvt_ on 2010-08-17
Nobody?

---

### Post by _cvt_ on 2010-08-19
I realy need this

---

