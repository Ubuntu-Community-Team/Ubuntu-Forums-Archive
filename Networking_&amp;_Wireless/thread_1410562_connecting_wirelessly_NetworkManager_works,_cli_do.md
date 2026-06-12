---
title: "connecting wirelessly: NetworkManager works, cli doesn't"
date: 2010-02-18
forum: Networking &amp; Wireless
---

### Post by rig99 on 2010-02-18
I have no problems connecting to my network with NetworkManager gnome applet.

I am trying to figure out why I cannot connect to a wireless ap when doing it through the command line like this:

ifconfig wlan0 down
dhclient -r
ifconfig wlan0 up
iwconfig wlan0 essid NETWORKNAME key WEPKEY
dhclient wlan0

After running these commands 20+ times I have yet to receive a DHCPOFFER.

The wep key is exactly the same, I've tried NETWORKNAME in quotes and without, I've tried specifying channel 6, and I've tried specifying the address of the ap. Nothing works. After I run the aforementioned iwconfig line I check to see the status of my wireless connection by running iwconfig with no arguments and it always shows me being "not associated" with any ap. So I am guessing the reason dhclient never receives any DHCPOFFERS is because I can't get associated with the ap. 

So I guess my question is why can't I get associated with my ap via command line but I can via NetworkManager? I can't figure this out.

---

### Post by chili555 on 2010-02-18
Network Manager is pretty deeply embedded in your system, it won't give up control easily. You might get it to work by preceeding your commands with:```
sudo /etc/init.d/network-manager stop
```Depending on your version of Ubuntu, it might be:```
sudo /etc/init.d/NetworkManager stop
```If you want to reliably use the command line, remove Network Manager.

---

### Post by rig99 on 2010-02-18
That didn't seem to change anything. After shutting network-manager down I had same problems. Not associated with any ap and not receiving and DHCPOFFER.

---

### Post by calrogman on 2010-02-19
What kind of security is the access point using? Specifying a key using ifconfig is fine for WEP but you'll need to configure wpa_supplicant if you are using WPA.

---

### Post by theharshone on 2010-02-23
I have this exact same problem. What kernel drivers are you using? I am using the rt2x00 (rt2500usb more specifically) kernel drivers. Before, I was using the legacy drivers which are now discontinued. The legacy drivers worked perfectly with cli but the new drivers do not work on cli. I think this is an ubuntu only problem because cli works fine in OpenSuse (a pretty old version of it too). Plus, I am using wep so iwconfig should work fine.

---

