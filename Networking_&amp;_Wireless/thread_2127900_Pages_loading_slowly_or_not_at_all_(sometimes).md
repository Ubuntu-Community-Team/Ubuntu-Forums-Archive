---
title: "Pages loading slowly or not at all (sometimes)"
date: 2013-03-21
forum: Networking &amp; Wireless
---

### Post by alreadytaken4536 on 2013-03-21
Our home wireless connection was just switched to Comcast XFINITY and we got a new router, all of a sudden my Ubuntu laptop cannot handle loading certain pages in a timely fashion, but other computing devices in the house are doing just fine. When I open my browser and try to load a page, it takes an extremely long time (5 minutes for a single page sometimes (first world problems)), and before it loads I'm met with several "server not found" messages from Firefox and I have to repeatedly refresh. Usually what happens though is that I finally load a page like Facebook and then all subsequent pages from that website load without fail. Sometimes a simple refresh takes care of a page not loading immediately, and sometimes it does no good. I was just on a page and pressed the back button and received a "server not found" message on the previous page! That has never happened to me before and I have no idea how that would even work if I had already loaded the page earlier.

I'm running Ubuntu 12.10 and I'm using an Acer Aspire 5560 laptop. I have little to no practical knowledge of how networking (especially wireless) works, so I'm not sure what other types of information would be useful in solving this predicament.

Sorry if this problem seems a little vague right now, it's difficult to explain exactly what's happening. This is extremely frustrating and I would really appreciate help from you guys.

---

### Post by wildmanne39 on 2013-03-21
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.
Thanks

---

### Post by alreadytaken4536 on 2013-03-21
Thank you very much. While I was running that command, the terminal said "wget: unable to resolve host address `dl.dropbox.com', which I suppose is part of the same problem I'm trying to fix. It worked when I ran it a second time.

---

### Post by wildmanne39 on 2013-03-26
Hi, delete all networks in network manager then reboot and let network manager find your network and change you wireless settings to match the screen shots.
Thanks

---

