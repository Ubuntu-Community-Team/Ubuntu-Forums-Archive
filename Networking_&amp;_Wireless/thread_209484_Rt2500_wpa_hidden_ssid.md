---
title: "Rt2500 wpa hidden ssid"
date: 2006-07-05
forum: Networking &amp; Wireless
---

### Post by Michael_aust on 2006-07-05
I am having troubles setting up my wireless network.  Ubuntu si going on my sisters machine and I am testing the wireless before I install , as I do not want to have to go through the job of installing ME again.  I am intending to use dapper.

I wireless usb connecter uses the rt2500 chipset.  It gets loaded on boot.  I have followed the instructions on; [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500)

for setting uop the interface.  The only difference is mine does not come up as ra0, it is rausb0, so I changed those accordingly.

I tried all of the examples shown but none of them worked, the closest I got was with using:

```
auto ra0 
iface ra0 inet dhcp
pre-up iwconfig ra0 essid " myssid "
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=11
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=TKIP
pre-up iwpriv ra0 set WPAPSK="A shared key"
pre-up iwpriv ra0 set TxRate=0
```

The other examples just bombed out on me, however with the above it appears to start trying to get a dhcp reply, it tried about 7 times then stops, saying that it could not get a dhcp reply.

I have ssid broadcast disabled and use WPA with PSK string passphrase.

I have absolutly no idea what I need to do to get it to connect.  I have read that there are problems with the rt2500 driver included in dapper and that I should use the cvs driver instead, obviously this is not not really an option as the wireless is the only means on getting the connection to that machine, so I would need to download build-essentials and its corosponding dependencies.

Does anyone have any solutions as to how I can get this to connect, or possibly know what is wrong.  It is abviously kind of working as it must be seeing the router as it is trying to connect to it.

Michael.

---

