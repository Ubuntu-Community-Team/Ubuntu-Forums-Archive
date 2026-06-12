---
title: "List SSIDs in terminal?"
date: 2013-01-11
forum: Networking &amp; Wireless
---

### Post by Roasted on 2013-01-11
I know you can do sudo iwlist wlan0 scan and see everything, but it gives me a LOT of information for each AP in the area. Is there a way to simply list the SSIDs with significantly more basic info? When I googled around everybody seemed to suggest sudo iwlist wlan0 scan and they were happy with that. Like I said, just hoping for something a bit more basic. Thanks!

---

### Post by haqking on 2013-01-11
> **Roasted said:**
> I know you can do sudo iwlist wlan0 scan and see everything, but it gives me a LOT of information for each AP in the area. Is there a way to simply list the SSIDs with significantly more basic info? When I googled around everybody seemed to suggest sudo iwlist wlan0 scan and they were happy with that. Like I said, just hoping for something a bit more basic. Thanks!

```
sudo iwlist wlan0 scan | grep ESSID
```

---

### Post by Roasted on 2013-01-11
> **haqking said:**
> ```
sudo iwlist wlan0 scan | grep ESSID
```

Nice! That's exactly what I wanted. Do you know if there's a way to kind of branch out a bit more to see a bit more info? I know that kind of goes against what I was initially asking but if there's a way to see more details (but not 70 lines of details) that'd be great... like the signal strength, encryption type, etc. If not, this is huge, as I can at least see the SSIDs without a ton of extra stuff.

Appreciate it!

---

### Post by steeldriver on 2013-01-11
if you have a recent version of network-manager, there's

```
 nmcli dev wifi list
```

---

### Post by Roasted on 2013-01-11
> **steeldriver said:**
> if you have a recent version of network-manager, there's

```
 nmcli dev wifi list
```

Nailed it. That's perfect. Thanks fellas!

---

### Post by haqking on 2013-01-11
> **Roasted said:**
> Nailed it. That's perfect. Thanks fellas!

Welcome.

remember to mark the thread as solved using thread tools.

Cheers

---

### Post by Roasted on 2013-01-11
One last question, does that:

nmcli dev wifi list

only work on 2.4ghz networks? I have 3 SSIDs at my house (router 2.4, router 5.0, and a 2.4 AP I added on the deck). I'm only seeing the router 2.4 and the 2.4 AP... not the 5.0 of my router...

---

### Post by steeldriver on 2013-01-11
Hmm.. it finds both of mine:-

```

$ nmcli dev wifi list | grep NETGEAR
'NETGEAR68-5G'                    20:4E:XX:XX:XX:XX   Infrastructure   5220 MHz   54 MB/s    87       WPA2       no
'NETGEAR68'                       20:4E:XX:XX:XX:XX   Infrastructure   2427 MHz   54 MB/s    98       WPA2       yes

```

Are you sure you're broadcasting the 5G SSID?

---

### Post by Roasted on 2013-01-11
Hm, it seems fine now. I was on my deck at the time. Perhaps I wasn't able to reach the 5.0 band out there? The regular GUI network manager had it listed though. I just turned my laptop back on (I'm inside now) and I see it. I also went back outside where I was and I saw it then too. No idea... but hey... all good now!

---

