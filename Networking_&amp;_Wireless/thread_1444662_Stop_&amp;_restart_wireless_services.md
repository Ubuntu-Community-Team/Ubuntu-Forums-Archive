---
title: "Stop &amp; restart wireless services"
date: 2010-04-01
forum: Networking &amp; Wireless
---

### Post by pycoed on 2010-04-01
Xubuntu 9.10 on a DELL Inspiron 1150.
I have a problem with intermittent dropping of my wireless connection ( see Belkin 7010 thread).Once dropped, the wireless will NOT reconnect (It just sits there saying "connecting" but never does) Same happens if I manually disconnect - I can never re-connect. On rebooting it will reconnect fine & all is well for sometimes 4 hrs...
How can I kill all wireless services & restart them without having to reboot the laptop?

---

### Post by sparky-steve on 2010-04-02
Have you tried

```
sudo /etc/init.d/networking restart
```

?

---

### Post by pycoed on 2010-04-02
Cheers, Steve I'll give it a go next time it freezes

---

### Post by pycoed on 2010-04-03
> **sparky-steve said:**
> Have you tried

```
sudo /etc/init.d/networking restart
```

?
Doesn't do the trick - I still need to reboot. any other ideas?

---

