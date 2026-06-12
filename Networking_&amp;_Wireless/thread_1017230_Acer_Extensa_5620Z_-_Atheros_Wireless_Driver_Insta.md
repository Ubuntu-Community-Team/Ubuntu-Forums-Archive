---
title: "Acer Extensa 5620Z - Atheros Wireless Driver Installation"
date: 2008-12-20
forum: Networking &amp; Wireless
---

### Post by patrickalexson on 2008-12-20
Hello, ive got a new system, the Acer Extensa 5620Z laptop with the internal Atheros Wireless Card. Im sorry, im not sure on the actual model, I would assume that its one of the more common ones. Im running 8.10 Ubuntu x86

Anyhow, I need someone to walk me through how to install the drivers.
Im not that familiar with the OS so walk me through slow please.

Here is what ive done,

Tried using the IFCONFIG command to see if my wireless card is present, only shows the LO (loopback?) and the eth0 which im guessing is my onboard NIC.

So...ive heard talk about madwifi drivers and a few other things but someone walk me through what to download, how to install, and from there, I know how to set up the connection.

Thanks!

---

### Post by patrickalexson on 2008-12-21
Any ideas anyone? I cannot use Ubuntu, as much as I would love to, if my wireless card doesnt work. Im extremely happy with this and so far, this is the ONLY problem I have encountered.

By the way, anyone know of any documentation that can sort of explain the OS folder structure? Id like to learn where certain things are and how everything is made up.

Thanks!!

---

### Post by hlina on 2008-12-21
> **patrickalexson said:**
> Hello, ive got a new system, the Acer Extensa 5620Z laptop with the internal Atheros Wireless Card. Im sorry, im not sure on the actual model, I would assume that its one of the more common ones. Im running 8.10 Ubuntu x86

Anyhow, I need someone to walk me through how to install the drivers.
Im not that familiar with the OS so walk me through slow please.

Here is what ive done,

Tried using the IFCONFIG command to see if my wireless card is present, only shows the LO (loopback?) and the eth0 which im guessing is my onboard NIC.

So...ive heard talk about madwifi drivers and a few other things but someone walk me through what to download, how to install, and from there, I know how to set up the connection.

Thanks!

Hello,
I have the same configuration and I had the same problem, after whole day of seeking the internet I finally found what I have been looking for and it works for me perfectly see:

[http://ubuntuforums.org/showthread.php?t=816780](http://ubuntuforums.org/showthread.php?t=816780)

PS: It works even if I have Ubuntu 32bit ;)

Hope that helps!

Regards

---

### Post by hlina on 2008-12-22
> **patrickalexson said:**
> 
By the way, anyone know of any documentation that can sort of explain the OS folder structure? Id like to learn where certain things are and how everything is made up.


OS folder structure is described e.g. here:

[http://library.gnome.org/users/user-guide/stable/nautilus-directories-file-systems.html.en](http://library.gnome.org/users/user-guide/stable/nautilus-directories-file-systems.html.en)

This also could be your guidepost if you're new to Ubuntu:

[https://help.ubuntu.com/8.10/index.html](https://help.ubuntu.com/8.10/index.html)

Enjoy!

---

