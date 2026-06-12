---
title: "[SOLVED] turn on wi-fi"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by RebelwithoutaClue on 2008-03-13
The antennae was not out on my wi-fi card at login, so consequently it was not active at startup.

When I was logged in I had no wi-fi connectivity.

I clicked and right-clicked the nm-applet but couldn't seem to find a re-start wi-fi or load nic or some such similar option to get me connected.

In the end I logged out and back in again, now with the card active and all was well.

However, I'd like to know what the process is in this instance as I just felt it is something *I should know.*

Thanks in anticipation of some sagely direction.

---

### Post by RebelwithoutaClue on 2008-03-13
I've just realised that I have posted this in multimedia.

Apologies for the error but I don't know how to relocate the thread.
:oops:

---

### Post by /home on 2008-03-13
Post the output of this command
> sudo cat /etc/network/interfacesfind witch one is your wifi card(if you can) 
Then do > sudo ifdown ****** then > sudo ifup *******

This will restart your wifi card and it should find your network.

---

### Post by RebelwithoutaClue on 2008-03-21
Thanks for your reply, I get this...

> auto lo
iface lo inet loopback


---

