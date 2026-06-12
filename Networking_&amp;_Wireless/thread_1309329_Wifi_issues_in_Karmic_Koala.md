---
title: "Wifi issues in Karmic Koala"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by FreeTheBee on 2009-11-01
Hi,
Last week I upgraded my laptop from Jaunty to Karmic Koala. Besides fixing some issues it also introduced a wifi problem. My laptop is connected through wifi using a D-Link 524UP. 

Ever since the upgrade my connection acts up roughly every 10 minutes. It doesn't drop completely but it seems there is a dns problem. I cannot open sites anymore using urls, but opening one directly from the ip is no problem. Disconnecting and reconnecting solves the problem for the next couple of minutes. In jaunty this problem did not occur and also in XP, which I have in dual boot, I never experienced anything like this.

I am not really sure where to start solving this issue, does anyone have an idea what could be causing this?

---

### Post by mattweed9 on 2009-11-01
I am not sure what is causing this problem. A lot of people are having the same if not similar issues. The only thing  I have found " to work for me at least", is to install the Wicd network manager from the softwarote center. It at least makes the connection more sable. Once I installed it and rebooted, it worked fine other then poor signal strength. But it is the only thing I have found that seems to work in the mean time while the issue with Network Manager is being addressed.  I have tried just about all the other tools, and it's the only one for me, that provides a stable and usable connection.

Hope this helps.

---

### Post by FreeTheBee on 2009-11-01
Thanks for the advice. I switched to wicd and so far (approx.45 minutes) the connection is stable. Before it would have dropped a few times already, so it seems this did the trick.

---

### Post by obi22 on 2009-11-01
Hello!

I'm having the same issue since Karmic alpha5. It looks like a network manager problem, maybe something like apt-pinning and installing Juanty version would help?

---

### Post by chezzo on 2009-11-02
I'm also experiencing this problem... Really hoping a fix will be along soon!

---

### Post by FreeTheBee on 2009-11-02
For me things are still running fine now with Wicd. The connection has been 100%  since I installed it and no dns problems anymore.

I noticed I have dnsmasquebase as a redundant package in the janitor now, but I am not sure if it was in there before. Perhaps it is related to the issue. Just a shot in the dark, since I don't really know what I am talking about :-)

---

### Post by chezzo on 2009-11-09
Wicd doesn't work for me unfortunately - my wifi simply stops working completely when I install it.

So I'm bumping this topic, on the basis that the built-in Ubuntu Network Manager really should be able to handle wifi and I shouldn't have to switch to a different program anyway.

---

### Post by chezzo on 2009-11-16
bump

---

### Post by boz86 on 2009-11-16
wicd didn't work for me either in the wireless mode.

---

### Post by boz86 on 2009-11-16
wicd will authenticate just fine with the wireless network but seems unable to negotiate an IP address from it. Using WPA and confirmed I have the right passphrase.

wired worked just fine.

---

### Post by chezzo on 2009-11-17
I've managed to bypass the issue by switching my router settings from WPA(TKIP) to WPA2(AES). So seems TKIP may be the root of the problem?

---

### Post by WylieE on 2009-11-17
I'm also having this problem with NM or Wicd.   I can get around it by disconnecting and reconnecting every time I load a page (what a pain).


> **chezzo said:**
> I've managed to bypass the issue by switching my router settings from WPA(TKIP) to WPA2(AES). So seems TKIP may be the root of the problem?

Unfortunately, I don't know how to access my wireless network without TKIP, but this does seem to be related to the problem, because I can access other networks that don't require a key without any problem.

Any advice on how to solve this, or how to get around the TKIP requirement would be super appreciated.
Thanks!

---

### Post by chezzo on 2009-11-26
> **WylieE said:**
> Unfortunately, I don't know how to access my wireless network without TKIP

I had to boot into Windows to do it... I assume you don't have access to any other OS than Ubuntu then?

---

### Post by obi22 on 2009-11-30
Hi, you can try installing linux-backports-modules-karmic-generic - it works for me.

---

### Post by FreeTheBee on 2009-12-13
Hi,
After switching to wicd everything seemed fine but unfortunately I had cheered too early and the problem returned. Eventually I ended up booting into vista more and more. A while ago I did a fresh install of karmic and this didn't solve the problem either. I also installed the backports package, to no avail
Today I was looking into the settings of my router and unticked the wcn box (windows connect now). Ever since, the connection has been stable. As earlier it has only been a couple of hours, but it looks promising so far :).

---

### Post by rahnen on 2009-12-13
My wireless keeps disconnecting as well. I am currently "trying" to run 9.10 64bit w/ a Atheros AR5B93 and the wireless connects at @90%, then drops off to @50% after a couple of minutes, and then randomly disconnects there after. I installed WICD but continue to have the same problem.

---

### Post by rahnen on 2009-12-14
CoffeeCat Has the SOLUTION!
[http://ubuntuforums.org/showthread.php?t=1332317](http://ubuntuforums.org/showthread.php?t=1332317)

I loaded the (4) backport files as suggested and I am connected long and strong.

---

### Post by FreeTheBee on 2009-12-19
It seems my system is just playing jokes on me. Two days after turning off WCN the connection started dropping again. I went over the dpkg logs to see if I installed any updates related to the connection, but couldn't find anything. 
Now it seems to be ok again after installing the 2.6.32 compat drivers from [http://wireless.kernel.org](http://wireless.kernel.org).
I do hope this time the fix will be permanent.

---

### Post by FreeTheBee on 2009-12-21
Once again after two days the connection starting acting up. After ticking the WCN box in my router it worked again. 

It seems that the previous fixes were more a matter of somehow completely renewing the connection then actually making changes for the better. First, switching WCN off did the trick and then switching it on had the same effect. Installing the new wifi drivers also fixed it for a few days, so just a restart of the router does not seem to be the reason.

Does anyone have any idea what could be the cause of these issues? Perhaps a some cache problem or something.

---

