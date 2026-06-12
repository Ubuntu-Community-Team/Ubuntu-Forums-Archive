---
title: "Network Connections.. bug?"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by MichaelLerch on 2012-02-13
I'm connected to my wireless network perfectly but Ubuntu 11.10 dock doesn't show anything. It shows the wireless signal meter blank and when I click on it says "Wireless Networks: device not managed".. but clearly I am online.

Any ideas?

---

### Post by Iowan on 2012-02-13
I don't suppose you configured the wireless via */etc/network/interfaces*? In previous versions, Network Manager wouldn't "manage" devices configured there.

---

### Post by MichaelLerch on 2012-02-13
I actually found my fix here: [http://askubuntu.com/questions/69480/wireless-networks-device-not-managed](http://askubuntu.com/questions/69480/wireless-networks-device-not-managed)

I'm sure this is what you were referring to and it was something I didn't think about when I installed 11.10 but it's working now. Thank you so much! :)

---

### Post by Iowan on 2012-02-13
Glad you got it fixed.
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

### Post by MichaelLerch on 2012-02-13
Absolutely my good sir. :)

Out of curiousity though, is there a way to remove that dock interface? I read about GNOME 3 but it's not really supported and I would prefer the classic interface over the knew Unity interface. At least the ability to scale the dock would be nice.

---

