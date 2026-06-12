---
title: "slow connection over LAN"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by aaronp on 2010-01-09
Hi all,

I'm running Ubuntu Karmic on my desktop machine which is connected to my wireless router (via LAN cable).

I have two laptops on the LAN as well.
One is my wife's Windows 7 laptop and the other is my Ubuntu Karmic laptop.

They both connect wirelessly to the LAN and all three computers have static IP addresses assigned.

So here's the issue.
The desktop serves the laptops over the LAN with Samba file sharing, SSH, VNC and DAAP.

From the Windows 7 laptop, the connection over the LAN is fine. I generally use it to connect to the Samba shares and occasionally use it for VNCing to my Desktop's....desktop.
It is fast and responsive.

From the Ubuntu laptop though, everything seems very slow.
Connecting to the samba shares results in a wait of at least 30-60 seconds, even if they have only recently been accessed. Once it has connected (i.e. once the share opens up and you can see files) actually opening the files themselves is delayed too, but not to the same extent.

Also, connecting to the desktop via VNC is intolerably slow, with mouse movements being so delayed that it is almost impossible to click on anything.

SSH takes a long time to connect too (up to 30 secs) but obviously once connected it is fine. In a similar vain, FreeNX connection takes a long time to connect but once the desktop has loaded it is fine too.

I can use FreeNX instead of VNC but actually like using both for different functions. I understand VNC is slower than FreeNX but over a 100Mbps LAN connection I wouldn't expect it to be slow at all.

This laptop used to be a Windows Vista/Win7 laptop prior to being replaced with Ubuntu and it was able to connect to the server with no speed problems.


Any ideas what this could be? 

thanks
Aaron

---

### Post by ler0y on 2010-06-02
Maybe IPv6 slowing things down? 

This thread may be some help:
[http://ubuntuforums.org/showthread.php?t=14721541](http://ubuntuforums.org/showthread.php?t=14721541)

---

