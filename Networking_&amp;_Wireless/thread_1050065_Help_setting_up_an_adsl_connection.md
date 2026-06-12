---
title: "Help setting up an adsl connection"
date: 2009-01-25
forum: Networking &amp; Wireless
---

### Post by aquavitae on 2009-01-25
I an trying to set up a connection to the internet. The modem/router is a d-link dsl-2500u and the isp is Paradigm Solution in south africa. I can get to the modem configuration screen through firefox, but i can't actually connect to the internet. Ifconfig shows 2 devices: eth0 and lo. I can ping the modem, but nothing external.

Does anyone have any suggestions of what i'm doing wrong?

Edit: I've also noticed that in the modem config web interface, it shows adsl status as down. Presumably i have a setting wrong somewhere...?

---

### Post by x33a on 2009-01-25
if you want bridged mode, then type

sudo pppoeconf in the terminal, and follow the instructions. your connection will be ready in a few minutes.

---

