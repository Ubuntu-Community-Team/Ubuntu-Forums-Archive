---
title: "Speed test by command line?"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by Magma828 on 2010-06-26
I'm using a remote dedicated server running ubuntu server edition, and I have no idea what the upload/download speeds are.

Is there a reliable method to test these speeds via the command line?

---

### Post by jonobr on 2010-06-26
Try looking around for iperf.

jperf is that gui version, but stick with the iperf.

It allows you to uplink and downling test with both TCP and UDP and changing packet size
If you need a hand with the syntax let me know
I should also add.... one side of the link will be the client and one the server,
you need iperf on both sides of a link, not just one.
I dont know if you can do that with your setup

---

### Post by jgb2185 on 2010-08-18
I am interested in compiling speed statistics on the 30 mbps service I signed up for with my local ISP. iperf looks like it could do the trick, but it relies on an upstream server, and I cannot find any reliable public iperf servers.

1) Does anyone know of any reliable public iperf servers?

2) What other techniques can be used to reliably test and record the download speed of an ISP connection?

Thanks...

JGB

---

