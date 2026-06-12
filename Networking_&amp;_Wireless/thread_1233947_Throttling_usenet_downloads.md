---
title: "Throttling usenet downloads"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by imbjr on 2009-08-07
I have a WINE-based usenet reader that consumes pretty much all the download bandwidth, especially when it is retrieving new headers.

I'd like to throttle the download, but so far trickle does not work - possibly because of the reasons it states in its documentation.

The other solutions involving tc or tcng seem horrendously complex and my router does not support QoS.

Does anyone know of a method that is reasonably simple to implement and that will not affect any other internet traffic?

---

### Post by madman100 on 2009-08-07
hi try a different  news reader like SABnzbdplus  or pan or KLibido there are lot of readers for usenet in the package manager

---

### Post by imbjr on 2009-08-07
> **madman100 said:**
> hi try a different  news reader like SABnzbdplus  or pan or KLibido there are lot of readers for usenet in the package manager

Pan I had problems with. It works perfectly and then boom, nothing but a re-install would fix the problem of new message retrieval.

SABnzbdplus appears to be more concerned with binaries, whereas I am concerned with text-only groups.

KLibido also looks like a binary-orientated reader and I'm trying to avoid dragging in KDE dependencies.

I examined the help files of Forte Agent, the reader I do use, and there's nothing in there about traffic limiting.

I've even considered writing my own Usenet reader but I have other fish to fry.

Apart from trickle, there really does not seem to be a simple way of limiting bandwidth, unless I should be thinking about.

This looks do-able:
[http://www.securityfocus.com/infocus/1285](http://www.securityfocus.com/infocus/1285)

but setting up tc requires some serious head-scratching trying to figure out the appropriate parameters.

---

