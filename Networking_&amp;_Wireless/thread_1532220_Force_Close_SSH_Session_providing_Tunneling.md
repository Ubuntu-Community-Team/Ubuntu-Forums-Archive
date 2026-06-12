---
title: "Force Close SSH Session providing Tunneling"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by ojconcentrate on 2010-07-16
Hello All,

i've recerntly changed to ubuntu full time (about a month now) and i love it. I recently discovered that i can use the ssh server i installed to provide a tunnel using putty from my windows office computer to be able to access some blocked sites (i know sounds strangely 'suspicious' but i really thing the network admins here are a bit paranoid blocking even harmless sites like whatismyip.com and other technology related websites/forums which sometimes i actually need to access when doing research).

Anyway, the tunneling works great (as far as my upload speed at home allows me to download via the tunnel).

I noticed that when I type logout or exit in the putty window, the window doesn't close until all the applications which is using the tunnel via the proxy created by putty. I read that this is the normal behavior which the system works under normal circumstances.

Is there anyway to force this remote connection to close?

I even tried to kill the remote shell process but the command hangs until all the applications close and then it kills the session/tunnel normally.

Regards,

OJ

---

### Post by ojconcentrate on 2010-07-17
bump... anyone? any suggestions are much appreciated.

---

### Post by oomar on 2010-07-17
if youve already tried killing it.... well then I have no idea but...

why do you need to force close it?

---

### Post by ojconcentrate on 2010-07-17
in case I leave the tunnel open and some application that, while sitting mostly idle, will keep the connection alive and potentially suck bandwidth from my home connection.
I mean... its easy to simply "remember to close everything"... but i was hoping that there would be a way to force close the tunnel.

OJ

---

