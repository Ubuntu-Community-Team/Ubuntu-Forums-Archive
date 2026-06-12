---
title: "Is NAT routing to blame for most of the Wifi issues?"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by fixitdude on 2012-04-05
Do you guys think it's NAT routing that might be the problem?

I've been looking into this a little and it looks like the NAT routing stuff doesn't actually check the packet integrity and that may be a big problem with wireless.

Example would be if the close bit is set because of a transmission glitch, now the NAT routing code thinks the socket is done and stops passing packets on to the user end.

Some of you know more about this and I'm hoping you can show how small bit errors in transmission can't screw up a TCP connection.

Another thing I run into is that you can still ping with pretty good speed but yet TCP can't seem to get a simple short web page to get through the sometimes missing packets via "crappy" or on the edge wireless connections.

I'm just trying to figure out how this can happen when TCP should be retrying and getting the packets through no matter what the connection looks like.

---

### Post by fixitdude on 2012-04-07
It looks like the problem comes from them using the checksum to check the TCP packets.

Checksum is susceptible to single bit error corruption of data, that's why they came up with CRC.

It looks like the NAT routing code only uses the checksum to check if the packet is valid.

If a single bit gets corrupted or two bits, and if it happens to be the "close" bit, then NAT thinks that TCP session is done and no longer forwards the packets to the user down the line.

Anything sent to that port number from the internet side is then dropped, and TCP at the user end (think browser) just sits waiting for anything to come in for it's port number.

It's like firewalling TCP in the middle of a connection.

This is why when you have a borderline wireless connection, you can sometimes stop a web page that's half loaded but sitting there, then hit return (or reload) and the page will suddenly come in full - because the connection got better for that second and everything made it and no important bits were trashed.

TCP won't open a new port to try again, it keeps trying over and over using the same port, just sending more packets.

So is this a good theory?

I think this is coming up as a problem now because before this all networks were wired and single bit errors were hard to get. With a wire you either get bits or you don't.

What would be the fix?

Is there something the developers / project support people of NAT could do?

---

