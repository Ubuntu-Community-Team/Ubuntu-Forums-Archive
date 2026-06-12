---
title: "PPTP still a Problem, I can't refuse eap"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by insllvn on 2009-04-26
I am having a problem with VPNs. This problem has been discussed, and ostensibly solved, in other areas of the forum. The problem is that the latest version of network-manager-pptp does not support the option to refuse EAP, a necessary step for some VPNs. The solution is  to add a key to gconf that refuses eap; it should be a string called "refuse-eap" and set to yes. I have attempted to add this key, but it doesn't stick. My question is why would gconf fail to save the key, and how can I fix it so I can connect to my university's vpn?

---

### Post by insllvn on 2009-04-26
For what it is worth, I attempted to add the key again, then I restarted both NetworkManageer and nm-applet. NetworkManager offered no complaint, but nm-applet gave 

** (nm-applet:6396): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:6396): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Not sure what this means, I am still learning.

---

