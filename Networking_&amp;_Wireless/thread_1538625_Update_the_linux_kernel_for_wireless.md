---
title: "Update the linux kernel for wireless"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by genericuser8133 on 2010-07-25
Hi,
I have a sl510 thinkpad with a realtek 8172 network controller. I know that I need to "just update linux kernel from lucid-updates" to get the card to work, but I don't know how to do that. I got this from:

[https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172]("https://help.ubuntu.com/community/WifiDocs/Device/Realtek%208172")

Thanks!

---

### Post by Bachstelze on 2010-07-25
Normally, you should have the latest version from lucid-updates already.  What's the output of

```
dpkg -l | grep linux-image
```

---

### Post by genericuser8133 on 2010-07-25
2.6.32-21.32 for "Linux kernel image"
Again, 2.6.32-24.38 for "Linux kernel image"
And 2.6.32-24.25 for "Generic linux kernel image"

(Sorry, but since the internet isn't working on the thinkpad, I had to transcribe this in an abbreviated format)

---

### Post by Bachstelze on 2010-07-25
Okay, so yes, you have the latest one.

---

### Post by genericuser8133 on 2010-07-25
Then is there another way that I can get the wireless card to work? The networkmanager applet just says "Disconnected" under the "Wireless Networks" label.

---

