---
title: "Wireless connection stops working"
date: 2013-03-02
forum: Networking &amp; Wireless
---

### Post by mathguy54 on 2013-03-02
I have some issues with my wireless connection. My wireless connection stops working for an hour or so, then starts working for about a minute, then drops again. I don't know what to do to fix this! Can someone help?

Computer: Dell XPS L702-X
Ubuntu 12.04 LTS

If you can, please make it as simple as possible.

---

### Post by gordintoronto on 2013-03-02
After a reboot, how long does it work before it stops working? What wireless hardware?

Open a terminal, enter the command: lspci
It should produce a dozen or so lines of output, and one of them should include "802". That's your wireless adapter. Copy/paste that line into your response.

---

