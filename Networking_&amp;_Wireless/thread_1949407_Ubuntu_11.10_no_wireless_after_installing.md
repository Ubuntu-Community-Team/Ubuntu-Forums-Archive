---
title: "Ubuntu 11.10 no wireless after installing"
date: 2012-03-30
forum: Networking &amp; Wireless
---

### Post by xiaowei85 on 2012-03-30
Dear all

After installing Ubuntu 11.10, the wireless cannot work, showing:

"wireless is disable by hardware switch"

How can I solve this problem?

Many thanks

---

### Post by cyiucsy on 2012-03-30
Perhaps you can give us some more details about your platform?
and what does 'ifconfig' show?

---

### Post by Bill Z on 2012-03-30
I had the same problem when loading 11.10 on my laptop.  When loading I had eth0 connected for speed and I suppose the install didn't check for a wireless.  I'm not technical to really know why.

However, what I did was to re-install without the eth0 connected thinking it would use the wireless, which it did.  Now, both work just fine.

---

### Post by ts3 on 2012-04-01
> **xiaowei85 said:**
> "wireless is disable by hardware switch"

How can I solve this problem?

First thing I'd try, on general principles, is run in terminal

```
sudo rfkill unblock all
```

Then run

```
rfkill list all
```

to see if there's still a software/hardware block; if there's a hardware block I'd toggle the hardware switch (it's the F12 button on my hp laptop, YMMV) then run sudo rfkill unblock all again.  

If wireless is still not working or if rfkill list all shows a software block it would be best to post again with a bit more info about your set-up.  This is a good intro to troubleshooting wireless and gathering the necessary information (it's an 11.10 guide): [https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html](https://help.ubuntu.com/11.10/ubuntu-help/net-wireless-troubleshooting.html)

Cheers

---

### Post by kurt18947 on 2012-04-01
> **Bill Z said:**
> I had the same problem when loading 11.10 on my laptop.  When loading I had eth0 connected for speed and I suppose the install didn't check for a wireless.  I'm not technical to really know why.

However, what I did was to re-install without the eth0 connected thinking it would use the wireless, which it did.  Now, both work just fine.

If I understand correctly, that's how it's supposed to work.  Ubuntu will use a wired network connection (eth0) over a wireless network(wlan0 or similar) if there's a wired network available.  When you unplugged, the wired network was no longer available and the wireless came online.  Clever, that penguin. :p

---

### Post by Bill Z on 2012-04-02
> **kurt18947 said:**
> If I understand correctly, that's how it's supposed to work.  Ubuntu will use a wired network connection (eth0) over a wireless network(wlan0 or similar) if there's a wired network available.  When you unplugged, the wired network was no longer available and the wireless came online.  Clever, that penguin. :p

Yes.  I would think that it should work that way.  But it didn't.

Like I said, I had to re load the OS (not reboot) for the wireless to work.

---

