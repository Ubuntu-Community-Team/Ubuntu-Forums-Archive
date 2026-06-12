---
title: "OpenVpn issues"
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by anduweb on 2011-03-15
Hello,

I'm trying to set up a OpenVpn on my Ubuntu 10.04 and after doing the configs from here: [https://help.ubuntu.com/10.04/serverguide/C/openvpn.html](https://help.ubuntu.com/10.04/serverguide/C/openvpn.html)


I get an error:

```
anduweb@ubuntu:/etc/openvpn/easy-rsa/keys$ sudo /etc/init.d/openvpn restart
 * Stopping virtual private network daemon(s)...                                                                            
  *   No VPN is running.
 * Starting virtual private network daemon(s)...                                                                            
  *   Autostarting VPN 'server'                                                                                            
   /etc/openvpn/up.sh: 7: /usr/sbin/brctl: not found      [fail]
```And the daemon.log says:
```
Mar 16 02:20:03 ubuntu ovpn-server[20664]: OpenVPN 2.1.0 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] [MH] [PF_INET6] [eurephia] built on Jul 20 2010
Mar 16 02:20:03 ubuntu ovpn-server[20664]: NOTE: when bridging your LAN adapter with the TAP adapter, note that the new bridge adapter will often take on its own IP address that is different from what the LAN adapter was previously set to
Mar 16 02:20:03 ubuntu ovpn-server[20664]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Mar 16 02:20:03 ubuntu ovpn-server[20664]: Diffie-Hellman initialized with 1024 bit key
Mar 16 02:20:03 ubuntu ovpn-server[20664]: /usr/bin/openssl-vulnkey -q -b 1024 -m <modulus omitted>
Mar 16 02:20:04 ubuntu ovpn-server[20664]: Control Channel Authentication: using 'ta.key' as a OpenVPN static key file
Mar 16 02:20:04 ubuntu ovpn-server[20664]: Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mar 16 02:20:04 ubuntu ovpn-server[20664]: Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Mar 16 02:20:04 ubuntu ovpn-server[20664]: TLS-Auth MTU parms [ L:1574 D:166 EF:66 EB:0 ET:0 EL:0 ]
Mar 16 02:20:04 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/tap1, iface: tap1)
Mar 16 02:20:04 ubuntu NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/tap1, iface: tap1): no ifupdown configuration found.
Mar 16 02:20:04 ubuntu NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/tap1: couldn't determine device driver; ignoring...
Mar 16 02:20:04 ubuntu ovpn-server[20664]: TUN/TAP device tap1 opened
Mar 16 02:20:04 ubuntu ovpn-server[20664]: TUN/TAP TX queue length set to 100
Mar 16 02:20:04 ubuntu ovpn-server[20664]: /etc/openvpn/up.sh br0 tap1 1500 1574   init
Mar 16 02:20:04 ubuntu ovpn-server[20664]: script failed: could not execute external program
Mar 16 02:20:04 ubuntu ovpn-server[20664]: Exiting
Mar 16 02:20:04 ubuntu NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/tap1, iface: tap1)
```Any ideas what is wrong?

Thank you in advance

---

### Post by velkymx on 2011-07-06
I am also having the same issue with 11.04 - any updates?

---

### Post by caxap on 2011-10-17
Have you try to change
/usr/sbin/brctl
to 
/sbin/brctl
in
/etc/openvpn/up.sh
and
/etc/openvpn/down.sh
?

Check where is brctl in your system:
which brctl

---

### Post by SOMDdan on 2011-10-21
If you try to use those instructions to set up a openvpn server on a Ubuntu desktop you are going to be SOL. The instructions are for setting up openvpn on a server, i.e. a machine with more than one interface. I have been trying to set up my Ubuntu laptop as an openvpn server for a week and have yet to find any correct, accurate instructions ANYWHERE.

---

