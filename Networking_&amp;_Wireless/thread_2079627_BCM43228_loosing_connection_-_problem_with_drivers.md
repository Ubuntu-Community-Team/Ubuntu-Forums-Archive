---
title: "BCM43228 loosing connection - problem with drivers"
date: 2012-11-02
forum: Networking &amp; Wireless
---

### Post by goozez on 2012-11-02
Hi,
I have a Broadcom Corporation BCM43228 802.11a/b/g/n Network Controler on Ubuntu 12.10. The system connects perfectly to my network, but after some random time I am unable to connect to any website although the NM states I am connected and I still have an IP address. After rebooting the NM would connect after a long time, but still no website is reachable. I have gone through a variety of threats on the internet but none did help me. By experimenting (loading/unloading/rebooting) I found a workaround (which worked every time) for my problem by:

```

sudo apt-get purge bcmwl-kernel-source
#reboot system
#after reboot:
sudo apt-get install bcmwl-kernel-source

```As you might guess it is pretty annoying to reboot every time I get this issue. I wish the network controler run without user interference.

I would be grateful for any help you may provide.

Regards 

Goozez

---

### Post by goozez on 2012-11-05
Update
I followed some posts involving changing the blacklists. I don't know which one did the job but now I only need to do:
```
 
sudo modprobe -r wl
sudo modprobe wl
```which didn't work earlier.  It is much better, although the controller still keeps disconnecting.

---

