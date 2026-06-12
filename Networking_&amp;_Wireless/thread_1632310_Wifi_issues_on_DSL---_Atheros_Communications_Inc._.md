---
title: "Wifi issues on DSL--- Atheros Communications Inc. AR5001 Wireless"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by tuxlord43 on 2010-11-27
I have recently had a HDD take a poop on me, and since I am too stubborn to go out and pay for a new one, I have decided to try out UbuntuLive on a pendrive, works brilliantly besides the fact it crashes quite often. Now I have turned to DamnSmall Linux, also works beautifully. But... I cannot seem to connect to my wireless network, which I am sure is because I do not have any drivers for my Wifi adapter. I have tried the wlanwrapper, but since there is no HDD I am sure this is pointless. I have tried DriverLoader but it doesn't provide any drivers for my card, also I have tried Madwifi, but the darn thing won't make install! I am at a loss! I could really use the advice of a linux guru at this point! Thank you to all those who reply.

---

### Post by cybergnome on 2010-11-28
If you use one of this year's versions of Ubuntu, the new madwifi is included.  You should be able then to configure the device with IWCONFIG.

---

### Post by tuxlord43 on 2010-11-28
And thats one of my issues...I am using 10.10. UbuntuLive crashes quite often! DSL Doesn't.

---

### Post by uncaspi on 2010-11-28
I have ubuntu 8.04 live on a pen drive on my brand new Acer Timeline X without no problems. The wireless driver I have stored on /media/casper-rw dir and I have to copy the driver to /lib/modules/$(uname -r)/kernel/drivers/net/wireless and sudo depmod -a and  sudo modprobe <driver> every time I have booted . The clue is to find the right driver for your card.

---

### Post by cybergnome on 2010-11-28
OK, I guess Ubuntu 10.10 is too much for the pendrive.  The (new) madwifi with the ath5k driver (included in Ubuntu 9.10 versions and later) is the proper software for your chipset.

Visit madwifi.org and see what you need to download and install for Damn Small Linux.  I can't help you there.

---

