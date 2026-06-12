---
title: "Ndiswrapper and Ethernet Card"
date: 2008-12-19
forum: Networking &amp; Wireless
---

### Post by makaveli0129 on 2008-12-19
Ok this is the problem that i am using ndiswrapper but the problem is that it keeps loading modules b43, b44, and ssb. The only way to get the wireless to work is to remove all of those. The only problem is that when i do that the ethernet card won't work now. 

How do i make the driver be ndiswrapper while also having the module b44 and ssb loaded for my ethernet card. I have ubuntu 8.10.

Thanks for all the help

---

### Post by cariboo on 2008-12-19
Add the drivers you don't want loaded to /etc/modprobe.d/blacklist. To open blacklist, press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist
```

Check the example below

```
# Don't need this driver
blacklist b43
```

Add other drivers as needed.

Jim

---

### Post by Ayuthia on 2008-12-19
This comes from the [no-fluff guide]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Version%200.3"):
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```
Just copy the code and paste it into the Terminal.  This will add a little script that gets called when ndiswrapper gets loaded.  It will unload the b43, b43legacy, b44, and ssb modules before it loads ndiswrapper.  Then it will load the b44 module after ndiswrapper is loaded.

---

