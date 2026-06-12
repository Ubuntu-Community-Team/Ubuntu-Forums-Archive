---
title: "VPN connection very slow"
date: 2011-09-29
forum: Networking &amp; Wireless
---

### Post by raidoh on 2011-09-29
I'm connecting an Ubuntu 10.04 Server x64 client to a Sonicwall 2400 Pro via their NetExtender SSL VPN software, version 5.5.707 with Sun Java 1.6.0_26. The installation went fine; I can browse the network shares and VNC or RDP to my work machine. However, it's dog slow. Both browsing and VNC are fairly unusable, although connecting via NetExtender on my Macbook Pro works perfectly. Does anyone have any suggestions as to configuration settings I might look into to speed this connection up?

Things I've checked:

[LIST]
[*]SpeakEasy.net showed me about 15Mb down and 5Mb up for both the Ubuntu and OSX machines so equivalent and reasonably quick network connections.
[*]All machines are connected via Gigabit ethernet LAN (5e cables, switches, and cards) to a FIOS router, although the internet should definitely be the throttle here.
[*]iperf over separate subsequent VPN connections to office Windows iperf server
[LIST]
[*]Ubuntu client at home and Windows server at work = 70 Kb/s
[*]Mac client at home and Windows server at work = 5500 Kb/s
[/LIST]
 
[*]Checked MTU by sending smaller packet sizes until 0% packet loss. changed MTU to 1472 in NetExtender configuration as well as /etc/network/interfaces
[*]Ubuntu is on a static IP since it's my fileserver while the MBP is DHCP. (just FYI, as this this seems unrelated.)
[/LIST]
Now, I'm kinda stuck. Any ideas of what more I can try?

Thanks for the help.

---

### Post by chindichor on 2012-03-14
Looks like this is pretty common. Did you get a solution to this issue? I am suffering from the same!

My post is a tumbleweed now :( [http://ubuntuforums.org/showthread.php?p=11740027](http://ubuntuforums.org/showthread.php?p=11740027)

---

### Post by raidoh on 2012-03-14
I was never able to improve the connection. Downloading the latest software is a good start, though. Good luck.

---

