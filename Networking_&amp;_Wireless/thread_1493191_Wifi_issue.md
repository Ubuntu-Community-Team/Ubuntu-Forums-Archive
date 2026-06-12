---
title: "Wifi issue"
date: 2010-05-25
forum: Networking &amp; Wireless
---

### Post by b1llyboy on 2010-05-25
Hi all:

Got some problems connecting to the internet through wifi (I'm using Lucid 64 bit).
Things were working fine, but this morning I found that I could not contact my wireless router. I still get asked for the password to the keychain, but the Network Manager icon does not appear.
I've assumed so far that the problem involves an inability to access my USB wireless adapter because of the lack of a Network Manager icon.

Any thoughts on how to resolve this very much appreciated. Could it be something really silly like Network Manager somehow being turned off, and if so does anyone know how to turn it back on?

Thanks,

Billy.

Quick update - I can get the Network Manager back by typing:

sudo killall NetworkManager

I guess it restarts, but it says my wifi is not managed. If I try nm I get

(nm-applet:1973): WARNING **: <WARN> constructor(): Couldn't initialize the D-Bus manager

---

