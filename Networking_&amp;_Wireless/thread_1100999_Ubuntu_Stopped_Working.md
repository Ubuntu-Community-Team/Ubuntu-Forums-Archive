---
title: "Ubuntu Stopped Working"
date: 2009-03-19
forum: Networking &amp; Wireless
---

### Post by BigDaveyJ on 2009-03-19
Well, I restarted my computer today and it seems my WiFi has stopped working on my laptop. It was working for around 3 days, never turned the laptop off, to get it working, I needed to use the linux backport modules, (explained in this thread: [http://ubuntuforums.org/showthread.php?t=1024472](http://ubuntuforums.org/showthread.php?t=1024472) ) Can anyone help me figure out the problem?

---

### Post by pytheas22 on 2009-03-20
Please post the output of these commands:
```

lspci -nn
lshw -C Network
sudo iwlist scan
dmesg | grep -e wlan -e ath
lsmod | grep ath
```

---

### Post by BigDaveyJ on 2009-03-21
Sorry it took so long, I was on Vista, I gave up until I had an idea..... Which is temporarily working.

[http://pastie.org/422991](http://pastie.org/422991)

That all of them.

---

### Post by pytheas22 on 2009-03-21
According to your dmesg output, it looks like your device is recognized, but you can't connect to a network.  Is that what's going on?  Or are you unable to see wireless networks at all?

If you can't seem to connect, you might have better luck if you use [wicd]("http://wicd.sourceforge.net") instead of NetworkManager.  The messages about 'deauthenticating by local choice' are related to a bug in NetworkManager, I believe.

---

