---
title: "Firefox sees through proxy, but not apt/anything else"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by BetterSense on 2011-12-23
I really need to set up a Linux box at work. I have it connected to the corporate network with a wireless dongle. I can configure firefox to "use proxy autoconfiguration URL" and type in the url of the PAC file and firefox works and can get to the external internet. But I cannot figure out how to get the rest of the system that way! I really need to install updates and programs or the system is useless. I also want to be able to use Synergy. I've been trying for a long time, and google isn't helping. It seems like anyone who tries to use Ubuntu on a corporate network needs to be able to do this?

I've gone to System/Preferences/Network Proxy Preferences and checked "automatic proxy configuration" and entered the proxy .pac URL just like Firefox, and I hit the "Apply System-Wide" button, but apt still won't work. Please help? I really want to use Linux at work.

---

### Post by zippyut on 2012-01-02
I've been trying to figure out something similar and posted a previous email.  Seems no one knows how to do this.  There was a little blurb about using the command: export http_proxy="http://ip : port" (no spaces between the ip and port, just didn't want it to change it to a :p).  Give it a try.  If you find another solution, please post!  :)

---

