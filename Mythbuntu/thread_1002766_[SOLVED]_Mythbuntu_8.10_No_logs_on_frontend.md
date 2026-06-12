---
title: "[SOLVED] Mythbuntu 8.10 No logs on frontend ?"
date: 2008-12-05
forum: Mythbuntu
---

### Post by drifting on 2008-12-05
I am finally able to spend some time on my supposed HD frontend. I say supposed as I have never got it to work on HD content without pausing. Having googled for hours on end, I still cannot find out where you turn logging on, on the frontend? Now I may have lost the plot on this, but I can find no settings. (If I have blame it on this cold that is keeping me from work :-) )

BTW HD works on the server, and my main workstation, the machine I am having problems with is an Asrock AliveNF6P-VSTA, built in nvidia 6000 series, 2GB ram (well it was cheap) and an Athlon X2 3800

Paul.

---

### Post by newlinux on 2008-12-05
How are you running mythfrontend? from the command line or menu?

I know in hardy, if you run it commandline you can either do:
```

mythfrontend --service

```
 (which will use the optionss in the /etc/mythtv/session-settings file and use logging to /var/log/mythtv/mythfrontend.log)

or you could do:
```

mythfrontend -l /var/log/mythtv/mythfrontend.log

```

---

### Post by newlinux on 2008-12-05
Also, you might want to play with your playback profile settings for HD. That is a common problem. I recommend starting with CPU++

---

### Post by klc5555 on 2008-12-05
> **newlinux said:**
> Also, you might want to play with your playback profile settings for HD. That is a common problem. I recommend starting with CPU++

Also the networking connection to the backend might be too slow. HD generally seems to need hardwired 100Mbps Fast Ethernet, running full duplex. Which usually means networking with a Fast Ethernet switch instead of the more usual hub that tops out at half-duplex.

SD, on the other hand, would probably work OK even if you had to carry the bits to the frontend by hand.

---

### Post by drifting on 2008-12-06
Thanks guys.

Yes one of the reasons for wanting the logs was to find out where the problem was happening.

It was the logging to /var/logs/mythtv that got to me, as it was always empty? And all anyone ever mentions is the that the log should be there. I was auto starting the frontend, mythbuntu default, assumed this would log by default.

And as for my network, I use a 1GB switch, so hope it's not that :-) to be fair all I have read about h264 basically says it is a stinker to get running.

Regards
Paul.

---

### Post by SiHa on 2008-12-06
Is  /var/log/mythtv world - writeable?```
sudo chmod a+w /var/log/mythtv
```

---

### Post by drifting on 2008-12-07
> **SiHa said:**
> Is  /var/log/mythtv world - writeable?```
sudo chmod a+x /var/log/mythtv
```

Yep, you were right, it was permissions, wonder why the guys at Mythbuntu missed that one ? Mind you I would mess up way more, often amazed at the end product.

Regards Paul

---

