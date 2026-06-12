---
title: "issues with firestarter"
date: 2009-01-06
forum: Networking &amp; Wireless
---

### Post by ubdime on 2009-01-06
I have recently set up firestarter and ran across 2 issues. eth0 is external, eth1 is internal.

1. The configuration for the gui is really basic. I could not find a way via the gui to stop firestarter from dumping massive amounts of useless data into /var/log/messages (I use conky to tail my /v/l/m.) I finally got this via the console with LOG_LEVEL=none in /etc/firestarter/configuration. I'm unsure if this would work but perhaps also Edit/Preferences/Interface/Events, under Do not log for the following, add "0.0.0.0/0"

2. The second issue is the biggest problem. It seems that whenever the eth1 is down, the firewall shuts down! If this is the "working as intended" case, firestarter should not even try to be a firewall and just be an "ics" addon! In order for firestarter to protect eth0, I **have** to keep eth1 up at all times!? I was hoping to use firestarter to get my laptop online. But as soon as I unplug eth1, firestarter stops and leaves my eth0 wide open!

I'm completely baffled by the 2nd issue, which seems to be so counter-intuitive. I looked everywhere, I read most of the firestarter posts on ubuntuforums, read fs page's faq and documentation and even tried to google for it, but no where else are other people having issues with this?

---

### Post by ubdime on 2009-01-06
After messing around further with firestarter.

1. "none" is not a log level. Instead, I just commented out the whole line. When I manually start firestarter, I get a whole bunch of errors: "Try `iptables -h' or 'iptables --help' for more information. iptables v1.4.0: log-level `' ambiguous."  But it seems to work none the less.

2. I commented out the following lines in /etc/firestarter/firestarter.sh:
```
#if [ "$NAT" = "on" ]; then
#       if [ "$INMASK" = "" -a "$1" != "stop" ]; then
#               echo "Internal network device $INIF is not ready. Aborting.."
#               exit 3
#       fi
#fi
```
This seems to stop the firewall from stopping simply because eth1 is down.

---

