---
title: "Card (seems to be) working - just can't grab IP"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by barrmulio on 2006-05-29
Ubuntu Dapper
The infamous D-Link DWL G120 (USB)

So far:
- Network identifies the device as active under eth1
- Wifi Radar has all the APs listed, including my own essid ("Network" for the sake of this post)
- 'Network' is bg, channel auto, wep protected (currently turned off wep for isolation)
- I've tested the connectivity on a winxp machine without any problems
- I'm using eth0 lan thru the same router right now to type this (ie it works fine)
- Link light on the dlink never come on
- My router never sees an attempt to connect from the router :-k 
- iwconfig sees my device, tried different modes and still no attempt to connect
- iwlist sees the networks as well
- no filtering on the router (mac or ip)

I Read:
- [http://www.linuxquestions.org/questions/showthread.php?t=337158](http://www.linuxquestions.org/questions/showthread.php?t=337158) 
- [http://www.linuxquestions.org/questions/showthread.php?t=214805](http://www.linuxquestions.org/questions/showthread.php?t=214805)

So...
- I still can't grab an IP, I must be missing something (easy - i hope) ](*,) ](*,) ](*,) 

I would appreciate any help - I'm trying to get this pc into my living room where there's no cat5.  Thanks in advance

---

### Post by barrmulio on 2006-05-30
well i did something wrong, and now ubuntu won't recognize the device at all (no power light when on the usb port) - tried a bunch of ports and reboots...](*,) 

i'm gonna play around with it tonight in the hopes i can get ubuntu to see it again...

here's the message dump
```
May 29 23:14:56 localhost kernel: [4303762.700000] usb 4-5: new high speed USB d evice using ehci_hcd and address 6
May 29 23:14:57 localhost kernel: [4303763.213000] islsm: Unknown symbol ieee802 11_txb_free
May 29 23:14:57 localhost kernel: [4303763.213000] islsm: Unknown symbol alloc_i eee80211softmac
May 29 23:14:57 localhost kernel: [4303763.213000] islsm: Unknown symbol ieee802 11softmac_wx_get_scan_results
May 29 23:14:57 localhost kernel: [4303763.213000] islsm: Unknown symbol ieee802 11_set_geo
May 29 23:14:57 localhost kernel: [4303763.213000] islsm: Unknown symbol ieee802 11softmac_start
May 29 23:14:57 localhost kernel: [4303763.213000] islsm: Unknown symbol ieee802 11softmac_wx_set_essid
May 29 23:14:57 localhost kernel: [4303763.214000] islsm: Unknown symbol ieee802 11_rx
May 29 23:14:57 localhost kernel: [4303763.214000] islsm: Unknown symbol ieee802 11softmac_wx_get_wap
May 29 23:14:57 localhost kernel: [4303763.214000] islsm: Unknown symbol ieee802 11_rx_mgt
May 29 23:14:57 localhost kernel: [4303763.214000] islsm: Unknown symbol ieee802 11softmac_wx_get_essid
May 29 23:14:57 localhost kernel: [4303763.214000] islsm: Unknown symbol ieee802 11softmac_wx_set_wap
May 29 23:14:57 localhost kernel: [4303763.214000] islsm: Unknown symbol ieee802 11softmac_stop
May 29 23:14:57 localhost kernel: [4303763.226000] islsm_device: Unknown symbol isl_debug
May 29 23:14:57 localhost kernel: [4303763.226000] islsm_device: Unknown symbol islsm_alloc_dump
May 29 23:14:57 localhost kernel: [4303763.226000] islsm_device: Unknown symbol isl_fn_exit
May 29 23:14:57 localhost kernel: [4303763.226000] islsm_device: Unknown symbol islsm_ping_device
May 29 23:14:57 localhost kernel: [4303763.226000] islsm_device: Unknown symbol isl_fn_enter
May 29 23:14:57 localhost kernel: [4303763.226000] islsm_device: Unknown symbol isl_fn_exit_v
May 29 23:14:57 localhost kernel: [4303763.264000] islsm_usb: Unknown symbol unr egister_islsm
May 29 23:14:57 localhost kernel: [4303763.264000] islsm_usb: Unknown symbol fre e_islsm
May 29 23:14:57 localhost kernel: [4303763.264000] islsm_usb: Unknown symbol isl sm_wait_timeout
May 29 23:14:57 localhost kernel: [4303763.264000] islsm_usb: Unknown symbol all oc_islsm
May 29 23:14:57 localhost kernel: [4303763.265000] islsm_usb: Unknown symbol isl _debug
May 29 23:14:57 localhost kernel: [4303763.265000] islsm_usb: Unknown symbol isl sm_bootup_input
May 29 23:14:57 localhost kernel: [4303763.265000] islsm_usb: Unknown symbol isl _fn_exit
May 29 23:14:57 localhost kernel: [4303763.265000] islsm_usb: Unknown symbol isl sm_data_input
May 29 23:14:57 localhost kernel: [4303763.265000] islsm_usb: Unknown symbol isl sm_free
May 29 23:14:57 localhost kernel: [4303763.266000] islsm_usb: Unknown symbol uar t_init_dev
May 29 23:14:57 localhost kernel: [4303763.266000] islsm_usb: Unknown symbol reg ister_islsm
May 29 23:14:57 localhost kernel: [4303763.266000] islsm_usb: Unknown symbol isl sm_request_firmware
May 29 23:14:57 localhost kernel: [4303763.266000] islsm_usb: Unknown symbol uar t_release_dev
May 29 23:14:57 localhost kernel: [4303763.266000] islsm_usb: Unknown symbol isl _fn_enter
May 29 23:14:57 localhost kernel: [4303763.266000] islsm_usb: Unknown symbol isl _fn_exit_v
May 29 23:14:57 localhost kernel: [4303763.267000] islsm_usb: Unknown symbol isl _dump_bytes
```

---

### Post by jml on 2006-05-30
Once you get you card recognized again, try connecting without using encryption first.  If that works, you have validated your hardware.  Then add WEP encryption if needed/wanted.  WPA encryption is not supported out of the box in Ubuntu, but there are multiple posts on this sub-forum discussing it.

Joe

---

### Post by barrmulio on 2006-06-04
well i decided to do a clean install  for dapper, because all my attempts probably screwed up some settings

now, Ubuntu will recognize the device: 
```

Jun  4 00:57:58 localhost kernel: [4294726.917000] usb 4-6: new high speed USB device using ehci_hcd and address 5
Jun  4 00:59:36 localhost kernel: [4294825.001000] usb 4-6: USB disconnect, address 5

```

it is also in the lsusb section: 
```

Bus 004 Device 005: ID 2001:3701 D-Link Corp. [hex] DWL-G120 Spinnaker 802.11b 

```

and also in the device settings it's there

but ndiswrapper returns
```

$ ndiswrapper -l 
prisma02     invalid driver!!
$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9-386/kernel.drivers/net/ndiswrapper/ndistwrapper.ko): Operation not permitted

```

but the device will *not* power up or appear in the Networking section - help....

---

### Post by barrmulio on 2006-06-04
*snip*
since I'm using dapper now, can a mod move this over to the Dapper HW support section?

started over with a fresh ubuntu dapper desktop install and formatted everything - so let's start fresh:
- Dapper updated to latest files, included network-manager, ndisgtk, ndiswrapper
- Dapper finds the device on boot !! auto-setup as eth2 :D 

- In network manager, i see all the wireless networks around me :D 
- However, the link is never established, my router never sees the device even attempting to connect

- In ndisgtk, I can install my driver (prisma02) but it says it can't find hardware
- With ndiswrapper -l, I get a invalid driver error

- Router is setup without encryption for easier troubleshooting, note that i tried some other non encrypted networks around me and I still can't connect.

Now I feel I must be close...

---

### Post by barrmulio on 2006-12-02
thought i'd post the final solution that i finally uncovered today.....
kudos go to the guide  [here]("http://www.linuxforums.org/forum/linux-networking/68864-howto-install-d-link-dwl-g120-ubuntu-linux-6-06-lts-guide.html")

basically the only step missing was to blacklist some items:
```

sudo gedit -e /etc/modprobe.d/blacklist

```

*add*
```

blacklist islsmusb
blacklist islsm
blacklist islsm-usb

```

*save & reboot*


works great now, although all signals are @ 100%

---

