---
title: "Intermittent network connection using 802.1x wired"
date: 2010-10-04
forum: Networking &amp; Wireless
---

### Post by chturne on 2010-10-04
I'm trying to connect to a university network using tunnelled TLS with PAP. I can connect okay, but my connection drops seemingly randomly at varying intervals of usage, i.e. sometimes after 10 minutes, other times after 4 hours. I haven't found that running any particular application causes the problem.

I've been checking /var/log/daemon.log, and found an interesting snippet, which I believe is connected to my problems, (everytime my connection drops, there is the following message just written to the log)

```
Oct  4 17:06:52 spartan wpa_supplicant[917]: CTRL-EVENT-EAP-STARTED EAP authentication started
Oct  4 17:06:52 spartan wpa_supplicant[917]: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 21 (TTLS) selected
Oct  4 17:06:52 spartan wpa_supplicant[917]: OpenSSL: tls_connection_handshake - Failed to read possible Application Data error:00000000:lib(0):func(0):reason(0)
Oct  4 17:06:53 spartan wpa_supplicant[917]: CTRL-EVENT-EAP-FAILURE EAP authentication failed
```I did a search on some keywords in that snippet, and found bugs from past versions of network manager, which were apparantly all closed and fixed in Lucid. I'm running 10.04. My network manager version is 0.8-0ubuntu3 and my wpa_supplicant version is 0.6.9-3ubuntu3.

This is an ethernet wired connection. 

```

charlie@spartan:/var/log$ dmesg | grep 'Ethernet'
[    1.626164] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded

```I'm puzzled as to how to further troubleshoot the issue. Any advice would be much appreciated. Thank you for reading.

-- Charlie

---

### Post by chturne on 2010-10-06
After some investigation I'm currently of the opinion that the driver for my network card doesn't support his type connection properly.

I have RealTek RTL8168b/8111b NIC driver.

I tried manually setting my connection up using the following configuration for my university which most closely matched what I found in NetworkManagers own, different, configuration file. I followed the wpa_supplicant.conf man page,

```

ctrl_interface=/var/run/wpasupplicant
ctrl_interface_group=users
ap_scan=0

network={
   key_mgmt=IEEE8021X
   eap=TTLS
   anonymous_identity="anon @ example. com"
   identity="identity @ example. com"
   password="secret"
   phase2="auth=PAP"
   ca_cert="/etc/ssl/certs/Equifax_Secure_CA.pem"
}

```

Running wpa_supplicant using that config file and debugging gives out some messages like this

```

wpa_driver_wext_set_wpa
Driver does not support WPA.

```

Maybe this would explain why my connection drops "randomly", when the computer tries to authenticate with the network, my driver doesn't support it, so it just quits. This doesn't explain how I can connect in the first place though, and why reinserting the ethernet cable fixes the problem for a while... :(

Can anyone help me confirm this, I wasn't sure where to look, it seems the driver comes from RealTek, at least they offer a Linux driver, but I couldn't determined whether is claimed to support this type of connection.

Thanks,

-- Charlie

---

