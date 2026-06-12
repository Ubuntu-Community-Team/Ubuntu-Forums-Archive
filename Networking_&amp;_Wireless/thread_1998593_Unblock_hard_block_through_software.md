---
title: "Unblock hard block through software?"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by Kaspberger on 2012-06-07
I have my doubts that this is possible, but here's the story: I have a Lenovo S10-3 netbook with the proprietary wireless driver installed. I ran ```
rfkill list
``` and it says

```
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```I attempted the ```
sudo rfkill unblock all
``` command, but that obviously doesn't affect the hard-blocked wireless. I'm not dual-booting with Windows, so I can't log into Windows and turn on the switch. Neither the Fn + F5 keystroke nor the physical switch on the side of the machine seem to work. I've reset the BIOS, but that doesn't seem to do much either.

Thanks in advance.

---

