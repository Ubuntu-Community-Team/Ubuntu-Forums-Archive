---
title: "Edimax EW-7128G won't connect to Verizon DSL router/modem"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by t-readyroc on 2009-06-22
I setup my friend with a clean Jaunty install, but she didn't have a wireless card at the time.  She just purchased an Edimax EW-7128G to connect to her Verizon DSL router/modem.  She's been on the phone with both Verizon & Edimax, but still can't connect to the wireless network.  I'm trying to help her out long-distance, so bear with me.

She can see the network in the network mgr applet, and apparently confirmed with Edimax that the card's been correctly installed.  Verizon had configured her router/modem for WEP, & the key is on the outside of the unit.  When she trie to connect, it tries, it thinks, and after a few minutes the connect window pops up again.  She then hits connect again and it tries, and then the window pops up again.  This sequence happens 4 or 5 times and then it gives up.

She chose the WEP 40/128 bit setting in the manager, and input the router tower code in the box next to "key."  If she inputs a key/security code that is too short or too long the "connect" button cannot be selected as it will not be active (grayed out and shadowed).

At this point, I started digging around the forums, & read a bunch about the RaLink drivers & the serialmonkey drivers, etc.  I think these are now included in the distribution by default?  I also read about setting up [RutilT]("http://ubuntuforums.org/showthread.php?t=554089&highlight=rutilt")...  is this the next step she should try?  Anyone else have this card working successfully in Jaunty?  Any issues maybe related to connecting to that Verizon router?

Any help appreciated.

---

### Post by t-readyroc on 2009-07-02
[Installing wicd]("http://ubuntuforums.org/showthread.php?t=1150797") seems to have fixed my issues.  Wonder why the Gnome network mgr in Jaunty's so borked?

---

