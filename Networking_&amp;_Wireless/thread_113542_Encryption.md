---
title: "Encryption"
date: 2006-01-06
forum: Networking &amp; Wireless
---

### Post by CarlosinFL on 2006-01-06
I need to enable wireless encryption on my wireless router (Linksys WRT54G) & have several options.

I know Ubuntu supports WEP since I can see it below however what about support for WPA or WPA2?

Can I enable WPA encryption on my AP and still use wireless on Ubuntu?

[IMG]http://img314.imageshack.us/img314/6910/wireless7yv.png[/IMG]

---

### Post by Rob2687 on 2006-01-06
[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)

---

### Post by jml on 2006-01-06
The link that was posted is a very good resource for WPA supplicant set up.  There is one thing that the document does not emphasize enough in my opinion.  Before you go through all of the steps outlined there, make sure that your Wireless card is supported by WPA Supplicant.  I spent several hours spread over many days trying to get it to work on my laptop, only to discover that the rt2500 chipset my Averatec uses was not supported.  So my one bit of advise is to go to the WPA supplicant web site first and make sure your card 's wireless chipset is supported.

Joe

---

