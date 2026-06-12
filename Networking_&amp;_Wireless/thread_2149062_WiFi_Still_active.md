---
title: "WiFi Still active?"
date: 2013-05-27
forum: Networking &amp; Wireless
---

### Post by asearle on 2013-05-27
Hi Everyone,

I have a Samsung Series5 Ultrabook style laptop and most things work fine including WiFi (although sometimes I have a suspicion that the signal is not received as effectively as it could/should be).

I find that I can switch WiFi off and on using the Ubuntu Network icon/menu (no problem).  The hotkey (on the keyboard) for switching WiFi on and off doesn't seem to work (but that is not a big issue).

But the strange thing is that, when I switch WiFi off the WiFi light (on the side of the laptop) is still on.  This makes me think that somehow WiFi is still active and is draining my battery and therefore reducing the time between charging.

Does anyone have any thoughts on this?  What could I check to see what is really happening?

Many thanks,
Alan Searle

---

### Post by varunendra on 2013-05-28
> **asearle said:**
> The **hotkey** (on the keyboard) for switching WiFi on and off **doesn't seem to work** (but that is not a big issue).
That ^^ may be the reason why the light stays even though the adapter is off. It indicates that maybe your laptop's hotkeys are not properly supported by whatever wmi driver is loaded for it.

The problem (actually not a problem) you described is somewhat same as what happens with my Asus laptop when I blacklist "asus_nb_wmi" driver. After that, I have to tap the key combination two to four times to turn both the adapter and its light off.

However, as long as the adapter itself is off, it shouldn't matter whether the light is on or off. As far as I know, both the hardware and software switches send a "sleep" signal to the adapter which sends it to minimal power mode (sleep), thus saving power.

To confirm whether the adapter is actually off or not, you can also use the rfkill command :
```
rfkill list
```
The hotkey causes "Hard Block", while network manager causes "Soft Block". But as far as I know, it will be in the same power saving (sleep) mode when either hard or soft (or both) block is applied. So you shouldn't need to worry about power drain.

---

