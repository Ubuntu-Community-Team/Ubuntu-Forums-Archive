---
title: "Can't browse Samba shares with Jaunty"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by Pitel on 2009-10-03
Hi,
I've 2 machines here, both using Jaunty. And I can see them in Nautilus's network view. But whenever I double click on them, I get "Can't get share list from server" (translated) error window.

I use Jaunty's default /etc/samba/smb.conf on both machines and set up the shares by usershares (using right click menu in Nautilus). So i guess I used the BFU method, but it doesn't work.

---

### Post by swerdna on 2009-10-04
Run this command to turn off firewalls. If it helps you can later fix the firewalls to allow Samba
[LIST]
[*]check firewall allows samba: sudo ufw status
[*]turn off: sudo ufw disable
[*]turn on: sudo ufw enable
[/LIST]

Reference: [Opening the UFW Firewall for Samba]("http://ubuntu.swerdna.org/ubulanprimer.html#firewall")

At the very least you'll know if it's a firewall issue.

---

### Post by Pitel on 2009-10-04
Thank you for the link! I was missing the nf_conntrack_netbios_ns module in ufw config.

---

