---
title: "Aircrack And Me"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by Geek9 on 2010-06-24
So after a long time coming I finally managed to install and configure aircrack, however I"m running into some troubles right now. It seems that I can never get enough data to decrypt the passphrase, I left my laptop next the router running all night and it still didn't get enough, and every time I try to do an injection attack it says my card is on channel 1, but the router is on channel 6. I have the code to the router this is a POC for me, any help you can offer will be great. I'm on Ubuntu 10.04, with the latest aircrack and the iwl3945 driver patch.

---

### Post by kevdog on 2010-06-25
Its been a long time since I monkeyed with aircrack, however there are several types of attacks.  I would try each of them.  You really need to do packet injection, and you can change the wireless channel that your virtual card listens on.

---

### Post by Geek9 on 2010-06-27
well tbh I'm just trying to capture data packets right now, and if I try injection it gives me this blasted error and it refuses to change the channel for me.

---

