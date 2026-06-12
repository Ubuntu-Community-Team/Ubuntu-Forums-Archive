---
title: "ndiswrapper-utils-1.9 not installed!"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by MickKi on 2009-09-10
Hi All,

Fresh installation of Ubuntu 9.04.  I am trying to get my Netgear WG511 v2 going (the one with the Marvell chipset).  I have downloaded the wg511.inf file to the laptop and tried running ndiswrapper -i or -l.  On both occasions I am getting:```
Error: ndiswrapper-utils-1.9 not installed!
```

Trying to install it gives me:```
E: Package ndiswrapper-utils has no installation candidate
```

It offers me to install ndiswrapper-common which I have now installed - but the "ndiswrapper-utils-1.9 not installed!" is repeated every time I try to install the MSWindows .inf file.  :(

Any idea how I can fix this?

PS.  I seem to have ndiswrapper-1.53 loaded.

---

### Post by ajgreeny on 2009-09-10
Very odd!  The version of ndiswrapper in the repos is **1.53-2ubuntu1 (jaunty)**, so you are OK there, but you should be able to find the utils application package with no problem.  I have exactly the same wireless card on a laptop I seldom use, and it all installed and worked very easily, though only with WEP.  I will be interested to hear if you can get WPA working with it, when you do finally get the utils package on the machine.

Try ```
sudo apt-get update
```or synaptic, to renew your repos, or try another server in System > Administration > Software Sources.

---

### Post by MickKi on 2009-09-13
Thank you ajgreeny,

Not sure what went amiss on the CLI and the installation of ndiswrapper-utils was not successful.  I think I had already enabled the multiverse repos.  Anyhow, I have used the GUI as you suggested and managed to find ndiswrapper-utils which was nicely installed and working.  I now have the card configured which works nicely.

I didn't try WPA1/2 because this router is configured to only use WEP because of some old PCs/NICs pn the LAN that can only do WEP.  However, to get WPA working you will need to install wpa_supplicant and configure it either via the existing Ubuntu network manager, or via wpa_gui (may need to install this separately).  It may be simpler to just edit /etc/wpa_supplicant/wpa_supplicant.conf (not sure if this is where Ubuntu stores the wpa_supplicant configuration file).

Thanks again.

---

