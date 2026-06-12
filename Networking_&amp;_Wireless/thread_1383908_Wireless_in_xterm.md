---
title: "Wireless in xterm?"
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by chrispche on 2010-01-17
Whats the terminal command to bring up the wireless connection without loading in to GUI?

Thanks.

---

### Post by The Toxic Mite on 2010-01-17
```

$ iwconfig

```

:)

---

### Post by chrispche on 2010-01-17
Is there any way to activate wireless on boot up rather than waiting for network manager.

---

### Post by The Toxic Mite on 2010-01-17
Why don't you want to use the network-manager?

---

### Post by chrispche on 2010-01-18
I want wireless Internet access from the command line, before starting a GUI.

---

### Post by chrispche on 2010-01-18
Any idea's?

---

### Post by kerry_s on 2010-01-18
put the commands in /etc/rc.local
example:

```

iwconfig wlan0 essid myhouse &
dhclient wlan0 &

```

---

### Post by adam814 on 2010-01-18
I believe you can still get away with setting it up in /etc/network/interfaces.  I'd heard that this was deprecated, although that seems to be an unfounded rumor at this point.

---

### Post by kerry_s on 2010-01-18
> **adam814 said:**
> I believe you can still get away with setting it up in /etc/network/interfaces.  I'd heard that this was deprecated, although that seems to be an unfounded rumor at this point.

that will disable wireless in network manager.

---

### Post by adam814 on 2010-01-18
> **kerry_s said:**
> that will disable wireless in network manager.

Maybe I'm misunderstanding then, I thought the OP didn't want to use NetworkManager and instead wanted a wireless connection set up before/without using any GUI programs.

---

### Post by kerry_s on 2010-01-18
> **adam814 said:**
> Maybe I'm misunderstanding then, I thought the OP didn't want to use NetworkManager and instead wanted a wireless connection set up before/without using any GUI programs.

it will be setup before the gui, but when the gui starts it will take over, so he can have what he wants without messing up anything.

---

### Post by chrispche on 2010-01-20
> **kerry_s said:**
> put the commands in /etc/rc.local
example:

```

iwconfig wlan0 essid myhouse &
dhclient wlan0 &

```

What's the myhouse bit? My wireless network is called Talk Talk and I have a passphrase to use. What do I need to enter into that file to get it to come online as the system boots up?

---

### Post by adam814 on 2010-01-20
Assuming your wireless interface is wlan0 and you use WEP encryption you'd do this:
```
iwconfig wlan0 essid "Talk Talk" key <WEPkey> &
dhclient wlan0 &
```(substitute your actual WEP key of course)

If you use WPA you'll have to set up a config file for wpa_supplicant.  For info see "man wpa_supplicant.conf".

---

