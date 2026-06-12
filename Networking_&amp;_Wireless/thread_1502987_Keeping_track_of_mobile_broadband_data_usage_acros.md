---
title: "Keeping track of mobile broadband data usage across computers?"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by size_XXM on 2010-06-06
I was wondering if anyone addressed such a problem - the data usage information from the carrier is often several hours old and is accessed in some arcane ways (logging into their website, sending a specific SMS message at best).
Here's my idea: single-session data usage is perfectly reported by *ifconfig ppp0*. The problem is, how to[list][*]keep track of previous sessions[*]accumulate the numbers [*]rollover to zero at specified date[/list] To be able to do this across computers means that one needs to store it on the modem/SIM card itself. (As a specially crafted SMS message, or a contact). Does anyone know such a tool? It's likely just a neat script and an udev rule, but it would be massively helpful.

---

### Post by alexfish on 2010-06-06
hi

have a look at man pages for pppstats
then also look at gammu or wammu

---

### Post by size_XXM on 2010-06-06
Thanks, I use wammu, good to know there's a command-line version. pppstat seems a bit over the top for me, cat-ing /sys/class/net/$IFACE/statistics/[tr]x_bytes will probably do the job, and will probably work for hso interfaces as well.

---

