---
title: "How do I make wpa_cli or wpa_gui work with DBUS?"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by not_a_phd on 2010-11-03
I need wpa_cli to work with my wpa_supplicant process to diagnose issues I have been having with my wireless in 10.10. I think originally, the communication method between wpa_cli and wpa_supplicant has been a socket interface. wpa_supplicant has recently been configured to run with a DBUS interface to network-manager and other apps.

One of the command line switches tells wpa_cli the path for the control socket:

```
wpa_cli [ -p path to ctrl sockets ] [ -i ifname ] [ -hvB ] [ -a action file ] [ -P pid file ] [ command ... ]

```

Please. For the love of all that is true. Could someone tell me how to set the -p switch so that I can issue configuration messages to my running wpa_supplicant process under 10.10??

It seems like a simple question. But, I can find no documentation how to run this application with the DBUS interface. Maybe it is not possible. But, I would like to hear that from an authoritative source.

---

### Post by proycon on 2011-04-10
I see this has not been answered yet, but I have the very same question now...  Does any one know the solution to this?

---

### Post by jonathanrlively on 2011-07-03
Yeah, same problem here with Ubuntu 11.04. Cannot find documentation on this anywhere. Need to be able to connect wpa_cli to an existing wpa_supplicant process for an application.

---

### Post by gburca on 2011-09-15
You need to start wpa_supplicant with the -O option. By default wpa_supplicant only uses the D-Bus interface. wpa_cli however expects to talk to it over a control socket. For more details see: [http://ebixio.com/blog/2011/09/15/how-to-make-wpa_cli-talk-to-wpa_supplicant-in-ubuntu/]("http://ebixio.com/blog/2011/09/15/how-to-make-wpa_cli-talk-to-wpa_supplicant-in-ubuntu/")

---

