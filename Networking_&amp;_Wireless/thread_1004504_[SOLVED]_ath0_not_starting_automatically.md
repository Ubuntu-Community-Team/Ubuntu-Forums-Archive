---
title: "[SOLVED] ath0 not starting automatically?"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by rixtr66 on 2008-12-07
The madwifi drivers i installed work great.It solved my connection problems!
However it doesnt start automatically?I have to sudo modprobe ath_pci,
every time i log in,wich is annoying.how do i make it so ath0 starts auto matically? any help would be great!
Thanks):P
peace
Rick

---

### Post by jmoorse on 2008-12-07
Add it to the modules file (determines modules loaded at boot):

`sudo nano /etc/modules`

---

### Post by rixtr66 on 2008-12-07
OH!! DUH!!i should have known that.
thanks!
Peace
Rick):P

---

