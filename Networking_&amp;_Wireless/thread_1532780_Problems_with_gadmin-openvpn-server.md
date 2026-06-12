---
title: "Problems with gadmin-openvpn-server"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by 4hm on 2010-07-16
I've been trying to setup a vpn network at my apartment for a couple of days now and I keep hitting a wall.  Finally I downloaded this GUI to help organize things, but it is returning a curious error.  It says that it is unable to open the plugin: "/etc/openvpn/openvpn.pam.auth.so"

Looking through my file system I noticed that the plugin's name was actually "/etc/openvpn/openvpn.auth.pam.so"

I dutifully tried to change this in the server configuration but it just reverts back to the old name when I try to activate the server.

Any ideas?

---

### Post by hannuko on 2011-01-02
Same problem here, thanks for finding the the root cause!  try this: cd /usr/lib/openvpn/ sudo ln -s openvpn-auth-pam.so openvpn-pam-auth.so  see also this: [http://ubuntuforums.org/showthread.php?t=1462749](http://ubuntuforums.org/showthread.php?t=1462749)

---

