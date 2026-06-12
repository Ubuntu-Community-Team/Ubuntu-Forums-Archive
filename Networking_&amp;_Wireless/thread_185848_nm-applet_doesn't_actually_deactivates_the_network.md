---
title: "nm-applet doesn't actually deactivates the network"
date: 2006-06-01
forum: Networking &amp; Wireless
---

### Post by darkvad0r on 2006-06-01
Hi,
I'm running dapper on an IBM T42 with a centrino processor. I use the nm-applet to manage my network. The problem is that when I try to disable the network card (to save battery when I have no wi-fi around) the applet says the wi-fi card has been disabled but it isn't really (I tried "disabling" it while I was at home and I still had internet access :confused:  )
Can anyone confirm this behaviour of the nm-applet/gnome-network-manager ?
Thanks in advance

---

### Post by twisted_steel on 2006-06-01
Are you trying to disable the card by right-clicking on the applet and unchecking enable wireless/enable networking, or are you disabling it with the Fn+F5 shortcut?  I have a T42 and would be happy to play around with it.

---

### Post by Jingo on 2006-06-02
How did you install network-manager ?
Did you install it after a fresh dapper final install?

---

### Post by darkvad0r on 2006-06-05
I installed it with synaptics packet manager and no I didn't installed it after a fresh dapper final install, in fact I installed it when I was on breezy, the I made a full distro upgrade through synaptics packet manager.
Fn+F5 seems to be effectively powering off the wi-fi, I'll check later if the battery improves just to make sure it really is powering it off.

---

### Post by MaddMatt on 2008-05-01
I have that problem in Hardy as well, and I'm on a home-built system. Running the madwifi-ng driver, and that's caused problems in the past so it's possible it's related? I don't know about the T42... What I did notice is that in Hardy the usuall network commands don't seem to work:
```

$sudo ifdown ath0

```
which normally does the trick. have you tried that?

---

