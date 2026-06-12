---
title: "How can I set up my server such that I can VPN through it?"
date: 2013-05-07
forum: Networking &amp; Wireless
---

### Post by blazemore on 2013-05-07
I'd like to use the **out-of-the-box VPN functionality** (no additional client software downloads) on my Ubuntu desktop machines to tunnel my Internet traffic through an encrypted VPN tunnel to my server.

I could also possibly accomplish this wish just an SSH tunnel, but I'd like to make sure *all* my traffic goes through it.

---

### Post by Lars Noodén on 2013-05-07
I hadn't heard of any built-in VPN.  You have to install it.  [OpenVPN](https://help.ubuntu.com/community/OpenVPN) would be your best option for that.

If you are just wanting to tunnel web traffic and e-mail, then you can use an SSH connection as a SOCKS proxy.  If you're using Firefox, network.proxy.socks_remote_dns must be set to 'true'.  Same for other browsers and mail clients. 

For that make an SSH connection to your server with dynamic port forwarding:

```

ssh -Nf -l user -D 9341 server.example.org

```

Then point your web browser, mail client or whatever at *localhost* and port 9341.

---

### Post by blazemore on 2013-05-07
I mean built in VPN support in network-manager. I don't know if that's OpenVPN or not. I know I have to install something on my server; I'm asking what I can install to connect through Ubuntu's built-in network manager.

---

