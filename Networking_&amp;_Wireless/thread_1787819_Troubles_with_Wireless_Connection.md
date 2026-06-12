---
title: "Troubles with Wireless Connection"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by MagnoliaKaki on 2011-06-21
Hello.

*For the record, I have already read the other threads. Either they don't work for me or are too difficult. *

I installed ubuntu 10.10 with the LiveCD (the alternative one) as the only operating system. After the installation, the connection worked. Then, after restarting my laptop, it didn't anymore. 

It doesn't connect and when it tries, I'm asked the password. Even if it is correct, it doesn't work.

Writing lsusb in the terminal, I get:

> Bus 001 Device 010: ID Obda:8171 Realtek Semiconductor Corp. RTL8188SU 802.11n WLAN Adapter

I bought it because it said it was compatible with Linux but maybe only with older versions?

I tried following the other threads but as I have no experience, I don't understand them at all. I'm new to Linux as well.

Another thing:
I have another wireless usb adapter, which is:
> Bus 001 Device 011: ID 083a:7522 Accton Technology Corp. Arcadyan 802.11N Wireless Adapter
but I have the same problem as the other one. 

Thank you very much for your help in advance! :P

---

### Post by chili555 on 2011-06-21
Can we work on the Accton first? Please open a terminal and do:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot. Now is it working?

Is your network set to WPA2 or the tricky and difficult WPA and WPA2 mixed mode?

---

