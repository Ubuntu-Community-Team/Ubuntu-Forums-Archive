---
title: "ndiswrapper stops working after update - belkin 54g"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by adamjacobs173 on 2010-10-23
Hi all,

I'm trying to get internet set up on my grandad's laptop (sony pcg-f590), which has a fairly old pcmcia belkin 54g wireless card. I've installed the relevant bcmwl5a.inf driver through ndiswrapper, and for a time wireless worked so I installed updates through update manager. however after restarting the network manager menu comes up with "wireless networks disconnected" and no list of networks (I know there are because my laptop works and his is sitting next to the router!). The light is on on the network card so I know the laptop is talking to it.

Unplugging and replugging the card does nothing, and neither does restarting again.
What should I do?

Adam

---

### Post by cavalier911 on 2010-10-23
A kernel update can break ndiswrapper. Hold down the **shift** key on reboot after bios to bring up the grub2 menu. If you upgraded the kernel the previous version kernel should be listed in addition to the new one.Use the arrow keys to highlight and boot into previous kernel. See if the wireless works now.

If there was no kernel update or booting into the previous version didn't fix the wireless.

Open terminal and post the output from entry's matching the date the wireless broke:
```
cat /var/log/dpkg.log | grep upgrade

```

---

