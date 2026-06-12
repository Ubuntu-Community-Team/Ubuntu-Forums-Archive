---
title: "Disable MythTV DLNA"
date: 2009-07-19
forum: Mythbuntu
---

### Post by joutsen on 2009-07-19
Hello

Does anyone know of a clean way to disable the DLNA support on an existing MythTV backend installation?

I have another DLNA server (coherence) doing what I want, and having two DLNA servers on the network is just confusing for my Samsung TV.

Thanks!

---

### Post by ian dobson on 2009-07-19
Hi,

Do you mean UPNP? You can disable it by editing /etc/default/mythtv-backend and adding/changing the line #EXTRA_ARGS="--verbose" 

to read 
EXTRA_ARGS=" --noupnp --verbose"

then restarting mythtv-backend

Regards
Ian Dobson

---

### Post by Dupey on 2009-10-12
I am having a similar problem with my Mythbuntu 9.10 setup. I can get a functional DLNA server by using miniDLNA but the non-functional UPNP built into Myth still will not go away. Even when I edit the EXTRA_ARGS as suggested. What am I missing?

---

### Post by joshoekstra on 2009-10-12
Dunno, did you uncomment it? ie by taking # out?
Yesterday a patch went into trunk to change dlna-capability to mythtv. DLNA should work at least for samsung-TVs now. I'm keeping my fingers crossing for my sony Bravia :)

---

