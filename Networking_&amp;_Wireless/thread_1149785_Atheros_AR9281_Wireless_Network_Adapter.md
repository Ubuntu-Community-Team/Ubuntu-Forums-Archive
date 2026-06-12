---
title: "Atheros AR9281 Wireless Network Adapter"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by mzdrojowy on 2009-05-05
ok prolly a question asked many time's but I really need an answer geared for a total newbie . just started working with ubuntu 8.04.1 i3 and it's installed from windows vista  via a "wibi" (i think thats what it's called) . also just started working with the BASH shell too.

anyways my question has to do with my Atheros AR9281 Wireless Network Adapter , it does not work ... i can "see" it in the bash shell with "ls network" and i think i see a driver but i'm not sure ... 

recomendations for a total noob ? 
:confused:

---

### Post by mzdrojowy on 2009-05-06
one day down lol no answers for the noobs huh?

---

### Post by dandnsmith on 2009-05-06
> **mzdrojowy said:**
> ok prolly a question asked many time's but I really need an answer geared for a total newbie . just started working with ubuntu 8.04.1 i3 and it's installed from windows vista  via a "wibi" (i think thats what it's called) . also just started working with the BASH shell too.
It's wubi, not wibi

> anyways my question has to do with my Atheros AR9281 Wireless Network Adapter , it does not work ... i can "see" it in the bash shell with "ls network" and i think i see a driver but i'm not sure ... 

You may have to investigate using Windows drivers under ndiswrapper, since it's 8.04. For me my Atheros interface only started working out-of-the-box with 9.04 Ubuntu Netbook Remix (almost worked with 8.10).

---

### Post by mzdrojowy on 2009-05-06
so are you using the netbook remix with a normal laptop or an actual netbook ? 
of course thank you for your time :)

---

### Post by dandnsmith on 2009-05-07
With an actual netbook - Acer aspire One

---

