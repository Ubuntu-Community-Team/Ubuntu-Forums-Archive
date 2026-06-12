---
title: "Remote Access to Ubuntu Server"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by yameen101 on 2011-03-29
Dear Friends,

I am newbie to ubuntu server. We have installed Ubuntu Server 10.04 LTS for file share (Samba) at our local network.

I want to access my local server (Local IP 192.168.1.200) via internet from remote location. I have already installed SSH on our ubuntu server. I understands that using "Putty" we can access our server. Furhter, our Internet IP is dynamic (which is not an issue for us).

Can anybody guide me on the issue?
Thanks.

---

### Post by Drenriza on 2011-03-29
```
ssh username@192.168.1.200
```

This will allow you to connect to the server. When asked for a password, its the password for the user you type in on the remote host.

---

### Post by yameen101 on 2011-03-29
Dear Drenriza,

Thanks for your reply. Its working fine if i login from local network. I need guidance on remote location.
Thanks

---

### Post by Drenriza on 2011-03-29
> **yameen101 said:**
> Dear Drenriza,

Thanks for your reply. Its working fine if i login from local network. I need guidance on remote location.
Thanks

Argh sorry sorry.

The way i would do this is i would create a VPN tunnel, to your local network through your WAN network.

Try follow this guide
[http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-pptp-vpn-server-with-ubuntu-10-04-lucid-lynx.html)

---

