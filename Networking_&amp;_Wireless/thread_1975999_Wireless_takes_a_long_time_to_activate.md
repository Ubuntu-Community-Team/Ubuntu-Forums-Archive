---
title: "Wireless takes a long time to activate"
date: 2012-05-08
forum: Networking &amp; Wireless
---

### Post by x-shaney-x on 2012-05-08
On startup or resuming from suspend, it takes a pretty long time to  activate, around 10 to 15 seconds.
On Windows it comes on instantly.

I posted on kubuntu forums (takes even longer on kubuntu) and was given this advice:
```
sudo sh -c "echo 'options ath9k nohwcrypt=1' >/etc/modprobe.d/ath9k.conf"
```
It didn't make any difference though.

```
Network controller: Atheros Communications Inc. AR9287 Wireless Network Adapter (PCI-Express) (rev 01)
```

---

