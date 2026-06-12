---
title: "RT 2400 wireless card won't connect"
date: 2006-02-14
forum: Networking &amp; Wireless
---

### Post by tsg1zzn on 2006-02-14
I used the configuration GUI to enter the correct detailes and then clicked activate. A window popped up and stayed for a few minutes (it had a kind of a progress bar travelling left and right). Then the connection was supposedly activated, but I can't reach the internet.

I tried to add 192.168.1.1 (my router) to the list of DNS servers, but no luck.

Output of ifconfig and iwconfig:
[IMG]http://img131.imageshack.us/img131/994/blur2564eq.png[/IMG]

---

### Post by jrb114 on 2006-02-14
Well I'm no expert, but glancing at the attachment, the immediate thing to notice is that ra0 hasn't got an IP address.

On the checklist:

1) Make sure you haven't got any security turned on, get it working first without, then have a shot with WEP or, for WPA use wpasupplicant (or is it wpa_supplicant).

2) Try doing a:

```
dhclient ra0
```

If your router is set up to work as a dhcp server.

3) Check that your /etc/network/interfaces has the line

```
iface ra0 inet dhcp
```

and 

```
auto ra0
```

Which as far as I understand it, will tell the machine that ra0 is a valid interface which can access the web and can be set up with dhcp. The auto line tells it to bring ra0 up on booting.

If this doesn't work, then it's beyond me, but try other commands like "ifup" "ifdown" to get a feel for it.

HTH 

J

---

### Post by tsg1zzn on 2006-02-14
Thank you, it seems to work now.

---

### Post by tsg1zzn on 2006-03-29
No, it was a once-in-a-lifetime experience. It doesn't work. The two green lights on it doesn't even blink once even when it is supposedly sending a dhcp request. The lines you gave me are in the /etc/network/interfaces file together with a loopback device.

Edit: Yes, the router is setup with dhcp ;)

---

