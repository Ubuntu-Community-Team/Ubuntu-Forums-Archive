---
title: "Ubuntu Server and wifi"
date: 2011-12-14
forum: Networking &amp; Wireless
---

### Post by paulwilson5x on 2011-12-14
Hi, Im completely new to Ubuntu. I have installed Ubuntu server on my laptop, have no way to connect by ethernet and want to access my college's wifi, how is this possible? Thanks

---

### Post by praseodym on 2011-12-14
Hi,

which Ubuntu version is that? Richt-click on the network-manager-applet top right in your panel->Edit connections->Wireless->Add

Choose the name of the network you want to connect to, choose the encryption mode and add the passphrase (if any)

Or start the network-manager from terminal (CTRL+ALT+T) via

```
gksu nm-connection-editor
```
If you want to scan the networks around you manually:

```
sudo iwlist scan
```

---

### Post by jonobr on 2011-12-14
Im assuming there is no GUI

Also assuming the driver is working ok here

If so maybe take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1894424")

or if your having issues, review [this sticky thread]("http://ubuntuforums.org/showthread.php?t=370108")

---

