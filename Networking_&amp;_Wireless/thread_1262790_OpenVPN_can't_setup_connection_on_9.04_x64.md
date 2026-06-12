---
title: "OpenVPN can't setup connection on 9.04 x64"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by MrMojoRisin on 2009-09-10
Hi there, 

This worked perfectly before, on 9.04 x86, but now my openvpn connection does not seem to set up properly.

Here's from my syslogd:

Sep 10 15:04:46 rainbows ovpn-client[2564]: TLS Error: TLS key negotiation failed to occur within 60 seconds (check your network connectivity)
Sep 10 15:04:46 rainbows ovpn-client[2564]: TLS Error: TLS handshake failed
Sep 10 15:04:46 rainbows ovpn-client[2564]: SIGUSR1[soft,tls-error] received, process restarting
Sep 10 15:04:48 rainbows ovpn-client[2564]: IMPORTANT: OpenVPN's default port number is now 1194, based on an official port number assignment by IANA.  OpenVPN 2.0-beta16 and earlier used 5000 as the default port.
Sep 10 15:04:48 rainbows ovpn-client[2564]: WARNING: No server certificate verification method has been enabled.  See [http://openvpn.net/howto.html#mitm](http://openvpn.net/howto.html#mitm) for more info.
Sep 10 15:04:48 rainbows ovpn-client[2564]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Sep 10 15:04:48 rainbows ovpn-client[2564]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Sep 10 15:04:48 rainbows ovpn-client[2564]: LZO compression initialized
Sep 10 15:04:48 rainbows ovpn-client[2564]: UDPv4 link local (bound): [undef]:1194
Sep 10 15:04:48 rainbows ovpn-client[2564]: UDPv4 link remote: xxx.xxx.xxx.xxx:1194

Can you advise what would be wrong?

Regards,

M.

---

### Post by Humphreybas on 2010-06-17
Did you find a solution?
I have exactly the same problem (9.04 x64) with additional info:

I first used the network-manager openvpn GUI and had no problems. Then I had to switch to WICD as network manager so needed to do openvpn trough CLI terminal. And there I stranded like you...

---

### Post by MrMojoRisin on 2010-06-17
It turned out to be a wrong username in the openvpn configuration file, my cut 'n' paste skills were lacking. After this, openvpn has been running smoothly ever since.
--
Mike.

---

