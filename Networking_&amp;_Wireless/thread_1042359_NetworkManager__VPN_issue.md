---
title: "NetworkManager / VPN issue"
date: 2009-01-17
forum: Networking &amp; Wireless
---

### Post by IainPurdie on 2009-01-17
Hi folks. Hope someone can help me!

I've followed the instructions elsewhere for setting up a simple PPTPD VPN service on our rag-tag Ubuntu box. All the XP and Vista clients (i.e. everyone except me) can get on fine and it works a treat.

However, I'm running 8.04 Hardy and I'm struggling.

I'm following the instructions from here:

[https://help.ubuntu.com/community/VPNClient#Using%20NetworkManager](https://help.ubuntu.com/community/VPNClient#Using%20NetworkManager)

and looked also on here:

[https://help.ubuntu.com/community/NetworkManager#VPN%20support](https://help.ubuntu.com/community/NetworkManager#VPN%20support)

but neither help. I've downloaded and installed the network-manager-pptp package to work with Network Manager. As soon as I popped that on, I had the option to create VPN connections from my NM applet. I entered the details for my connection... but it doesn't appear as an option to connect to.

If I go to NM and left-click, select VPN Connections... I'm only given the option to "Configure VPN" (and a greyed out "Disconnect"). There's no sign of the one I just added. However, if I go into "Configure", the connection is there to be edited or deleted.

As an aside, I've tried looking at the details in gconf-editor, but I don't have a "networking" thread underneath "system". Could this be related?

---

### Post by elperrillo on 2009-02-22
The reason why you don't see networking on gconf-editor is because you are trying to open it issuing a command on a terminal screen, you have to run it using alt-f2 and entering the command there.

---

### Post by IainPurdie on 2009-02-25
Thanks elperrillo. I managed to get past this issue but am still struggling with getting the VPN going - but that issue's on another topic :)

---

