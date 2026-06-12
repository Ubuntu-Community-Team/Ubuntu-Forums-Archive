---
title: "ANOTHER network manager issue"
date: 2011-06-06
forum: Networking &amp; Wireless
---

### Post by Dleacy on 2011-06-06
So woke up this morning turned on the laptop and network manager wont connect. It doesn't even start the automatic connection which struck me as odd. This used to happens sometimes on vista and i just restarted the router but this hasn't worked this time.

Tried WICD but get a bad password error on version 1.7 and unable to get IP address when using 1.6 so I gave up on that. After re-installing network manager and running it through terminal this is the output:

________________________________________________________________________

** (nm-applet:1971): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1971): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:1971): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:1971): DEBUG: foo_client_state_changed_cb
** (nm-applet:1971): DEBUG: foo_client_state_changed_cb
** (nm-applet:1971): DEBUG: going for offline with icon: notification-network-ethernet-disconnected
** (nm-applet:1971): DEBUG: foo_client_state_changed_cb
** (nm-applet:1971): DEBUG: going for offline with icon: notification-network-wireless-disconnected

** (nm-applet:1971): WARNING **: _nm_object_get_property: Error getting 'FirmwareMissing' for /org/freedesktop/NetworkManager/Devices/0: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:1971): DEBUG: old state indicates that this was not a disconnect 3
** (nm-applet:1971): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:1971): DEBUG: old state indicates that this was not a disconnect 2

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x91882d0 disposed twice

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(nm-connection-editor:2318 ): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `(null)'

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(nm-connection-editor:2318 ): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x8ff82e8 disposed twice

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x8ff8238 disposed twice

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x8ff8448 disposed twice

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x8ff8398 disposed twice

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x8ff85a8 disposed twice

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x8ff84f8 disposed twice

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x8ff8708 disposed twice

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x8ff8658 disposed twice

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x913e900 disposed twice

** (nm-connection-editor:2318 ): WARNING **: dispose: CEPolkitButton object 0x913e850 disposed twice

** (nm-applet:1971): WARNING **: <WARN>  activate_connection_cb(): Connection activation failed: Connection was not provided by any settings service

** (nm-applet:1971): DEBUG: foo_client_state_changed_cb
** (nm-applet:1971): DEBUG: going for offline with icon: notification-network-ethernet-disconnected

** (nm-applet:1971): WARNING **: <WARN>  activate_connection_cb(): Connection activation failed: Connection was not provided by any settings service

** (nm-applet:1971): DEBUG: going for offline with icon: notification-network-ethernet-disconnected

** (nm-applet:1971): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:1971): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/7
** Message: <info>  No keyring secrets found for Auto Wain40N/802-11-wireless-security; asking user.


** (nm-applet:1971): WARNING **: applet.c.2882 (applet_settings_new_secrets_requested_cb): couldn't find details for connection
** Message: <info>  No keyring secrets found for Auto Wain40N/802-11-wireless-security; asking user.

** (nm-applet:1971): DEBUG: foo_client_state_changed_cb
** (nm-applet:1971): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:1971): DEBUG: foo_client_state_changed_cb

** (nm-applet:1971): WARNING **: _nm_object_get_property: Error getting 'State' for /org/freedesktop/NetworkManager/ActiveConnection/8: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:1971): WARNING **: _nm_object_get_property: Error getting 'Default' for /org/freedesktop/NetworkManager/ActiveConnection/8: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:1971): DEBUG: old state indicates that this was not a disconnect 9
** (nm-applet:1971): DEBUG: going for offline with icon: notification-network-wireless-disconnected
______________________________________________________________________

the Debug 1971 message : old state indicates this was not a disconnect has appeared before but all of the other stuff is brand new and seeing as it contains the words critical invalid and failed I'm guessing its a bad thing.

A lot of this appears twice which makes sense as the icon whilst it connecting is solid and then flashes between the bars and what looks like a loading circle. It does this very quickly though and is something i have seen before when I have had connection problems

If any one can help out please do, I'm all up for changing code etc as this is a project laptop that I've been rebuilding so I'm not afraid of screwing the laptop up

Cheers

Running natty

---

### Post by Dleacy on 2011-06-21
came back from holiday, reinstalled networkmanager after uninstalling wicd automaticaly and deleted all leftover files such as wicd-curses folder etc and then installed all updates for my systema nd it now works better than ever

---

