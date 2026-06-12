---
title: "secure connection fails to re-authenticate"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by civillian on 2009-02-08
When I have my computer connected to the wired connection in my university's halls of residence (connecting using an 802.1x secure connection with EAP-PEAP, MSCHAPV2) the connection will work for a while after connecting following login, however, every now and then the connection will stop working.
I checked with the sysadmin, and he said that 

> looking at the logs it looks like your computer has not been
authenticating every time, you should check it is sending the correct login
credentials so it can re-authenticate every time it is challenged.


I have all the network logins and passwords set up for the connection, so in theory it should just resend, however, it apparently doesn't, which means I have to manually reconnect (re-select the network and wait for authentication) which while not serious, can be annoying when I'm using pidgin or watching iPlayer etc.

Any help is welcome, and it should be noted that I cannot get packages from apt-get as the ports it uses are blocked by the network admins so any packages I want to install i have to download from packages.ubuntu.

Thanks for any help.

---

