---
title: "Ubuntu LiveCD to help test network connection?"
date: 2012-04-30
forum: Networking &amp; Wireless
---

### Post by Garnett on 2012-04-30
Hi there,

I'm having some problems with my network connection. My ISP is being as helpful as possible but they're pretty keen to try and exhaust every possible cause that might not be their responsibility.

I've run antivirus, and made sure there are no processes running that might be hogging bandwidth, but I thought I could make absolutely sure by doing a ping test and a trace route from a LiveCD.

There might be simpler Linux Distros to use, but Ubuntu recognises my wireless keyboard and mouse and is generally pretty friendly.

Is there a way to add network tools to the Live CD?

Thanks for any help with the above solution or suggestions for other ways of achieving the same goal.

---

### Post by chili555 on 2012-04-30
Running the live CD is a perfectly valid strategy. As well, all the network tools, if you mean ping, traceroute, dig, etc. are already there. What may or may not be there is the driver for your network device. If it's ethernet, I estimate that the chances are 98%; if wireless, maybe 75%. That's because the OEMs are forever coming up with new products with more features, lower price and no Linux driver.

If we can help you further, post back and we'll be happy to help.

---

### Post by Garnett on 2012-04-30
Hi Chilli, thanks for the reply.

I can get online wired fine with the LiveCD, but I could not find ping or traceroute and a quick google led me to beleive they are not on the LiveCD but need to be installed separately.

Perhaps I'm wrong?

---

### Post by chili555 on 2012-04-30
I am sorry I was evidently mistaken. You might try:```
sudo apt-get install gnome-nettool
```

---

