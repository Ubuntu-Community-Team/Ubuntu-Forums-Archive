---
title: "RTL8187 WiFi fails to connect on Ubuntu 10.04"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by hitankar on 2010-07-10
Hi,

My Realtek RTL8187 Wifi fail to connect using WPA security. The authentication window shows up repeatedly every time I try to connect. Please note the password is correct. 

I searched and haven't found a conclusive solutions as of yet. Please help me on how to resolve this problem.

Thanks,
Ray

---

### Post by rogerdg on 2010-07-10
Edit the configuration and verify the following:

SSID must be the name of the network as presented by the device you are connecting to.  Your devices SSIDs must match.

MODE must be Infrastructure or Ad-Hoc and must be the same on all devices on the network.

MTU should be set to Automatic.  MTU can be set to a different value and will sometimes increase the network speed if you adjust it, but it's easier to establish a connection if it's automatic.

Last, verify the password there is a check-box that will show the currently stored password.  Make sure the password is really what you think it is.

If this doesn't work you may need to uninstall and reinstall the network manager.

---

