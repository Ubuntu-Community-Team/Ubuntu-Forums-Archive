---
title: "Connect to home PC - bypass modem"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by Alnico on 2009-02-16
My home PC uses a D-Link 501T DSL modem for which I need to use the internal IP address 192.168.1.1 to connect to the modem.

So the setup is like this:

```
PC --> Modem --> Internet
```

I would like to connect to my home PC either through SSH or Remote Desktop so that I can control it remotely. If I use the IP address of my home PC, I can only log in to the modem, not the PC through the browser or telnet.

How do I connect directly to the PC? I read something that I need to enable port forwarding. If so, I would need some help on what I need to do.

Thanks!

---

### Post by dmizer on 2009-02-17
If you have a local IP address of 192.168.X.X, your modem is functioning as both a modem AND a router.

You will need to configure the router portion of your modem for port forwarding ssh.

BEFORE you do that, you'll need to seriously think about making SSH secure enough to use from the internet. Without some configuration, someone can gain access to your computer if they guess your username and password. Depending on your username and password, your system could be compromised in a matter of minutes.

Please see this guide regarding securing SSH using RSA keys: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Once you have secured SSH, then you can forward your SSH port. Here's some information on how to forward ports on some common router equipment: [http://portforward.com/](http://portforward.com/)

---

