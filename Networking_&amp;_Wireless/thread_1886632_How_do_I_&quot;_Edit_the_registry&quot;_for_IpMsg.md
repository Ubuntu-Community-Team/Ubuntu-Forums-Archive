---
title: "How do I &quot; Edit the registry&quot; for IpMsg ?"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by raghav.venky on 2011-11-25
I use IpMsg.On installation I could see only the IPs on my floor. There's a neat registry edit for Windows which solves the problem :

Windows Registry Editor Version 5.00

[HKEY_CURRENT_USER\Software\HSTools\IPMsgEng\BroadCast]

"1"="172.25.2.2"
"2"="172.25.2.3"
"3"="172.25.2.4"
"4"="172.25.2.5"
"5"="172.25.2.6"
"6"="172.25.2.7"
"7"="172.25.2.8"
"8"="172.25.2.9"
"9"="172.25.2.10"
"10"="172.25.2.11"

so on upto "999" different IPs

What this does is it basically adds all the 999 IPs to 'Broadcast Setup for Wide Area Network'

How should I do this in Ubuntu 11.10? I can manually add all but there are 999 IPs!

I had Installed IpMsg using Wine.

---

### Post by s9032g@comcast.net on 2011-11-25
Ubuntu does not have a registry. Google it.

---

### Post by raghav.venky on 2011-11-26
I know. So how should I add all the IPs to the broadcast?

---

### Post by EarlsFurniture on 2011-11-26
Here's the page for IPMsg.  Scroll to the bottom.  There is a list of *nix versions.

[http://ipmsg.org/index.html.en](http://ipmsg.org/index.html.en)

Also, this second page is invaluable for understanding Linux networking:[http://www.aboutdebian.com/network.htm](http://www.aboutdebian.com/network.htm).

You might find after reading that one, that what you are trying to do is accomplished differently in Linux.

Here is a more thorough resource on Linux networking: [http://linux-ip.net/html/index.html](http://linux-ip.net/html/index.html)

Finally, I'm not super versed on networks yet, but my recollection was what you are trying to do should be handled by the router.  If you are running a message server, the message app or config file for it should handle what you want. (IPMsg is a way to broadcast without a message server, so this may not apply anyway.)

---

### Post by raghav.venky on 2011-11-26
Wow! I did understand some part of the above.

But my doubt still remains: How do I add all the IPs(Maybe with a code) to the broadcast settings in the IpMsg?

Or maybe, as you said, it has to do something with the Ubuntu settings?

---

### Post by EarlsFurniture on 2011-12-05
As I noted for the first link, there is a native linux version. (several actually)  I'd use one of those and perhaps you'll see the setting you are looking for.  (the version are for different desktops, if you aren't sure which you need, let me know)

I'd ditch the Wine version since you have a native linux option.

If after doing so, and reading the other two links on linux networking, you don't find what you are looking for, holler back and maybe someone else can lend a hand.

---

