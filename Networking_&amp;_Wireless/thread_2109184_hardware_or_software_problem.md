---
title: "hardware or software problem?"
date: 2013-01-26
forum: Networking &amp; Wireless
---

### Post by enuckon on 2013-01-26
Hello,
Internet connection has suddenly stopped working on Ubuntu 10.04, and I haven't been able to connect through either wireless or cable.  Network Manager says "Networking disabled" without giving any option.  "Ifconfig" gives HWaddr for both wireless and cable interfaces.  "Iwconfig" says "no wireless extension" and "unassocisted  ESSID: off/any" for wired. 

I would appreciate any suggestion on how to test what went wrong and how to see if this is hardware or software problem.   Everything else seems okay.  

Thanks in advance,
E.

---

### Post by ahallubuntu on 2013-01-26
Can you boot a Ubuntu live CD?  If that doesn't work either (wired at least), then it's almost certainly a hardware issue.  If that works, it's obviously a software thing with your 10.04 installation.

---

### Post by enuckon on 2013-01-26
> **ahallubuntu said:**
> Can you boot a Ubuntu live CD?  If that doesn't work either (wired at least), then it's almost certainly a hardware issue.

Thanks for your suggestion.  I have found what looks like a solution: [http://www.geekyard.com/os/linux-os/fix-network-manager-disabled-problem-in-ubuntu-10-04/]("http://www.geekyard.com/os/linux-os/fix-network-manager-disabled-problem-in-ubuntu-10-04/")
The NetworkManager came back with all the internet options.  I am still wondering what would cause it to stop working without any apparent reason.

---

