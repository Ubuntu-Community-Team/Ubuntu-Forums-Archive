---
title: "Aircard ICS"
date: 2009-12-18
forum: Networking &amp; Wireless
---

### Post by n.brenner on 2009-12-18
THE EASY WAY I FOUND TO ICS YOUR USB WIRELESS/BROADBAND DEVICE

SETUP---I dont need routing as my router does that.
THIS IS USING A SMALL AND UNUSED BOX AS A GATEWAY AND GETS RID OF WINDOWS
1: Open net manager and select wired: Auto ethx: edit:
   set for manual and give it an address of 192.168.0.1/255.255.255.0/0.0.0.0
  mark connect automaticly and system settings.-----OK

This connects you from the computor to the WAN input of the router.

2:  Make sure your Broadband/wireless usb device has connected to its service.
    (in my case it is a Sierra Aircard 595U)

3:  This next step is what NOBODY has mentioned or figured out till now.
    Open a Terminal window (Applications > Accessories > Termminal).
    type in lsusb.  It will list all the usb ports and the "bus" the device is on.
    this will tell you where your usb device is (busx)

OK now were set to go

4:  IN TERMINAL
    sudo iptables -A FORWARD -i ethx -o busx -s 192.168.0.0/24 -m conntrack --ctstate NEW -j ACCEPT
    sudo iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
    sudo iptables -A POSTROUTING -t nat -j MASQUERADE
This configures NAT

5:  IN TERMINAL
    sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
    sudo gedit /etc/sysctl.conf
      look for "FUNCTIONS PREVIOUSLY FOUND--"
      Remove "#" from net.ipv4.ip_forward=1
      Add net.ipv4.conf.default.forwarding=1
          net.ipv4.conf.all.forwarding=1
      save/exit
THIS ROUTES THRU THE MACHINE( ie SHARES THE USB DEVICE)

6:  IN TERMINAL
    sudo apt-get install dnsmasq

YOU ARE GOOD TO GO

MY PROBLEM IS WHEN I TURN THE MACHINE OFF FOR THE NIGHT AND TURN IT BACK ON,
I HAVE TO REINSTALL THE IPTABLES (STEP 4)
can anybody figure a way around that too

also im sure with a little tweaking and address changing this can work
for 2 or 3 computors

i Have 11  combo wired and wireless with Windows and Ubuntu

---

### Post by linux6994 on 2009-12-18
On the eth0 port under the IPV4 settings in the Network Manager select "shared to other computers" vice DHCP or Static that is all that needs to be done.

---

