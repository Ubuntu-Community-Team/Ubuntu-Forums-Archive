---
title: "Alternative to wide -dhcp-client in Maveric (e.g., ISC)?"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by DaveAtFraud on 2011-03-09
Hi All -

I'm attempting to get ready for IPv6 by modelling the major pieces of my network on a VMware ESXi box as Virtual Machines (VMs).  At the moment I'm stuck trying to get the wide-dhcp-client to work with a CentOS hosted dhcp6s server (another VM has a CentOS client and dhcp6c works as expected on it).  The problem is that wide-dhcp-client fails with a message of "client6_recvreply: unexpected reply" which I only get with maximal debug (-D).  This behavior repeats as long as I leave the client running and this seems to be a known bug.

Maveric has the most recent released version of the wide-dhcp-client (20080615-7) and development of the wide dhcp stuff has apparently stopped in favor of the ISC server and client (Natty will use ISC).  I've tried tweaking what information is requested by the client and messing with other settings but nothing makes the "unexpected reply" message go away.

I see the following as possible solutions (in order of desirability):

1) Someone knows how to tweak a setting in either the client or server to make the problem go away and is willing to share it.
2) There is a way to swap out the wide client for the ISC client (e.g., by enabling another repo, download it from ???, etc.).
3) There is a way to back port the Natty ISC client to Maveric.
4) I build the ISC client from source.

I'll look into getting the source for the ISC client and building it but my preference is to stay with packages that are maintained.

Cheers,
Dave

---

