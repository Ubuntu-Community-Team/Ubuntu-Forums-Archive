---
title: "Downloading Issue (PLEASE HELP)"
date: 2006-01-18
forum: Networking &amp; Wireless
---

### Post by zimele on 2006-01-18
Hey this is my problem

Before i was having Problems connecting to the Internet Using Firefox In Ubuntu Badger Breezy 5.10 and i managed to sort the issue out with the help of Ubuntu guide but now my problem is with downloading Repositories or any other Ubuntu based software this is software that is within the Add packages option, it starts the download but then after a minute or So it say it timed out, i found that my Internet issue was with 

 **Q: How to load Web site faster in Mozilla Firefox?**

Read General Notes 
Applications -> Internet -> Firefox Web Browser 
Mozilla Firefox 
Address Bar -> about:config

Filter: ->
network.dns.disableIPv6 -> true
network.http.pipelining -> true
network.http.pipelining.maxrequests -> 8
network.http.proxy.pipelining -> true


Now this is what i did and My Internet Started to work. now my main problem is with downloading new things

---

### Post by mips on 2006-01-18
Try this,

Open a terminal and enter:
**sudo gedit /etc/modprobe.d/aliases**

Look for the line that reads:
**alias net-pf-10 ipv6**

Change it to:
**alias net-pf-10 off #ipv6**

**Save and reboot your PC.**

alternatively you can stop the IPv6 module loading.
Try adding your dns servers amnually.
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by zimele on 2006-01-19
Thanks for the Help One more Question is there anyway to speed up downloading cause i noticed that on my Windows Machine i am able to download way faster than on my Linux Machine, now my question is that is it possible to speed this up or is this how it is?

---

### Post by mips on 2006-01-19
What are you using for downloads in windows & linux ?

For faster webpages install the Fasterfox extension.

---

