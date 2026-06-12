---
title: "Broadcom BCM4352 WiFi Not Working Following Reboot"
date: 2020-01-10
forum: MINT
---

### Post by dpdamato-optonline on 2020-01-10
[COLOR=#000000][I]I just installed a Broadcom BCM4352 wifi on my Optiplex 9010 AIO running Linux Mint 19.3 (Ubuntu 18.04) and am using the bcmwl-kernel-source driver.  It works well and is very fast, except that it requires a "sudo modprobe wl" every time I reboot. I've seen others suggest adding wl to the /etc/modules file, and I did so, but it made no difference.  Any other suggestions?

Thanks for any guidance you can provide.

[/I][/COLOR]

---

### Post by chili555 on 2020-01-11
I think we should first find out why it doesn't load automagically as expected and why it doesn't even help to add it to /etc/modules!

Please provide the wireless info as described here. We hope we shall see and fix the problem: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by dpdamato-optonline on 2020-01-11
Thanks Chili --- wireless-info.tar.gz attached.

---

### Post by jeremy31 on 2020-01-11
Moved to Mint

You might want to remove ndiswrapper, that is why you need to sudo modprobe wl

---

### Post by dpdamato-optonline on 2020-01-11
Jeremy,

Removed ndiswrapper, but no change --- still requires sudo modprobe wl.  Thanks anyway.

---

### Post by jeremy31 on 2020-01-11
Post new wireless script results please

---

### Post by chili555 on 2020-01-11
> Removed ndiswrapper, but no change --How did you do so? I hope with:

```
sudo apt purge ndiswrapper*
```Followed by a reboot. If you did something different, please try this and then post a new wireless info as requested.

---

### Post by dpdamato-optonline on 2020-01-11
That was it!   [I had only used the Software Manager.]  Thank you very much! Wifi now works great.

---

### Post by chili555 on 2020-01-11
> **dpdamato-optonline said:**
> That was it!   [I had only used the Software Manger.]  Thank you very much! Wifi now works great.Awesome! Glad it's working. Please use Thread Tools at the top to mark Solved. The searchers will appreciate it.

---

