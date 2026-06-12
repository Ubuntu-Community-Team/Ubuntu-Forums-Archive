---
title: "Local Network Connections Die... But the Internet Still Works"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by lapgoat on 2010-10-23
I've been having this problem for some time now but have always worked around it.  It's just finally gotten so frustrating that I've decided to seek help.

First of all, info:
[LIST]
[*]I'm running Ubuntu 10.10, but this problem has existed for me since 9.10 (I didn't run Ubuntu on this hardware before 9.10)
[*]I have an Edimax EW-7128G PCI wireless card with an RaLink RT2561/RT61 chipset.  Ubuntu got the right drivers on its own and I've never had to mess around to get it connected.
[*]My network is WPA2
[*]I use Gnome's wireless manager to connect to my network
[*]I have tried both DHCP and static IP
[*]I have tried three different routers with the same exact issue
[*]Other network devices do not have any similar problems, I've narrowed this down to specifically something wrong on the affected machine
[*]IPtables are clean
[*]dmesg shows absolutely no relevant information (it won't show anything for literally days before I am forced to restart the connection)
[*]It's not some sort of weird hardware issue because the issue is not present when this computer is booted into Windows.
[/LIST]

Now, the problem:
After a seemingly random amount of time, (anywhere between 1 and 10 hours) my computer will stop responding to all devices on my local network.  This happens with every single thing I have tried: (HTTP, FTP, SSH, pings, Samba, HTTP/FTP on nonstandard ports)

This issue will also interrupt any existing LAN connections, so it's not just an issue with creating connections but also with maintaining them.

When this happens, however, my computer has no issues whatsoever communicating with the internet.  I can even connect to the computer from local devices by routing through the internet (which, obviously, is not a solution).

If I use the affected computer to ping other devices, *sometimes* the problem clears up for connections with that device for an hour or so.  It's successful maybe 1/3 of the time.  Constantly pinging devices was a workaround I tried, but if I constantly pinged them the solution went from successful 1/3 of the time to never successful.  It makes no sense to me.

I can clear up the problem with a 100% success rate by doing one of three things: I can disconnect from the network and reconnect completely (losing all active connections in the process).  I can right click the network manager applet and click on the name of the network, which seems to reauthenticate with the access point and keeps me from losing active connections.  I can run `sudo service network-manager restart` which also seems to force a reauthentication and doesn't drop any active connections.

dmesg with the relevant info from the last time this happened
```
[69185.548085] lo: Disabled Privacy Extensions
[71835.040090] wlan0: deauthenticating from 00:1c:10:12:49:09 by local choice (reason=3)
[71835.110072] cfg80211: All devices are disconnected, going to restore regulatory settings
[71835.110077] cfg80211: Restoring regulatory settings
[71835.110080] cfg80211: Calling CRDA to update world regulatory domain
[71835.434213] cfg80211: World regulatory domain updated:
[71835.434216]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[71835.434218]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[71835.434221]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[71835.434223]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[71835.434226]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[71835.434228]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[71836.580031] wlan0: authenticate with 00:1c:10:12:49:09 (try 1)
[71836.581562] wlan0: authenticated
[71836.581578] wlan0: associate with 00:1c:10:12:49:09 (try 1)
[71836.583764] wlan0: RX AssocResp from 00:1c:10:12:49:09 (capab=0x411 status=0 aid=1)
[71836.583766] wlan0: associated

```

I wasn't having any issue for about an hour of SSH usage, then it dropped.  About 10 minutes later I used the network manager applet to restart the network connection, which is what you see beginning at [71835.040090].  The line before seems to be irrelevant (there are a several instances of it in dmesg, however, anywhere from a minute apart to 8 hours apart).

I'd really appreciate any suggestions on this; it's really annoying to have to go run back to this machine every hour or so to manually restart the network manager if I'm connecting to it from another machine.

---

