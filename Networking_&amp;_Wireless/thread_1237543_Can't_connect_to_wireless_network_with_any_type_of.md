---
title: "Can't connect to wireless network with any type of encryption"
date: 2009-08-11
forum: Networking &amp; Wireless
---

### Post by Milwbikerboy on 2009-08-11
Hello, new to Kubuntu/ubuntu, but LOVING it :) Anyway, leaving Microsoft for good, had recently tried Mandriva, and then latest Debian. Both worked fine with wireless card and encryption. Wanted to try Ubuntu, and love it so I'm staying with it. I have a Dell Latitude D-800 using a Broadcom mini-pci card. Installed it using the ndiswrapper as the fwcutter version didn't work for me. Tried following the walk through on setting it up in terminal mode, same thing. Can't get connected. I have no problem connecting to a wireless network that is open with no encryption, so for now i'm just hiding my essid and connecting with no encryption. I have searched through a lot of the forum, and on the internet, and found this problem listed in a lot of places, but with no real resolution. I guess my question is, is anyone working on this issue, and if so please point me in that direction :)

Patiently waiting, just wanted to see if it was being addressed, or if anyone can help me out. I can post more info about system if needed, just ask what you need.

Thanks much!

\\:D/

---

### Post by Milwbikerboy on 2009-08-18
Hey all, found somewhat of a decent fix. There appears to be a problem with encryption using ubuntu/kubuntu's network manager. Tried experiment, and it worked. This may not be the permanent fix for the  ubuntu package, but will work and get you running. Go to your Synaptic package manager and search for WICD. Its a wired and wireless network manager whose home is on sourceforge, but whose package is available in the ubuntu repo's. I am using a broadcom built in mini-pci wireless card on my Dell, nothing was fixing the connection trying to use encryption. If your connection is working on an open system without encryption, but not with encryption. Try the WICD package. NOTE: it WILL remove the gnome and/or KDE network manager when it installs. I have not tried the connection with both WEP and WPA, both WORKS!! YAHOO! :D 

Anyway, wanted to post this info for all those that have been stuck in same boat :)

---

