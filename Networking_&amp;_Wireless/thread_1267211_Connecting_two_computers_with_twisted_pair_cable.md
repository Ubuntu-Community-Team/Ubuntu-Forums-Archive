---
title: "Connecting two computers with twisted pair cable"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by Nevon on 2009-09-15
I'm trying to connect two computers with a twisted pair cable in order to transfer some rather large files (over wireless the speed pretty much maxed out at 250kbps), however, simply plugging the cable in does not seem to work.

Is there something special I have to do in order to be able to send files over that connection? Do I have to disable the wireless network?

---

### Post by issih on 2009-09-15
Assuming you are using a crossover cable then its just a matter of setting an IP address on the same subnet for both machines..

You do NEED a crossover cable if you are connecting directly from one machine to another without a hub/switch or router between them.

Crossover cables look exactly like normal network cables, but one pair of wires within them are wired up differently, so they are not interchangeable.

Hope that helps

---

### Post by jml on 2009-09-15
Standard CAT5 network cable will not work for a direct computer to computer connection.  You need to use something called a crossover cable.  Its basically a regular CAT5 cable with two of the wires reversed.  This will provide the physical connection.  (Alternatively, you can plug both computers into a multi-port router.)

Next you have to set up networking on both computers.  That,
unfortunately I do not know how to do.  Hopefully, someone will be able to help you complete the process.

A low tech way to do a one time transfer would be to download the files to the biggest thum drive you can get your hands on.  I have seen them as large as 16 Gig.  Then physically transfer the drive to the other computer and upload them.

Joe

---

### Post by tkoco on 2009-09-15
As pointed out already, you will need a cross-over network cable. Some caveats though, make sure the cable is CAT5-E or CAT6 rated, have the faster computer on auto negotiate, have the other one maxed out on speed, and make sure that the port is set to Full Duplex (assuming that you can set the duplex). Lastly, as also pointed out, make sure both computers are on the same IP segment (like 192.168.12.12 & 192.168.12.13). Also, don't forget the software needed to transfer between the computers. FTP, Rsync, or SAMBA are examples.

> **Nevon said:**
> I'm trying to connect two computers with a twisted pair cable in order to transfer some rather large files (over wireless the speed pretty much maxed out at 250kbps), however, simply plugging the cable in does not seem to work.

Is there something special I have to do in order to be able to send files over that connection? Do I have to disable the wireless network?

---

### Post by Nevon on 2009-09-15
Twisted pair == crossover cable. 

Anyway, I've gone with transferring through the router instead - as that is fast enough for my needs (~7-8mbps) and there's no need for endless manual configuration. However, I might come back to this thread if I need higher speeds. As for transferring methods, I'm currently using SMB. But I could use SSH (or SCP, I suppose) if that would give me any higher transfer speeds.

---

### Post by tkoco on 2009-09-15
Glad to hear that you have it going. I typically deal with gigabytes of info which have to be sent within minutes and you need all the transfer speed that the computer(s) can muster.

> **Nevon said:**
> Twisted pair == crossover cable. 

Anyway, I've gone with transferring through the router instead - as that is fast enough for my needs (~7-8mbps) and there's no need for endless manual configuration. However, I might come back to this thread if I need higher speeds. As for transferring methods, I'm currently using SMB. But I could use SSH (or SCP, I suppose) if that would give me any higher transfer speeds.

---

### Post by CoolHand on 2009-09-15
> **Nevon said:**
> Twisted pair == crossover cable. 

Anyway, I've gone with transferring through the router instead - as that is fast enough for my needs (~7-8mbps) and there's no need for endless manual configuration. However, I might come back to this thread if I need higher speeds. As for transferring methods, I'm currently using SMB. But I could use SSH (or SCP, I suppose) if that would give me any higher transfer speeds.

First I hope you mean that your twisted pair is a crossover with that because they are definitely not the same thing.  Since you abandoned that though on to the transfer type:

You will not improve speed with SCP or SFTP.  It adds encryption overhead and will slow you down if anything.  Personally I would install an ftp server if I wanted more speed but there are other ways to go.  If you already have SMB going it will probably be fine if it's a one time deal.

---

### Post by Nevon on 2009-09-15
> **CoolHand said:**
> First I hope you mean that your twisted pair is a crossover with that because they are definitely not the same thing.
No? What's the difference then?

> **CoolHand said:**
> If you already have SMB going it will probably be fine if it's a one time deal.

SMB was kind of dodgy. Sometimes the computers could find eachother, sometimes they couldn't. So I just connected over SCP instead, as I already had that set up. This is not really a one time deal, but more like a "a few times a month" deal, but I think I can live with the transfer speeds. It still only takes about 3 minutes to transfer a gigabyte. The files I'm transferring are around 7 gigabytes, so that's roughly 20 minutes.

---

### Post by Iowan on 2009-09-15
If you take the cable, hold both ends with tab down and cable toward you:
if the wire colors are identical (from left: white-orange, orange-white...) it is a standard cable - not a crossover. The ends are different on a crossover cable - one will be as above, but the other will (probably) be white-green, green-white...
Connecting from computer to switch, hub, or router usually uses standard cable, but from computer to computer usually requires a crossover.

---

### Post by Nevon on 2009-09-16
> **Iowan said:**
> If you take the cable, hold both ends with tab down and cable toward you:
if the wire colors are identical (from left: white-orange, orange-white...) it is a standard cable - not a crossover. The ends are different on a crossover cable - one will be as above, but the other will (probably) be white-green, green-white...
Connecting from computer to switch, hub, or router usually uses standard cable, but from computer to computer usually requires a crossover.

They are identical, yes. green-green, orange-orange

---

### Post by grotesk on 2009-09-16
Just for a measure of clarity:

"Twisted Pair" refers to the way the cable itself is constructed internally. Inside the outer sheath, there are four pairs of wire. Each pair is twisted together, and then all the pairs are twisted around one another. From an electrical perspective, this helps to reduce interference from the outside, and cancel out crosstalk between pairs.

The wikipedia page on the topic has a more in-depth view:

[http://en.wikipedia.org/wiki/Twisted_pair](http://en.wikipedia.org/wiki/Twisted_pair)

Finally, a crossover ethernet cable has two pairs reversed, such that the "Transmit" conductors of one ethernet card are connected directly to the "Receive" pair of conductors on the other ethernet card. Think about this for a moment: if you use a straight-through cable, the Transmit pair will be connected to the other Transmit pair, and vice versa, which clearly won't work.

Again, I refer you to Wikipedia for a more detailed explanation. There's also a wiring diagram if you're making your own cable:

[http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

---

