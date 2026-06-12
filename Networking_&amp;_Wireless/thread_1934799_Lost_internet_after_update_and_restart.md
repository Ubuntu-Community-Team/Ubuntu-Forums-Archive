---
title: "Lost internet after update and restart"
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by sdegan on 2012-03-02
Today I downloaded some updates from apt and restarted my box. When it came back up, I no longer had the ability to connect to the internet. I'm really confused about what's going on. 

eth0 is a static IP with dhcp3-server giving out IPs on my internal network

eth1 is connected to my WAN and is able to get a DHCP lease from the DHCP server it's connected to.

Route shows only 1 gateway pointing towards eth1. IP forwarding is enabled. netstat shows 0.0.0.0 using the default gateway specified by the DHCP server, 172.20.80.1. 

I can't ping the gateway, I can't ssh into the box using the assigned IP address, and I can't access any network devices. 

What's even stranger is I no longer see any network connections in the nm-applet. I have ifupdown disabled, but I used to at least see auto eth0 and auto eth1. Those are missing now as well. 

Does anyone have any insights which I could use to fix this? I'm pretty stumped. I can post whatever information is needed, just let me know.

---

### Post by Iowan on 2012-03-02
From a terminal, does **ifconfig -a** show IP addresses for the interfaces? If not, check **sudo lshw -C network** for information about the interfaces.

---

### Post by sdegan on 2012-03-02
ifconfig -a does show an IP address for both eth0 and eth1. eth0 shows the ip address that I specified in /etc/network/interfaces and eth1 shows an ip address from my WAN's DHCP server. I'm doing this in my laboratory on campus so I called our IT department. They confirm that my computer is successfully leasing an IP from their DHCP server. 

When I do a lshw command, I do see the two network cards listed and they are NOT showing up as DISABLED. (I do have one virtual adapter that shows up as well, but is flagged disabled)

If you want, I can try and find a way to copy the output into a text, save it to a USB and then transfer it to here, if that would help.

---

### Post by sdegan on 2012-03-07
I ended up formatting my computer and reloading with 10.04. This solved the problem.

---

