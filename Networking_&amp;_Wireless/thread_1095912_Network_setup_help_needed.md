---
title: "Network setup help needed"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by diver boy on 2009-03-14
I just installed ubuntu studio.  During the installation I could not configure the dhcp interface.  I now have studio running, but no network connectivity.  I am on a Lenovo T60 laptop and want to enable my wireless interface.  WHat should I do?

---

### Post by mikewhatever on 2009-03-14
Post the output of the following to start with.
**sudo lshw -C network**

Usually compatible network devices are activated using DHCP by default, regardless of whether or not networking was configured during the installation.

---

### Post by diver boy on 2009-03-15
I would expect them to be discovered.  During the install it did discover the ethernet controller, but not the wireless.  If I run the hardware tests, it does see them both, but I have been unable to establish any connectivity withteh internet.

---

### Post by josephe on 2009-12-11
Hi Diver Boy
I have a very similar problem on a Dell Inspirion. Although the machine seems aware of the ethernet and wireless networks I con't seem to make it connect. If I boot with the ethernet in place then I get wired network ok, but no wireless (which I'd like as default anyway)
 
lets hope we find a solution soon
 
Joseph

---

