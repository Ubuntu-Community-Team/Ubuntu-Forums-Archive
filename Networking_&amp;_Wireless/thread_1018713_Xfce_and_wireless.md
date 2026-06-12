---
title: "Xfce and wireless"
date: 2008-12-22
forum: Networking &amp; Wireless
---

### Post by skewray on 2008-12-22
I just installed xubuntu onto my Acer Aspire netbook.  There were no problems, and the wireless driver appears to be running.  In Xfce, I get an icon in the upper bar for the wired ethernet, but there is no icon for the wireless, and I can't find anything in the menus that mention wireless.  I don't see how to set up the wireless.  I suspect that there is a package missing.

Any help appreciated!

Brian

---

### Post by prshah on 2008-12-22
> **skewray said:**
> I get an icon in the upper bar for the wired ethernet, but there is no icon for the wireless

Have you tried clicking that icon? It should then display a list of detected wireless networks.

If it doesn't, can you open a terminal (Applications-Accessories-Terminal) and post the output of ```

iwconfig
lspci | grep -i -E wireless\|ethernet
lshw -C network
```

---

### Post by skewray on 2008-12-24
After a few reboots to make /tmp and /var/tmp reside in memory, the wireless started working spontaneously.  Problem solved, I guess.

Brian

---

