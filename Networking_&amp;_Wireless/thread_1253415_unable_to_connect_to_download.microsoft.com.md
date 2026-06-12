---
title: "unable to connect to download.microsoft.com"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by Gavla on 2009-08-30
I have a system here where I have one computer with Ubuntu on one hard drive and XP on another, and I boot between them. This one is connected to my Netcomm NB5 modem by ethernet. I also have a second computer sitting next to it with XP and a single USB connection to that modem.

Now, for the sakes of wine/winetricks, I wanted to get files from download.microsoft.com. I can access this site only through my two windows'; in Ubuntu, neither Firefox nor terminal can get there.

So I went to #ubuntu and #winehq looking for help and some great helpful people had me run some tests:
Iptables says I don't have any ip blocked. 
Dig returns:

[INDENT]dig download.microsoft.com
;; reply from unexpected source: 192.168.1.1#3072, expected 192.168.1.1#53
;; reply from unexpected source: 192.168.1.1#3072, expected 192.168.1.1#53
;; reply from unexpected source: 192.168.1.1#3072, expected 192.168.1.1#53

; <<>> DiG 9.5.1-P2 <<>> download.microsoft.com
;; global options:  printcmd
;; connection timed out; no servers could be reached
[/INDENT]

So they said that they thought my router DNS server was doing the wrong things, perhaps because it assumed it was on windows; with my present set up I can actually use the USB windows connection and the Ethernet Ubuntu connection at the same time. 

I upgraded the firmware, but that didn't help. I also tried using opendns.com to no avail. The user switcher firefox plugin, just in case Microsoft decided to block the browser/linux, also did nothing.

I did read somewhere about some windows users who were blocked from getting to this site via a trojan, but I am repeatedly assured that even if it did get into my wine, It couldn't do this.

Anyhow. I can really live without Civilization IV in wine (I can just boot to one of my windows'!); but those people helping me thought It was a bit of a brain scratcher. What's going on? Why am I denied my download.microsoft.com?

---

### Post by Gavla on 2009-08-30
Okay. Even though this wasn't a 'just for a couple of hours problem' as I first tried and failed and set aside for later a couple of days ago, it just started working for no real reason I can tell. BIZ-ARRE!

---

