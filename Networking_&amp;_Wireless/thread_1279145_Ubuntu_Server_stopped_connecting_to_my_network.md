---
title: "Ubuntu Server stopped connecting to my network"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by zacharyabresch on 2009-09-30
Hey everyone. I'm stuck and I need to get this server up and running. I had an Ubuntu Server (8.04) running forever on my small businesses' network. We did some spring cleaning and when we rebooted the server it won't connect to our network. The server has a static IP and, as far as I can tell, no networking setting were changed since the last re-boot. My Apache and Samba come and show no errors. I get no errors on boot up. I can ping 127.0.0.1 but all other external hosts return "Destination Host Unreachable" when pinged. I have tried pinging the server from my Mac and I receive the following:

ping: sendto: No route to host
ping: sendto: Host is down

None of the computers on this network are having problems at all. I've checked my /etc/network/interfaces and everything seems good in there.

Does anyone have any ideas? What additional information would you need to troubleshoot the issue? I have no idea where to go from here and I need to get the drives in the server accessible as soon as humanly possible. Any help would be greatly appreciated.

---

### Post by Iowan on 2009-09-30
Check gateway setting via **route -n**. (I don't suppose the cable got knocked loose during the cleaning.)

---

### Post by zacharyabresch on 2009-09-30
Thanks a lot for your response. I ended up fixing it by rebuilding my routing tables from scratch. It's working, for now!

---

### Post by Iowan on 2009-09-30
Keep your fingers crossed - hope it survives a reboot...

---

