---
title: "Wireless will not pick up correct DHCP"
date: 2011-12-24
forum: Networking &amp; Wireless
---

### Post by tommckellips on 2011-12-24
This is a new one on me, I just installed Ubuntu 11.10 on a Dell Inspiron 1545 (replaced windows). The wireless works however it will not obtain a correct DHCP address. I run a class A 10. network and I am out in the country with no other wireless around me to interfere and no wep. The Dell picks up on the correct wireless router but it always sets the address at a class c 192.168.0.100 I have no servers running this address setup. I have a primary and backup DHCP that assigns addresses 10.0.0.100 through 10.0.0.225 I have brought in other wireless laptops that have connected just fine and picked up proper addressing. I have gone through the network settings and made sure it is set appropriately for DHCP and still the same results. IF is manually set the class a address in it the system works fine, it is just not pulling a correct DHCP any ideas?

---

### Post by dandnsmith on 2011-12-24
I presume that you've checked the router settings for assignable DHCP IP addresses, and that the router is being accessed correctly (whatever the encryption scheme is that you're using.

Have you also run a monitor to see what other wireless signals are showing up - I know Inssider exists for Windows, but don't know what the linux equivalent might be?

I certainly looks odd, and I cannot think of a reason, given what you've said.

---

### Post by tommckellips on 2011-12-24
No other wireless signals exist, already checked all that. Router DHCP is shut down and DHCP is served by my Fedora servers. I have Ubuntu running on all my desktops and other laptops and everyone has been good, this one is an odd issue.

---

### Post by dandnsmith on 2011-12-24
Are there logs kept by the DHCP service, to show whether (or not) any of them are attempting to provide the address, and are successful?

---

### Post by tommckellips on 2011-12-24
Checked logs on both systems and neither shows that the wireless client attempted to connect to them.

---

### Post by ReginaldPerrin3 on 2012-01-17
Hi, just read this forum. I hope you're still monitoring new replies.  This seems to be a prickly problem from your description.  The wireless router is the device which normally either issues ip addresses, or directs connection requests to a seperate dhcp server (which is what it sounds like you have). Either way, it seems that the upgrade or installation of Ubuntu 11.10 has reset some network defaults. Perhaps the Dell has a static address? Or perhaps the Fedora dhcp server has a static address set for the Dell's MAC address?  It is an odd thing to get wrong. I would suggest, from my experience and from your description, that there has been a mistake in set-up somewhere... a Homer Simpson "D-Oh!" moment.  If you haven't already resolved the issue, there are a few things I would try: Firstly, go back to the start with the Dell, and set up its connection from scratch. This will ensure that you have done everything right, and not accidently made the same mistake as you potentially may have made before. Secondly, I would try a Linux Live Disc (like Ubuntu 11.10) in the Dell, to see if it connects correctly and with the correct ip address (this will eliminate the question of hardware errors in the Dell). Third and lastly, I would try to reinstall the Ubuntu operating system in the Dell from a newly downloaded source (the Ubuntu 11.10 disc you used above).  If you have resolved the issue(s), please put a reply back on here with a few details about what you found to be wrong, and how you resolved it.  Hope this helps. Cheers

---

