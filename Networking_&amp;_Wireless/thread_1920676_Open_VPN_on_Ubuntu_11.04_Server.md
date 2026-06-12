---
title: "Open VPN on Ubuntu 11.04 Server"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by wardave on 2012-02-05
So I setup OpenVPN with this [https://help.ubuntu.com/11.04/serverguide/C/openvpn.html](https://help.ubuntu.com/11.04/serverguide/C/openvpn.html) guide and I get the following error when trying to start the vpn server "NOTE: OpenVPN 2.1 requires '--script-security 2' or higher to call user-defined scripts or executables"

This is my server.conf file

[http://pastebin.com/XAjCGNLH](http://pastebin.com/XAjCGNLH)

and the open vpn I installed was from apt-get install openvpn

I'm very new to linux but having fun learning it.

Any ideas?

---

### Post by SeijiSensei on 2012-02-05
Most OpenVPN command-line switches can be incorporated into the configuration file.  Just add the line "script-security 2" to the bottom of the file and try again.

For a discussion of the security levels, run the command "man openvpn" to read the program's "manual" page.

---

### Post by wardave on 2012-02-05
Yea I forgot about the man page, thanks heh. It worked.

---

