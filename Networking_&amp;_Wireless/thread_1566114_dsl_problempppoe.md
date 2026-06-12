---
title: "dsl problem:pppoe"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by amalnath on 2010-09-02
hi all,
 now having problems with dsl.have been using dsl without a glitch for a long time. all of a sudden, from today, dsl not connecting.
plog gives output: unable to complete PPPoE discovery......what to do???):P

---

### Post by dineshs on 2010-09-02
Are you using 10.04?
How do you connect to modem/router?Wifi or ethernet?
Can you ping modem(default gateway)?
What does```
ifconfig -a
```say

---

### Post by amalnath on 2010-09-03
):Phi,
         First of all, thanks for the quick reply.........
now it seems the dsl is working after a few restarts. dont know what went wrong earlier.moreover dsl was working in windows..
using LUCID, connect dsl by pppoeconf..:lolflag:

---

### Post by dineshs on 2010-09-04
If you are using Lucid try this
[http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2)

---

### Post by amalnath on 2010-09-05
Hi, 
  'm connecting/disconnecting router by using sudo pon dsl-provider/poff. so shall i have to make any other configuration changes before executing the commands in the given link?? [http://ubuntuforums.org/showpost.php?p=9611450&postcount=2](http://ubuntuforums.org/showpost.php?p=9611450&postcount=2). moreover now after leaving the screen idle for a few minutes, it goes blank and gets a small window stating 
"Ubuntu is running low graphics mode.
 your screen, graphics card and input settings could not be 
 detected correctly.You will need to configure these yourself"
it seems OK after a restart..

---

### Post by dineshs on 2010-09-05
If pon dsl-provider is working fine you need not try the link
> Ubuntu is running low graphics mode.
your screen, graphics card and input settings could not be
detected correctly.You will need to configure these yourseMay be a driver issue.try google search to find answers like this
[http://ubuntuforums.org/showthread.php?t=628790](http://ubuntuforums.org/showthread.php?t=628790)

---

### Post by amalnath on 2010-09-07
i have already reconfigured 'X'. but it doesn't seems to work.
May b some loose cable issues or so.Anyway now it occurs only if i leave the screen idle for some time.

---

