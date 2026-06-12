---
title: "Flash doesn't work with chromium on Ubuntu 16.04"
date: 2016-06-20
forum: Multimedia Software
---

### Post by max-nedelchev on 2016-06-20
[COLOR=#242729][FONT=Arial]Hi,

According to [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash) after install of flashplugin-installer package flash should work in chromium, but mine doesn't. It installed libflashplayer.so into /usr/lib/flashplugin-installer and firefox works perfectly with it. However, chromium doesn't see this plugin. chrome://plugins/ show nothing. 

If i run "chromium-browser --ppapi-flash-path=/usr/lib/flashplugin-installer/libflashplayer.so" it see plugin, but on page with flash it says "Could not play".[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]libflashplayer.so: 11.2.202.626 chromium: Version 50.0.2661.102 Ubuntu 16.04 (64-bit)[/FONT][/COLOR]

---

### Post by chocolatey-squirrel on 2016-06-20
I have found Flash doesn't work with chromium, I use Chrome instead. Also be aware flash support is being dropped from many browsers soon.

---

### Post by howefield on 2016-06-20
> **chocolatey-squirrel said:**
> Flash doesn't work with chromium, try chrome instead.

Of course it does.

---

### Post by coffeecat on 2016-06-20
> **max-nedelchev said:**
> Hi,

According to [https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash) after install of flashplugin-installer package flash should work in chromium, but mine doesn't. It installed libflashplayer.so into /usr/lib/flashplugin-installer and firefox works perfectly with it. However, chromium doesn't see this plugin. chrome://plugins/ show nothing. 

It's odd that you should quote an Ubuntu wiki that recommends installing the package adobe-flashplugin, but you then install the different package flashplugin-installer. flashplugin-installer will not give you flash playing capability in Chromium. If you install flashplugin-installer for Firefox, you need to install pepperflashplugin-nonfree for chromium.

Far better though is to do what the quoted wiki page says. "Add the Canonical Partners software source, and install adobe-flashplugin." That will give you flash in both browsers. It will uninstall flashplugin-installer, but that's OK because the adobe-flashplugin package is much preferable.

Do you need any help with enabling the Canonical Partners repository?

---

### Post by max-nedelchev on 2016-06-20
Thanks, installing  adobe-flashplugin instead of flashplugin-installer made it work. Now chromium can play flash.

---

