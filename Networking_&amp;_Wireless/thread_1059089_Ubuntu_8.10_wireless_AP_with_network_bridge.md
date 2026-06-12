---
title: "Ubuntu 8.10 wireless AP with network bridge"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by MunkyJunky on 2009-02-03
I don't have a wireless router in my flat, and buying one isn't an option (I live in university halls - routers are a big no), but I'd like wireless networking set up through my Ubuntu 8.10 desktop box, mainly so I can download files on my iPhone over wireless, and so my mates can get on the internet when they come round. 

My computer has 3 network cards - 
[LIST]
[*]eth1 - internet connection
[*]eth0 - for connecting random network things
[*]wlan0 - what I hope to be my wireless AP
[/LIST]

I'd like to set up wlan0 as a wireless AP so I can connect into it from laptops/my iphone, and I'd like it to deal out DHCP addresses too. 

I've created a bridge using a guide from PokerJoker ([http://ubuntuforums.org/showpost.php?p=2420977&postcount=2](http://ubuntuforums.org/showpost.php?p=2420977&postcount=2)) using 

```

sudo brctl addbr Bifrost

sudo brctl addif Bifrost eth1

sudo brctl addif Bifrost eth0

sudo brctl addif Bifrost wlan0

sudo brctl show

sudo dhclient Bifrost

```

where Bifrost is the name of the bridge. However, this isn't a permanent fix - anyone know how to make this permanent? 

So, to sum up, from you all I would be ever so pleased if you could provide me with: 

[LIST]
[*]Wireless AP how-to using a wireless card
[*]Permanent bridge, to bridge internet from eth1 to wlan0
[/LIST]

---

