---
title: "Can't enable wireless"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by Luis1 on 2011-11-19
I'm running Ubuntu 11.10 on a Lenovo B575, with an Atheros wireless card.

Under the dropmenu, I'm getting:
Wired Network
disconnected
Wireless Networks
Wireless is disabled
VPN Connections >
(check)Enable Networking
Enable Wireles
Connection Information
Edit Connections

When I click "Enable Wireless", the menu closes, and when I open it back up, Wireless is still disabled.

I have the driver installed, being ath9k.

I can only connect to the internet, via wired connection.

Help?

---

### Post by matt_mccarron on 2011-12-13
I'm in the exact same boat!

Please help!

---

### Post by pastalavista on 2011-12-13
Post the output from terminal ```
lsmod
```

---

### Post by pastalavista on 2011-12-14
> **matt_mccarron said:**
> I'm in the exact same boat!

Please help! I got an email notification with your lsmod output. Don't see it here now, though.

You need to unload the acer-wmi wireless module ```
sudo rmmod -f acer-wmi
sudo rfkill unblock all
```

The full solution is in this post: [http://ubuntuforums.org/showthread.php?t=1745317]("http://ubuntuforums.org/showthread.php?t=1745317")

---

