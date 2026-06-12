---
title: "KVM Statically Assigned IP's Reset to DHCP After VM Restart"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by tufcamman on 2009-12-30
Hi,

   I have set up kvm on my ubuntu server with two different VM's (both ubuntu guest) according to the instructions here.

[http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.10](http://www.howtoforge.com/virtualization-with-kvm-on-ubuntu-9.10)

   Throughout the setup, I would always assign static IP's (10.45.54.121), and when the VM is launched for the first time, it has that ip, and /etc/network/interfaces is configured correctly for the static IP.  The problem comes when I restart to VM.  It boots up and pulls an address from my DHCP server running on my router.  I can ssh into it using its new IP and run /etc/init.d/networking restart and it immediately goes back to its static ip and is good from then on.

   I cannot think of why it does not have that address assigned during bootup, and why it broadcasts for an address.  This happens on all the guests I have under that KVM server.

   Thank you for any replies

---

