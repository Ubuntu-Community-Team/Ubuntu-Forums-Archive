---
title: "Intrepid network-manager behaves strangely"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by ubuntergeist on 2008-12-20
Hello,

My wireless chip is fully supported and I can connect to the internet. 

However network-manager doesn't connect me automatically when I turn on my computer, it keeps asking me for my passphrase. But wait I don't have to enter it, I just have to click on "Cancel" and it connects me as if nothing happened.

In addition, when I log out (or suspend my PC) network-manager refuses to connect me. I have to unload the wireless module and reload it (with modprobe) to be able to reconnect the PC.

BTW, my system is up to date and I didn't modify my system's parameters. It is a vanilla 64-bit ubuntu intrepid.

I've heard many guys complaining about that but none had a solution.

Is there any workaround ?

thanks a lot.

---

### Post by Aearenda on 2008-12-20
The problem arises because in 8.10 NM doesn't always give the wireless drivers enough time to associate. Second time around, it usually works. I think there was an update that was supposed to ease this, but you should already have that. Plenty of threads around on this topic, as you say. See [Bug 272185]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/272185").

For reconnecting after suspend, add the name of the driver to the end of the file /etc/pm/config.d/00sleep_module, like so (assuming you use ath_pci, for example):```
SUSPEND_MODULES="ath_pci"
```This causes the module to be unloaded on suspend, and reloaded on wake. ([This post]("http://ubuntuforums.org/showpost.php?p=6264243&postcount=8") shows how to do this if you need it)

I can't say why it won't work on logoff/logon.

---

### Post by ubuntergeist on 2008-12-21
thanks a lot Aearenda :)

---

