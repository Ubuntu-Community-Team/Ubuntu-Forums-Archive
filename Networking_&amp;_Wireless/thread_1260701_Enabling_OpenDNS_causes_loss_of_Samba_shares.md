---
title: "Enabling OpenDNS causes loss of Samba shares"
date: 2009-09-07
forum: Networking &amp; Wireless
---

### Post by timzak on 2009-09-07
I'm trying OpenDNS on a single computer on my network.  I added the DNS numbers to the machine in question.  Internet access worked properly and OpenDNS website recognizes that I'm using their DNS numbers.  However, I cannot access any Samba shares on the machine I added OpenDNS to.  Other machines on the network access shares just fine (including the machine with OpenDNS).  It's just the OpenDNS machine that cannot access any Samba shares.

I've removed the OpenDNS numbers and now Samba shares work fine again.  Anyone know of a way to get OpenDNS working with Samba shares?

Thanks.

---

### Post by darco on 2009-09-07
Did you setup an account w/OpenDNS? If so ,go to Dashboard/Networks.. you may just need to add the network and you should be good to go...

darco

---

### Post by timzak on 2009-09-07
I did do this, but still having the issue.  Is their definition of network the same as my LAN?  Since I only have OpenDNS on a single computer out of my network, perhaps this is causing the problem?

---

### Post by VortexCortex on 2009-09-10
OpenDNS was messing up my VPN a while back.

My VPN problem may be a related to your Samba problem...

If OpenDNS sees a hostname it can't resolve via the internet, you'll get routed to their search page (even if the hostname is a local server or on a VPN)

Here's how to keep OpenDNS from returning the search page.

Log into your OpenDNS account and go to the [settings page]("https://www.opendns.com/dashboard/settings/")

In the 'advanced settings' area under the heading 'Domain Typos'
Disable Typo Corrections.

Alternatively you may be able to add exceptions (the names of your samba shares or VPN hosts)

You may also have to disable the proxy under Network Shortcuts heading.

This fixed my local server problems while using OpenDNS, hope it helps.

P.S.
Make sure your IP address is updated as well under the 'Networks' tab.
If your IP address changes none of your settings will be applied until the change is updated in your OpenDNS account.

P.P.S. I just finished writing a nifty shell script that keeps your IP updated with OpenDNS.  It can run in the background at boot, and also handles No-IP, and DynDNS updates too.  MSG me if you'd like to have it.

---

