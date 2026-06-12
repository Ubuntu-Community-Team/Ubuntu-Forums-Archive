---
title: "Always with the wireless issues!! please help"
date: 2006-02-10
forum: Networking &amp; Wireless
---

### Post by hyde200j on 2006-02-10
Well I've looked through forums and the wiki and spent a solid week with this, but it's just not coming together.  Apologies if I'm beating a dead horse, but let it be known, I tried.  Further apologies for being shamelessly new to some of this.

BCM4306 card on my Dell Inspiron 600m
I successfully got the ndiswrapper bit working (used bcmwl5a.inf.  Really what this means to me is ifconfig shows wlan0 where there was no wlan0 before.  In System->Admin->Networking properties, it sees my network essid (and my neighbour's unencrypted one as well).:p 
Pinging anything gives 'network unreachable' and furthermore, any changes made to wlan0 (essid, ap, mode) through GUI, interfaces file, or command line does not change anything according to iwconfig.  The ap remains 00:00:... and essid remains as 'off/any'.  WEP key is set though.

Everything works fine with Windows.

Hopefully this is enough information to get some advice for.  Let me know what other information you need (and preferably how to attain it) if you want to help.

I love you all for helping.  Thanks so much.

---

### Post by hyde200j on 2006-02-10
Oops, maybe this is important too
Breezy 2.6.12-10-386

---

