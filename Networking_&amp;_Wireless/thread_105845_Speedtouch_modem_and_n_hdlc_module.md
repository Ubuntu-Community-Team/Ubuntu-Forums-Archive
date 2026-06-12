---
title: "Speedtouch modem and n_hdlc module"
date: 2005-12-19
forum: Networking &amp; Wireless
---

### Post by cadr on 2005-12-19
Hi,

I'm trying to get my old revision 0 Alcatel Speedtouch modem to work in Ubuntu 5.10 (I've got it working before on the same computer with several other Linux distros, so it definitely ought to work). I think I have everything configured correctly, but pppoa3 is unable to load the n_hdlc kernel module. This module isn't in my /lib/modules. I read in some places that it is necessary to alias n_hdlc to tty-ldisc-13, but I've tried this and it doesn't help. Will I need to build a custom kernel? I'm comfortable with doing this, but I'd rather not if I don't have to.

I'd be very grateful for any suggestions.

Alex

---

### Post by cadr on 2005-12-19
Got it working now. It seems that the n_hdlc error message was a red herring. The template peer file in the documentation that's bundled with the speedtouch package didn't work for me; I had to use a peer file like the following. Maybe someone will find this useful. (My ISP is Wanadoo, btw).

```

lcp-echo-interval 2
lcp-echo-failure 7
noipdefault
defaultroute
name YOUR_USERNAME
noauth
lock
asyncmap 0
holdoff 4
persist
maxfail 25
updetach
usepeerdns

plugin pppoatm.so
YOUR_VCI.YOUR_VPI

```

My /etc/ppp/options files is as follows:

```

noauth
usepeerdns
lock
noipdefault

```

Alex

---

