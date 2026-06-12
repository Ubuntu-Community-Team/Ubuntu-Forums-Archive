---
title: "On demand network config"
date: 2009-08-23
forum: Networking &amp; Wireless
---

### Post by ghat on 2009-08-23
hi

I need to know how to do this correctly on jaunty..

I have a notebook with wlan0 and eth0. Independently both wlan0 and eth0 work perfectly. 

1. If I switch on the laptop and there is a ethernet cable plugged into eth0 then it should configure eth0, **else it should skip configuring eth0.**
2. If the configured wlan is available configure the wlan and assign it a lower metric.

right now it spends trying to do a dhcp discover on eth0 when no cable is plugged into it.. 
cant it just detect that there is no cable on the port and it should just skip it ?

Ghat

---

### Post by Iowan on 2009-08-23
Verify that eth0 isn't configured via */etc/network/interfaces*.

---

### Post by slakkie on 2009-08-23
Try this: [http://ubuntuforums.org/showthread.php?t=124153](http://ubuntuforums.org/showthread.php?t=124153)

This is how I've set it up, basicly does what you want.

Basic requirements:
ifplugd, guessnet, wpa_supplicant (for wireless).

I've attached my custom startup script for wpa, place it in /etc/init.d/

Symlink it to:

```

/etc/rc2.d/S19wpa
/etc/rc6.d/S21wpa

```

So it starts up in time.

---

