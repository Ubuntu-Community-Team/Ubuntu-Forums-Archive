---
title: "Redirect udp video packets to another machine"
date: 2011-11-04
forum: Networking &amp; Wireless
---

### Post by titaniumleg on 2011-11-04
Hello,

I have a device that can take in video from a source like a camera and stream it out to an IP address using UDP.  

This device has a very non-user friendly UI.  What I'd like to do is set the device to always stream to my ubuntu machine and then from there have my ubuntu machine redirect those packets to a target destination that is more easily set than on the device.  

I'm not sure how the best way to approach this would be.  Is this something that mangle can handle with iptables?  Also, am I correct in thinking that REDIRECT can only redirect to a local host?

---

### Post by jonobr on 2011-11-04
Using IPtables would do this

[This]("http://ubuntuforums.org/showthread.php?t=1855192") thread may offer some ideas

---

