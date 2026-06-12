---
title: "What I Don't Like About NetworkManager"
date: 2006-03-10
forum: Networking &amp; Wireless
---

### Post by groggyboy on 2006-03-10
So I was using gtkwireless to manage my internet for a while, but i've recently switched to NetworkManager - it has more (altho crappy) support for WPA, plus it has a better GUI (in my opinion).

I have some issues with nm, tho:
1) it always starts up by connecting to a wired connection! anybody know of a way to prevent it from doing this?  ideally, i would like it to automatically connect wirelessly to whichever of my preferred networks are available, before using my wired connection (which i never EVER use anyway).
2) does it always have to ask for that DAMN keyring password?  someone mentioned using gnome-password-keyring in another thread, but in that same thread someone mentioned that gnome-password-keyring doesn't even work properly!
3) is there anyway to get native WPA support (via wpa_supplicant) in networkmanager, without the use of scripts or a kernel upgrade (i've seen forums/HowTos explaining both)?

hmmm, maybe gtk-wireless isn't that bad after all. the GUI was kinda nice! ;)
cheers!

---

### Post by kwaanens on 2006-03-10
[QUOTE=groggyboy]3) is there anyway to get native WPA support (via wpa_supplicant) in networkmanager, without the use of scripts or a kernel upgrade (i've seen forums/HowTos explaining both)?[/QUOTE]

WPA-integration is in newer versions of NetworkManager. Dapper has 0.5. (Breezy 0.4), possibly WPA is integrated in 0.5.
See here: [http://www.iceni.org/cgi-bin/blosxom.cgi]("http://www.iceni.org/cgi-bin/blosxom.cgi") for more on WPA in Network-manager

- Ketil

---

