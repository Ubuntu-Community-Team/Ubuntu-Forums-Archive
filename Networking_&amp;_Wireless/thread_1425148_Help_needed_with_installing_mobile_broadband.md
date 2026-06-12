---
title: "Help needed with installing mobile broadband"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by mooz123 on 2010-03-08
Hi,
I am trying to switch to mobile broadband, Ubuntu 9.10, Huawei E1750 modem, provider Telia Sweden. So far I tried this:

(previous: tried to get started with an Option Icon 550 modem, but could not do it. Ubuntu froze completely, networkmanager refused to see the modem after this. Read somewhere that it is (next to) impossible with Ubuntu, but Huawei is a better chance. Maybe I changed some settings on the way, went and got a Huawei)

-connected modem, nothing happened
-rebooted to Windows Vista, installed modem
-rebooted to Ubuntu networkmanager sees the modem, when I select it, it gives a message 'GSM network, disconnected'
also: Ububtu sees the usb stick as a folder

what would be a good next step?
//Mark

---

### Post by mooz123 on 2010-03-09
Solved!
My connection was set up for the first modem, so I tried to remove it. This didn't work, due to a strange effect in NetworkManager, but I could create a new connection for the Huawei. Now it works.
So: install in Windows, use in Ubuntu

---

