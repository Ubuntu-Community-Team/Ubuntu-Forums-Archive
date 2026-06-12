---
title: "Bluetooth modem: Mobile Broadband does not appear in Network Manager"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by Robert S on 2010-12-14
I have just installed 10.04 LTS on an eeepc.  I have managed to get wireless broadband working through my Nokia E71 over a bluetooth connection by inserting my bluetooth dongle, running `rfcomm bind yes' then running `pppd call <chatscript>', using the /etc/bluetooth/rfcomm.conf and the instructions on a number of sites (eg "The old, hard way" on [https://help.ubuntu.com/community/BluetoothDialup]("https://help.ubuntu.com/community/BluetoothDialup")).

I would like to simplify this by making Mobile Broadband available through Network Manger.  When I right click on the applet icon, there is no option to enable Mobile Broadband.  I have set up a wireless broadband account (under Edit Connections).

I've tried fixing this by running the Blueman applet and selecting `connect to Dialup Network', but I get a dialog saying `CDMA or GSM not supported'.

Can anybody help here?

---

### Post by Robert S on 2010-12-14
I seemed to have cracked this one - see this wiki with my addition at the end on automation: [http://blog.chewearn.com/2010/09/30/ubuntu-lucid-lynx-mobile-broadband-tethering-to-nokia-n95-part-2/]("http://blog.chewearn.com/2010/09/30/ubuntu-lucid-lynx-mobile-broadband-tethering-to-nokia-n95-part-2/")

---

