---
title: "Berry4All Tether Connects, But No Network"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by OrionXIII on 2010-08-22
Okay, I've managed to get Berry4All installed and connected. I have an IP address and the ppp protocol appears to be doing its thing according to the Berry4All window.

Except...Firefox doesn't see the network.
Even from terminal, ping gives nothing...

Berry4All Shows:
Local IP: 25.193.158.209
Peer IP: 169.254.1.1
DNS Server: 10.177.0.34
Alt. DNS: 10.166.71.132
Connection Info shows 0 on the speeds and transfered except Max Speed which is 2/3.
Connect time is clocking up.
(This matches the information shown under SYSTEM->ADMINISTRATION->Network Tools under Network device: Modem Interface (ppp0))

Route from a terminal shows this:
Destination  Gateway   Genmask         Flags   Metric   Ref   Use Iface
169.254.1.1     *      255.255.255.255   UH        0        0        0  ppp0

But ping mail.yahoo.com shows:
ping unknown host mail.yahoo.com

Even ping 209.191.92.114 gives:
connect: Network is unreachable

So...what have I jacked up? Helllp! LOL

Thank you in advance...

Orion

---

### Post by OrionXIII on 2010-08-22
And now for some reason whenever I try to connect I just get
PAP authentication succeeded.
Could not determine local IP address
Connect time 0.1 minutes.
Sent 124 bytes, received 100 bytes.
Connection terminated.

And that's it.

WTF?!?

Orion

---

