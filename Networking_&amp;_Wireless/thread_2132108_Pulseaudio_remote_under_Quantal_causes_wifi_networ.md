---
title: "Pulseaudio remote under Quantal causes wifi network to drop"
date: 2013-04-03
forum: Networking &amp; Wireless
---

### Post by ecowan on 2013-04-03
The setup:
two servers, three laptops.
My proxy server runs Ubuntu 12.04. It's on a wired connection to the router.
The game server runs 12.10.
I use x2go to access the servers from my laptop (12.04).
The kids have two laptops, one 12.04, the other 12.10.

Whenever I try to use pulseaudio to redirect sound from the game server (12.10) to my laptop (12.04) the wifi network drops for everyone.

But I have no problem to pipe audio from the proxy server to my laptop.

Does anyone have any ideas? I'm about ready to abandon 12.10 and rebuild the game server with 12.04.

Thanks. - Erny

---

### Post by ecowan on 2013-04-24
Actually, now _every_ attempt, with or without audio, to connect from my Precise laptop X2go client to my Quantal X2go server using wifi results in the entire wifi function crashing on both computers. Only a reboot of both systems seems to restore connectivity.
- Erny

---

