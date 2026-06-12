---
title: "&gt;5min Wifi without signal and Automatic Connect is not working - I must click"
date: 2011-06-15
forum: Networking &amp; Wireless
---

### Post by ]SiB[ on 2011-06-15
Hello Everybody,

I have a little Nettop nT425 as my home PC with integrated WIFI Atheros AR9285 - OS is Ubuntu 11.04.
At first I speak that Wifi signal is very good - 2m from AP=AccessPoint!.

I do a simple test with power on/off my AP and I found problem in Ubuntu 11.04 WiFi working it self, it means:

0)
Test configuration is very simple. I edit connection created by my Network Manager set it as ENABLE:
*) Connect automatically
*) Available to all users

1)
Status: AP is off, PC is on
Action: Power on AP and after 10sec I can see that my Ubuntu find my WiFi and connecting to it.
Result: OK

2)
Status: AP is on, PC is on
Action: Power off AP by 1..4minuts and power on AP.
NM WiFi icon is try reconnect to WiFi and when AP is ON then Ubuntu reconnect to WiFi and it's working fine.
Result: OK

3)
Status: AP is on, PC is on
**When WiFi signal is lost at more then 5 minutes and more the Ubuntu 11.04 stops trying to reconnect WiFi and EVEN if I power on AP then Ubuntu is not try re-connect my WiFi!. I must click in NM to connect my WiFi. This is working in 1).**
Result: **[COLOR="Red"]FAIL[/COLOR]**

In do this test because I would move both device on roof my house and I cannot go with keyboard/mouse going to CLICK/activated my WiFi connection.

Can anyone know where and what I can change in Ubuntu to have a protected system of breaking wifi signal more then 5minuts??

Best Regards
Marcin from PL.

---

### Post by ]SiB[ on 2011-06-15
/var/log/syslog:

```
Jun 15 17:13:02 user NetworkManager[700]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jun 15 17:13:02 user NetworkManager[700]: <info> (wlan0): device state change: 5 -> 9 (reason 11)
Jun 15 17:13:02 user NetworkManager[700]: <warn> Activation (wlan0) failed for access point (dlink)
Jun 15 17:13:02 user NetworkManager[700]: <info> Marking connection 'Auto dlink' invalid.
Jun 15 17:13:02 user NetworkManager[700]: <warn> Activation (wlan0) failed.
Jun 15 17:13:02 user NetworkManager[700]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Jun 15 17:13:02 user NetworkManager[700]: <info> (wlan0): deactivating device (reason: 0).
```

---

### Post by ]SiB[ on 2011-06-16
I send this bug: [https://bugzilla.gnome.org/show_bug.cgi?id=652696]("https://bugzilla.gnome.org/show_bug.cgi?id=652696")

---

