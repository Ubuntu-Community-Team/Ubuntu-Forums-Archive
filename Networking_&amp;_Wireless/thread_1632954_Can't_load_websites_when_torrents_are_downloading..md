---
title: "Can't load websites when torrents are downloading."
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by Kindatired on 2010-11-28
This is sorta a strange problem as it also happened in Windows Vista as well, one of the reasons I tried out Linux was to fix this problem (then fell in love with it and didn't go back). 

Anyway, problem is that when ever I start downloading a torrent, no matter what speed the file is downloading at - fast or slow, as soon as I open a browser and then load a website it's like my internet connection has died. "Chrome was unable to find the website" "Firefox could not load this site" ect ect.

The torrents will still keep downloading/uploading, instant messages programs still work, but websites will not load.

Does anyone have any idea what might be causing this?

Any help would be greatly appreciated.

---

### Post by cybergnome on 2010-11-28
This sounds like a bandwidth issue that's independent of operating systems.  Also some applications are known to be bandwidth hogs.  Some torrents, which I personally avoid, also employ a ratio scheme, in which your download feed is relative to what you upload.

In short a faster internet connection is the best fix.  Scheduling downloads to autorun, perhaps at night, when internet load is less and you're not doing any other web activities is another approach.

---

### Post by eentonig on 2010-11-28
> **cybergnome said:**
> This sounds like a bandwidth issue that's independent of operating systems.  Also some applications are known to be bandwidth hogs.  Some torrents, which I personally avoid, also employ a ratio scheme, in which your download feed is relative to what you upload.

In short a faster internet connection is the best fix.  Scheduling downloads to autorun, perhaps at night, when internet load is less and you're not doing any other web activities is another approach.


What brand and type of router do you have? Torrents make A LOT of separate connections (and NAT sessions). Some weaker models can't cope with that and hit their limits, causing new connections (your http request in example) to fail.
I had the same issue (with the router heating up very much, which pointed me in the right direction) until I changed my router for a more performant model.

---

### Post by lovinglinux on 2010-11-28
You need to setup your torrent client UPLOAD limit to 80% of your real UPLOAD speed, otherwise it will clog your network.

See [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923)

---

