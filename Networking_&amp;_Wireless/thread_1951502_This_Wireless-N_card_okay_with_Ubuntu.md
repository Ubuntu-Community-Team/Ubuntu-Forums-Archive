---
title: "This Wireless-N card okay with Ubuntu?"
date: 2012-04-02
forum: Networking &amp; Wireless
---

### Post by spoons on 2012-04-02
[http://www.overclockers.co.uk/showproduct.php?prodid=NW-054-TP&groupid=46&catid=1597&subcat=](http://www.overclockers.co.uk/showproduct.php?prodid=NW-054-TP&groupid=46&catid=1597&subcat=)

Got this in checkout, looks perfect for my uses, however does it work in Ubuntu 11.10/12.04?

Thanks muchos. ):P

---

### Post by chili555 on 2012-04-02
I suspect it does. I downloaded the Windows XP driver from their website and in the .inf file, I see this:> [Atheros]
; DisplayName               Section                 DeviceID
; -----------               -------                 --------
; TPLINK
%ATHER.DeviceDesc.0300T%    = ATHER_DEV_30A4.ndi,     PCI\VEN_[COLOR="Red"]168C[/COLOR]&DEV_[COLOR="Red"]002D[/COLOR]&SUBSYS_0300168C
%ATHER.DeviceDesc.0301T%    = ATHER_DEV_30A4.ndi,     PCI\VEN_168C&DEV_002D&SUBSYS_0301168C
%ATHER.DeviceDesc.0300T%    = ATHER_DEV_30A4_30A4.ndi,    PCI\VEN_168C&DEV_002E&SUBSYS_30A4168C
This device is supported in the wireless driver *ath9k*:```
$ modinfo ath9k | grep 002D
alias:          pci:v0000[COLOR="Red"]168C[/COLOR]d0000[COLOR="Red"]002D[/COLOR]sv*sd*bc*sc*i*
```I don't know if it will reliably achieve N speeds; N is still a bit tricky in Ubuntu.

You might get some additional clues by searching this forum for the pci.id: 168c:002d.

---

### Post by spoons on 2012-04-02
Just bought it. I don't need N speeds as G will do - I just need a PCI-E card that's relatively cheap. Will let you all know how I get on. :)

---

### Post by chili555 on 2012-04-02
Post back if you need help. We aim to please.

---

### Post by spoons on 2012-04-10
Using 11.10 and it is working perfectly. Instantly detected and connected.

Connected to my BT HomeHub 2.0 and running at the 130Mb/s Draft-N speed the router supports.

Thanks for the replies!

---

