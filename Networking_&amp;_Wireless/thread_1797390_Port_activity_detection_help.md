---
title: "Port activity detection help"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by Mattaus on 2011-07-05
Hi all,

Apologies if this is in the wrong section, please move this post if there is a more appropriate place for my ramblings.

Long story short but can someone please provide me with some information or a point in the right direction on how to use Wireshark, from the command line, to detect port activity on a closed port?

I need to test if a firewall port on a firewall sitting between 2 servers, has been opened but BEFORE the port has been set up on the target server. The idea is that Wireshark can tell me if something is trying to get through on the port or not. If Wireshark shows attempted activity then I can assume the firewall has been opened correctly.

If Wireshark is inappropriate for this task could you possibly recommend what would be a good way to go about this?

I am definitely NOT a network person, so any help or useful links would be greatly appreciated.

Regards,

- Mattaus

---

### Post by jmoorse on 2011-07-12
tcpdump is the way to go.  You can write to a file over a long period of time and review the results with wireshark.

Example: udp port 53

sudo tcpdump -i eth1 udp port 53 -vvvv -s0 -w capture.pcap

Another example: ip 10.1.2.3

sudo tcpdump -i eth1 host 10.1.2.3 -vvvv -s0 -w capture.pcap

I hope that is helpful.  I recommend you man tcpdump b/c there are a ton of other options

---

### Post by Mattaus on 2011-07-12
Hey thanks...I'll have to look into it and like you said, read the man page.

I'll let you know how I get on.

Cheers.

---

