---
title: "ath9k USB device dropping connection soon after resuming 13.04"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by kurt18947 on 2013-05-18
Here is a problem that has appeared in my 13.04 install since the latest image update.  The wireless would work after resuming for a few minutes but would stop working.  The wireless indicator would not indicate a disconnect (gnome-shell on Ubuntu) but the activity indicator light on the adapter (Netgear WNA1100 would not be illuminated and I'd be prompted for either my WiFi password, SUDO password saying networking settings have changed or both.  The latter was somewhat alarming; did I have a nasty trying to hijack my network?  

I unplugged the Netgear adapter, waited a couple seconds, plugged it back in and the activity light came on. Network connectivity resumed and all seemed well.  Hmmm, this seems familiar.  RTL-8192SU based  adapters would do the same thing after resuming from suspend except they  wouldn't work at all after suspend, ath9k adapter would sorta work for a little while.  Nevertheless, I decided to try the fix that solved the RTL-8192SU problem.  In a terminal I entered the following:

```
sudo gedit /etc/pm/config.d/config

```

and added the following line:

```

"SUSPEND_MODULES=ath9k_htc"

```

After a few suspend/resume cycles all seems well.  I also came across an interesting tidbit while researching this.  One source claimed that the request to re-enter a network password did not necessarily mean that the network password entered was incorrect, only that the system was unable to establish a network connection.  The reason for the inability to establish a network connection may have nothing to do with the network password.

Edit:  Adding the suspend modules code also fixed a suspend/resume problem with my Saucy daily install.

---

