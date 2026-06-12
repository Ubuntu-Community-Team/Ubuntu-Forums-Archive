---
title: "Network Settings after 8.10 Upgrade"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by Mjsch on 2009-06-30
Last night, after much putting it off -- I upgraded from 8.04 to 8.10. Among my reasons for doing so was the new network manager -- I liked the idea of having my VPN settings remembered, and in the same place as my home network settings. I installed the network manager VPN plugin: network-manager-vpnc

Now, after booting into 8.10 for the first time -- I notice something strange in my network settings (as the first thing I did was try to use VPN). I do not see my home network settings in the new network manager -- which is strange considering that I am still connected to the network, and have internet access through it. Are my settings stored elsewhere? If so, how do I move them to the new network manager.

Another question: how do I switch between connections now that I have a VPN and a home network set up? I try to run the applet -- nm-applet -- but it fails and does not start. The panel applet does not seem capable of switching between active connections...

Can anyone help me?

---

### Post by pytheas22 on 2009-06-30
It's possible that NetworkManager is auto-detecting your locations and saving the configurations.  If your connection works properly at both home and work, this is probably what's going on.

If you left-click on the NetworkManager icon, you should see an option at the bottom of the popup for configuring VPN connections (provided you have the VPN plugin installed, as you said).  You can also configure VPN settings by right-clicking NM, selecting "Edit Connections" and looking under the VPN tab.

---

### Post by Mjsch on 2009-06-30
I try to start the nm-applet and I get:

** (nm-applet:21121): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:21121): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed


where do I go from here?

---

### Post by pytheas22 on 2009-07-01
Ah -- I didn't realize your problem was that nm-applet is not running at all.  I thought you were just confused about the new interface to NM in Ubuntu 8.10.

nm-applet should be on by default.  According to someone on the [Gentoo forums]("http://forums.gentoo.org/viewtopic-t-399222-highlight-.html?sid=4d142e8dfca21e821f3df3e8c25067f5"), running this command should fix the problem you're experiencing:
```

sudo gtk-update-icon-cache -f /usr/share/icons/hicolor/
```

Let me know if that fixes it (you may need to reboot for the change to take effect, but probably not); if not, we can keep googling for more answers.

---

