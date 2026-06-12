---
title: "NetworkManager applet 0.7.0 default settings"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by g0l3m on 2009-04-13
Hello all,

I'm running ubuntu 8.10 with NetworkManager applet 0.7.0 and I have the following problem:

The network manager has a default connection (Auto eth0) that uses DHCP. I do not want to use this setting and I have my own static eth0 connection where I specify my own static IP and settings. Once I've logged in, I select it and everything works fine. The problem is, after I reboot, the default Auto eth0 connection is automagically selected again. So every time I reboot, I have to go and re-select my own static one, restart samba, etc. Even if I delete the Auto eth0 connection, one is always created (and selected) by default. Can someone please tell me how I can force my own static connection to be the one selected when I reboot?
I have played with the "connect automatically" and "system setting" check boxes on the applet with no luck.

thank you in advance,
g.

---

### Post by Jenkins1 on 2009-04-13
ok 

not sure if you have tried this so sorry if you have. 
right click and select edit connections
select auto eth and click edit (May need to enter root password)
untick the "connect automatically" box and then click apply.
Enter all you information into a new connection and make sure you click "connect automatically"

Reboot and try.

---

### Post by g0l3m on 2009-04-13
hello,

Thank you for your reply. I just tried this again just to make sure but with no luck. The problem is, after I reboot the auto eth0 connection has the "connect automatically" check box ticked again.

So, I change things as follows:
auto eth0 connection has auto connect OFF and system setting on.
static eth0 connection has auto connect on and system setting off.

If I log off and log back on, things remain the same and everything is great. However, if I restart/shutdown then the next time I log on the auto eht0 connection has auto connect ON and system setting on. It completely forgets/ignores my choices and forces itself to be the default connection.

It's such a simple and nice applet...Why can it not remember my settings and just work? :(

Any other ideas much appreciated.
cheers,
g.

---

### Post by Jenkins1 on 2009-04-14
This appears to be a known bug in ubuntu and network manager. Have a look at this it does mean not using network manager. 

[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

---

