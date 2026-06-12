---
title: "Wired network - connection lost on router reboot"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by varangian on 2009-02-22
Just for background I'll explain that my ISP is the root cause of this problem. Their DNS service is closed to clients outside of their own, you can ping the servers but they won't respond to DNS requests. This would be fine except that every now and then the dynamic IP address they allocate clients is one that's not on the magic list so I end up with an essentially useless connection unless I care to access sites by memorising their IP addresses.

When this happens there are two basic solutions, the first being to add OpenDNS to the DNS lookups. If I do this it works but OpenDNS tends to be a bit slow so if I'm not in a hurry I choose plan B which is to switch off the router/modem, wait a bit then switch it back on. The odds of getting another duff IP address are vanishingly small so this should work just fine.

This method has revealed a problem on the Ubuntu (7.10) side of the system, however. Whilst the router restart works most of the time about 1 time in 4 it fails. At first I thought I'd beaten the odds and got a 'bad' IP address again but on further investigation it turned the problem was closer to home. The Ubuntu client, whilst not reporting any network problems, was no longer connecting to the router - or at least pinging the router from the PC failed. The problem is not on the router side, rebooting the PC to either Ubuntu or XP whilst leaving the router alone and it all works.

Seems as if Ubuntu is not always noticing the wired connection coming back up after the router/modem has rebooted. Any way of fixing this?

---

### Post by superprash2003 on 2009-02-22
find out the interface which is connecting to your router say eth0 .. and then in the terminal type sudo dhclient eth0

---

### Post by varangian on 2009-02-23
Thanks, I'll give that a go next time fate allows me to replicate this problem.

---

### Post by varangian on 2009-02-25
Well the roll of the dice gave me chance to try out the suggested fix sooner than expected and it does the trick, so cheers for this. A couple of additional observations/questions:

Firstly this failure to reconnect to the network isn't consistent, that's why it took me a while to spot it was the Ubuntu side where things went wrong. Initially I'd assumed the problem was on the router side. So Ubuntu can dynamically adjust to the changing state of the router but for some reason doesn't do so consistently. Also although my ISP has had this problem for some years I've only noticed things going wrong as described above over the last year or so. Since I've not tinkered with the network config it's possible some system update has introduced this glitch. Anyone know if later  Ubuntu releases suffer from this? I've been thinking about updating but since my setup is (apart from this) nice and stable I've been in no rush.

Secondly this does rather break the 'just works' goal of Ubuntu. I may get some flak for pointing it out but XP copes with the router power on/off just fine. Since I cut my teeth on Unix systems many years ago a bit of command line tinkering isn't a problem but it shouldn't be necessary. Incidentally I kept an eye on the network connection icon when I went through the routine this time around. Just like its XP counterpart it correctly reflected the powerdown of the router and then updated again when the router powered up. So - if I understand things correctly - the basic ethernet level of things is established ok but the dhcp side of things goes awol.

---

