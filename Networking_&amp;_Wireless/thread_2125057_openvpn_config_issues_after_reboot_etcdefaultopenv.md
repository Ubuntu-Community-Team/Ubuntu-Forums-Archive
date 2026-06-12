---
title: "openvpn config issues after reboot /etc/default/openvpn"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by sjhupp on 2013-03-12
So I have a vpn service, and can connect manually via cli on my 12.04 server via (as root):

openvpn --config /etc/openvpn/client.conf --ca /etc/openvpn/ca.crt --auth-user-pass /etc/openvpn/password.txt --redirect-gateway def1

I have my password and ca in /etc/openvpn as per the guides, works fine.

But, when I also set up the /etc/default/openvpn file with relevant details, I'm finding that a reboot wipes that file back to default (AUTOSTART="none" and blank optargs), so I lose all my changes and can't connect!?
Is this normal? It seems odd.
How can I lock the file and make it persistent through reboots?
Or am I stuck using a cron job to bring it up?
Thanks.

---

