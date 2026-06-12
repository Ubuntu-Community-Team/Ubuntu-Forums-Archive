---
title: "Anonine's OpenVPN - TUN/TAP issue"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by Chorgal on 2011-01-02
I'm at #3 and I'm getting this message in the terminal;

```
Options error: You must define TUN/TAP device (--dev)
Use --help for more information.
```What am I supposed to do?


Command-line based start:             

[LIST]
[*]1. Install openvpn package by using apt-get install openvpn
[*]2. Extract anonine_openvpn.zip ([download here]("https://www.anonine.com/files/anonine_openvpn.zip")) into /home/<USERNAME>/openvpn              directory
[*]3. Start connection with:
               sudo openvpn --client --config $HOME/openvpn/anonine.ovpn --ca $HOME/openvpn/anonine.ca.crt
[*]4. Enter username
[*]5. Enter password
[/LIST]

---

