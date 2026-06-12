---
title: "can't detect my wireless network"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by DrAgãO on 2009-02-18
I start working with ubuntu, still learning. It's is happening the funniest thing, and i say funny because for it doesn't make any sense, butt what do i know :O
I installed the ubuntu on my laptop (compal) and it doesn't detect my wireless network, 
it detects all my neighbours so wireless card working, 
if change SO do win XP, it detects and connect perfectly, besides I have 2 other PC's connect to the router wired and wireless whit no problems so it's not from the router a think.
I've successfully connected my laptop in ubuntu do other wireless networks whit no probs.
My router is a Draytek 2800VG, it supports more than one protocol butt to avoid conflicts I'm using 802.11b(already tried g and superG), security WPA-PSK 
does some one knows why this happens?

---

### Post by x33a on 2009-02-19
open a terminal and post the output of
```
iwconfig
iwlist scan
```

since you can detect other people's networks, i assume that your card is working. one more thing, are the other networks encrypted?

---

