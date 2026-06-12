---
title: "Torrent downloading in Ubuntu 11.04 causes unstable wireless transfer"
date: 2011-07-02
forum: Networking &amp; Wireless
---

### Post by bedhead75 on 2011-07-02
Every time I download torrents in Ubuntu 11.04 on my desktop, using Transmission or Deluge clients, the wireless transfer speed abruptly drops off, becomes very choppy, and in general doesn't remain stable. It's not only the torrent download that slows down, but it's everything including web surfing, even though I'm not maxing out my connection speed.  It's not that I'm getting disconnected from my router, it's just that the wireless transfer speed drops off, becomes intermittent, and never gets back up to full speed.  
     At first I thought that my ISP was throttling my connection, but this issue doesn't happen with a direct cable connection to my router, nor did it happen when I was running Ubuntu 10.04 before.  It also doesn't happen when I'm downloading the exact same torrents over wireless using my netbook running Ubuntu Netbook Remix.  This issue ONLY seems to happen when using a bittorrent client while on wireless on Ubuntu 11.04 on my desktop. I can max out my internet connection speed by streaming videos, downloading from FTP, etc. using wireless just fine, and the transfer speed remains stable.  This also seems to happen with a couple of different wireless USB adapters (rt73usb or rtl8187 drivers) so I'm not sure if it's a specific driver issue.

    I'm at a loss here as to where to file a bug report.  Has anyone else noticed this?

---

### Post by SeijiSensei on 2011-07-02
Is the problem resolved if you disconnect the power from your router then reconnect it?  If so, you need to reduce the number of **simultaneous connections** that your torrent client is using.

---

### Post by bedhead75 on 2011-07-03
> **SeijiSensei said:**
> Is the problem resolved if you disconnect the power from your router then reconnect it?  If so, you need to reduce the number of **simultaneous connections** that your torrent client is using.

Unfortunately that doesn't work.  It seems to be an issue specific with Ubuntu 11.04 and wireless.  Like I said before, this issue doesn't happen when I download the same files using my netbook running Ubuntu netbook remix, using the same torrent clients with the same settings.  Could there be some kernel issue or issue with the network manager applet?

---

### Post by MaindotC on 2011-07-03
There is no "Ubuntu 11.04 wireless".  It seems to be a driver issue.  I would find the driver being used for your device and see what options are available.  Modprobe may be using the incorrect driver and you may wish to try another.

The first place to start is the [Ubuntu Wireless Troubleshooting Guide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide).  In order for your device to work properly you need the physical connectivity (plugged in all the way and/or turned on via your machine's BIOS), a driver to communicate between the device and the operating system, and then the proper configuration of the device which typically is via DHCP.  Please follow the guide and indicate at what point you are having difficulty.

You can probably skip to the part about determining the driver being used.

---

### Post by Vinse on 2011-08-06
I believe I am having the same problem. I have used a series of torrent clients, latest one being Deluge, which I was led to believe is the most reliable client available. Every time I launch a torrent file it will run for about twenty minutes at normal speed then it 'stalls' and kills my internet connection. I have found that if I disconnect from my network and then reconnect it will work for another twenty minutes or so. My drivers are up to date and everything is in order. If it makes a difference I am on a Gateway Netbook running 11.04.

---

### Post by hike on 2011-08-18
Same issue (wifi connection drops while torrenting, regardless of the torrent client) with me (Ubuntu 11). Some people suggested that it could be related to max number of connections ([http://ubuntuforums.org/showthread.php?t=1738426](http://ubuntuforums.org/showthread.php?t=1738426)), but i think this issue is generic to natty. I am running win 7 on dual boot, and do not experience any problems with torrent while using windows. Note that in win 7 my utorrent is configured to have 500 connections, while in ubuntu i lowered it to 150 and still get problems. I even tired to torrent from inside guest XP via virtual box - same issue.

It's been suggested that the issue might be related to gnome network manager ([http://ubuntuforums.org/showthread.php?t=1770819](http://ubuntuforums.org/showthread.php?t=1770819)), i'll try wicd and post the results.

My other concern is ath9k driver, i have an atheros card that is capable of wifi N (works perfectly on win 7), but on ubuntu it only connects to wifi G despite of the ubuntu 11 release claims that N is supported. I'll test if win 7 experiences any problems if connected to wifi G.

---

### Post by Vinse on 2011-08-20
Problem solved on my end. I just downloaded the Wicd Network Manager and everything works perfectly. Hope this helps everyone else with this issue.

---

### Post by hike on 2011-08-21
Update

wicd solved the problem --> after installing wicd, i can torrent at full throttle and set max number of connections as i did in win 7 (500 for utorrent)

Follow this link for original post on using wicd --> [http://ubuntuforums.org/showthread.php?t=1770819](http://ubuntuforums.org/showthread.php?t=1770819)

As i mentioned before, i checked test if win 7 experienced any problems if connected to wifi G, and it did not, so the fact that ath9k driver on ubuntu is not letting me to have wifi N connection is not related to the problem. The bug was in gnome network manager.

---

