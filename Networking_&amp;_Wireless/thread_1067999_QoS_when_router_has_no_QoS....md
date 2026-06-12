---
title: "QoS when router has no QoS..."
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by matt_b on 2009-02-12
Hi all,

My 1-port DSL router does not support QoS, but the switch it is connected to is fully managed and does support QoS. I have a number of Dapper/Hardy servers connected to this managed switch, one of which is running Asterisk for VoIP.

My question is this: given that I can prioritise VoIP traffic on the switch, is it a problem that I cannot setup QoS on the DSL router? I think that as the switch is the only device sending data to the router and it is dealing with VoIP traffic first, it doesn't matter that there is no QoS on the router as it deals with packets in "first come first served" order, and my VoIP packets are always first.

Am I completely wrong in my understanding here?

Thanks
Matt

---

### Post by jonobr on 2009-02-12
Hello


My thinking is that given you are prioritizing your traffic in your switch,
Im thinking that the voip traffic will be allowed out of the switch before all other traffic from other systems, so even though your DSL router doesnt have the concept of priority, your network does and it sounds like a workable solution.

There could be a problem with the inbound RTP given that All traffic recieved at the dsl point will not priotise inbound RTP packets.

This may result in situations where people can hear you fine, however during large downloads, you may experience the usually voip bandwidth tell tale symptoms, of popping or clicking on the line or just a general degradation of quality on the inbound leg.

I would just execute a simple test by generating a lot of traffic using downloads and perform a few calls,
You could of course have to generate traffic in both directions, upload and download.
Watch the jitter and latency during that period, as these will have the greatest impact on your voice quality

---

