---
title: "Maverick may be getting a new and improved ureadahead afterall..."
date: 2010-09-22
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-09-22
> ureadahead (0.100.0-8) maverick; urgency=low

  * Decrease the buffer size to just 8MB, after much testing we don't
    need much more than this since it will be limited by the size of the
    page cache anyway.

    This is in lieu of a new version of ureadahead for Maverick, which
    while work is ongoing, isn't ready for shipping at this time.
    LP: [#600359]("https://launchpad.net/bugs/600359").
 -- Scott James Remnant <[scott@ubuntu.com]("https://launchpad.net/%7Escott")>   Mon, 20 Sep 2010 18:34:31 +0100Bring it on, I say.

22 seconds a 4 year old laptop simply isn't fast enough.

---

### Post by VinDSL on 2010-09-22
> **Starks said:**
> Bring it on, I say.

22 seconds a 4 year old laptop simply isn't fast enough.I feel your pain!

21 sec boot on my 7 year-old desktop box could use a boost too...    8-)

---

