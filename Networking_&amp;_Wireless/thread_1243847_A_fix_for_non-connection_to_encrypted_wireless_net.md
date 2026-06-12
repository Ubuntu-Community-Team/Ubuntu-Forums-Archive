---
title: "A fix for non-connection to encrypted wireless network"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by Milwbikerboy on 2009-08-18
There appears to be a problem with encryption using ubuntu/kubuntu's network manager with some wireless chips. I was one of them, looked everywhere for help. Could connect to my wireless network if using no encryption, but just couldn't connect using ANY type of encryption. Stumbled across this, tried experiment, and it worked. This may not be the permanent fix for the ubuntu package, but may work and get you running.

 Go to your Synaptic package manager and search for WICD. Its a wired and wireless network manager whose home is on sourceforge, but whose package is available in the ubuntu repo's. I am using a Broadcom built in mini-pci wireless card on my Dell, nothing was fixing the connection trying to use encryption. If your connection is working on an open system without encryption, but not with encryption. Try the WICD package. 

NOTE: it WILL remove the gnome and/or KDE network manager when it installs. I HAVE tried the connection with both WEP and WPA, both WORKS!! YAHOO! :D 

Anyway, wanted to post this info for all those that have been stuck in same boat :) 

Again, try this at your own risk, etc, etc. But if it works for you, maybe add to this thread so others will have other examples of different cards or setups.

---

### Post by w_1_n_d on 2009-08-18
i can't connect, how im i suppose to get the program??:popcorn::popcorn:

---

### Post by Milwbikerboy on 2009-08-19
heres a link to download the file and save manually

[http://packages.ubuntu.com/jaunty/all/wicd/download](http://packages.ubuntu.com/jaunty/all/wicd/download)

---

### Post by w_1_n_d on 2009-08-19
Kool thanks for the help.

---

### Post by daal21 on 2009-08-25
Worked for me too. Thanks!

---

