---
title: "help with networking setup in our office - port aggregation and managed switches"
date: 2012-07-04
forum: Networking &amp; Wireless
---

### Post by greavette on 2012-07-04
Hello,

I realize that this isn't an Ubuntu type question...so if there is a more appropriate forum to place this post within these forums, please let me know.

We are re-working our small office computer/networking layout and I'd like to understand some things when I work on this.  I'd also like to ensure our Ubuntu Servers (running Proxmox) have the best throughput from each workstation.

Our lab had used a lot of small switches in each room. These switches would then connect to a bigger switch in our Server room. It was a hassle when computers had networking issues trying to track down which cable/switch was in trouble.  So I'll be implementing a starfish pattern with regards to networking where we have two large switches in our Server room and we'll have Cat6 network cables to each hardware (printers and workstations) from these switches. Like I said, network throughput is important to us so I think port aggregation is important from our Ubuntu Servers to these managed switches.  

[LIST]
[*]What managed switches would you recommend we buy?  I figure we'll need 48 ports in each. This will ensure that one switch can run all hardware in our network.
[*]How important is it to use a starfish pattern...or is it all right to use connect hardware to unmanaged switches throughout the office?
[*]So if I use Port  Aggregation on our Ubuntu Servers and setup each switch to accept the bigger throughput, and I'm using 2 bonded network cables from my server to the switch...do I split the two network cables from my server into each switch?  
[*]As I mentioned, each workstation in our office has one network cable connected to one of our switches in our server room.  Am I improving throughput by having bonded nics on my Server from the switch from the data sent from these workstations?  
[*]Related to the above point..I'm trying to solve for having a larger throughput on our network to our Servers, but also I'm trying to solve for if one switch dies or has issues, my network isn't completely dead.  I know that workstations connected to the dead switch won't work so does it make sense to use two switches and split how my servers are connected to each switch? Or should I just use one switch and have the second one ready to be dropped in when required.
[*]Is there a way to improve throughput by not using a managed switch? 
[/LIST]

Any advice you'd like to impart on how I should setup this network are all welcomed.

Thank you.

---

### Post by dino99 on 2012-07-04
Some urls about hardware & ubuntu:

[https://wiki.ubuntu.com/HardwareSupport/](https://wiki.ubuntu.com/HardwareSupport/)
[https://help.ubuntu.com/12.04/installation-guide/i386/hardware-supported.html](https://help.ubuntu.com/12.04/installation-guide/i386/hardware-supported.html)
[https://help.ubuntu.com/community/NetworkDevices](https://help.ubuntu.com/community/NetworkDevices)

---

### Post by lisati on 2012-07-04
*Thread moved to **Networking & Wireless**.*

Whew! And I only have five devices able to be hooked up to my home network (eight if you count a handful of spare modem and router type gadgets)

---

