---
title: "reset networking configuration?"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by alexweber15 on 2009-08-06
I recently updated a bunch of packages including firefox and a whole bunch of other updates that synaptic offered me and also installed ubuntu tweak and now everything internet-related is so SLOW.  most websites time-out or the DNS can't get resolved.  other computers in my network are fine.

i uninstalled ubuntu tweak but since I don't remember exactly what else I updated i cant exactly rollback the changes, 
**is there any way I can reset my networking settings?**

I have a feeling its a DNS issue...

im running Jaunty, connect using wireless and have a local lampp server set up...

thanks!

ps - I know, linux newbies shouldnt tweak their settings so much, I regret it but I can't do much about it now other than ask for help! :)

---

### Post by MadHatter21 on 2009-08-06
You could try changing you DNS to something like Open Dns. If you want to change your dns to open dns enter the following code into terminal.

```

sudo pico /etc/resolve.conf

```

Once you are in the editor, you can go down to the lines that say nameserver and swich them with the ip addresses of open dns. 

Change
```

nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

```

To
```

nameserver 208.67.222.222
nameserver 208.67.220.220

```

This will only change your dns server to Open DNS's servers. I am not one hundred percent sure if your dns is the problem though.

---

### Post by alexweber15 on 2009-08-06
thanks!

I followed the tutorial for ubuntu on the openDNS website and now everything is working perfectly (at least for the time being...)

---

