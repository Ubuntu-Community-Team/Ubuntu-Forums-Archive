---
title: "I can't connect to the internet!"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by dr.zeius on 2006-06-10
I've just installed Breezy but I have some problems setting up my ADSL connection. I'm using the D-Link DSL-300T modem configured as a bridge.
When I start **pppoeconf** and follow the instructions as described in the [wiki]("https://wiki.ubuntu.com/ADSLPPPoE") all seems to work but firefox can't lookup any website.
If I type **plog** in terminal, just after launching **pon dsl_provider**, then I obtain the following output:
```

maurizio@casa:~$ pon dsl-provider
Plugin rp-pppoe.so loaded.
maurizio@casa:~$ plog
Jun 10 10:53:09 localhost pppd[9508]: Using interface ppp1
Jun 10 10:53:09 localhost pppd[9508]: Connect: ppp1 <--> eth0
Jun 10 10:53:09 localhost pppd[9508]: Couldn't increase MTU to 1500
Jun 10 10:53:09 localhost pppd[9508]: Couldn't increase MRU to 1500
Jun 10 10:53:09 localhost pppd[9508]: Couldn't increase MRU to 1500
Jun 10 10:53:09 localhost pppd[9508]: Remote message: permission denied
Jun 10 10:53:09 localhost pppd[9508]: PAP authentication failed
Jun 10 10:53:09 localhost pppd[9508]: Couldn't increase MTU to 1500
Jun 10 10:53:09 localhost pppd[9508]: Couldn't increase MRU to 1500
Jun 10 10:53:09 localhost pppd[9508]: Connection terminated.

```

The /etc/ppp/peers/dsl-provider file (which, as I understood, is edited by pppoeconf) contains the text below:

```

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "famigliabilotta@alice.it"
```

What's wrong?
NOTE: I know this problem could be solved changing modem configuration; the DSL-300T can itself establish a connection with my ISP and then autenticate properly but I'd like to keep it configured as a bridge.
THANKS IN ADVANCE.

---

### Post by Iowan on 2006-06-13
Have you tried uncommenting the **mtu 1492** line?

---

### Post by dr.zeius on 2006-06-26
Thanks but now it's OK!! Excuse me if I'm replying late...
[This thread]("http://ubuntuforums.org/showthread.php?t=143951&highlight=pppoeconf") helped me compiling the PPPoE client rp-pppoe (which was another issue).Only I had some problems disconnecting (pppoe-stop did not terminate the connection), but using the gui version of rp-pppoe made things go right.

Now the question is: Is there a way to launch the gui version without having to recompile the whole program each time (as the go-gui script does)?

---

