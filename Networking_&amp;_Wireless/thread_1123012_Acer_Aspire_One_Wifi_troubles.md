---
title: "Acer Aspire One Wifi troubles"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by Mercedes300 on 2009-04-11
Ok, I love my Acer, but ever since I switched my wireless security to WEP 128 to accommodate a network camera, I get very intermittent wireless connectivity. Most of the time, I can't connect at all. It just keeps asking me for the pass phase or key (I've tried both ASCII and HEX). I was able to connect last night with full access to the network. Now network manager says I'm connected, but I can't ping my local network or the internet.

The driver I'm was listed on this page [here]("https://help.ubuntu.com/community/AspireOne") but they seem to have changed it... if you can tell me how to check, I'll report back with the info.

Please help!

Thanks.

---

### Post by Mercedes300 on 2009-04-12
Ok, it looks like the driver on the page I linked to before is the one to use. Can someone help me "uninstall" the present driver so I can follow the How-To to install the new one?

Thanks. :KS

---

### Post by t0mppa on 2009-04-12
To get rid of any older versions of the driver before installing the new ones, do the following. After unpacking the tarball (the "tar -xzf ..." command) run these commands:
```

cd madwifi-hal-0.10.5.6*/
cd scripts/
sudo ./madwifi-unload
sudo ./find-madwifi-modules.sh $(uname -r)
cd..
```
Then continue with the install.

---

