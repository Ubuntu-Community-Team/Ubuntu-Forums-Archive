---
title: "OpenVPN connection via network manager"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by andi99 on 2009-11-30
Hi everybody!

I try to get OpenVPN working on my netbook running Ubuntu Netbook Remix 9.10. The OpenVPN stuff itself runs smoothly, a command like

```
sudo openvpn --config myconfigfile.ovpn
```

gives me the required connection. Now I wanted to use the network manager applet to handle the connecting and disconnecting. I installed the openvpn network manager plugin and imported my config file (VPN connections... ==> Configure VPN ==> Import)  and it seemed to have worked. But if I try to connect to my VPN it either fails silently or there is a message that the openvpn service could not be startet. 

Do I miss something?? (obviously I do, else it would work, wouldn't it? :p)

I couldn't even find debug information, network-manager does not seem to log to /var/log/messages...
Does anybody know where I can find the network-manager logs??

Any help would be appreciated!

Thanks,
Andi

---

### Post by andi99 on 2009-12-01
Hi everybody,

I answer to my ow post because I solved my problem. The issue was twofold: 

1) The Import/Export function seems to be broken for VPN connections. You can import stuff, the fields in the GUI are filled out correctly, but the connection doen't work. When you fill in everything by hand it works... stange! Moreover the network manager plugin does not seem to understand all OpenVPN configuration directives... :-(

2) The network manager OpenVPN plugin only supports two hash functions for the "HMAC firewall", SHA1 and MD5. I used RIPEMD160 but I couldn't convince the network manager plugin to use it too. A list of possible hashes can be obtained by issuing the command 

```
openvpn --show-digests
```All the network manager configuration stuff is stored somewhere in ~/.gconf/system/network/. I tried to edit the files by hand but changes are forgotten.

But, alas, it works now!

---

### Post by jame86 on 2009-12-12
How exactly did you fix it?  Sorry if im being dense but its late and im tired!

I have a working openvpn server on a remove ubuntu box,
I have a working openvpn client on my client ubuntu box (when run via openvpn --config client.ovpn

But I want to add it to network manager so it loads on boot.  

How can I do this?  I have the openvpn addon for NM but dont know what to put where.

Thanks

J

---

