---
title: "Internet Sharing Ubuntu 10.10"
date: 2010-10-21
forum: Networking &amp; Wireless
---

### Post by Aztek on 2010-10-21
I've seen several similar questions but no answers that solved my problem. I'll make it dead simple for you:

I have a laptop with wireless and an ethernet port. It's hooked to the internet through the wireless (router address is 192.168.2.1). I have my Xbox 360 plugged into the ethernet port with internet sharing enabled. The xbox can connect to the internet but I have 2 problems:

1) Ubuntu is setting up a strict NAT (I checked to make sure it wasn't the router) which causes problems with Xbox Live.

2) The address of the Xbox is 10.42.43.41, so obviously ubuntu is running its own DHCP. This makes it so the Xbox can't network with any other computers/xboxes on the 192.168.2.x network, which is a real bummer.

Even if I could only resolved number 2 that's the important one. I want to change (or disable) the settings for the DHCP and put the Xbox on the same network as the rest of the house. There has to be a way to do this.

---

### Post by RedSingularity on 2010-10-21
Try [this](http://ubuntuforums.org/showthread.php?t=1183420&highlight=xbox+360+bridge) page.

---

### Post by Aztek on 2010-10-22
Thanks for the reply and link to the thread. My xbox can already connect to the internet like those in that thread. The problem I'm having is that it can't see any of the other xboxes/pcs on my network because it's on a completely different DHCP server (ubuntu). I need a way to reconfigure or just turn off the ubuntu DHCP.

---

### Post by RedSingularity on 2010-10-22
Did you try right clicking the network icon, going to edit network connections, going to "wired" tab, and editing the settings in there?

---

### Post by pfeitosa on 2011-01-07
You'll need to set your Ubuntu adapters in bridge mode, not NAT (router), in order to keep both ethernet adapters (and your Xbox) in the same network that the other clientes of your router (such as other Xboxes) are.

Try [https://help.ubuntu.com/community/NetworkConnectionBridge?](https://help.ubuntu.com/community/NetworkConnectionBridge?)  and
[https://help.ubuntu.com/community/NetworkConnectionBridge?](https://help.ubuntu.com/community/NetworkConnectionBridge?)

---

