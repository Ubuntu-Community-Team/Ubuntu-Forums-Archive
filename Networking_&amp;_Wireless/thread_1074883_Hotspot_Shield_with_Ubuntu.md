---
title: "Hotspot Shield with Ubuntu"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by garmo on 2009-02-19
I followed this instructions for using hotspot shield in ubuntu  [http://markusthielmann.com/blog/hotspot_shield_ubuntu](http://markusthielmann.com/blog/hotspot_shield_ubuntu)
but I don't know how to use this.
I get this log message:
Feb 19 14:31:42 garmo-desktop pppd[23594]: pppd 2.4.4 started by root, uid 0
Feb 19 14:31:42 garmo-desktop pppd[23594]: Using interface ppp0
Feb 19 14:31:42 garmo-desktop pppd[23594]: Connect: ppp0 <--> /dev/pts/2
Feb 19 14:31:43 garmo-desktop pppd[23594]: No CHAP secret found for authenticating us to LinuxVPNserver
Feb 19 14:31:43 garmo-desktop pppd[23594]: CHAP authentication succeeded
Feb 19 14:31:43 garmo-desktop pppd[23594]: CHAP authentication succeeded
Feb 19 14:31:43 garmo-desktop pppd[23594]: local  IP address *.*.*.*
Feb 19 14:31:43 garmo-desktop pppd[23594]: remote IP address *.*.*.*
Feb 19 14:32:47 garmo-desktop pppd[23594]: Modem hangup
Feb 19 14:32:47 garmo-desktop pppd[23594]: Connect time 1.1 minutes.
Feb 19 14:32:47 garmo-desktop pppd[23594]: Sent 269596392 bytes, received 1280 bytes.
Feb 19 14:32:47 garmo-desktop pppd[23594]: Connection terminated.
Feb 19 14:32:47 garmo-desktop pppd[23594]: Terminating on signal 15

and that happens every time, could someone help with this or know what this means?

---

### Post by garmo on 2009-02-24
Is there something wrong with my post?
does it need more info or am I asking in the wrong place?

---

### Post by frumple on 2009-03-19
I having a similar result, although the problem seams to be different.

Here is my xl2tpd -D output:

xl2tpd[13166]: This binary does not support kernel L2TP.
xl2tpd[13166]: xl2tpd version xl2tpd-1.1.12 started on evristow PID:13166
xl2tpd[13166]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
xl2tpd[13166]: Forked by Scott Balmos and David Stipp, (C) 2001
xl2tpd[13166]: Inherited by Jeff McAdams, (C) 2002
xl2tpd[13166]: Forked again by Xelerance ([www.xelerance.com](www.xelerance.com)) (C) 2006
xl2tpd[13166]: Listening on IP address 0.0.0.0, port 1701
xl2tpd[13166]: Connecting to host 64.55.144.10, port 1701
xl2tpd[13166]: Connection established to 64.55.144.10, 1701.  Local: 53700, Remote: 61237 (ref=0/0).
xl2tpd[13166]: Calling on tunnel 53700
xl2tpd[13166]: Call established with 64.55.144.10, Local: 34879, Remote: 32027, Serial: 1 (ref=0/0)
xl2tpd[13166]: start_pppd: I'm running: 
xl2tpd[13166]: "/usr/sbin/pppd" 
xl2tpd[13166]: "passive" 
xl2tpd[13166]: "-detach" 
xl2tpd[13166]: ":" 
xl2tpd[13166]: "refuse-pap" 
xl2tpd[13166]: "auth" 
xl2tpd[13166]: "require-chap" 
xl2tpd[13166]: "name" 
xl2tpd[13166]: "4j558x" 
xl2tpd[13166]: "debug" 
xl2tpd[13166]: "file" 
xl2tpd[13166]: "/etc/ppp/options.l2tpd.client" 
xl2tpd[13166]: "/dev/pts/2" 
xl2tpd[13166]: Maximum retries exceeded for tunnel 53700.  Closing.
xl2tpd[13166]: Untrustingly terminating pppd: sending KILL signal to pid 13595
xl2tpd[13166]: pppd 13595 successfully terminated
xl2tpd[13166]: Connection 61237 closed to 64.55.144.10, port 1701 (Timeout)
xl2tpd[13166]: Unable to deliver closing message for tunnel 53700. Destroying anyway.

Also after the vpn activation my routing table contains two default routes:

default         *               0.0.0.0         U     0      0        0 ppp0
default         FDSNET_RISTOW.v 0.0.0.0         UG    0      0        0 eth1

Thanks.

---

### Post by leithon on 2010-03-17
After running the same procedure I got this: SIOCADDRT: No such device  after line:

route add -net 0.0.0.0 dev ppp0


any idea? I'm completely new in linux...

thanks all!

---

### Post by Beholder87 on 2010-07-07
I found some info and I quote from this website: [http://www.kalvster.com/tools/vpn-ubuntu-hotspot-shield.html]("http://www.kalvster.com/tools/vpn-ubuntu-hotspot-shield.html")

> So it appears they are filtering non-iPhone connections and so using this method is not possible.

My other options now are:

Using virtualization software
Connecting through a server that has HotSpot Shield already set up.

I have been trying as well to set up HotSpot Shield in my Ubuntu, but with no success...

=/

Ps: I found in some websites that people were recommending to use ultrasurf because it might work w/ ubuntu... here is a link to a tutorial: [http://jaxov.com/2009/09/how-to-unblock-any-website-in-ubuntu-via-ultrasurf-linux/]("http://jaxov.com/2009/09/how-to-unblock-any-website-in-ubuntu-via-ultrasurf-linux/")

---

### Post by joshofbarse on 2010-10-08
Any luck with getting this going? Not being able to connect to l2tp vpn's is a serious hinderance to using ubuntu in countries that block internet access..

---

