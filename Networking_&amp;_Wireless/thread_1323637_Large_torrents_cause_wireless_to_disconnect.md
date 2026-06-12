---
title: "Large torrents cause wireless to disconnect"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by ElTimo on 2009-11-11
Whenever I try to download a large (more than ~600 MB) torrent, it will work fine for awhile, and then suddenly it will stall for a few seconds before the wireless disconnects completely. This problem only appeared after upgrading to Karmic and has persisted through multiple updates. I'm using a Dell Latitude D820 with Core 2 Duo T7250, Intel 3945 wireless card, nVidia Quadro 110m 128 MB, and 80 GB hard drive. At first I thought my router might be to blame, but considering that this problem didn't exist in Jaunty, I'm led to believe that it's got something to do with the wireless driver/kernel module or something.

Relevant chunk from syslog:
```

Nov 11 21:58:51 Cygnus-X1 wpa_supplicant[1061]: CTRL-EVENT-SCAN-RESULTS 
Nov 11 21:58:57 Cygnus-X1 wpa_supplicant[1061]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov 11 21:58:57 Cygnus-X1 NetworkManager: <info>  (wlan0): supplicant connection state:  completed -> disconnected
Nov 11 21:58:57 Cygnus-X1 kernel: [80572.230051] wlan0: no probe response from AP 00:15:e9:69:07:2e - disassociating
Nov 11 21:58:57 Cygnus-X1 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov 11 21:58:58 Cygnus-X1 wpa_supplicant[1061]: CTRL-EVENT-SCAN-RESULTS 
Nov 11 21:58:58 Cygnus-X1 wpa_supplicant[1061]: Trying to associate with 00:15:e9:69:07:2e (SSID='Robertson' freq=2437 MHz)
Nov 11 21:58:58 Cygnus-X1 wpa_supplicant[1061]: Association request to the driver failed
Nov 11 21:58:58 Cygnus-X1 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov 11 21:58:58 Cygnus-X1 kernel: [80573.948018] wlan0: direct probe to AP 00:15:e9:69:07:2e try 1
Nov 11 21:58:58 Cygnus-X1 wpa_supplicant[1061]: Associated with 00:15:e9:69:07:2e
Nov 11 21:58:58 Cygnus-X1 kernel: [80573.953351] wlan0 direct probe responded
Nov 11 21:58:58 Cygnus-X1 wpa_supplicant[1061]: CTRL-EVENT-CONNECTED - Connection to 00:15:e9:69:07:2e completed (reauth) [id=0 id_str=]
Nov 11 21:58:58 Cygnus-X1 kernel: [80573.953359] wlan0: authenticate with AP 00:15:e9:69:07:2e
Nov 11 21:58:58 Cygnus-X1 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov 11 21:58:58 Cygnus-X1 kernel: [80573.955251] wlan0: authenticated
Nov 11 21:58:58 Cygnus-X1 kernel: [80573.955256] wlan0: associate with AP 00:15:e9:69:07:2e
Nov 11 21:58:58 Cygnus-X1 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed
Nov 11 21:58:58 Cygnus-X1 kernel: [80573.957682] wlan0: RX ReassocResp from 00:15:e9:69:07:2e (capab=0x431 status=0 aid=1)
Nov 11 21:58:58 Cygnus-X1 kernel: [80573.957687] wlan0: associated

```

Any help would be greatly appreciated. This has been driving me up the wall ever since I upgraded.

---

### Post by ElTimo on 2009-11-13
Bump. This is really driving me crazy. All I want to do is download a Linux distro for god's sake.

---

### Post by s3a on 2009-11-13
Does this happen on other versions or with previous and current version live CDs?

---

### Post by ElTimo on 2009-11-14
Nope, just with Karmic. I downloaded entire discographies when I used Jaunty without issue.

---

### Post by mercury80 on 2009-11-16
I got the same problem, on TWO totally different computers (drivers ath9k & ipw2200), and they are both fresh Karmic installs. I have been running Ubuntu on ipw2200 theme since 8.04. I think the problems was present in 9.04 but not bad enough to notice. I have also noticed it gets worse when the download load is heavy. 

After some disconnects & reconnects the authentication for the AP is gone and needs me to re-enter it, at that point it is of no use and i have to disable and enable wireless in NetworkManager to get it to work. It seams there are lots with the same problem. I have seen some posts recommending to use WICD in stead of NetworkManager. Very annoying!

---

### Post by AlexH76 on 2009-11-20
Same issue here.
Saw this on jaunty sometimes. Now on Karmic more frequently, even from torrents >250MB
Never saw solution to this... :(

---

### Post by AlexH76 on 2009-11-21
Issue seems solved (for me) after firmware upgrade on the wireless router - no more disconnects so far.

---

### Post by saygin on 2009-11-29
Using kubuntu 9.10 with a fresh install and have the same problem. I think it is not about how big the file is, it can be seen with small file-sized torrents too. Tried both ktorrent and deluge, ended up with the same issue. A fix would be perfect...

---

### Post by ElTimo on 2009-12-10
I tried using Wicd as suggested somewhere (I forget where, and I don't have time to find it again), which, of course, didn't work. This is really starting to bug me, as I can't get anything to torrent now. I've tried torrenting on Windows and on my Powerbook, and both went off without a hitch. This definitely seems like a driver issue to me.

---

### Post by ElTimo on 2009-12-12
The issue doesn't appear to be limited to Ubuntu. I tried Fedora 12 and Opensuse 11.2, both of which use the 2.6.31 kernel, and the issue persisted. This definitely rules out any application-specific problems.

---

### Post by saygin on 2009-12-15
well, no solutions yet? This bug really annoys me! Can't download anything in torrent. I could use windows for it, but I usually spend time in ubuntu. If this bug lasts more, this may change soon. :@

---

### Post by Ni85 on 2010-05-17
hey guys
did you find any solution for this?
i have the same issue on lucid and it's driving me crazy!
thanks

---

### Post by iponeverything on 2010-05-17
Its common problem with wireless routers. Torrent programs don't do very good of properly closing out tcp connections and as result the internal tcp connection table will fill. 

Trying lowering the number of connections that the torrent client is allowed to make.

[http://superuser.com/questions/121657/soho-netgear-wireless-router-disconnects-when-downloading-torrents](http://superuser.com/questions/121657/soho-netgear-wireless-router-disconnects-when-downloading-torrents)

---

### Post by Ni85 on 2010-05-17
i doubt that this is related to the router: it works on other computers running on windows.
i think it's a very similar problem to the one described here [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1141473&page=3](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1141473&page=3)

i do remember that i had to fix this in intrepid or jaunty, just got a tip from a chat, but too long has passed and i forgot how to... now that i have installed a clean lucid, it started again

---

### Post by iponeverything on 2010-05-17
> **Ni85 said:**
> i doubt that this is related to the router: it works on other computers running on windows.
i think it's a very similar problem to the one described here [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1141473&page=3](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1141473&page=3)

i do remember that i had to fix this in intrepid or jaunty, just got a tip from a chat, but too long has passed and i forgot how to... now that i have installed a clean lucid, it started again

Perhaps the windows torrent client has more sane defaults or is better behaved in properly closing tcp connections. The "it works with windows" argument, does not mean much in many cases.

Regardless, If the problem is on the Linux side, its most likely not an intrepid or jaunty problem -- but a bug in the driver for your specific hardware or a bug manifested by the conditions introduced through a torrent download and the interaction of your wireless driver and wireless spec implementations on the wireless router.

The fact that the launchpad bug referenced in the below link in post #24 only has 13 subscribers, would seem to support that the issue is not common. 

That said, you should not dismiss anything out of hand.

---

### Post by Marcosview on 2011-09-12
> **saygin said:**
> Using kubuntu 9.10 with a fresh install and have the same problem. I think it is not about how big the file is, it can be seen with small file-sized torrents too. Tried both ktorrent and deluge, ended up with the same issue. A fix would be perfect...



See here for a possible solution:
[http://www.raymond.cc/blog/archives/2007/09/10/stop-bittorrent-from-killing-your-internet-connection/](http://www.raymond.cc/blog/archives/2007/09/10/stop-bittorrent-from-killing-your-internet-connection/)

---

