---
title: "Libgupnp not found"
date: 2010-02-11
forum: Multimedia Software
---

### Post by docblob on 2010-02-11
Hey,

Kinda new to ubuntu so I could be making a silly mistake here.

I am trying to compile [rygel]("http://live.gnome.org/Rygel") on ubuntu. Its not a normal ubuntu build though I am running a port for ubuntu on an the arm chip. As I am trying to get a DLNA media server running on a [beagleboard ]("http://beagleboard.org/")for a uni project. While running the ./configure script I encountered an error saying that package 'gupnp-1.0' was not installed. I could not find the exact package but I installed the libgupnp-1.0-2 package ([search]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libgupnp")) which I believe has the gupnp-1.0 package included?

Any tips on how to get past this? Does anyone know the right package I may need?

I am running 9.10 fyi :)

---

### Post by mc4man on 2010-02-11
You'd want the [-dev package ]("http://packages.ubuntu.com/search?keywords=libgupnp-1.0-dev")

---

### Post by docblob on 2010-02-11
Hadn't installed that package yet but unfortunately it didn't do the trick either, the exact error is:

Requested 'gupnp-1.0 >= 0.13' but version of gupnp-1.0 is 0.12.6

---

### Post by mc4man on 2010-02-11
Well it's telling you the version of libgupnp (and headers) that is available on karmic isn't new enough - you need the 1.0.3 version. (0.13.X)

So to proceed you need to provide it or possibly get an earlier source of rygel that can build with what you have available.

As far as providing - you could try building the libgupnp 0.13.X source as static and linking to your rygel build or look at the possibility and or advisability of updating your current libgupnp and libgupnp-dev to 1.0-3.2 - available in lucid.


It's possible to do, whether advisable don't know and can't say.

(you'd need to remove current  libgupnp-1.0-dev, install libgssdp-1.0-2 and libgssdp-1.0-dev from lucid, install libgupnp-1.0-3.2 from  lucid  and then finally install the lucid libgupnp-1.0-dev.

Edit: actually it seems that both the 1.0-2 and 1.0-3 of libgupnp can coexist, only 1 dev version can be installed - see screen

---

