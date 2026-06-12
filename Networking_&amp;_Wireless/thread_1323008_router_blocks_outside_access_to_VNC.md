---
title: "router blocks outside access to VNC"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by cb951303 on 2009-11-11
I enabled the gnome remote desktop daemon on one of my computers (local IP 192.168.1.101). In order to access it outside of my local network. I also forwarded the TCP port 5900 to the IP of the same machine and I added a firewall rule to allow WAN to LAN packets for port 5900. Still I can't connect to the machine.
Below are some screenshots of the admin panel of my router. Any ideas?

Thanks.

---

### Post by dmizer on 2009-11-11
VNC is **_TOTALLY_** unsafe for accessing over the internet. Please close port 5900 ASAP and use an encrypted protocol for accessing your desktop. Try this instead: [https://help.ubuntu.com/community/VNC#SSH%20port-forwarding](https://help.ubuntu.com/community/VNC#SSH%20port-forwarding)

---

### Post by cb951303 on 2009-11-11
done.
trying ssh. will report.

---

### Post by cb951303 on 2009-11-11
ok I successfully forwarded the SSH port (22) but outside connections are "refused". is it the internal ubuntu firewall blocking or should I setup SSH to allow remote access?

---

### Post by cb951303 on 2009-11-11
I configured ufw as in screenshot but still ssh connections are refused outside of local network.

PS: I restarted ssh and ufw services.

---

### Post by dmizer on 2009-11-11
SSH should be configured correctly by default. You still need to have a VNC server running on the target machine.

If you do have the Ubuntu firewall enabled, that's a good possibility for the cause of your problems. If you are unsure, you can check by looking at the output of this command:
```
sudo iptables -L
```
If the firewall is disabled, the output will look like this: [http://pastebin.com/f564e1a42](http://pastebin.com/f564e1a42)

Edit:
If your Ubuntu machine is behind a firewalled router, there's no real need for you to have a local software firewall on Ubuntu. Just disable it and be really careful about what you forward to the machine through your router.

---

### Post by cb951303 on 2009-11-11
1. Ubuntu firewall is disabled: [http://pastebin.com/m4f11d9a](http://pastebin.com/m4f11d9a)
2. VNC server is running: connecting through localhost:5900 works.
3. SSH server is running: "ssh localhost" works.
4. Port 22 is forwarded from router: Any online port scanner that I tried sees the port 22 as open.

and yet I get "connection refused" when I try "ssh IP.TO.MY.ROUTER"

---

### Post by dmizer on 2009-11-11
> **cb951303 said:**
> and yet I get "connection refused" when I try "ssh IP.TO.MY.ROUTER"
Are you testing this from inside your local network, or from a remote location?

---

### Post by cb951303 on 2009-11-12
> **dmizer said:**
> Are you testing this from inside your local network, or from a remote location?

tested it with both, same result.

---

