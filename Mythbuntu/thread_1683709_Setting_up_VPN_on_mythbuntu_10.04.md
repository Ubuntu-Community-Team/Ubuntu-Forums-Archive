---
title: "Setting up VPN on mythbuntu 10.04"
date: 2011-02-07
forum: Mythbuntu
---

### Post by map7 on 2011-02-07
I've been using Mythbuntu 10.04 64bit on my system for a while and have it nicely setup (so I don't really want to have to upgrade to 10.10). I'm trying to setup a VPN to work using NetworkManager and it's not working.

I can create the VPN connection but when I click on the VPN connection I've made it doesn't connect.

I get the following error:
Feb  8 13:22:45 mythserver-desktop NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'office' failed to connect: 'No VPN secrets!'.

---

### Post by nickrout on 2011-02-08
> **map7 said:**
>  'No VPN secrets!'.

Looks like your certificates or passwords, or whatever you are using to authenticate, is not set up right.

PS, googling > ubuntu "no vpn secrets" leads to a lot of supposed solutions, you should try it!

---

