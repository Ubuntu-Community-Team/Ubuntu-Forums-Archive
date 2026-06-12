---
title: "&quot;No VPN Secrets&quot; + Not storing password"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by HangukMiguk on 2011-09-10
I'm trying to import an OpenVPN connection from a *.ovpn file.  The import works fine, but when I insert my password and save the configuration within network manager, upon logon attempts, it tells me there are "no VPN secrets."

Now, after toying with this for 24 hours, I noticed something: Network Manager is not storing the password for the connection. As in, I can enter the password, save the connection, then immediately reopen the connection to find the password field blank again.  I'm assuming this is the root of my problem.

Any way to fix this?  And is there any way to manually input the connection into OpenVPN through CLI so I can use this connection in the interim?

---

### Post by HangukMiguk on 2011-09-10
Bump

---

### Post by neosrix on 2011-09-12
Hi,

By default the .ovpn file from openvpn server encapsulates the client settings and relevant certificates in one txt file. if you have that file then you can connect to VPN using cli as follows

```
sudo openvpn --config yourconf.ovpn
```If you want to import them using the network manager then you need to extract the certificates from the default ovpn file. [http://openvpn.net/index.php/access-server/docs/admin-guides/228-how-to-extract-the-ca-cert-and-key-from-openvpn-as-certificates.html](http://openvpn.net/index.php/access-server/docs/admin-guides/228-how-to-extract-the-ca-cert-and-key-from-openvpn-as-certificates.html) tells you how to do it. 

When I imported the files, the network manager detected the settings and certificates correctly , however refused to store the password. To resolve it, All I did was to manually create an identical vpn connection entry like the one detected by Network manager and NM obliged to store the password this time. Guess it's a bug in NM. Neverthless this fix worked for me.

---

### Post by HangukMiguk on 2011-10-01
> **neosrix said:**
> Hi,

By default the .ovpn file from openvpn server encapsulates the client settings and relevant certificates in one txt file. if you have that file then you can connect to VPN using cli as follows

```
sudo openvpn --config yourconf.ovpn
```If you want to import them using the network manager then you need to extract the certificates from the default ovpn file. [http://openvpn.net/index.php/access-server/docs/admin-guides/228-how-to-extract-the-ca-cert-and-key-from-openvpn-as-certificates.html](http://openvpn.net/index.php/access-server/docs/admin-guides/228-how-to-extract-the-ca-cert-and-key-from-openvpn-as-certificates.html) tells you how to do it. 

When I imported the files, the network manager detected the settings and certificates correctly , however refused to store the password. To resolve it, All I did was to manually create an identical vpn connection entry like the one detected by Network manager and NM obliged to store the password this time. Guess it's a bug in NM. Neverthless this fix worked for me.

Thanks for this input, will remember this if it screws up for me again.

At any rate, reinstalling caused it to work right.  Don't know why the initial install didn't give keyring the option to store the password, I'm not sure which program was to blame, whether it was NM or Keyring, but after installing, Keyring popped up asking for a default password as usual.

---

