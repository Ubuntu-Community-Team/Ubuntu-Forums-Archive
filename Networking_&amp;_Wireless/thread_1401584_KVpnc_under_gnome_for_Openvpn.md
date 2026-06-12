---
title: "KVpnc under gnome for Openvpn"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by adam22030 on 2010-02-08
Perhaps this will help others who are trying to use Openvpn (or other variants) with NetworkManager and have been struggling to get it to work and getting messages like these:

NetworkManager: <WARN>  nm_vpn_connection_connect_cb(): VPN connection 'openvpn' failed to connect: 'No VPN secrets!'.

NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active.

I had read many of the posts on vpns and applied the suggestions to bring up a stable vpn connection; nothing worked that was consistently stable. Sometimes the vpn would come up, but would shortly die other times it would not come up at all using the NetworkManager. I had a bit more success establishing a connection from the command line, but I since I am running on a netbook I was looking for a simple "point and click" solution.

I read an old post about about running KVpnc under Gnome so I decided to give that a try. (It is also mentioned in the VPNClient Documentation). The configuration was simple, just point the application to the correct config, key, cert, etc. files after you create the initial vpn profile. I did not have to make any changes to /etc/network/interfaces . I tested it with a wired and wireless connection and both work perfectly.

NOTE: If you get a connection but are not able to access webpages or ping any domains, go to Network - General and check "Update DNS configuration"

I am using 9.10 Netbook Remix installed via Wubi on an HP Mini 1030NR 2GB 32GB Runcore SSD.

Hope this can help others....

Adam \../

---

