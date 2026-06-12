---
title: "Cannot resolve archive.ubuntu.com with apt update"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by Nixie Pixel on 2009-04-13
I'm trying out Ubuntu Server, but I assume the name resolution is the same, so I'm asking this here -

I am trying to run aptitude update and/or apt-get update, but the update fails with the following error:
Could not resolve 'archive.ubuntu.com'
(also could not resolve archive.canonical.com and us.archive.ubuntu.com)

I have assigned the server a static IP address, and had given it the OpenDNS servers (208.67.222.222 and 208.67.220.220) as nameservers in /etc/resolv.conf. 

When the update failed, since I am using a router which pulls DNS info from the same servers, I tried assigning my router as the nameserver. This didn't work either.

Any ideas?  Thanks!

---

### Post by Nixie Pixel on 2009-04-13
As a side note, /etc/resolv.conf was not automatically created, so I had to create it myself.  Could this be an issue?

---

### Post by Fr3d.org on 2009-04-13
Can you ping archive.ubuntu.com (91.189.88.45)? (Or even anything else... Google.com, Yahoo.com, BBC.co.uk, etc)

If you can't, it could be a problem with your default gateway setup.

---

### Post by InCrypto on 2009-04-13
@Nixie plz check if u can ping to the DG and OpenDNS servers also . Like i mentioned , this is a minor Human error imo . Do let us know if otherwise :)

---

### Post by Nixie Pixel on 2009-04-13
Hmm, no, I can ping my local network, I can ping my gateway, but I can't ping outside the network.

---

### Post by Nixie Pixel on 2009-04-13
Ahah, it was a gateway problem, I had fat-fingered the ip address.  Thanks for all the help!

---

### Post by bigbrovar on 2009-04-13
glad u had it resovled* :lolflag: :guitar:

---

