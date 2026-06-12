---
title: "Huawei E398 is not always detected by Xubuntu 13.04"
date: 2013-05-30
forum: Networking &amp; Wireless
---

### Post by horonitel on 2013-05-30
Hello everyone.
I've read some E398-related threads here, but could not find a solution, so I start a new thread.

**Here is my problem:**

I have a E398 3G modem, I use it with samsung N145-JP02 netbook. If the modem is plugged in before I turn computer on, It is detected as modem and virtual CD drive, and I am able to connect to the internet with network-manager applet.
But when I replug the modem, or plug it after xubuntu boot, I can't see it in network-manager and can't connect to the internet.

[B]My ideas:
[/B]Sometimes I had similar problem with other modem in 12.04-based Linux Mint. I used "service network-manager restart" to re-detect it, and it worked like a charm. I did not need to reboot to use internet. Now this does not work.
I thought it might be kernel problem, so I tested it on both generic and 3.9.3-pf kernels, no luck.

Can anyone help?

---

### Post by alexfish on 2013-06-01
Not sure about

as far as or was aware , some of the Huawei devices or recocognition of same may be built into the kernel,

if so then I am assuming it must be present at boot,

after boot can present various problems '

1. UDEV . need to look at Hot Plugging , as in relation to usb_mode switch

2. is usb_modeswitch installed

Can find from the terminal

```
which usb_modeswitch
```

from here think the best advice will be to visit the usb_modswitch Forum link is at this site
[h=3][SIZE=2][Draisberghof - Software - USB_ModeSwitch]("http://www.google.co.uk/url?sa=t&rct=j&q=usb%20modeswitch&source=web&cd=1&cad=rja&ved=0CDIQFjAA&url=http%3A%2F%2Fwww.draisberghof.de%2Fusb_modeswitch%2F&ei=qtqpUa3lJMe7O5mXgOgH&usg=AFQjCNHXRDd_7g_A3ekgGQ2d_tARDOR6iA&bvm=bv.47244034,d.ZWU")[/SIZE][/h]
visit the forum and Ask first , IE do not attempt to install the software at the site.

There is one cosulation , It works at boot , so U can get Connected ;)

BR

Alex

---

