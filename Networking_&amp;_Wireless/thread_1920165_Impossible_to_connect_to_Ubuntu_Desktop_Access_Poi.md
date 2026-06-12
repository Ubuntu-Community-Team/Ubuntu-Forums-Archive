---
title: "Impossible to connect to Ubuntu Desktop Access Point"
date: 2012-02-04
forum: Networking &amp; Wireless
---

### Post by MrPantucci on 2012-02-04
Hello, I have created a wireless access point on my eeepc 701 running a fresh install of Ubuntu 10.04. 
The configuration: 
Ubuntu 11.04 laptop --WIFI--> (ath0)eeepc (eth0) --ethernet cable-->My ISP router-->Internet 

I followed this guide accurately: [https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router) (only difference, I set my wireless card running Madwifi drivers issueing 
```
sudo wlanconfig ath0 destroy, sudo wlanconfig ath0 create wlandev wifi0 wlanmode ap ath0
```, which seemed to work as my ath0 is now in Master mode. 

My other machine can now see the connection, but can't seem to connect to it. Looks like the connection attempt times out. 

Why could it be? I have spent two or three days reading how-tos and man pages, but as informative as it has been I still can't get things to work. 

Some info (I put it on pastebin so I would not flood the thread, please tell me if I need to include it here): 

[http://pastebin.com/8pXrRB4p](http://pastebin.com/8pXrRB4p)

Any help would be very appreciated. Please let me know if I need to post further info. 
Thanks

---

### Post by MrPantucci on 2012-02-05
bump!

---

### Post by MrPantucci on 2012-02-06
bump?

---

