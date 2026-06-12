---
title: "Compaq 110 &#8210; nearly there with wireless..."
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by engine on 2011-02-09
After installing the recommended driver, I'm now soooo close to having wireless access! but can't work out what to do next.

Here's what the netbook tells me about the components ...

```
> lshw -C network
*-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:5e:04:db:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
```

Network Manager tells me wireless is enabled, and correctly identifies networks in the area.

Then I get the prompt for the wifi password, and after a while the warning

```
Authentication required by wireless network
Passwords or encryption keys are required to access the wireless network {name}
Wireless security: WPA & WPA2 Personal

```

In a different wifi area, of course, it identifies a different type of security.

Can anyone out there help me get that last bit of the way? Hope son abd thanks in advance!

---

### Post by chili555 on 2011-02-09
> Wireless security: WPA & WPA2 PersonalI don't know if it's the driver, Network Manager or wpa_supplicant but the system as a whole has trouble with mixed WPA **and** WPA2 mode. Can you change the router to one or the other but not both?

---

### Post by engine on 2011-02-12
> **chili555 said:**
> I don't know if it's the driver, Network Manager or wpa_supplicant but the system as a whole has trouble with mixed WPA **and** WPA2 mode. Can you change the router to one or the other but not both?

The router offering mixed WPA mode was for public WiFi access, not under my control; also, different environments (for example, at home with a WEP passphrase router) give exactly the same problem :-{

Thanks anyway, and I'm still open to suggestions!

---

### Post by hunansux on 2011-07-18
Hey there I'm not sure if the OP ever found a solution to this problem, but I'm having the same issue!

I'm rather new to ubuntu and linux in general. I'm running 10.4 (I think?) Netbook Remix on a Compaq Mini 110. My brother helped me make sure all the drivers are up to date. I have wifi working as in it sees networks and can connect to some of them... however my home network as well as some of the other networks I regularly use won't allow me to connect. I know the passwords I'm using for those networks are correct. Any help would be greatly appreciated!

---

