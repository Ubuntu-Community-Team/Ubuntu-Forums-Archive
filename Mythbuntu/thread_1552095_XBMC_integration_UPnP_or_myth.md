---
title: "XBMC integration: UPnP or myth:// ?"
date: 2010-08-13
forum: Mythbuntu
---

### Post by zagor on 2010-08-13
Hi,

my Mythbuntu 10.04 box is a standalone frontend/backend.
It has no permanent network connection: I occasionally connect it to my home LAN (through a router) either by ethernet or wireless.
The point is: the pc is if generally NOT connected to the home network.

Therefore myth backend is set to run on 127.0.0.1.

Now I'd like to use XBMC as a frontend to myth backend, on teh same pc.

Two issues:
1. I can't find mythtv as a UPnP share
2. I can setup a myth:// share to the backend, but this works only if the pc is connected to the network, it doesn't if it's not connected

As a side not to 1., I have a NAS acting as UPnP server on the same home network. XBMC sees this, but still does not see Myth UPnP

Any suggestion?
Unfortunately I can't keep the myth/xbmc box connetcetd to the network all the time...

Thanks!

---

### Post by nickrout on 2010-08-13
upnp does not work if you are set to use 127.0.0.1

What is your myth:// path set as?

---

