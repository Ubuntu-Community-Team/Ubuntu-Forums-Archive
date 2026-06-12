---
title: "Slow network connection"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by Word on 2010-07-29
I have a dual boot laptop windows 7 and ubuntu desktop 10.04. Also have a torrent server on my VMWARE esxi box at home. Its ubuntu server 10.04.

When i try to access files via smb from my linux laptop to linux server copying files is so slow. a 551mb(true blood) file took 20 minutes to copy. That same file from windows 7 can play straight from the linux smb share or copy in 6 or 7 minutes. 

The laptop is connected at 54mbs the server is connected to the wireless device at 1000 to the switch 100 to the wifi.

-----
Things ive tried

using a wire cut the wireless off no luck
changed the mtu no difference.



Thankls for any help you can provide.

---

### Post by marc.verwerft on 2010-07-30
> The laptop is connected at 54mbs the server is connected to the wireless device at 1000 to the switch 100 to the wifi.
That's probably what they are capable of - their max settings.

Verify your actual settings with:
[http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/](http://www.cyberciti.biz/faq/linux-change-the-speed-and-duplex-settings-of-an-ethernet-card/)

Regards,

Marc

---

