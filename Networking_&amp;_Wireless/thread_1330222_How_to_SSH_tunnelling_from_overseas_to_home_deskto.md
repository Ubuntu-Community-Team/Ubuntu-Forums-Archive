---
title: "How to SSH tunnelling from overseas to home desktop ?"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by phryangle on 2009-11-18
What I'm trying to do is use my laptop (which is with me overseas) and SSH tunnel into my home desktop. All I want to achieve with this is to use my non-hostile home internet connection to do work online since I don't quite trust the internet connections available around me. My laptop and desktop are both running Hardy and I am not yet overseas so I have physical access to my desktop. 

Upon combing through the forums and google, I've come up with the following:

1. Install OpenSSH server and client. [here]("https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html").
2. Configure SSH server. [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring").
3. Create keys. [here]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").
4. Forwarding. [here]("https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding").
-->Seeking clarification, #4 involves opening the SSH port through my router to receive a connection for me to use. Yes/No? Firestarter is thrown around often and is it necessary to accomplish #4? 

Since I have just started learning about SSH 2 days ago, I don't quite understand the next step to achieve my goal described above. Can anybody shed some light on what is the next thing I need to do? Any help and input is greatly appreciated! Be gentle to this n00b[-o<

---

### Post by phryangle on 2009-11-18
ttt

---

### Post by eremyja on 2009-11-18
i believe you want a vpn and not ssh. or maybe a vpn over ssh? google openvpn

---

### Post by Lars Noodén on 2009-11-19
You would set up the connection for overseas just about the same way you would for in the same room. Keybased authentication with a strong passphrase is the way to go.

Two main choices:

You can set up a SOCKS5 proxy using dynamic port forwarding.  Firefox supports that, [Thunderbird](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/481281) doesn't.

```

$ ssh -CNTnq -l phryangle  -D 12121 homecomputer.example.org

```

If run from your notebook, that would give you the local port 12121 to connect to as a SOCKS5 proxy.

Some applications may need additional tuning to work fully.  e.g. firefox needs these set in about:config[indent]network.proxy.socks_remote_dns   user set   boolean   true
[/indent]

Or you can use ssh for an ad hoc vpn:
[https://help.ubuntu.com/community/SSH_VPN](https://help.ubuntu.com/community/SSH_VPN)

A much lamer choice would be to tunnel VNC or X11 over SSH.

---

