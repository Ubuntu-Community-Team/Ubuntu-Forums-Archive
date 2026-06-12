---
title: "Jdownloader"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by gberet on 2009-12-16
Is there a program like jdownloader for UBUNTU, and if not,how can I download multiple links from rapidshare and other servers?

---

### Post by konqueror7 on 2009-12-16
> **gberet said:**
> Is there a program like jdownloader for UBUNTU, and if not,how can I download multiple links from rapidshare and other servers?

you just need an installed java environment,,,jdownloader is platform independent, it runs on windows, mac, and linux just the same...

if you don't still have java, type this in a terminal,
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by gberet on 2009-12-16
Thanks dude, but I have already installed Java.. still not opening

---

### Post by gberet on 2009-12-16
Thanks dude, but I have already installed Java.. but still when opening Jdownloader Jar I find no respond..
Plz tell me what to do

---

### Post by konqueror7 on 2009-12-17
have you downloaded the linux version of jdownloader?

have you more java platforms installed? like openjdk or ice? uninstall them and update your java,

```
sudo update-java-alternatives -s java-6-sun
```

this will able to select the default environment to use, if you have multiple instances, see if it works,,,while mine here works perfectly...

---

### Post by schnelle on 2010-01-06
I wrote HOWTO for Kubuntu but it should work for Ubuntu too. Check it out: 

[http://ubuntuforums.org/showthread.php?t=1374208](http://ubuntuforums.org/showthread.php?t=1374208)

---

