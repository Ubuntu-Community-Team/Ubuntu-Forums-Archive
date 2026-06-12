---
title: "wireless hard block set for HP Pavilion"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by dsa42 on 2010-11-01
I had wireless up and running for several months on a new laptop (HP Pavilion Entertainment PC). Suddenly, a week ago, the wireless came up disabled (and continues to come up disabled), and the "enable wireless" option in the NetworkManager Applet 0,8 is greyed out. I ran "rfkill list" (I found that while doing a google search for this problem), and "hard block" says "yes."

Removing battery and power and hitting the boot-up button did not reset this. Neither did "sudo rfkill unblock 0" where "rfkill list" shows identifier 0 as "0: phy0: Wireless LAN"

I upgraded to 10.10, but it didn't help.

Why is Ubuntu (10.04 LTS and 10.10) doing this? How can I get the wireless re-enabled?

Also, as long as we're talking about this, normally at log on, the wireless is enabled. I often disable it through the NetworkManager Applet while I'm working on a wired connection. If I suspend or hibernate, when I come back, the wireless in enabled again. Should I submit a bug report?

Thanks for any help anyone can give.

---

### Post by dsa42 on 2010-11-01
I solved this accidentally.  The wireless light on the laptop is actually a switch.  It is a very sensitive heat sensor.  I don't need to push it, just run my fingers near it.  This sets the hardware switch for the wireless to "block."

---

