---
title: "Using 3G USB modem with pppd/chat?"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by 9001 on 2010-03-31
I happen to own a 3G modem, "ZTE MF636", which used to work just fine back in the 9.04 days. However, after some kernel update (don't know which), networkmanager has stopped seeing it. Luckily I'm still able to connect using a simple wvdial script.

I'm not here to complain about regressions, but I'd like to know whether I could possibly ditch wvdial somehow. If I understand correctly, wvdial is just a fancy frontend for pppd and chat, right? I have a perfectly working script, but as wvdial doesn't come preinstalled in Ubuntu, I need to borrow a public wlan to install it... Kind of a pain whenever I wish to format my system, however rare that may be.

So, to sum it up, how do I use pppd and chat directly, instead of through wvidal?

---

### Post by pdc on 2010-03-31
like you, I use wvdial when I dialup with my MF636; it works quickly and well

> how do I use pppd and chat directly, instead of through wvidal? 

Don't know; why would you want to?

Others suggest gnome ppp

Peter Curtis is very knowledgable

[http://www.pcurtis.com/ubuntu-mobile.htm#wvdial](http://www.pcurtis.com/ubuntu-mobile.htm#wvdial)

a bit of light reading for you

[QUOTE]Luckily I'm still able to connect using a simple wvdial script./QUOTE]

George Vita has posted extensively on the MF636

[http://www.acomelectronics.com/GeorgeVita/ZTEonUBUNTU.html](http://www.acomelectronics.com/GeorgeVita/ZTEonUBUNTU.html)

---

### Post by 9001 on 2010-03-31
Thanks for your response.
> **9001 said:**
> as wvdial doesn't come preinstalled in Ubuntu, I need to borrow a public wlan to install it.
I have no problem with using wvdial on a daily basis; I just don't want to depend on a public internet connection to get my own modem working after a fresh install.

---

### Post by reef2dive on 2010-06-10
Hi
I had the same issue, I have a very special modem. What I had to do is to use my windows partition and a USB probe (software) to clue out the commands that is sent to the modem at start-up. When I had the sequence I could create my chat-script.
There are some USB probe software available for temporary use.

Else there is a standard, :-) in [www.3gpp.org](www.3gpp.org) that defines all the AT commands that should be supported by standard modems to actually bring up a connection. It might work for yours, as that is probably more standard compliant than mine.

In my case, I had an issue to wvdial, as it does not seem to support more than 10 commands (0 to 9) and I actually needed more during the testing phase.

It takes a couple of evenings to get it working, now it always works for me.

---

