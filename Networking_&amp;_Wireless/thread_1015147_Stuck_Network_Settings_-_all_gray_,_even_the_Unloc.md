---
title: "Stuck: Network Settings - all gray , even the Unlock!"
date: 2008-12-18
forum: Networking &amp; Wireless
---

### Post by talofo on 2008-12-18
Ubuntu 8.10

I'm trying to put Netgear wn121T to work here.
There is no Linux Drivers for it apparently.

1) I've download the .inf file.

2) I've instaled ndiswrapper to manage the .inf 

3) I've instaled ndisgtk (for a graphic way of doing it)

When I clicked Configure Network I get a message: "No network manager found" this is not true cas I'm having "NetworkManager Applet 0.7.0. So I don't get why I was having this message.

Searching the forums, I found that, that messages will disappear if we install something like: gnome-network-admin

so,

4) I've instaled gnome-network-admin



NOW, I still can connect using the USB wireless antena. I don't know why.
But this gnome-network-admin is all gray . I cannot click anywhere. Only Close, or Help. I cannot click Unlock.




Update: I've try running network-administration from the command line:

I get this errors and warnings:
(network-admin:6778): Gtk-WARNING **: Unknown property: GtkComboBox.items

** (network-admin:6778): CRITICAL **: Unable to lookup session information for process '6778'



What should I do to make this work?

Any help on these please?

Regards,
MEM

---

