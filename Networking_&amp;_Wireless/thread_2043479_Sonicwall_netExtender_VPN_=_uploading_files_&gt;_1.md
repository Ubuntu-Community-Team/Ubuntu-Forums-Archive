---
title: "Sonicwall netExtender VPN = uploading files &gt; 1Mb disconnect the VPN"
date: 2012-08-16
forum: Networking &amp; Wireless
---

### Post by hipogrito on 2012-08-16
Hello,

Ubuntu 12.04 32 bits
Sonicwall netExtender 5.5.707

I am using Sonicwall nextExtender VPN to connect to my work network. Everything works fine until I try to upload a file > 1 Mb into the network. Then, VPN disconnects and reconnects, but my file has not been transferred. Download works fine.

Any idea?

- This has happened in several other Ubuntu versions before.
- This has happened with different cable providers at my home.
- This has happened in more places than my home in different states.
- This does NOT happen if I use Windows XP.

Thanks,

Regards,
Hipo

---

### Post by hipogrito on 2012-08-30
Hi,

Just an update.

This keeps happening with netExtender 6.0.

Trying to find the solution with the SonicWall guys or at least trying to determine if the problem is in my network/configuration or in netExtender... still unclear...

Regards,
Hipo

---

### Post by Xlorep DarkHelm on 2012-09-21
Interesting, I have a similar problem with this, only it is with opening a remote desktop connection while using the SonicWall VPN netExtender to connect to my work computer. I get brief access to the computer, and then it drops & reconnects the VPN connection, which causes my RDP session to freeze until I retry the connection, and that inevitably repeats the problem. This makes it impossible for me to connect to work, especially as the StrongSwan VPN functionality for NetworkManager is currently broken: [https://bugs.launchpad.net/ubuntu/+source/network-manager-strongswan/+bug/872824](https://bugs.launchpad.net/ubuntu/+source/network-manager-strongswan/+bug/872824)

---

### Post by hipogrito on 2012-11-30
Hi,

This was a bug in Sonic Wall server firmware, fixed few months ago. So, for those using Sonic Wall (DELL) VPN get the latest client and the latest firmware for your hardware box, and you'll be all set.

It works like a charm for me now...

Regards,
Fran

---

