---
title: "Installed 8.10, no internet/network connection"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by davehkent on 2009-01-01
Following problems upgrading to 8.10 from 8.04, I've done a clean install of 8.10 from a live cd, but now I have no internet or network connection.

Following the installation, I went to System > preferences > network configuration, clicked on the 'wireless' tab and entered the ssid and password for the network. However, when I left click on the network icon up by the clock, there are no options to connect to any network, although if I right click the icon the 'enable networking' box is ticked.

The pc uses a Netgear WG121 wireless usb adapter to connect to the Netgear router downstairs, and it worked perfectly on 8.04. When I first installed Ubuntu on this pc (version 7.04), I had exactly the same problem, and had to do a lot of fiddling about with 'ndiswrapper' to get it working. Presumably I've got to do the same again???

Thanks
davehkent

---

### Post by prshah on 2009-01-01
> **davehkent said:**
>  When I first installed Ubuntu on this pc (version 7.04), I had exactly the same problem, and had to do a lot of fiddling about with 'ndiswrapper' to get it working. Presumably I've got to do the same again?

Quite right.

See [[SOLVED] How to activate WG311v3 (or any ndiswrapper or native) wireless]("http://ubuntuforums.org/showpost.php?p=4723545&postcount=1") for a step-by-step on how to activate wireless networking from the command line.

If you run into problems, post back here with the outputs from the point where you are facing problems.

---

### Post by davehkent on 2009-01-01
Thanks for the reply.

Yes, I thought I might have to go through the ndiswrapper business again.

Won't be able to get round to this now for a couple of days, but will come back if any problems.

Thanks
davehkent

---

