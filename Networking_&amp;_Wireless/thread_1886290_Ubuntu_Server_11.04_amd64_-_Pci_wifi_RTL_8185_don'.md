---
title: "Ubuntu Server 11.04 amd64 - Pci wifi RTL 8185 don't set mode master"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by emilio2hd on 2011-11-24
I've a pci wifi with chip realtek RTL-8185L, and I'm trying configure my ubuntu server to works like a AP. All tutorial tell me to set mode Master, but I don't know why this goddamn it don't works.

I did download of the driver from Realtek site [http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#352")

Make
Make install
Reboot

...and when I type:
iwconfig wlan0 mode Master

I get the error:
Error for wireless request "Set Mode" (8B06)
SET failed on device wlan0 ; Invalid argument

What's wrong?

Thank you in advance.

---

