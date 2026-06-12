---
title: "Mythbuntu Can't Find HDHomerun Tuners"
date: 2015-04-29
forum: Mythbuntu
---

### Post by chris_g2 on 2015-04-29
[COLOR=#333333][FONT=Arial]'m sitting here, typing this on a WIndows 7 PC which is currently connected to and accurately displaying TV from my HDHR Prime.[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]I have a home server with a mythbuntu VM. For some reason, the mythbuntu machine is able to ping the HDHR, but when using the command:[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]hdhomerun_config discover[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]we get the response of "no devices found"[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]Tons of google searching, but I can't pin point where there's an issue. Because I can't locate the devices, I am unable to connect to them through the mythtv-setup.[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]Any idea what may be wrong?  I've read on another forum that there may be issues with a VM and different subnet masks, but I checked and they're both set to 255.255.255.0.  I originally had an Ubuntu Server VM installed which was working fine and easily located the HDHR Tuners, but I took it down to try Mythbuntu which I am now struggling with.

Any help would be appreciated.

Thanks.[/FONT][/COLOR]

---

### Post by mathog on 2015-04-29
Do you have a firewall running?  If so, is it blocking packets from that device?  Not the "ping" packets, but the ones to/from the ports used for controlling the video.

---

### Post by chris_g2 on 2015-04-29
I have nothing manually configured.  

All of my devices are attached to a TP-Link 24 port switch.

Besides the out of box settings, I have not touched a thing.....yet.

---

### Post by chris_g2 on 2015-04-29
It's gotta have something to do with the way the KVM hypervisor configures the network connection.

I'm just struggling to get the VM to be able to recognize things on my network, on vice versa.  I can connect to the outside world using DHCP, but that doesn't solve these problems.

---

### Post by uteck on 2015-04-30
I had the same issue, could not discover it on my laptop, but the server running MythTV could, so I was not too worried.  I recently reformatted and reinstalled my laptop, and just tried and now it works.  Might have been a firewall setting in the old lappy, not sure if I had that enabled or not.

---

