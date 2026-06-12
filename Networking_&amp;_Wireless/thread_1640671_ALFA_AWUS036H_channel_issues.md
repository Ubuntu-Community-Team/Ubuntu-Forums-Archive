---
title: "ALFA AWUS036H channel issues"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by msjones on 2010-12-08
I work for a firm of solicitors as the IT guy and I have been asked to assess the security of our network.

I have recently bought an ALFA AWUS036H USB wireless adapter to help test the wireless networks. We have a few old devices that only run WEP, which I know from the start is bad.

I'm trying to use the adapter with aircack. I issue the command:

```
sudo airmon-ng start wlan1 11
```

So I know the channel the networks are on from using the WiFiFoFum iPhone app. So I issue the command above which should put the adapter into monitor mode on channel 11. Next I fire up airodump:

```
airodump-ng -c 11 -w ~/wireless/fp_wifi mon0
```

So now I am capturing packets on channel 11 and saving to the fp_wifi files using mon0. Next I run aireplay to test injection:

```
aireplay-ng -9 -e fp_topfloor -a *MAC* mon0
```

Now this is where I am having the problems. I keep getting an error saying:

> Adapter is set to channel -1, access point is on channel 11

Now I set the adapter to channel 11 using airmon but running iwlist mon0 channel says the adapter is not running on any channel at all.

Has anyone else experienced simular issues, and if so how was this resolved?

Thanks in advance, help us much appreciated.

---

### Post by msjones on 2010-12-08
Forgot to add that I have also tried stopping the network-manager service but this still does not help!

---

### Post by msjones on 2010-12-08
Sorted thanks to this thread:

[HTML]http://ubuntuforums.org/showthread.php?t=1598930&highlight=AWUS036H[/HTML]

Must remeber the search option!

---

