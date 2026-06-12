---
title: "internet too slow to stand and no fix yet has worked."
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by megamindstorm101 on 2011-09-15
I just got a fujitsu laptop for 300$ [http://ncix.com/products/?sku=62616&vpn=FPCR46034&manufacture=Fujitsu](http://ncix.com/products/?sku=62616&vpn=FPCR46034&manufacture=Fujitsu) I was planning on running ubuntu linux on it (or mint) and it has a strange problem where the internet is slow as heck. I remember now that last time I installed on my desktop it was slow as well so it is not just my laptop. Basically in windows and I download something huge it will download at 2 megabytes per second or so but in ubuntu when I am downloading something i get 60kb/s which is ridiculously slow. I was about to give up but my friend keeps telling me to post on the forums so I am here now hoping someone can find the answer to my misery. 

regardless of weather i am wired or wireless the intnernet is about the same speed (in fact it seems about 20kb/s faster when I am using wireless).

I am running ubuntu 64bit 11.04

---

### Post by varunendra on 2011-09-16
Let's pick one interface at a time, either wired or wireless. Since wired LAN issues are usually less complicated, I'd suggest to pick it first. Then, when it gets resolved (or if we give up on it ;)) we can pick the wireless one.

So, in order to find the answer to your misery :), we need details which the outputs of the following commands may provide:
[Note: Do some browsing first for a couple of minutes, then enter these commands in a terminal one-by-one]```

sudo lshw -C network

ifconfig -a

cat /etc/resolv.conf

ping google.com
(or any site which appears painfully slow in comparison to windows)
```Wrap each set of output in [ code] and [ /code] tags as described [here]("http://ubuntuforums.org/misc.php?do=bbcode#code") for better readability.

Also, how do you connect to internet? If it is an adsl modem/router, which brand and model? There have been some models whose firmwares had been reported to cause problems with linux kernel in the past.

---

### Post by megamindstorm101 on 2011-09-22
alright well I uninstalled ubuntu on this machine because it took forever to get a response from someone and I think I am goingto reinstall itthis weekend and try this out. 


as for the router its a cisco linksys (forget the model number) its the 80$ wireless N router. 


I find a lot of people having problems with this atheros card though thats in my laptop and no other fix has worked yet. its very bothersome because I _REALLY_ want to use ubuntu on this laptop (75% of the reason I got it) and with no internet it is virtually useless.

---

