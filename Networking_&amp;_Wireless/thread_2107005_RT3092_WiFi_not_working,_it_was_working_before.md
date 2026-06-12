---
title: "RT3092 WiFi not working, it was working before"
date: 2013-01-20
forum: Networking &amp; Wireless
---

### Post by zyngawow on 2013-01-20
I swapped one of my HDDs and then I put the one I had first back. Then, Grub wasnt working, so I had to fix it. After I fixed it, my WiFi wasnt working. It was before. It appears as unavailable. Here are some logs:

[http://pastebin.com/YpcKnfkZ](http://pastebin.com/YpcKnfkZ)

On the logs, it appears as disabled, but I have it enabled.

sudo ifconfig wlan0 up returns: SIOCSIFFLAGS: Input/output error

Can anyone help me?

---

### Post by zyngawow on 2013-01-20
I found this on the syslog.1

NetworkManager[830]: <info> (wlan0): deactivating device (reason 'managed') [2]
NetworkManager[830]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]

---

