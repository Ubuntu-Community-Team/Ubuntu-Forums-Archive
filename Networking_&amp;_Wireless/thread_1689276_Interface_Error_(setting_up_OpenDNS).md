---
title: "Interface Error (setting up OpenDNS)"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by Nbala on 2011-02-16
[LIST]
[*][FONT=Garamond]Im trying to setup OpenDNS on my wireless connection.[/FONT]
[/LIST]

[LIST]
[*][FONT=Garamond]I followed all the steps requested in the OpenDNS site, but reached failure at a certain step[/FONT]
[/LIST]
[FONT=Garamond]$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
 $ gksudo gedit /etc/dhcp3/dhclient.conf
 # append the following line to the document
 prepend domain-name-servers 208.67.222.222,208.67.220.220;
 # save and exit
***$ sudo ifdown eth0 && sudo ifup eth0***

(NOTE: Im on wireless and it is set up as eth1- according to Wireshark interface list, which BTW shows the **wireless** tower-icon beside eth1, and eth1 is the only active interface. eth1 sounds like an ethernet interface, Im not sure why its coming up like this. **wlan0** and **wlan1** show up as unrecognized or unconfigured in a terminal **ifconfig**

@  $ sudo ifdown eth1 && sudo ifup eth1 - I then receive the msg:
**"ifdown: interface eth1 not configured"**

So I checked the interfaces file to see what this 'not configured' pertains to-
***interfaces*** file in: *** etc/network*** is this:
[B]
auto lo
iface lo inet loopback[/B]

I am not sure why the **wireless** interface is listed as **eth1 **
Any ideas on how to set this up correctly would be very much appreciated, Im a novice/intermediate to linux so there are many gaps in my knowledge-base![/FONT]  request..)

[FONT=Century Gothic]***:)Thank you for all previous and hopefully future help!***[/FONT]:)

---

