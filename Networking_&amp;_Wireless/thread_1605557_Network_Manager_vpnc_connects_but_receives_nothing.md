---
title: "Network Manager vpnc connects but receives nothing"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by zzantozz on 2010-10-25
I'm trying to connect to a Cisco VPN at work from Ubuntu 10.10. On earlier versions, I was able to import the config and get it working. In 10.10, though, the best I've gotten is being able to connect to the VPN, see the welcome message, and have packets sent over the tunnel. I don't receive any packets, though.

The command-line vpnc client connects just fine. It's Network Manager that's giving me a headache. I found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/655124](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/655124)

The symptoms it describes are exactly what I'm seeing. The apparent solution is to "make sure in your config that LZO Compression is enabled (checked) under Advanced"; however I see neither an option for compression nor an "Advanced" tab, button, or anything on my VPN config in Network Manager.

Any help?

---

### Post by limaunion on 2010-10-25
Hi! I'm having exactly the same problem as previously described, I can establish the vpn session with network-manager but can't connect to any host inside the vpn network. If I use vpnc from CLI I can connect to any host without problem.

Does anyone have any idea on what's going on? I'll try to debug the network-manager session tomorrow.

LU

PS: I'm using Ubuntu 10.10 fully updated.

---

### Post by limaunion on 2010-10-25
> **zzantozz said:**
> 
The command-line vpnc client connects just fine. It's Network Manager that's giving me a headache. I found this bug report:
[https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/655124](https://bugs.launchpad.net/ubuntu/+source/network-manager-openvpn/+bug/655124)



@zzantozz: the bug you're describing applies to the 'network-manager-openvpn' package and probably you're using the package 'network-manager-vpnc-gnome' like me. That should be the reason why the lzo option doesn't appears.

---

### Post by siam.a on 2010-12-19
I too am encountering this problem in Ubuntu 10.10. 
I can connect fine and then browse when connecting to the VPN from command line, but when entering the same settings in the network-manager GUI, it connects as it should but I cannot connect to any websites.

Any updates on this issue?

---

### Post by Orlsend on 2010-12-23
I also experience the same problem for ubuntu 10.04 and 10.10, any ideas yet?

---

### Post by jrogers360 on 2012-03-06
I also am having this trouble.  

I managed to get it working by using vpnc from the command line, and using the cisco-udp nat method, and also updating the vpnc script from the maintainers website.

---

