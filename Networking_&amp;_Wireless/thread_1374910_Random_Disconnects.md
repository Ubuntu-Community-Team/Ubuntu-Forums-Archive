---
title: "Random Disconnects"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by adam22 on 2010-01-07
Hey, guys. Recently, I've been getting random disconnects in Ubuntu 9.10. I don't know why since I did not have a problem with the previous version or the first couple of weeks while using Karmic. I cannot reconnect without restarting either, even when I provide the correct security key. I have no clue what is causing this, but it's become pretty crippling, as sometimes it happens within five minutes of turning the laptop on, and other times it might come six hours later.

Here's some information about the wireless card:

```
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```

System Specifications:
AMD Athlon X2 Dual Core
ATI Radeon 3200 HD Graphics
4 GB DDR2 RAM
64 Bit Ubuntu 9.10
Netgear Rangemax G Router

---

### Post by gh4ever on 2010-01-07
I have the exact same problem. I just switched from Karmic on one computer to Mint 8 on a new computer. I have the exact same network card, which may be the problem, as I didn't have that network card on my last computer and it worked fine.

---

### Post by dougwyl on 2010-01-07
> **adam22 said:**
> Hey, guys. Recently, I've been getting random disconnects in Ubuntu 9.10. I don't know why since I did not have a problem with the previous version or the first couple of weeks while using Karmic. I cannot reconnect without restarting either, even when I provide the correct security key. I have no clue what is causing this, but it's become pretty crippling, as sometimes it happens within five minutes of turning the laptop on, and other times it might come six hours later.

Here's some information about the wireless card:

```
09:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
```System Specifications:
AMD Athlon X2 Dual Core
ATI Radeon 3200 HD Graphics
4 GB DDR2 RAM
64 Bit Ubuntu 9.10
Netgear Rangemax G Router

This might be the solution you are looking for. Do a search for this thread *Wireless problems - ath9k on Ubuntu 9.10.*  It worked perfectly for me.  It's now been more than 24 hours and I haven't disconnected and my signal strength is 100%.

---

### Post by adam22 on 2010-01-07
I will look into that, but my signal strength is always pretty low. There's no packet loss and it performs fine and I get 100% in Windows, but it always appears pretty low. between 30 and 60%.

---

### Post by gh4ever on 2010-01-08
Right now I'm trying a *sudo apt-get install linux-backports-modules-karmic *followed by a* sudo apt-get install linux-backports-modules-wireless-karmic-generic* which seemed to work for most people on this thread: [http://ubuntuforums.org/showthread.php?t=1316126](http://ubuntuforums.org/showthread.php?t=1316126)
Apparently it's a Linux kernel bug.
Good luck, guys!

---

### Post by adam22 on 2010-01-14
I reluctantly tried it but I do think it has helped. It's only been about 15 minutes but no disconnect and I'm downloading much faster than I had been and signal strength is also a little better.

---

### Post by fosschick on 2010-01-27
> **gh4ever said:**
> Right now I'm trying a *sudo apt-get install linux-backports-modules-karmic *followed by a* sudo apt-get install linux-backports-modules-wireless-karmic-generic* which seemed to work for most people on this thread: [http://ubuntuforums.org/showthread.php?t=1316126](http://ubuntuforums.org/showthread.php?t=1316126)


This also worked for me.  I'm now at 2.6.31-17-generic using ath9k on an EeePC 1005HA and wireless is working fine.

---

