---
title: "Print serving"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by False Dmitry II on 2009-09-24
Right now I've got an old box running xubuntu as a file/print/scan server. I got all parts working, but apparently the way the clients have been set up to interface to the server is not ideal. I simply followed the instructions for how to get a print server up on macs because CUPS is an apple thing and it seemed to work okay. The problem is that on the windows computers when you use programs like word or adobe acrobat to print, it shows up as a 2 KB empty file on the server that somehow also makes the printer "jam". Today when after I had added another comp using bonjour (only reason I can think of) it made other windows comps slow to a crawl when they tried to look at printing, I printed stuff from my laptop which was booted into ubuntu just to see if I could, and it did. I rebooted the server and it was back to the way it normally is. What would be a better method to use in order to get windows computers to talk with it better? And it would be great if they had full driver support instead of just being "generic postscript". It's a HP D7360, so I'm pretty sure it has the drivers on the linux side.

---

### Post by False Dmitry II on 2009-11-05
I just got samba to handle it. While not ideal it just works.

---

