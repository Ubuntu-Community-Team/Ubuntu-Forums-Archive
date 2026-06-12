---
title: "Not able to hear anything."
date: 2022-01-12
forum: Multimedia Software
---

### Post by tavishmankash on 2022-01-12
Please look at the attached link. I'm new to alsa and don't understand a lot. [https://drive.google.com/file/d/15Pm9WyTkI2w0vURy7tqUKEqAI3FF92EB/view?usp=sharing](https://drive.google.com/file/d/15Pm9WyTkI2w0vURy7tqUKEqAI3FF92EB/view?usp=sharing)

---

### Post by TheFu on 2022-01-12
Sorry, I can't get to drive.google.com - blocked here.

Pulse sits on top of ALSA to make sound management easier.  For desktop Ubuntu, there is a sound guide. [https://help.ubuntu.com/stable/ubuntu-help/media.html.en](https://help.ubuntu.com/stable/ubuntu-help/media.html.en) which might be helpful.

---

### Post by him610 on 2022-01-12
This is only a guess, but it appears to me as if it may not be completely installed. 
Run this from the command line, *dpkg -l alsa* *
Compare to what the same command shows on my system...
```

$ dpkg -l alsa*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name               Version              Architecture Description
+++-==================-====================-============-=========================================
un  alsa               <none>               <none>       (no description available)
ii  alsa-base          1.0.25+dfsg-0ubuntu5 all          ALSA driver configuration files
un  alsa-oss           <none>               <none>       (no description available)
ii  alsa-topology-conf 1.2.2-1              all          ALSA topology configuration files
ii  alsa-ucm-conf      1.2.2-1ubuntu0.11    all          ALSA Use Case Manager configuration files
ii  alsa-utils         1.2.2-1ubuntu2.1     amd64        Utilities for configuring and using ALSA

```

---

