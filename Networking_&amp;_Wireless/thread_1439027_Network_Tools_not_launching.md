---
title: "Network Tools not launching"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by JohnJD on 2010-03-25
Okay, first off, I did this --> [https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)
 
My computer says the driver is installed and the device is present. All of that went fine. Now I need to connect my card to my house's wireless network. Am I supposed to do that in System-->Administration-->Network Tools? The problem is that whenever I click on network tools, the application looks like it is going to start-up and then quits/crashes/runs away, whatever. Any ideas on what is causing this?

EDIT:  Okay, I tried launching from the terminal, here is what I got:

```

johnny@johnny-desktop:~$ gnome-nettool

(gnome-nettool:2231): Gtk-CRITICAL **: gtk_statusbar_push: assertion `GTK_IS_STATUSBAR (statusbar)' failed

(gnome-nettool:2231): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-nettool:2231): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-nettool:2231): Gtk-CRITICAL **: gtk_label_set_mnemonic_widget: assertion `GTK_IS_LABEL (label)' failed

(gnome-nettool:2231): Gtk-CRITICAL **: gtk_combo_box_set_model: assertion `GTK_IS_COMBO_BOX (combo_box)' failed

(gnome-nettool:2231): Gtk-CRITICAL **: gtk_bin_get_child: assertion `GTK_IS_BIN (bin)' failed

(gnome-nettool:2231): Gtk-CRITICAL **: gtk_entry_set_completion: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-nettool:2231): Gtk-CRITICAL **: gtk_entry_completion_set_model: assertion `GTK_IS_ENTRY_COMPLETION (completion)' failed

```

---

### Post by JohnJD on 2010-03-25
Okay, solved the Network Tools problem by just uninstalling and then reinstalling from the software-center.  Now I'm still lost.  I did everything to configure the card from the previous link.  I tried sudo ifup wlan0 and got "ignoring unknown interface wlan0=wlan0"

---

