---
title: "Bluetooth/Blackberry can't maintain connection"
date: 2009-01-29
forum: Networking &amp; Wireless
---

### Post by pmgeahan on 2009-01-29
Folks - 

Bizarre problem here with a new Bluetooth adaptor.  I bought a USB->Bluetooth adaptor for my work PC.  Primarily, I want to use it to run BlueProximity with my Blackberry 8830.  

Here's the issue:  When I first pair the BB with the adaptor, everything works great.  When I leave the area and then return(causing the bluetooth connection to drop and then re-acquire) the BB and the adaptor don't maintain a constant connection.  The connection is dropped and reacquired approximately once a second.  

Checking syslog, I see the following:

```
Jan 29 10:21:36 MACHINENAME bluetoothd[5972]: link_key_request (sba=00:10:60:F1:xx:xx, dba=00:1C:CC:DB:xx:xx)
```
plus notes that it's repeated approximately every 6-7 seconds.

What I can't figure out is why this is happening.  I've paired this BB with many other bluetooth devices, without issue.  I've paired it with other Linux devices without issue.  There are no other error messages in the log related to the bluetooth.

Does anyone have any clue what might be going on here?  lsusb identifies the BT adaptor as:

```
Bus 001 Device 010: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
```

I'm new-ish to the whole Bluetooth thing, so any help would be greatly welcome.

Thanks!

---

### Post by Maheriano on 2009-01-29
Who is your provider?

---

### Post by pmgeahan on 2009-01-29
> **Maheriano said:**
> Who is your provider?

Verizon.

---

### Post by Maheriano on 2009-01-29
> **pmgeahan said:**
> Verizon.

Ding. I called them before picking up a Blackberry with them, they lock down the OBEX portion of the JSR-82 service on their devices. Sprint is the only CDMA carrier I know that leaves it open.

---

### Post by pmgeahan on 2009-01-29
> **Maheriano said:**
> Ding. I called them before picking up a Blackberry with them, they lock down the OBEX portion of the JSR-82 service on their devices. Sprint is the only CDMA carrier I know that leaves it open.

I'm not trying to do OBEX transfers, at all.  I'm merely trying to make a connection, to use BlueProximity.

More to the point, this BB has paired successfully, long-term, with other Linux boxes.  I don't think OBEX is the issue.

---

