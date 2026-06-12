---
title: "DHCP not working.  Not sure if its me or the network."
date: 2009-12-20
forum: Networking &amp; Wireless
---

### Post by lorderico on 2009-12-20
Hello,

I am running 64-bit ubuntu 9.1 on a Lenovo T-500 thinkpad, and I am trying to connect to my dorm's network, either wirelessly or wired.  I installed wicd after the network manager didn't give me any information.  When I run dhclient on either the wired or wireless setup, it always times out, giving me a "No DCHP offers".
I have vista dual-booted on my machine, and vista has essentially the same problem (cannot get dhcp).  However, My desktop machine running 9.10 is able to get dhcp from the wired network (the same exact port and ethernet cord).  And, as far as i know, no one else has had a problem with dhcp.  I am not sure whether this is a problem with my computer's hardware, software, or a problem with the network.

Any suggestions would be appreciated.

Eric

---

### Post by lorderico on 2009-12-20
Ok, nevermind, I called tech support and they said the network is down.  The strange thing is, I am using the network right now to browse the internet.  Hmmm, must only be for new connections...

Eric

---

### Post by slakkie on 2009-12-20
Perhaps their DHCP server is down?

You could analyze traffic with wireshark and/or tcpdump. Have a look at their man pages for usage.

What happens when you use a static IP (eg. the IP you get from windows: ipconfig /all)?

---

### Post by lorderico on 2009-12-20
I was able to look at the traffic with wireshark, but I haven't a clue how to interpret all of the packets.

Eric

---

### Post by slakkie on 2009-12-20
You need to see traffic going like this:

You: DHCPDISCOVER
Server: DHCPOFFER
You: DHCPREQUEST
Server: DHCPACK

If you only want to see only DHCP traffic, listen only on ports 67,68.

---

### Post by lorderico on 2009-12-20
ok, it works for the machine I am running on right now.  Now I just have to get wireshark over to my laptop and check it out.

Eric

---

### Post by jamesisin on 2009-12-20
If appropriate, you should mark this thread as SOLVED.

---

