---
title: "Wireless Problem (HP DV2530EA) Solved 10.10 (64 Bit)"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by The Fatsnacker on 2010-10-30
Have been experiencing a problem with the Wireless switch on the HPDV2500 type laptop and Unbuntu 10.10.

In my case the probem was solved doing the following


1) Place the wireless switch into the on position (even though) it show orange (disabled)

sudo gedit \var\lib\NetworkManager\NetworkManager.state

change the line for wireless from false to True and save.

whilst in the terminal session, type

RFKILL LIST

Where the wireless is shown as hardware disabled type the following

RFKILL UNBLOCK <identifier> where the identifier is numerical a detailed in the list displayed from the rfkill list command.

leave the wireless switch in the on posiotion (still showing Orange=disabled) and reboot the machine.

for me this cured the problem...

regards

---

