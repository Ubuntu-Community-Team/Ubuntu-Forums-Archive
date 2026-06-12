---
title: "Ubuntu 9.10 Slowing Down Wireless Network"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by BritishBlue on 2009-11-06
Hi, I've already posted this in the Newcomer section but thought that perhaps this would be a more appropriate forum for my problem. So apologies for the double post. :)
I recently migrated to Ubuntu from XP so I'm very new to Ubuntu and Linux in general.

Ubuntu has been great so far but it seems to be having an erratic effect on my internet connection as well as the wireless connection to my PS3 and laptop, both of which worked fine when I was using XP.

My ISP is Virgin Broadband (UK) which is connected to my NETGEAR WGR614v5, when I boot up Ubuntu everything goes pear shaped. I can't help but think perhaps Ubuntu is interfering somehow but I can't find anything in the help section. I went to the Netgear site and updated the router firmware, just in case, and fiddled with the various settings but no luck. 
I also checked the forums, a guy mentioned Wicd Network Manager which I currently have installed but unfortunately hasn't done the trick. I would greatly appreciate any help. Thank you in advance. :grin:

---

### Post by sgosnell on 2009-11-06
Exactly what does "everything goes pear-shaped" mean?  You haven't described your problem well enough for me to understand it.  Exactly what goes wrong, where?

---

### Post by BritishBlue on 2009-11-06
I'm not very good at explaining it because, as I said, I'm very new to Ubuntu Linux. 

Here's my best explanation: my 6 year old PC used to have XP but windows being windows it slowed my PC to a crawl. Even though the PC itself was slow the internet connection wasn't.
Then I installed Ubuntu which sped up my PC but has now ironically reduced my internet connection to a crawl instead. This, in turn, affects my wireless connection.

I know you're probably asking for more technical information so if there's other details you need let me know, I'll do the best I can.

---

### Post by sgosnell on 2009-11-06
Try [this fix](https://store.opendns.com/setup/device/ubuntu/).  It worked for me.  It seems that the DNS in Karmic is bent, if not broken, and using OpenDNS fixes things, at least for the time being.  I also set my router to use OpenDNS, and that may help.

---

### Post by BritishBlue on 2009-11-06
Thank you for the tip, I will try it. :KS

---

