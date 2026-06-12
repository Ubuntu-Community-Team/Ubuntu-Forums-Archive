---
title: "webmin: vpn connection to lan"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by Mr5o1 on 2009-11-11
Hi All, and thanks in advance for reading.

_Synopsis:_
I live in Aus, and use a VPN service (strongVPN) to access hulu. (works a treat!) I have a number of devices in my home (notably a ps3) which cannot add this vpn connection as a network adapter. So I'm trying to use a virtual machine running ubuntu to act as a router, the idea was to bridge (& firewall) the vpn connection and the LAN in the virtual box. Then any other devices on the network could access the internet via the VPN by simply defining the IP of the virtual box as that device's gateway. I could then simply switch back to my regular router as gateway to access the net without utilising the VPN.

_Disclaimer:_
My abilities with a linux based O/S are indeed limited, however I do have some experience (and can find my way around google!). My networking abilities are similarly 'ordinary'.

_What I've done:_
[LIST]
[*]the virtual machine is fine, running ubuntu 9.10
[*]have selected "bridge adapter" in virtual box for this machine
[*]have configured the VPN connection in ubuntu and confirmed that the v.box can access the net via the VPN
[*]have confirmed that the v.box can also access the net via eth0
[*]have confirmed that the ip of the eth0 adapter shown in the v.box, can be pinged by other devices on my network.
[*]have installed webmin
[/LIST]

_The problem:_
I cannot access the net by setting the "default gateway" & dns to the ip of the virtual machine. I assume something is wrong with my configuration of webmin.

I'm not sure what is the easiest way to show you my settings, for now I've uploaded a pic of the firewall config page, if there's another way to give you more info then let me know and I'll beonly too happy to oblige.

[IMG]http://img43.imageshack.us/img43/5527/webminfwall.jpg[/IMG]

So have I set something incorrectly? Is there something else I'm completely overlooking?

Once again, I realise this is a complex problem and I thank you for taking the time to even read this let alone consider a solution.

---

### Post by dmizer on 2009-11-11
First of all, Webmin is not supported in Ubuntu. It may be causing you problems, it may not.

Here's the howto I used for configuring my vmware host to route through my virtual gateway: [http://wiki.untangle.com/index.php/Untangle_Virtual_Appliance_on_VMware#Step_5.2:_Change_Routing_on_Your_Linux_VMware_Host](http://wiki.untangle.com/index.php/Untangle_Virtual_Appliance_on_VMware#Step_5.2:_Change_Routing_on_Your_Linux_VMware_Host)

The howto indicates that you need "root access to the command line". Simply prefix all the commands with "sudo" like so:
```
sudo route -n
```

If you need assistance, please post the results of the above command

---

### Post by wesg on 2009-11-16
> First of all, Webmin is not supported in Ubuntu.

Why is this? It seems to work well on my system so far.

---

### Post by dmizer on 2009-11-16
> **wesg said:**
> Why is this? It seems to work well on my system so far.

The beginning of this wiki article should explain things better than I can: [https://help.ubuntu.com/community/WebMin](https://help.ubuntu.com/community/WebMin)

---

