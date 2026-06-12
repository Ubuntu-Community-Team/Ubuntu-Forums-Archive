---
title: "Is there a way to revert to the older version of Amarok?"
date: 2009-05-06
forum: Multimedia Software
---

### Post by diablo75 on 2009-05-06
I'm not too thrilled about this newer version of Amarok that was included with the 9.04 upgrade.  On one system I installed Ubuntu on fresh, every time I try to start it, it just locks up at the splash screen, even after purging and reinstalling it.  On a friends PC, when he tries to play an mp3, it doesn't do anything more than load the file, show time time duration, but doesn't actually play it.

Complaints aside, I'd feel comfortable using the older version, even if one might consider it to be "obsolete" by comparison to the latest edition.  Is there a way to do this?

---

### Post by mc4man on 2009-05-06
Here's a link a stop short of the ppa page for amarok 1.4 redone for jaunty.
There are some instructions on the page for what  to do (basically add his repo and then do a sudo apt-get remove amarok && apt-get install amarok14

[https://edge.launchpad.net/ubuntu/+ppas?name_filter=amarok+14](https://edge.launchpad.net/ubuntu/+ppas?name_filter=amarok+14)

giving you it a stop short because it's a search page for ubuntu launchpad ppa's, could be handy

(click on the owners name to go to ppa

Edit: If the page comes up empty then search amarok 14

---

### Post by diablo75 on 2009-05-06
Got it, but I had to do a little gumshoe work.  Here's exactly how to do this:

Create a text file and paste the following inside of it:

> -----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESZG9dwEEAM5SRxksQzjok7uw93gEWMGT+89fLoKA5ij0FCn9mmMhJAgJeh3LTO6W9B9J
9wQNUPp+vzuP1Nib+/ZuiC8eB5J73ITdm/7o+zXwuX/KEeGBkvlb9/IeS4X3Sy4p5dWResuP
ZIP/VFrC/lMIO4J6/3IJld3jv8eQXm4q1DDY4PtNABEBAAG0IExhdW5jaHBhZCBQUEEgZm9y
IEJvZ2RhbiBCdXRuYXJ1iLYEEwECACAFAkmRvXcCGwMGCwkIBwMCBBUCCAMEFgIDAQIeAQIX
gAAKCRC58cQyrnSuY5g0A/9a/9Xds26+egxE+7j4e5ycRjgpSXe4oABBAqQ+SuMxr+OcCb8i
NRtJzUuxn4uGigc10DDinqfZlFhl13iLdQmypEPXVzeUIbvS/STHJKU/gu1Il4IRX+3FDDsG
WPgh0PQaCjXdCsMd9oka+4lgW95qKsOTihoLwvvx+ozAozAG0g==
=j5d9
-----END PGP PUBLIC KEY BLOCK-----

Save the file somewhere (I called my "key" and put it on the desktop).

Click System>Administration>Software Sources.  Add these two third party software sources:

deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main

Now click on the Authentications tab in Software Sources and import the text file with the above hash we pasted earlier.  Then click Close>Reload.

Finally, open a terminal and type:

sudo apt-get remove amarok && sudo apt-get install amarok14

(The second sudo was missing in the above post; I've corrected this here).

That's it!

---

