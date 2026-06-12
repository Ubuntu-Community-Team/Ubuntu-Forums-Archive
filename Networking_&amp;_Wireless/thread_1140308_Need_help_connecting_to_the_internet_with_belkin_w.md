---
title: "Need help connecting to the internet with belkin wireless pci card"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by joshischill on 2009-04-27
So I just installed ubuntu 9.04 on my dell desktop and am having a lot of trouble connecting to my wireless network. I have a belkin wireless G pci card. Under SYSTEM>ADMINISTRATION>HARDWARE DRIVERS I have the "Alternate Atheros madwifi driver" activated.  The computer is detecting the wireless network and I have entered the WAP2 password. It looks like it should work... but it will not connect, the icon in the top menu bar shows that it is trying to connect, but after a minute it stops and says that there is no internet connection.

This is the first time I have used a linux os and I have to admit I am pretty lost. If someone can give me the "idiots guide" as to what I might need to it would be greatly appreciated. Thanks.

---

### Post by pytheas22 on 2009-04-27
You may have better luck connecting if you install wicd, an alternative connection manager.  You can install wicd by typing these commands (these require you to already be connected to the Internet via the wire; if that's impossible, let me know):
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch it from the Applications>Internet menu, and try connecting again.

If wicd doesn't work, please open a terminal from the Applications>Accessories menu, run the following commands and post the output here:
```

lspci -nn
sudo iwlist scan
uname -rm
lshw -C Network
```

---

