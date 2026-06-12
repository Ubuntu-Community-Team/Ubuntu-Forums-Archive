---
title: "Need help configuring ethernet w/ Linksys router"
date: 2010-03-22
forum: Networking &amp; Wireless
---

### Post by temudjin on 2010-03-22
Hello!

I'm trying to configure my new ubuntu 9.10 install to work with a linksys router which is also connected to a Windows laptop.

So --> BROADXENT DSL Modem --> LINKSYS BEFSR41(ver.4.3) Cable/DSL Router --> Windows XP Laptop / Ubuntu Desktop.

I can connect to the internet directly through the modem with the Ubuntu Desktop and with the modem, or modem-->router on the Windows laptop.  **I have a Static IP** and the router has been configured with the static ip address and works fine with the windows box.

I've configured /etc/network/interfaces  
as such:

---
auto eth0
iface eth0 inet static
address 72.1.154.6
netmask 255.255.255.0
network 192.168.1.0
broadcast 72.1.154.255
gateway 72.1.154.1

*What's missing?*  What do i need to do so that Ubuntu plays nice with my router?  Or is something else going on?

**Thanks for any and all help.**  I'm cracking back into using Ubuntu again after a long journey through the desert of Windows, I need both machines running for now until i have my ultimate solution of virtual windows on a better machine running Ubuntu, but first things first, getting them both online together, and networked if possible!

---

### Post by gordintoronto on 2010-03-22
The IP address of a computer behind the router should be something like
192.168.1.14 (only the last number changes from computer to computer.)

The router is the only device which should be at the static IP address assigned by your ISP.

To control what data goes where, use "port forwarding." Have a look at the router manual for details.

---

### Post by theozzlives on 2010-03-22
> **gordintoronto said:**
> The IP address of a computer behind the router should be something like
192.168.1.14 (only the last number changes from computer to computer.)

The router is the only device which should be at the static IP address assigned by your ISP.

To control what data goes where, use "port forwarding." Have a look at the router manual for details.

What he said. I have all my computers setup dynamic and have the router act as a DHCP server. I assign the IPs in the router. The only thing you need is the MAC address which can be obtained with ifconfig, in Windows ipconfig /all.

---

