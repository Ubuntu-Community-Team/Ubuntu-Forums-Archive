---
title: "Config OpenVPN client for SwitchVPN in Network Manager from Windows ovpn files?"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by jimhabegger on 2011-07-17
I have ovpn configuration files for Windows from SwitchVPN. They do not provide configuration files for GNU/Linux. They said I can extract the certificate and key files from the ovpn files, but I'm confused about how to do that.

First of all, I don't know which Authentication Type to choose: "Certificates (TLS)," "Password," "Password with Certificates (TLS)" or "Static Key."

Second, I don't know what to put where from the ovpn file. I see a <ca> … </ca> section and a <tls-auth> … </tls-auth> section, but I don't see how those correspond to any of the Authentication Types. "Certificates (TLS)" and "Password with Certificates (TLS)" require two certificates and a key, "Password," requires one certificate and no key, and "Static Key" requires a key and key direction but no certificate. When I connect to SwitchVPN in Windows, it asks for a user name and password.

Here's an example of the ovpn files (certificate and key contents removed):

> route-delay 3
fast-io
client
dev tun
remote switchca.switchvpn.com 1195 udp
pull
resolv-retry infinite
nobind
persist-key
persist-tun
mute-replay-warnings
auth-user-pass
comp-lzo
reneg-sec 0
verb 3
;mute 10
explicit-exit-notify 1

<ca>
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----
</ca>

key-direction 1
<tls-auth>
#
# 2048 bit OpenVPN static key
#
-----BEGIN OpenVPN Static key V1-----
...
-----END OpenVPN Static key V1-----

</tls-auth>

Can anyone tell me how to get what I need from the ovpn files, and which Authorization Type to choose in the Network Manager VPN configuration GUI, and what to put in the blanks?

---

### Post by jimhabegger on 2011-07-18
Can anyone tell me, from looking at the *.ovpn file above, which was supplied by my VPN service to use in Windows, how to configure OpenVPN in Ubuntu using the Network Manager?

1. Which Authentication Type to choose?
2. What certificate and key files I need, and how to create them?
3. What to enter in the blanks?

The VPN service told me I could also do "openvpn --config x.ovpn" on the command line, but that fails every time with a message "AUTH: Received AUTH_FAILED control message".

---

