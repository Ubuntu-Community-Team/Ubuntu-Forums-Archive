---
title: "DHCP dosen't work after install."
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by dr_livsey on 2013-03-25
Hi!

    My problem is the following. During installation everything is fine. There is network and installer downloads the latest packages from the internet. But after install there is no network.
    I checked "ifconfig" and /etc/network/interfaces. There definitely is "eth0" among devices. "ifconfig eth0 up" does nothing. "dhclient eth0" hangs up for relatively long time with no result.

/etc/network/interfaces contains
auto eth0
iface eth0 inet dhcp

I tried commenting these two lines out and using "ifconfig eth0 up", "dhclient eth0" to run DHCP manually with no result.

I tried "Ubuntu server 12.04", "Ubuntu server 12.10" and even current version of "Debian" with same results. I.e. during installation there is internet connection. But no connection afterwards. There is one difference: in Debian attempts to get IP address are expressed with several lines "DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval XX" but in Ubuntu with no output.

Could one, please, explain me what I should do?

---

### Post by chili555 on 2013-03-25
We wonder if there is a proper driver associated with the hardware. Please run:```
ifconfig
```Is there an eth0? If not, the driver and hardware aren't associated. Let's find out what driver you need and try to figure out why it isn't loading correctly post-install:```
lspci -nn | grep 0280
```I doubt you want a potentially changing dynamic address on a server, so I'd suggest, once we get the driver working, that we set up a static IP address.

---

### Post by dr_livsey on 2013-03-26
> **chili555 said:**
> We wonder if there is a proper driver associated with the hardware. Please run:```
ifconfig
```Is there an eth0? If not, the driver and hardware aren't associated. Let's find out what driver you need and try to figure out why it isn't loading correctly post-install:```
lspci -nn | grep 0280
```I doubt you want a potentially changing dynamic address on a server, so I'd suggest, once we get the driver working, that we set up a static IP address.

First of all, thank you for your assistance! I've done what you asked me about and a few more things. Results are the following.

1) "ifconfig" gives exactly two interfaces: "lo" and "eth0". And it's output matches with what is written in /etc/network/interfaces. Yes, "eth0" presents there.

2) "lspci -nn | grep 0280" gives nothing as network adapter is 8139. When I invoke "lspci -nn | grep 8139" it shows me that adapter.

3) I took different router, replugged ethernet cable there and run "/etc/init.d/networking restart" - everything is perfect. DHCP works.

4) I checked original cable/network with different computer with WindowsXP OS - DHCP also works there.

5) I tried changing MAC address with "ifconfig eth0 hw ether xx.xx.xx.xx" when "bad" cable/network is attached. Checked if it is really changed with "ifconfig". Run "dhclient eth0" Result is the same - it thinks for about a minute and fails.

6) With original cable DHCP (and internet as a result) works only during install time. 

7) I can't change DHCP to static addressing as a network where it works so strange is office network with many computers. And this computer was a file storage, it hosted several servers and VPN tunneling until HDD failure. And now I try to resurrect it with so unexpectable trouble at the very beginning.

8) It worked perfectly before HDD failure with exactly the same cable and in the same network running Ubuntu server for very long time so Ubuntu version changed from 9.04 to 12.04 during it's nonstop work if I'm not mistaken.

9) I compared "good" and "bad" ethernet cable pinouts. They perfectly match also.

10) I tried different cable from those "bad" network - the same no connection after install and normal during install.

---

### Post by WhaleVPS on 2013-03-26
Can you get an output of "ps -ef | grep dhcp"?

---

### Post by chili555 on 2013-03-26
> I took different router, replugged ethernet cable there and run "/etc/init.d/networking restart" - everything is perfect. DHCP works.I'm confused, I guess. Doesn't this suggest it's the router and not the NIC?

---

### Post by Iowan on 2013-03-26
It's a bit far-fetched, but check **route -n** and firewall settings. I'm wondering if box is "too secure".

---

### Post by dr_livsey on 2013-03-29
Dear All, 

I'm very sorry for misinforming you. It must be it really was a problem of netowrk but not a computer. At the moment we experience the same or very similar problem with a few more computers in the network. So I do believe I'll have to replace the main router.

But it really was very strange that computer had internet during install but didn't have afterwards.

---

