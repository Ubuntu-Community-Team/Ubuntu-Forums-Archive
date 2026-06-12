---
title: "Networkmanager OpenVPN problem"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by fdimmling on 2009-05-11
While starting the VPN connection manually is working, using the NM applet in Jaunty seems to establish the connection but no data are sent or received, the daemon.log displays after establishing the connection

May 11 12:39:36 fd-eee901 nm-openvpn[4874]: Initialization Sequence Completed
May 11 12:39:37 fd-eee901 NetworkManager: <info>  VPN connection 'Hotsplots' (IP Config Get) complete. 
May 11 12:39:37 fd-eee901 NetworkManager: <info>  Policy set 'Hotsplots' (tun0) as default for routing and DNS. 
May 11 12:39:37 fd-eee901 NetworkManager: <info>  VPN plugin state changed: 4 
May 11 12:39:37 fd-eee901 nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' exited with error status 1.
May 11 12:40:06 fd-eee901 nm-openvpn[4874]: write to TUN/TAP : Invalid argument (code=22)
May 11 12:40:36 fd-eee901 nm-openvpn[4874]: write to TUN/TAP : Invalid argument (code=22)

The complete log of the initialisation is attached as a file.

Friedrich

[Added information] Starting openvpn manually leaves the resolv.conf unchanged

nameserver 192.168.0.1

starting it by the nm-applet inserts an extra line

nameserver 10.44.0.1

before the above given nameserver line.

---

### Post by jpl888 on 2009-05-28
I had exactly the same problem setting up my OpenVPN connection today. Turns out it was because LZO compression was enabled at the server end. Try enabling LZO compression in advanced settings for the VPN connection.

Worked for me anyway, hope this helps :)

---

### Post by voglster on 2011-02-22
Enabling LZO compression also worked for me.  Thanks!

---

### Post by gphilip on 2011-03-05
Enabling LZO compression worked for me as well. Thanks!!

---

### Post by jsedwards on 2011-06-10
It worked for me too, thanks!

---

### Post by arabkin on 2011-12-08
Solved the same issue by the same way, thanks a lot.

---

### Post by lz1dsb on 2012-11-04
> **jpl888 said:**
> I had exactly the same problem setting up my OpenVPN connection today. Turns out it was because LZO compression was enabled at the server end. Try enabling LZO compression in advanced settings for the VPN connection.

Worked for me anyway, hope this helps :)

Amazing. An old thread, but it also solved my issue :guitar:
Thanks :)

---

### Post by sefs on 2013-05-25
> **jpl888 said:**
> I had exactly the same problem setting up my OpenVPN connection today. Turns out it was because LZO compression was enabled at the server end. Try enabling LZO compression in advanced settings for the VPN connection.

Worked for me anyway, hope this helps :)

Wow jpl888 you have been saving bacons since 2011.  This worked for me as well. :D

---

