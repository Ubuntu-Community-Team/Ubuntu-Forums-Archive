---
title: "err messages directed to terminal (from c"
date: 2019-02-01
forum: Multimedia Software
---

### Post by lawrence_hickey on 2019-02-01
Running pithos and suddenly these messages begin to appear on my terminal window where I am working. I am running umbuntu 16.04 , very new 7530 dell. Seems to happen after I am running for a while. Maybe also occurs when looping on youtube playing some song. Not right away. seems to take some time before I get this.  If I could direct it away from the terminal that would be very good if not perfect.  Could I un-install chromium browser which I don't use anyway.

 [8912:8935:0201/131217.327613:ERROR:address_tracker_linux.cc(159)] Could not create NETLINK socket: Permission denied (13)
[8912:8926:0201/131217.394250:ERROR:udev_linux.cc(21)] Failed to initialize udev, possibly due to an invalid system configuration. Various device-related browser features may be broken.
[8912:8938:0201/131217.453869:ERROR:address_tracker_linux.cc(159)] Could not create NETLINK socket: Permission denied (13)
[8912:8912:0201/131217.594692:ERROR:x11_input_method_context_impl_gtk.cc(144)] Not implemented reached in virtual void libgtkui::X11InputMethodContextImplGtk::SetSurroundingText(const base::string16 &, const gfx::Range &)
[8912:8939:0201/131217.613983:ERROR:address_tracker_linux.cc(159)] Could not create NETLINK socket: Permission denied (13)

(chromium-browser:8912): IBUS-WARNING **: Unable to connect to ibus: Could not connect: Permission denied
[8912:8940:0201/131223.662529:ERROR:address_tracker_linux.cc(159)] Could not create NETLINK socket: Permission denied (13)
[8912:8940:0201/131225.446400:ERROR:address_tracker_linux.cc(159)] Could not create NETLINK socket: Permission denied (13)

---

### Post by TheFu on 2019-02-02
Start another terminal and use that. Leave the other one minimized since it seems to have been taken over as the console terminal.  This assumes you dind't run these programs from inside the first terminal. If you did, what you are seeing is a feature.  It is especially useful for troubleshooting problems.

---

