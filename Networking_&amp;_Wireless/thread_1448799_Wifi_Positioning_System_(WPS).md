---
title: "Wifi Positioning System? (WPS?)"
date: 2010-04-07
forum: Networking &amp; Wireless
---

### Post by iRiUX on 2010-04-07
I was thinking about whether its possible to make some kind of Wifi Positioning System (WPS). Apparently there is a way and a company has made one. Has anyone else attempted to do this? Is there any open source code available for this?

A WPS would, I guess, use all wireless access points within range to decide on its own location.

---

### Post by stefangr1 on 2010-04-07
> **iRiUX said:**
> I was thinking about whether its possible to make some kind of Wifi Positioning System (WPS). Apparently there is a way and a company has made one. Has anyone else attempted to do this? Is there any open source code available for this?

A WPS would, I guess, use all wireless access points within range to decide on its own location.

It's very well possible, especially from within the open source community. WPS relies on a database containing the locations of as many access points as is possible. From a programming point of view it shouldn't be too difficult.

The central constraint is whether users are prepared to spend time on regularly entering information about where they are at the present time (such that new entries with combinations of access points and locations can be added to the database).

---

### Post by iRiUX on 2010-04-07
I don't think it relies on a database with locations of the access points, that would make it less effective and constrain it to known public locations. The company that does this already makes it possible in all urban areas so they claim.

1) Do the packages sent from the access points contain any information about the time at which the packets were sent?

2) Assuming an access point is inaccessible to us (encrypted), can we send a request for the time and receive a reply? Regardless of whether we can not access it??

The information is sent at light speed, if we can ping an access point (which we can) and receive the time (preferable in a thousands milliseconds or even more precise), then we could use interpolation to decide our own location to an adequate level.

---

### Post by iRiUX on 2010-04-07
> **iRiUX said:**
> I don't think it relies on a database with locations of the access points, that would make it less effective and constrain it to known public locations. The company that does this already makes it possible in all urban areas so they claim.

1) Do the packages sent from the access points contain any information about the time at which the packets were sent?

2) Assuming an access point is inaccessible to us (encrypted), can we send a request for the time and receive a reply? Regardless of whether we can not access it??

The information is sent at light speed, if we can ping an access point (which we can) and receive the time (preferable in a thousands milliseconds or even more precise), then we could use interpolation to decide our own location to an adequate level.

On second thought, that would give you your located with reference to the access points, but you still wouldn't really know where you are with reference to a geographic map. So something else is needed to... for example a list of locations... but thats not good i think.

---

### Post by iRiUX on 2010-04-08
bump? :p

---

