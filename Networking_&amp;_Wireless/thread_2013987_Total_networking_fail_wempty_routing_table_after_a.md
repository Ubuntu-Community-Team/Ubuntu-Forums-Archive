---
title: "Total networking fail w/empty routing table after accidental 12.04 restart"
date: 2012-07-01
forum: Networking &amp; Wireless
---

### Post by Shay Guy on 2012-07-01
Like the title says. I put my Lenovo B570 laptop into sleep mode after some CPU problems (what is wrong with you ksoftirqd) and it restarted on me for some reason. Now networking is disabled altogether, my routing table is empty, and the total contents of /etc/network/interfaces is as follows:

```
auto lo
iface lo inet loopback
```

...though I don't know if that's how it's supposed to be or not.

I can't make heads or tails out of most of the troubleshooting advice that's out there. Some of it seems to consist of things like "check to see if such-and-such looks right" without any commentary on what such-and-such is *supposed* to look like. Can you give me any more substantial help?

---

### Post by steeldriver on 2012-07-01
That's what /etc/network/interfaces is supposed to look like IF you are running the standard desktop version (which uses network-manager instead of the older networking service)

Are you using a wired or a wireless interface? network-manager should be smart enough to bring up a default wired interface with DHCP. Wireless may take a bit more work. The first thing I would do is run these to see what state everything is in:

```

service network-manager status
nm-tool

```

---

### Post by Shay Guy on 2012-07-01
Plugging in an Ethernet cable does precisely squat. Still says "[COLOR="Gray"]Networking disabled[/COLOR]; &#10003; Enable Networking; (i) [COLOR="Gray"]Connection Information[/COLOR]; (pencil) Edit Connections..." As for the rest...

```
$ service network-manager status
/usr/bin/service: 123: exec: status: not found
$ nm-tool

NetworkManager Tool

State: asleep

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unmanaged
  Default:           no
  HW Address:        F0:DE:F1:90:7A:74

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unmanaged
  Default:           no
  HW Address:        94:39:E5:04:D1:50

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 



```

---

### Post by steeldriver on 2012-07-01
looks like it might be a problem with power management (suspend / resume) - can you do

```
rfkill list all
```

---

### Post by Shay Guy on 2012-07-01
```
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by steeldriver on 2012-07-01
> **Shay Guy said:**
> ```
$ service network-manager status
/usr/bin/service: 123: exec: status: not found

```

Hmm... wait... I missed that... very odd: could you please try

```
/usr/bin/env PATH=/sbin:/usr/bin service network-manager status
```

---

### Post by Shay Guy on 2012-07-01
```
$ /usr/bin/env PATH=/sbin:/usr/bin service network-manager status
network-manager start/running, process 919
```

---

### Post by steeldriver on 2012-07-01
OK well that sounds like an unrelated bug in /usr/bin/service

[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1008892](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/1008892)


I'm *almost* convinced that your issue is related to power management - I believe there are some tricks you can do with /etc/pm/config.d/config e.g.

[http://ubuntuforums.org/showpost.php?p=10226021&postcount=2](http://ubuntuforums.org/showpost.php?p=10226021&postcount=2)

(in your case I guess the driver name should be changed to "wl") but I'm hesitant to advise you since it's not something I've ever had to deal with - you may prefer to wait for a grown-up to come along ;)

---

### Post by Shay Guy on 2012-07-01
Yeah, the SUSPEND_MODULES thing didn't work. And I really know nothing about power management or how it interacts with networking.

---

### Post by steeldriver on 2012-07-01
have you tried suspending / resuming just to make sure it picks up the changes?

you could also check in the BIOS to see if there is an option to power down wireless on suspend and if so turn that off

that's all I've got - sorry

---

### Post by Shay Guy on 2012-07-01
..OK, now that's *really* weird. Clicking "Suspend" on the top-right menu" didn't even *work*. (Said menu, by the way, is in red "restart for upgrades" mode, if it's relevant.")

---

### Post by Shay Guy on 2012-07-01
Also, I really have no idea how to look into the BIOS.

---

