---
title: "envy is missing dependencies in kubuntu"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by Vodkayum on 2007-06-24
envy is missing dependencies in kubuntu. I ran the deb for envy and it says its missing dependencies. I recently ran same package in ubuntu and had no problems. How can I make this work in Kubuntu?

---

### Post by hakre on 2007-07-08
[QUOTE=Warning]Finally I would not recommend to execute Envy on a Kubuntu System afterall. The Version I'm reporting my experiences is envy_0.9.5-0ubuntu5_all.deb.[/QUOTE]

hi vodakum. i experienced the same but also read about a warning/info message to use "apt-get -f install".  **(Warning do not do this)** I executed this command after running envy in textmode and before rebooting the machine. 

well all this did not work out. screen was black afterwards on the X-console (is it named that way?). I then used the uninstall option of envy but the display was staying black.

I gave envy another chance with option 6 (uninstall all) but this was useless as well and just for completing this documentation.

since envy makes a backup file of the xorg.conf I was able to restore my old configuration. this finally brought my desktop back.

Then I wondered wether I can fully remove the envy.deb installation or not. **(Warning do not do this)** I removed it with the Debian Package Manager. Afterwards my Bluetooth Mouse was not working any longer and I could not open the Adept Package Manger. I now try to re-install the Packaging System and maybe the whole System.

Finally I would not recommend to execute Envy on a Kubuntu System afterall. The Version I'm reporting my experiences is envy_0.9.5-0ubuntu5_all.deb.

/EDIT: FYI: after one reboot adept did work again and after another one my bluetoothmouse did as well.

---

