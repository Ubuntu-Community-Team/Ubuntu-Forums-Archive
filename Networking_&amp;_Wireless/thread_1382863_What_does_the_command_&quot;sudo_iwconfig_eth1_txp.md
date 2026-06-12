---
title: "What does the command &quot;sudo iwconfig eth1 txpower off &quot; do?"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by alvin4 on 2010-01-16
Just wondering. Thanks! :)

---

### Post by chili555 on 2010-01-16
From *man iwconfig*:> txpower
              --- snip ---
              In addition, on and off enable and disable the radio, and auto
and  fixed  enable  and disable power control (if those features are available).
              Examples :
                   iwconfig eth0 txpower 15
                   iwconfig eth0 txpower 30mW
                   iwconfig eth0 txpower auto
                   iwconfig eth0 txpower offIt would seem that the result of your quoted command is to turn the radio off, that is, disable the wireless.

---

### Post by alvin4 on 2010-01-16
> **chili555 said:**
> From *man iwconfig*:It would seem that the result of your quoted command is to turn the radio off, that is, disable the wireless.Thanks for the info! :)

---

