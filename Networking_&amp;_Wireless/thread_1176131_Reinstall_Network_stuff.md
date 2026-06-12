---
title: "Reinstall Network stuff"
date: 2009-06-02
forum: Networking &amp; Wireless
---

### Post by alienjon on 2009-06-02
I upgraded kubuntu to 9.* something or other a month or so ago.  Since then I've found that I cannot connect to WPA networks via KNetworkmanager anymore.  (I could before the upgrade)  I did a bunch of stuff to try to connect to such networks, but it only ended up in me not being able to connect to anything via knetworkmanager.  At this point, I'm just not sure what to do.  I thought about just reinstalling altogether, but figured its worth posting first.

I was figuring that I could at least just re-install ubuntu networking, but I'm not sure what would be involved with that.  I can connect to nonWPA networks manually with iwconfig, but nothing automatic.

Google hasn't been helpful, really.  Any takers?

---

### Post by alienjon on 2009-06-02
Ok, stuff got added to my /etc/networking/interfaces that shouldn't have been there, but the WPA is still bad.

---

### Post by cak3 on 2009-06-02
Well... try reinstalling wpa-supplicant. You might also try using wicd (available in the repositories... just apt-get it) as the network manager isntead of the default, as on some cards the normal network manager has problems with WPA2-Enterprise (i.e. certificate-based authentication) networks.

Is the WPA network you are trying to connect to WPA2-Enterprise (like a university network or something)? Or you you have problems with any network using wpa encryption.

Would't hurt to try completely removing and reinstalling knetworkmanager either, if you haven't tried it already.

---

### Post by alienjon on 2009-06-03
The network is actually a wifi network I setup for my fiance's apartment, so just WPA-personal.  I can connect okay when I use a WEP key, and her Mac's (there's 2 of them) connect just fine so the network is okay.  Unfortunately, I won't be seeing her until this weekend, but I'll test these then and see where I can get.  Thanks :-)

Oh, I did want to ask, though, you mentioned trying to use wicd and to set it as the network manager, is that through system settings, or were you referring to a different way?

---

### Post by SuperSonic4 on 2009-06-03
wicd can be installed via the repos. It conflicts with KNetworkmanager so it will remove the latter and install itself. From there it's a system try app and I believe it adds itself to wherever kubuntu gets startup programs from.

I went with wicd because I didn't like the amount of room the plasmoid took up

---

### Post by alienjon on 2009-06-06
wicd worked perfectly.  Well enough, in fact, I'm thinking of trying it out on my desktop (which runs Gentoo)  Thanks for the help!

---

