---
title: "IP address keeps changing"
date: 2011-11-02
forum: Networking &amp; Wireless
---

### Post by alanshort on 2011-11-02
Hello...

I'm running Ubuntu in VMware Workstation 7.1.4.

Networking for the VM is NAT and is working okay. I'm connecting to the internet, host etc... from the VM

However, when I put the host to sleep and then restore, the IP address of the ubuntu virtual machine changes in steps of 2.
 
i.e :

IP is 192.168.20.148, then put host to sleep (VM is still running), wake up host and the VM will now have an IP of  192.168.20.150, put the host to sleep again, wake it up and the VM is now 52 etc.....

I'm using the VM as a web dev server, so it's very annoying that the IP address keeps changing !!

Please could someone guide me to either set up a static IP for the VM or to keep the same IP following a host sleep....

Thank you
Alan

:)

---

### Post by CharlesA on 2011-11-02
The host shouldn't be changing ip addresses when it goes to sleep.

You can set a static IP by following the steps here:

[http://www.cyberciti.biz/faq/linux-configure-a-static-ip-address-tutorial/](http://www.cyberciti.biz/faq/linux-configure-a-static-ip-address-tutorial/)

---

