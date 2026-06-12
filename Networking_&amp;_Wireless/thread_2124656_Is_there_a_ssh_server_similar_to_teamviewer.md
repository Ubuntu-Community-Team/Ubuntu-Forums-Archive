---
title: "Is there a ssh server similar to teamviewer?"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by PeterTaps on 2013-03-11
Hello,

We have a bunch of Ubuntu 12.04 based machines installed at various remote locations running our custom application. The operators of the machines have very little knowledge about computers.

Occasionally, we have to get into the machine remotely for troubleshooting. Teamviewer has worked well because the operators don't have to worry about firewall changes or IP addresses.

The problem with Teamviewer is that it is highly bandwidth intensive. The locations where the machines are installed do not have networking infrastructure. A mobile dongle is used temporarily for remote troubleshooting. Teamviewer responses are very slow over these mobile dongle networks.

Most of the work that we do requires just a terminal window. 

Openssh server would have worked great except that it requires messing around with the firewall. The operators won't be comfortable with this.

I guess the way Teamviewer works is that there is a server running somewhere that tunnels data between the host and the guest. Both, the host and the guest, are simply making  an outbound TCP or UDP connection. Most routers and mobile dongles do not block outbound connections.

I am wondering if there is any other lightweight remote terminal solution that works much like teamviewer.

Thank you in advance for your help.

Regards,
Peter

---

### Post by jonobr on 2013-03-11
> **PeterTaps said:**
> Hello,

We have a bunch of Ubuntu 12.04 based machines installed at various remote locations running our custom application. The operators of the machines have very little knowledge about computers.

Occasionally, we have to get into the machine remotely for troubleshooting. Teamviewer has worked well because the operators don't have to worry about firewall changes or IP addresses.

The problem with Teamviewer is that it is highly bandwidth intensive. The locations where the machines are installed do not have networking infrastructure. A mobile dongle is used temporarily for remote troubleshooting. Teamviewer responses are very slow over these mobile dongle networks.

Most of the work that we do requires just a terminal window. 

Openssh server would have worked great except that it requires messing around with the firewall. The operators won't be comfortable with this.

I guess the way Teamviewer works is that there is a server running somewhere that tunnels data between the host and the guest. Both, the host and the guest, are simply making  an outbound TCP or UDP connection. Most routers and mobile dongles do not block outbound connections.

I am wondering if there is any other lightweight remote terminal solution that works much like teamviewer.

Thank you in advance for your help.

Regards,
Peter


Its been a while since I have done this but have you thought of [reverse ssh]("http://www.howtoforge.com/reverse-ssh-tunneling")?
Again, its been some time for me, but hope this works for you

---

### Post by PeterTaps on 2013-03-11
Thank you for your help, jonobr. Looks like this technique would fit the bill.

Regards,
Peter

---

### Post by José Serra on 2013-03-30
Hi Peter, did you solve your problem?... reverse ssh is not an option for my case.

Best Regards.

---

