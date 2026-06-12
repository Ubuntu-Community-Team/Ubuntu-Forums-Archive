---
title: "d-link DWA-552 master mode on ubuntu 10.04"
date: 2010-05-20
forum: Networking &amp; Wireless
---

### Post by anwmalos on 2010-05-20
after successfully configuring the dwa-552 to work in master mode in ubuntu 10.04 (ath9k driver) I ran some file transfer tests. The download speed is very good (~50mbps) but the upload speed spikes at about 10-20mbps for the first few KB  and then it's nonexistent (0-1kbps). This only affects file transfers or otherwise bandwidth consuming processes. Normal web browsing or ssh is not affected. After running a speedtest of my internet connection which is routed through the AP I could upload to the internet with 1mbps which is my inet connection maximum so apparently this is not affected. Tried the same file transfers with netcat to eliminate any other factors and had the same problem. dmesg and hostapd debug did not report anything unusual

Any ideas about this?

---

### Post by Spydr4590 on 2010-05-20
Is this hard to setup? Could you provide some instructions? Going to try to dual boot win 7 and Ubuntu 10.04. Thanks :)

---

### Post by bkratz on 2010-05-20
> **Spydr4590 said:**
> Is this hard to setup? Could you provide some instructions? Going to try to dual boot win 7 and Ubuntu 10.04. Thanks :)

You might start here




[https://help.ubuntu.com/community/WifiDocs/MasterMode](https://help.ubuntu.com/community/WifiDocs/MasterMode)

---

