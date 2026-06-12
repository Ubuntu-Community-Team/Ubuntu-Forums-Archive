---
title: "Upgrading from 10.10 to 12.04 &#8280; saa7164 drivers for Hauppauge HVR-2250"
date: 2012-06-20
forum: Mythbuntu
---

### Post by keepitsimpleengr on 2012-06-20
I am looking to upgrade my 10.10 Mythbuntu .24 client/server to 12.04 Mythbuntu .25.  I have a HVR-2250 tuner with drivers (saa7164) compiled and installed with great help from [LowSky]("http://ubuntuforums.org/member.php?u=330216").

My question is:
[INDENT]will those drivers survive the upgrade and work with Mythbuntu 12.04
-or-
will I have to do a recompile?
[/INDENT]
*Note: *I have two clients, one a simple second HDTV which upgraded beautifully, and the second which is a workstation used for audio, graphics, videos, and Mythbuntu client &#8943; for support of the Mythbuntu system &#8943; which was a nightmare upgrade, now running Xubuntu without Unity.

---

### Post by crbnrod on 2012-06-20
I just installed from scratch on 12.04, so I can't say if the drivers will survive (I'd guess yes, though) or not, but there's much less to do for 12.04 to get the 2250 to work. Here's a link.

[http://ubuntuforums.org/showthread.php?p=11205874#post11205874](http://ubuntuforums.org/showthread.php?p=11205874#post11205874)

---

### Post by keepitsimpleengr on 2012-06-20
> **crbnrod said:**
> I just installed from scratch on 12.04, so I can't say if the drivers will survive (I'd guess yes, though) or not, but there's much less to do for 12.04 to get the 2250 to work. Here's a link.

[http://ubuntuforums.org/showthread.php?p=11205874#post11205874](http://ubuntuforums.org/showthread.php?p=11205874#post11205874)

Very cool! :p I post how it goes… 

Would you mind checking your /var/log/dmesg for version?

```
:~$ cat /var/log/dmesg | grep saa7164 | grep 'firmware upload'
[   15.650105] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3.fw)
```

For my old driver: "v4l-saa7164-1.0.3.fw"

---

### Post by crbnrod on 2012-06-20
```
[    3.688032] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
```

---

### Post by keepitsimpleengr on 2012-06-23
> **crbnrod said:**
> ```
[    3.688032] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
```

Well, the old firmware didn't make the upgrade, but your advice paid off hansomely :p

Now my version is:
```
[   22.276030] saa7164_downloadfirmware() Waiting for firmware upload (NXP7164-2010-03-10.1.fw)
```

Please, point your elbow at the ceiling and pat yourself on the back ):P

---

### Post by LowSky on 2012-06-23
I love getting credit. Haha. 
Anyway I always find it easier to reinstall the drivers.

---

