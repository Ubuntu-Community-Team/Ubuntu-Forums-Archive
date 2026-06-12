---
title: "need help to build new server"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by heart12341 on 2010-12-05
[B][SIZE=3]i[/SIZE][SIZE=3][COLOR=Blue] have usb modem prepaid and i got connected but only on port udp 53 

and i got openvpn account from someone selling it monthly with udp 53 port 

so i  need to build my own server  and create openvpn accounts 

and thats the config file i have it 

[/COLOR][/SIZE][/B][SIZE=3]
[/SIZE][SIZE=3][COLOR=Red]
    dev tun
    client
    proto udp
    remote 46.**.**.**   53  
    resolv-retry infinite
    nobind
    user nobody
    group nogroup

    # Try to preserve some state across restarts.
    persist-key
    persist-tun
    ca ca.crt
    cert ****
    key ****
    comp-lzo
    verb 3
    no-replay
    dhcp-option DNS 172.16.0.23   **[COLOR=Blue]is that dns for amazon aws ??[/COLOR]**
    redirect-gateway def1
    resolv-retry infinite
    auth-retry interact
    auth-user-pass ***
    [/COLOR][/SIZE][SIZE=3][COLOR=Blue]
[B]
so what i have to do to build server like this config file ??

[/B]

[/COLOR][/SIZE][SIZE=3]

[/SIZE]

---

### Post by heart12341 on 2010-12-06
[B][COLOR=Blue]any help please ?
[/COLOR][/B]

---

### Post by ubudog on 2011-01-21
This may help you, hope it does:

[https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

---

