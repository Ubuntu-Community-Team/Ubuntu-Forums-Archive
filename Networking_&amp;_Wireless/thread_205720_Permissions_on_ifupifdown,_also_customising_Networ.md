---
title: "Permissions on ifup/ifdown, also customising NetworkManager"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by korny on 2006-06-28
Greetings,
I have a laptop with both standard wireless interfaces, and an iburst pcmcia WAN card, using the ibdriver drivers ( [http://sourceforge.net/projects/ibdriver](http://sourceforge.net/projects/ibdriver) )

The basic configuration works, but I have to manually start and stop the interface.  Worse, I have to do this as root - if I run "ifup nas-ib0" I get an error:
[FONT="Courier New"]ifup: failed to open statefile /var/run/network/ifstate: Permission denied[/FONT]

So I have two questions:
- How do I change my network configs so I can bring up/down an interface without root permissions?  I'd really rather not have to run 'sudo' every time I want to re-start my connection.

- Is it possible to configure NetworkManager to automatically control this interface - i.e. bring it up automatically if I have no wifi or ethernet connections?  NetworkManager is a very handy tool, but I haven't found much information on customising it.

I can give more details on my network config if needed; basically I have the following configs:
in /etc/modprobe.d/iburst: (used to configure the pcmcia driver)
```
options ib-net ifname="nas-ib" debug=9
options ib-pcmcia debug=9
```
in my /etc/network/interfaces file:
```
iface nas-ib0 inet manual
  up ifconfig $IFACE up
  up pon dsl-provider
  down poff dsl-provider
  down ifconfig $IFACE down

```
and then a pppoe interface called dsl-provider configured with all the dialup parameters.

Any assistance greatly appreciated!

---

### Post by korny on 2006-07-08
bump?  Anyone got anything to add at all? :)

---

