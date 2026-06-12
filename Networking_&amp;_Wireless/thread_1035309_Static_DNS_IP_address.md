---
title: "Static DNS IP address"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by sani07 on 2009-01-09
Hello

Please, let me know what command to use to find out my current IP addresses for DNS server and default router.

and than

How to set static IP address for DNS server and default router.

---

### Post by stchman on 2009-01-09
> **sani07 said:**
> Hello

Please, let me know what command to use to find out my current IP addresses for DNS server and default router.

and than

How to set static IP address for DNS server and default router.

In a terminal type:

```
ifconfig -a
```

This will give you the IP address that has been assigined to your PC via the router.

If you want to get the IP address assigned to your by your ISP then do the following:

[https://addons.mozilla.org/en-US/firefox/addon/3372](https://addons.mozilla.org/en-US/firefox/addon/3372)

This addon will supply that information.

To set a static IP address for your PC go to System--->Administration--->Network

There you will be able to specify an IP address.  I recommend you put one outside the DHCP range of your router.  Say that your router supplies IP address 192.188.1.100 to .150 then specify an IP of 192.168.1.175.

Use a subnet mask of 255.255.255.0 and your gateway is your router's IP address like 192.168.1.1.

Hope this helps.

---

### Post by namdung on 2009-01-09
To view current IP settings
In terminal
```
ifconfig
```

To edit IP settings
```
sudo nano /etc/network/interfaces
```
U may also use **gedit** instead of **nano**, but *gedit* must first be installed.
```
sudo apt-get install gedit
```

To edit DNS settings
```
sudo gedit /etc/resolv.conf
```

---

