---
title: "Transmission Port-forwarding"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by SPARTAN-118 on 2009-06-21
Hi, I have a 2-Wire router/modem/access point from Bell, and would like to forward a port for use with Transmission.

I used the instructions in [http://www.portforward.com/](http://www.portforward.com/) for my router, however, I only made it to step 4, where you select the computer through which you are forwarding the port.

The problem is I have no idea which "computer" to select from the drop-down list. I am trying to forward the port to (or through?) the laptop, not the computer connected to the 2-Wire.
There are multiple "computers" listed, which are (in order):


[LIST=1]
[*]The computer which the 2-Wire is plugged directly into;
[*]ubuntu;
[*]192.168.2.12;
[*]192.168.2.13;
[*]Wii;
[*]NintendoDS;
[*]ubuntu (again)
[/LIST]
Now, I have no idea why ubuntu is listed twice, but I don't want to screw up my internet again (I've [tried] to do this before with a D-Link router) by using the process of elimination.
I can easily eliminate the Wii and NintendoDS, though I'm not so sure of the first one, the one that's directly plugged into the 2-Wire (or is it vice-versa?).

Can somebody please tell me which one of these I'm supposed to select? I'm tired of all my bit-torrent downloads either idling (aka FAILING) or being super slow.

Also, Step 5 in portforward's guide (found: [http://portforward.com/english/routers/port_forwarding/2wire/2701HG-G/default.htm](http://portforward.com/english/routers/port_forwarding/2wire/2701HG-G/default.htm)) seems a little confusing, with the TCP/UDP stuff though I'm pretty sure I use/have TCP. Any help in this area would also be welcome.

Thanks,
SPARTAN-118.

---

### Post by evermooingcow on 2009-06-21
From what I see in the guide I think you first want to define a custom application.

Name: (any)
Protocol: TCP
Port range: whatever transmission is set to use
Timeout: use default given
Map to host: same as the port range above. I think entering "Default" or leaving it blank works.

Then select the computer that you run transmission on from the list and add the newly created application profile to the hosted list.

---

