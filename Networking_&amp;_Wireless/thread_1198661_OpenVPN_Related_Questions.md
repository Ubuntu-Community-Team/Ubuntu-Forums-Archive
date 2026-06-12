---
title: "OpenVPN Related Questions"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by dfxdeimos on 2009-06-27
Hello All,
 
I am running Ubuntu 9.04 Server Edition on a Hyper-V virtual machine that is allocated 1 CPU core and 512 MB RAM.
 
I am attempting to set up a temporary VPN server that will provide access to my voice network (192.168.43.0 / 24). I have an ISA server (I live in a Windows world) on the data network (192.168.42.0 / 24) that provides VPN services, but my VoIP software has trouble registering new endpoints over it. I think it has something to do with broadcast traffic that isn't making it over the VPN.
 
So, I decided what I needed to make this work was an OpenVPN Bridged VPN box.
 
I have been trying to follow the tutorial over @ [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN), but I must say that I have become a little bit confused as to the network configuration portion and how to configure the /etc/network/interfaces settings.
 
Can someone provide a little more guidance on what the proper way would be to create a bridged vpn connection on a server that has 1 NIC with a public IP and 1 NIC that is inside a network?
 
I would appreciate any and all help.

---

### Post by dfxdeimos on 2009-06-29
Sorry for bumping this topic after such a short period of time, but I am really in a bind on this.
 
Does anyone have experience with OpenVPN?

---

