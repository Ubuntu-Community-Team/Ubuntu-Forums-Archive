---
title: "really poor wireless network connectivety"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by spiked4life on 2008-12-25
Very recently I converted one of my desktops from Win XP to Ubuntu 8.10. I have it up and running and everything seems to be working but the wireless network card is performing really poorly. I am able to connect maybe 1 out of every 20 attempts. However when it actually connects the signal is strong and i can download at full speed. 

Any reason why it should be so extremely difficult to connect to the network in the first place? Anything I can do about it? I I can't remember having these problems when I was running win XP. Would be swell to iron these kinks out.

---

### Post by pytheas22 on 2008-12-25
It might work better if you install wicd, an alternative connection manager.  To install it, connect to the Internet and run these commands:
```

echo 'deb http://apt.wicd.net hardy extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch wicd from the Applications>Internet menu.  Do you have better luck connecting this way?

If not, please post the output of these commands so that we can try other solutions:
```

lshw -C Network
uname -m
lsusb
lspci -nn
```

N.B.: installing wicd will force you to uninstall Network Manager (the default connection manager in Ubuntu).  If you ever want NM back, just type:
```

sudo apt-get install network-manager-gnome
```

---

