---
title: "Hotspot internet sharing on Ubuntu 13.04"
date: 2013-07-17
forum: Networking &amp; Wireless
---

### Post by Ertai87 on 2013-07-17
Hi guys!  A quick question about setting up a hotspot on Ubuntu 13.04.  I appear to be using hardware which is compatible with sending a hotspot signal (the output of iw list appears to indicate as such), but I seem to be unable to get the hotspot working.  Here's what happens:

When I enable the Hotspot (through Settings -> Networking), if it's the first time I've done so, it will usually show the "connected to wireless network" thing on my computer, but when I try to connect with another device (I'm specifically using a Nintendo 3DS, if it matters) it can't find the network.  If I enable the hotspot and then disable the hotspot and then re-enable the hotspot again, I don't get the "connected to wireless network" dialog at all.  What's going on and how can I make this work?

Thanks.

---

### Post by annevleeshouwers on 2013-07-30
Hey

I also had the same problem with my DSi. The problem for me was that the DS cannot see Ad-Hoc hotspot. You could use hostapd to configure it or use ap-hotspot (that is what I did because it is easier).
If you use ap-hotspot you can just make a default hotspot and remove the last 5 lines in the config file
I made a more detailed guide if you want: [http://littleprogrammingadventures.blogspot.nl/2013/07/set-up-wireless-hotspot-for-ds-in.html#more](http://littleprogrammingadventures.blogspot.nl/2013/07/set-up-wireless-hotspot-for-ds-in.html#more)
Could you let me know if it worked?

---

### Post by sbnwl on 2013-08-03
Hi
[COLOR=#DD4814][COLOR=#000000][annevleeshouwers]("http://ubuntuforums.org/member.php?u=1841567") [/COLOR][/COLOR]is right. ap-hotspot is easier to configure.

You may find easy guide at [http://ubuntuforums.org/showthread.php?t=2165035](http://ubuntuforums.org/showthread.php?t=2165035)
Tell if any problems.

---

### Post by Ertai87 on 2013-08-05
That worked great!  Thanks!

---

