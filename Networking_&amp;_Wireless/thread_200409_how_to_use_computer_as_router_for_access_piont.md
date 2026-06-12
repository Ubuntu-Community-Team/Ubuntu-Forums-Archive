---
title: "how to use computer as router for access piont?"
date: 2006-06-20
forum: Networking &amp; Wireless
---

### Post by haaglin on 2006-06-20
Hi. at my home, i have a Wireless router, and this computer connects to that with dhcp, and i have a second network card. is it possible to share the internet with this and add a Access Point to it to extend the range for other computers? i would like to have dhcp on that to. thanks.

---

### Post by robino on 2006-06-20
Hi, what you want, is definitely possible but it depends on your networkcard you are using to wireless broadcast your connection.

[Here you find a list of wifi-cards with drivers in Linux]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html"), as you can see the Atheros Madwifi and Prism54 FullMac support "Master (HostAP)", so with those drivers you should be able to make an Accesspoint out of your Linux-box.

You will need to put your card in this Master mode. Not sure how since I do not have experience with this, but I guess it should be something similar as (where ethX is your networkcard, check this with iwconfig):

```
sudo iwconfig ethX/wlanX mode master 
```

You can of course also put a cable between your computer and a second AP-router and after you configured you computer to share the connection to the second router, configure the router to rebroadcast the signal/ connection.

For further directions on sharing your internet-connection, see here a [HowTo]("http://help.ubuntu.com/community/InternetConnectionSharing") on the Ubuntu Wiki pages on sharing your internet-connection.

---

### Post by haaglin on 2006-06-20
Hi! thanks for the reply. so this is my setup:
------------------------------------------------------------------
[ath0, Atheros based Wlan card.]

connected to router with dhcp. The router is then given a static ip
from the isp.
------------------------------------------------------------------
[eth0, SIS 900 PCI Fast Ethernet]

The card i wish to connect the AP to extend the range with.
(for laptops and stuff)
------------------------------------------------------------------

Now, with the command you gave me, i lost the connection to internet.
```
sudo iwconfig ath0 mode master
```

Do i need to compile the madwifi driver from that site, or is the one included 
with ubuntu the right one. Thanks for your time.

---

### Post by robino on 2006-06-20
[QUOTE=haaglin]

Now, with the command you gave me, i lost the connection to internet.
```
sudo iwconfig ath0 mode master
```

Do i need to compile the madwifi driver from that site, or is the one included 
with ubuntu the right one. Thanks for your time.[/QUOTE]

Sorry, the command was mend for the wireless-network card to *re*broadcast the connection, not the card that receives the connection, in your case the Atheros Wireless card. 

You can bring back the card simply by putting it back again in managed mode. Normally, there are several modes you can put a card in (ad-hoc, managed, monitor, master).

```
sudo iwconfig ath0 mode managed
```

And then start your normal internet-connection in the way you always do so, if it does not go automatically.

I always bring the card down, and back up again -if it does not go automatically.

```
sudo ifconfig ath0 down
sudo ifconfig ath0 up
```

What I descriped above was *not* a howto, simply a quick reply to help you on your way.  What you can do is simple however, use the [howto on Internet Sharing]("http://help.ubuntu.com/community/InternetConnectionSharing"), to rebroadcast the connection to the router with your eth0 card, and then configure your second router to rebroadcast the wireless signal. It depends on your second AP/router if this is possible.

To test your internet-connection you can also first connect a second computer instead of the Wireless router with your wired network card (eth0 in your case).

I think I confused you, but you can *also *rebroadcast your wireless signal without a second hardware AP/router, but by having a *second* Atheros card which you then can put in 'mode master' and by that you created a router/ap from your box. As this was a direct reply to the title you choose for this thread: 'how to use computer as router for access point?'

---

### Post by haaglin on 2006-06-22
Ok! Thanks a lot. i figured it out!

---

