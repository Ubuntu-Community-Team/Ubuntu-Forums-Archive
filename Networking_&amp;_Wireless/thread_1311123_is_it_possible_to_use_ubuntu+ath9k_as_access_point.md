---
title: "is it possible to use ubuntu+ath9k as access point?"
date: 2009-11-02
forum: Networking &amp; Wireless
---

### Post by ZioNemo on 2009-11-02
Hi,
I did search... but I'm still very confused.

I have a new server (Zotac ION-A) which has a pretty wireless LAN (among other things).
It works ok to connect o my access point (sitecom).
I would like to turn t into a second access point to serve different section of the house.
Is it possible?
Can someone point me to the right docs?

TiA
ZioNemo

---

### Post by inportb on 2009-11-02
mmhmm... [http://www.aircrack-ng.org/](http://www.aircrack-ng.org/)

---

### Post by ZioNemo on 2009-11-17
> **inportb said:**
> mmhmm... [http://www.aircrack-ng.org/](http://www.aircrack-ng.org/)

?????

The pointer You gave me is for a "802.11 WEP and WPA-PSK keys cracking program".

I just wan to to setup my ath9kboard to act as an access point instead of acting as a client.
I certainly do not want to crack anything. I *might* be interested to verify I won't be cracked, but that's another story.

I do not understand.

Regards
ZioNemo

---

### Post by irose123 on 2010-01-27
I wanted to do the exact same thing after seeing the Zotac boards on mini-itx.com as they looked ideal. Couldn't find the info online so I emailed support at Zotac. Eventually got a brief reply that their boards didn't support master mode. I suspect that their card spec keeps changing so even if one version did support master mode they can't guarantee that it always will.

Just found your post after I'd just posted my own: [http://ubuntuforums.org/showthread.php?p=8734538](http://ubuntuforums.org/showthread.php?p=8734538)

Keep hunting, and if you find a way, please let me know.

---

### Post by andrey.zhdanov on 2010-02-07
The following page [http://blog.bokhorst.biz/3395/computers-en-internet/asrock-ion-330ht-as-wireless-access-point/](http://blog.bokhorst.biz/3395/computers-en-internet/asrock-ion-330ht-as-wireless-access-point/) seems to contain the solution, at least for AR9285 cards. I have not tested it myself yet, though

---

### Post by andrey.zhdanov on 2010-02-10
> **andrey.zhdanov said:**
> The following page [http://blog.bokhorst.biz/3395/computers-en-internet/asrock-ion-330ht-as-wireless-access-point/](http://blog.bokhorst.biz/3395/computers-en-internet/asrock-ion-330ht-as-wireless-access-point/) seems to contain the solution, at least for AR9285 cards. I have not tested it myself yet, though

An update: after some googling and testing on my laptop I found a simpler way to turn it into a wireless access point, so that now it shares 3G internet connection over wifi. Basically you need to:

1. Switch the network card into master mode. With my setup (AR9285 card, ath9k driver, Karmic 64 bit) this can be done by using hostapd. Details about setting it up [here]("http://ubuntuforums.org/showthread.php?t=1269671&highlight=ath9k").

2. Configure bridging/masquerading. For that I used [this document]("https://help.ubuntu.com/community/WifiDocs/WirelessAccessPoint"). I used the ppp0 interface created by the wvdial modem dialer instead of eth0 described in the document. Also, the way to switch the network card into master mode described in this document (by editing /etc/network/interfaces) did not work for me, so I used hostapd as described above.

Hope this helps.

---

