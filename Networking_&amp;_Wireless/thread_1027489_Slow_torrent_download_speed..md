---
title: "Slow torrent download speed."
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by gender on 2009-01-01
Hello,
I'd like to know what is causing slow download speed with my torrents and how I could fix it. Even on torrents with a big seeder-to-leecher ratio, 11KB/s is a rare sight, though my upload speed remains unharmed.
I've allowed service for port 6881 in Firestarter, but Transmission says that the port is closed, uTorrent doesn't see any incoming connections and displays the yellow sign. Also, I only seem to connect with peers from DHT, no matter where the torrent has originated from.
I don't have a router, if that matters.

Thanks in advance for your help!

---

### Post by gender on 2009-01-01
No, it's not my ISP, because I can hit my maximum download speed, it just happens very rarely.
My upload speed is capped at 100KB/s by uTorrent. My connection is 2/1MBps. [Not sure about the units]
I don't understand your last thing.

---

### Post by prshah on 2009-01-01
> **gender said:**
> 
I've allowed service for port 6881 in Firestarter, but Transmission says that the port is closed, uTorrent doesn't see any incoming connections and displays the yellow sign

Though you have allowed 6881 using firestarter, you have to open this port your router's firewall as well. If you post your (Internet) router's model, someone can guide you more specifically.

Typically, you can access the router config page at [http://192.168.1.1](http://192.168.1.1) , however, this is just a typical scenario, it may be differently setup in your case.

Also, you have to allow the RANGE 6881~6889 for Transmission, and uTorrent / Deluge use custom (non 6881~6889) port numbers; you can find the correct port number in the preferences / settings.

Usually, uTorrent / Deluge should automatically be able to configure the Internet router to open the port they want (using uPnP), but sometimes you need to do so manually.

For further guidance, you should post back your router model, and IP address (or just post back the output of the command ifconfig if you don't know the IP address)

---

### Post by Copernicus1234 on 2009-01-01
I always got poor speeds with Transmission even with ports configured correctly (it said the port was open).

Then I tried Vuze 4. Much better speeds right away. I recommend you try it.

---

### Post by AlexBellisBrown on 2009-01-01
[http://www.getdeb.net/app/Vuze](http://www.getdeb.net/app/Vuze)

4.0 Version here. Add/Remove programs still has the old version. :)

---

### Post by my_key on 2009-01-01
Maybe your ISP recently started packet shaping. Try if you torrent client supports making encrypted connections. This might hide that you're using bittorrent.

Also [http://www.portforward.com](http://www.portforward.com) holds guides on forwarding a port in your router.

---

### Post by AlexBellisBrown on 2009-01-01
Vuze supports encryption, though i dont know about transmission, its been ages since i used it.

---

### Post by gender on 2009-01-01
> **prshah said:**
> Though you have allowed 6881 using firestarter, you have to open this port your router's firewall as well. If you post your (Internet) router's model, someone can guide you more specifically.

As I mentioned in my original post, I do not have a router.

> **prshah said:**
> Also, you have to allow the RANGE 6881~6889 for Transmission, and uTorrent / Deluge use custom (non 6881~6889) port numbers; you can find the correct port number in the preferences / settings.

I had set uTorrent to use the port 6881, though I randomized that now [to 52340] and also allowed service for it in Firestarter.

> **prshah said:**
> For further guidance, you should post back your router model, and IP address (or just post back the output of the command ifconfig if you don't know the IP address)

No router.

> **my_key said:**
> Maybe your ISP recently started packet shaping. Try if you torrent client supports making encrypted connections. This might hide that you're using bittorrent.

Yes, uTorrent does support it and I have enabled it.

> **my_key said:**
> Also [http://www.portforward.com](http://www.portforward.com) holds guides on forwarding a port in your router.

I do not have a router.


And Vuze isn't my idea of a torrent program. I allowed service for the potr that Vuze is using (39608) after a whole lot of connections were refused. I restarted the torrent and it still doesn't pick up. The peak speeds were around 20KB/s. I'm using an OpenOffice.org torrent for testing and my seeds table shows only 2 (4). Vuze's own port testing program also said that the 39608 is closed. Annoying, eh? :KS

---

### Post by prshah on 2009-01-01
> **gender said:**
> As I mentioned in my original post, I do not have a router.

Sorry, I missed that part in your original post. So what kind of Internet connection do you have? Is it using a "broadband modem"? Can you post the model number / brand name of that? Or do you use a "cable" modem?  Do you get connected automatically when it's switched on, or are you "always connected"?

Of course my suggestions about the router are not applicable to you. Please post back with as much information about your Internet connection as possible.

One point of which I'm not too sure: Enabling "encrypted connections" options in any torrent client will only allow you to use seeders that offer encrypted connections; which is usually a lot less than those which are "open". Do you get better speeds if you turn off encrypted connections?

---

### Post by gender on 2009-01-01
> **prshah said:**
> Of course my suggestions about the router are not applicable to you. Please post back with as much information about your Internet connection as possible.

Well, I have a wire which I just plug into my computer. That's it. There is nothing in the middle of the wire or my computer, no modem, no router, nothing. It's been the same way for years. And, yes, I guess you could say that I am always connected, since the small indicator lights which are next to the hole where I plug my wire in, are on even if my computer is turned off. Sorry that I can't give you an exact name for it.
I don't know if the following statement is considered rude in the Ubuntu community, but I used to get maximum speeds all the time in Windows. I'm just saying that, I don't mean to offend any OS, haha.

> **prshah said:**
> One point of which I'm not too sure: Enabling "encrypted connections" options in any torrent client will only allow you to use seeders that offer encrypted connections; which is usually a lot less than those which are "open". Do you get better speeds if you turn off encrypted connections?

No, they remain the same.

And if you don't mind, I'll remove my IP address from a previous post. It seems like there have been done many traceroutes from the same IP address over and over again and there has also been an increase in other connections that have been blocked. I know Ubuntu is supposed to be safe, but having my IP address on display still makes me feel kind of uneasy.

---

### Post by nESbo on 2010-01-03
try typing down this in the console

```
sudo ufw disable
```

it disables ubuntu default forewall.

---

