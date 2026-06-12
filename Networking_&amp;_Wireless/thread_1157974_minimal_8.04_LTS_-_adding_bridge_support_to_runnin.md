---
title: "minimal 8.04 LTS - adding bridge support to running kernel"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by ngoddard on 2009-05-13
I am running 8.04 LTS on a 1and1 server.  It is a minimal configuration provided by 1and1 and evidently they disabled bridge support in the kernel - e.g., brctl reports "Pacakge not installed".  Is there any way to add in bridge support to the kernel without recompiling (e.g., as a module).  If so, how?

thanks

Nigel Goddard

---

### Post by jacksonj on 2009-06-16
Hi Nigel,

I think this command can help you enable bridge support without a reboot:

 sudo apt-get install bridge-utils


Thanks,
Jackson

---

