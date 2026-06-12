---
title: "Lost Network"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by hugh v. angle on 2009-11-07
I upgraded from 9.4 to 9.10 a couple of weeks ago and everything worked as before.

Yesterday I reconnected my computer from the router and directly connected it to the modem.  I lost the network. A red x now marks my network icon. 

Steps taken to diagnose the problem:

a) System monitor indicated no send/receive activity.
b) ifconfig indicated no IP address.
     [entered 'ifconfig eth0 <my ip address>'. Got send/receive activity, but no network]

c) Directly connected modem to second computer. Able to connect to internet.
d) Booted Eclipse (have dual boot arrangement). Eclipse unable to connect to internet
      [Dell support was able to connect Eclipse to network. The solution was to change     the NIC device property 'Speed and Duplex' from 'Auto Detect' to '10MbpsHalfDuplex'.  I suspect that I encountered a different cable speed/duplex when I switched from the
router and directly connected the NIC device to the modem.  However, when I returned the computer to this arrangement, Ubuntu was unable to connect, but Eclipse was successful]

If I am forced to live with Eclipse, then I will probably kill myself.

Hugh Angle

---

### Post by Iowan on 2009-11-07
Some modems require a reset (cycle power) before they will recognize a different MAC address... but if it worked on the second computer???
**ifconfig -a** shows a valid IP address (not 169.254.X.X)? If you have a valid IP address, can you **ping** the modem?

---

