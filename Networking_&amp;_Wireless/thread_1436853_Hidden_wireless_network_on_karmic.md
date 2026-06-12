---
title: "Hidden wireless network on karmic"
date: 2010-03-23
forum: Networking &amp; Wireless
---

### Post by alkyestrela on 2010-03-23
Hi,
My Karmic can't detect hidden wireless networks, this bug's workaround is to install network-manager-gnome, according to the kubuntu homepage.
I installed the package, however now there is another problem.
First, nm-applet cannot detect the hidden network automatically after reboot.
So, I have to delete the connection entry, and enter the network name and password every time, but sometimes it works, sometimes it just doesn't, I have completely no idea why. It seems very random to me. Sometimes it just does autoconnect flawlessly, very rarely though. Some other times it can detect the network but authentication fails, while the password is actually correct.
I have all the official updates till now.
I'm very confused and annoyed because now it takes me a lot of time just to connect. I uninstall network-manager, install wicd, just to connect, reboot, remove wicd and try nm-applet again, then knetworkmanager. Somehow after a while it will work, either with nm-applet, wicd, or knetworkmanager. I just don't know why.
I really kubuntu, this is the only problem I have with it, but it is very annoying. Windows 7 works flawlessly, autoconnecting and all.


lspci gives the following:
```
01:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
        Subsystem: Acer Incorporated [ALI] Device 029b
        Flags: bus master, fast devsel, latency 0, IRQ 28
        Memory at 93500000 (64-bit, non-prefetchable) [size=256K]
        I/O ports at 2000 [size=128]
        Capabilities: <access denied>
        Kernel driver in use: atl1c
        Kernel modules: atl1c

02:00.0 Network controller: Intel Corporation WiFi Link 100 Series
        Subsystem: Intel Corporation Device 1305
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at 92500000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

```

---

