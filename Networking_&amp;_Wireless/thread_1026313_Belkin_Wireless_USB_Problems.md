---
title: "Belkin Wireless USB Problems"
date: 2008-12-31
forum: Networking &amp; Wireless
---

### Post by Ntacman on 2008-12-31
I've been using Ubuntu for the past...Month or so, and I decided to go ahead and test out Wireless Networking. Since I didn't have any spare wireless cards on me, I was forced to use a Belkin wireless B USB network adapter, And had to install the drivers through wine. Now, the thing is, Ubuntu recognizes the Device, but fails to connect to any network, not just my own.

Very much appreciated,
Ntacman.

[COLOR="DimGray"]Edit:Forgot to mention I just recently had a fresh install of ubuntu, so Ill have to re-install Wine and the drivers.[/COLOR]

[COLOR="Blue"]Edit:Re-installed Drivers and such.[/COLOR]

---

### Post by spcwingo on 2008-12-31
Installing drivers through wine won't work for Ubuntu.  The only way I could see it helping is the driver inf and sys files could be used for ndiswrapper.  If you don't already have ndiswrapper.  You can install it by doing this:

```
sudo apt-get install ndisgtk
```

Alternately you could install by opening synaptic and searching for "ndisgtk" (without quotation marks).  Check it and press apply.  This will help you use a windows driver for Ubuntu.  To install the driver after installing ndisgtk just go to system>admin>install windows wireless drivers (assuming you are using the default Gnome environment).  Choose new driver and navigate to the inf file in your ~/.wine/drive_c/windows/inf directory.  Press OK and hopefully you will be all set.  Let me know if that get it done for you.

PS:  You might have to move the corresponding sys file to the same directory as the inf file for it to work.

---

