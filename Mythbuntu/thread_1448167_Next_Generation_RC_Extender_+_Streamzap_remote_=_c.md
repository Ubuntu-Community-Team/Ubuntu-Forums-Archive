---
title: "Next Generation RC Extender + Streamzap remote = crash"
date: 2010-04-06
forum: Mythbuntu
---

### Post by larsolav on 2010-04-06
This may be a bit esoteric, but here goes:

I have been running Mythbuntu without any major problems for a few years now, and in November I did a major upgrade to my entertainment system. I purchased the [[COLOR="Red"]Next Generation Remote Control Extender[/COLOR]]("http://www.amazon.com/Next-Generation-Remote-Control-Extender/dp/B000C1Z0HA") to extend my [[COLOR="Red"]Streamzap[/COLOR]]("http://www.streamzap.com/") remote control. 

Ever since using the RC extender, the Mythbuntu combined FE/BE machine will randomly and completely freeze, and will only respond to a hard reset. This may happen once or twice a day. I have noticed that once in a while the RC extender will flash a signal even if I am not pressing any buttons on my Streamzap remote.

In order to troubleshoot, I disconnected the power to the RC extender, and I have had no crashes for a week now after doing so. So I am thinking the RC extender somehow sends a signal that just messes up my Mythbuntu system (9.10). I tried looking for a LIRC log in /var/log/ but could not find any relevant log files there. 

Anyone have a clue as to what may be happening here?

---

### Post by novellahub on 2010-04-06
Do you have a powererd USB hub you could use for the Streamzap receiver base?  You could experiment using that to see if it has any affect.

---

### Post by larsolav on 2010-05-05
Thanks novellahub (a bit belated thanks...)for the suggestion.
Turns out the usb receiver got hosed somehow. It crashes everything it is plugged into. New MCE remote works fine.

---

