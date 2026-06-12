---
title: "Mobile Broadband almost working :-("
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by uqbar on 2010-10-20
Hi all.
I managed to have my USB Mobile Briadband modem recognised by the system.
I managed to create the relevant entry in the "Mobile Broadband" tab of the NetworkManager applet.
What happens is this:
```
Oct 20 18:58:34 uqbar NetworkManager[1090]: <info> starting PPP connection
Oct 20 18:58:34 uqbar NetworkManager[1090]: <info> pppd started with pid 4418
Oct 20 18:58:34 uqbar NetworkManager[1090]: <info> Activation (ttyACM0) Stage 3 of 5 (IP Configure Start) complete.
Oct 20 18:58:34 uqbar pppd[4418]: Plugin /usr/lib/pppd/2.4.5/nm-pppd-plugin.so loaded.
Oct 20 18:58:34 uqbar pppd[4418]: pppd 2.4.5 started by root, uid 0
Oct 20 18:58:34 uqbar NetworkManager[1090]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Oct 20 18:58:34 uqbar NetworkManager[1090]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Oct 20 18:58:34 uqbar modem-manager: (net/ppp0): could not get port's parent device
Oct 20 18:58:34 uqbar pppd[4418]: Using interface ppp0
Oct 20 18:58:34 uqbar pppd[4418]: Connect: ppp0 <--> /dev/ttyACM0
Oct 20 18:58:34 uqbar pppd[4418]: Remote message: Icera PPP - Password Verified OK
Oct 20 18:58:34 uqbar pppd[4418]: PAP authentication succeeded
Oct 20 18:58:36 uqbar pppd[4418]: LCP terminated by peer (001b: Normal Termination by NCP)
Oct 20 18:58:36 uqbar pppd[4418]: Modem hangup
Oct 20 18:58:36 uqbar pppd[4418]: Connection terminated.

```
"Almost working" as the PPP link is up but somehow it goes down in less than 2 seconds because "LCP terminated by peer (001b: Normal Termination by NCP)".

Any idea on how to troubleshoot this?
TIA.

---

### Post by uqbar on 2010-10-20
By chance I've seen the pppd process during the attempts:

```

/usr/sbin/pppd nodetach lock nodefaultroute ttyACM1 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam / ...

```
I can see a "nodefaultroute" which seems to be definitely wrong.
Right?

---

### Post by James.Lazo on 2010-11-21
I've been connecting via Blueman's DUN service - works flawlessly. Not an elegant solution, but quite easy. Just change the default dial up number #99 to #777.

---

