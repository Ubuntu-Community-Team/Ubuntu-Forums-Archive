---
title: "Network is &quot;invisible&quot;"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by posterberg on 2009-01-01
Hi,

I've got a problem that I believe has to do with supported WiFi channels, I just don't find out where I set the allowed channels.

There is a network that I was able to connect to on my old Hardy machine. With a broadcom card using the old fashion ndisdriver.

This stopped working at one point when the broadcom driver became native in Hardy.

My other computer that was using a iwl3945 card could still connect to that network.

This computer has now been upgraded to Ibex and can't connect anymore.

I had almost given up until I found this clue today.

I ran Kismet just for the fun of it and suddenly I could see the network in Kismet. I showed up right away. But still not visible in Gnome's network manager.

I could also see in Kismet that the channel for the network is 12.

I then tried to force the card to channel 12 with iwconfig. Iwconfig responded with "invalid argument". But channel 11 seem to be a totally ok argument.

So, the iwconfig is not allowed to set channel 12, but Kismet is it seems.

I suppose that this is the reason to why Gnome's network manager can't see the network either.

I tried grepping in etc to see if I could see the allowed channels list somewhere, but I was unable to locate it.

I suppose that there is such a list since the allowed channels vary from country to country.

Has the default allowed channels changed during Hardy? Where do I find the list to change it myself, if there is such a list.

As said, I can't connect with either iwl3945 nor broadcom, but I used to be able to with both machines. No changes has been made in the AP, also Kismet can see the network.

/Peter

---

### Post by posterberg on 2009-01-02
I found after some digging that adding the following line to /etc/modprobe.d/options did the trick.

```
options cfg80211 ieee80211_regdom="EU"

```

---

### Post by stderr on 2009-01-02
Ah!!

This rings bells with problems I encountered about a year ago. Setting the channel rarely worked, aside from occasionally. I think I managed to set it to 12 only once - I could never repeat it.

I'll give this a go later :D

---

