---
title: "no connction to LAN"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by msio on 2011-01-06
Hi
I have ubuntu 10.10 installed on asus u50vg. I have router asus wl500gp and wl500w. My wl500gp is connected with ISP (to WAN). One Port of this router is connected to thw WAN port of router wl500w.If I wanna connect my laptop to wl500w.I can't connect to the roiter wl500w. There is no connection via cabel or wifi. but with the windows I cann connect to this router. I dont know why it isn't working with the linux. but if I connect to the WL500gp(with ISP ) .it's working properly via wifi or cabel. On the router wl500w I changed default LAN IP from 192.168.1.1 to 192.168.0.0 and how I mentioned above. with windows it's working
what's the problem?
please help me
thank you :)

---

### Post by PatchesTheCaveman on 2011-01-06
Instead of plugging into the WAN port of the second router, plug into one of the normal ports, or the "uplink" port if it has one.  (Most modern routers can automatically detect an uplink connection and no longer have a special port.)

If you plug into the WAN port of the second router it firewalls all the devices connected to the second router from the first, like you'd want it to do if it were plugged into an Internet connection.  By plugging into one of the LAN ports instead, you just join the the two switches and bypass the firewall.

---

### Post by m4r1u52 on 2011-02-04
I have the similar problem with Asus WL500W. Running Windows 7 (running on Acer Ferrari One) I can make WiFi connection to the router but with Ubuntu 10.10 on Dell E6500 I can not. In this case it looks like there is some authentication problem. The authentication method that is set up on the router is WPA-PSK/WPA2-PSK with AES encryption. I am pretty sure that I could connect to the router if no authentication method was set up. But with WPA2 it just doesn't work on Ubuntu.

---

### Post by m4r1u52 on 2011-02-11
From a few days the problem no longer occurs :-) . But I don't know why. :-(

---

