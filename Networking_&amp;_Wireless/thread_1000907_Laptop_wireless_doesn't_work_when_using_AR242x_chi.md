---
title: "Laptop wireless doesn't work when using AR242x chipset  in 8.10"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by transverse_wave on 2008-12-03
Hi,

I've searched around alot and I've tried mant different things (though who knows if I've done them correctly) but there was one thing that finally allowed me to connect to my wireless network:
-Fresh install of 8.10 (x86)
-running this command:
sudo apt-get install linux-backports-modules-intrepid-generic

rebooting and enabling the ath5xxx driver and disabling the default one provided.

This allowed me to connect to the network, the next thing I did was run synaptic overnight to update all my packages. Reboot this morning to discover that I can't connect to my wireless network. I think my card is still enabled since I can see the option to connect to wireless networks when I left click on the network icon in the top-right; but the list of these networks isn't there anymore.

So I guess my question is: how do I diagnose this?

or

should I just do a clean install and not update my packages...?

The computer is a Compaq Presario laptop C757ca. I've got wired internet so I can run all sorts of commands in the terminal that require net access. Any help would be appreciated.

---

### Post by sanus|art on 2008-12-03
Not much a help here, but there is [madwifi]("http://madwifi-project.org/") project which main purpose is to develop "atheros" drivers. Try to see there maybe it'll help.

---

