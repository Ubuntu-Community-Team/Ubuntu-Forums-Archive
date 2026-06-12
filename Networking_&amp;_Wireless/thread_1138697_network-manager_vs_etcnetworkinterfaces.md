---
title: "network-manager vs /etc/network/interfaces"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by sefs on 2009-04-26
Hi there,

Up until intrepid i was using /etc/network/interfaces to manage network interfaces.  

I am not too sure how to do that now with network-manager.

The missing feature I am looking for is that with /etc/network/interfaces  the network seems to start on bootup and was connected even before it landed on my desktop.

With network-manager I only connect to the network after I log into my desktop and the network-manager does its ying yang animation and then says connected.

I'm on ubuntu jaunty 9.04.  Is there a way to fix that?

Thanks.

---

### Post by kevdog on 2009-04-26
Why cant you still use the interfaces file?  The interfaces file is read when the command ifup is run.

---

### Post by sefs on 2009-04-26
I've had to stop using rt73 serial monkey legacy as its no longer being developed...so I am using the inbuilt rt73usb but its no longer responding to the commands that rt73 would respond too ... i.e it does not recognize iwpriv.  So am currently stuck with being dependant on network-manager to do whatever it is it does.

---

### Post by fuego on 2009-04-26
If your adapter works with both network-manager and /etc/network/interfaces using either is just a choice but you can't use both because network-manager loads late in the boot sequence and 'interfaces' will override it. Network-manager will report 'Manual' configuration.

Using just network-manager (after commenting out the /etc 'interfaces' lines for your adapter), you should only have to put your configuration info in once and it will, thereafter, load automatically. I use it and like it because of easier options for loading other ap's. I'm using the 64 bit version of jaunty so your mileage may vary.

---

### Post by fuego on 2009-04-26
sefs,
When I switched to the rt73usb driver for the Asus adapter on my Debian box, I had to move from iwpriv to wpa-supplicant commands, e.g., from iwpriv-ssid to wpa-ssid, etc. I'm surprised you can use your rt73usb driven adapter with network-manager; I never could.

---

### Post by sefs on 2009-04-26
> **fuego said:**
> sefs,
When I switched to the rt73usb driver for the Asus adapter on my Debian box, I had to move from iwpriv to wpa-supplicant commands, e.g., from iwpriv-ssid to wpa-ssid, etc. I'm surprised you can use your rt73usb driven adapter with network-manager; I never could.

It only started working from jaunty for me without having to do a thing.


I had been trying with the below commands
```

wpa-driver wext
wpa-ssid myssid
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk mykey

```
They work but the connection is then dropped every second comes back and is dropped again.

---

