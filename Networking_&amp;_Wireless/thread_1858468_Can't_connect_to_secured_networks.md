---
title: "Can't connect to secured networks"
date: 2011-10-12
forum: Networking &amp; Wireless
---

### Post by bugscripts on 2011-10-12
I get a "Bad Password" error when trying to connect to any WPA or WEP networks. Unsecured networks work fine.

I'm using wicd and the authentication settings provided by the network administrator.

---

### Post by SeijiSensei on 2011-10-12
I never have a problem connecting to WPA2 networks with the native network manager in Kubuntu, at least in versions 10+.  People had problems with KDE 4.0's implementation of its network manager, which often led to the suggestion of using wicd instead.  However current versions like KDE 4.5+ work just fine.

Which Kubuntu is this?  I've found 10.10 to be the best Kubuntu release yet.

---

### Post by bugscripts on 2011-10-12
> **SeijiSensei said:**
> I never have a problem connecting to WPA2 networks with the native network manager in Kubuntu, at least in versions 10+.  People had problems with KDE 4.0's implementation of its network manager, which often led to the suggestion of using wicd instead.  However current versions like KDE 4.5+ work just fine.

Which Kubuntu is this?  I've found 10.10 to be the best Kubuntu release yet.

I'm using 11.04.

I switched to wicd because I had trouble getting KNetworkManager to recognize my wireless interface. The "Wireless" tab was dimmed even when everything else seemed to be set up properly (I could type iwlist scan to see all available networks.)

---

### Post by bugscripts on 2011-10-13
Finally got it work with the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=1600498"). Couldn't get KNetworkManager to log in but the Gnome version works.

---

