---
title: "[SOLVED] Where is the list of wireless networks (Intrepid)"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by rimbaud on 2008-12-03
Hello all

I'm sure there is a simple answer, but where is the list of local wireless networks in Ubuntu Intrepid?

The new Network Configuration tool (nm-connection-editor) is very nice but I can't find the old list of local networks (complete with icons to say whether they are secure on insecure).  There is also no help button in this tool!

I know I can install WiCD or use the shell etc, but I must be missing something obvious.

Thanks in advance

---

### Post by __Ryan__ on 2008-12-03
Left click on the NetworkManager applet icon in your top panel.

---

### Post by rimbaud on 2008-12-03
Thanks: that will be the problem.  The Notification Area applet broke when I upgraded to Intrepid.

---

### Post by __Ryan__ on 2008-12-03
try:

```
sudo iwlist wlan0 scan
```

replace wlan0 with your wireless interface

---

### Post by 2hot6ft2 on 2008-12-03
Or if you like a gui try wifi-radar or KWiFiManager

---

### Post by rimbaud on 2008-12-04
Thanks guys

---

