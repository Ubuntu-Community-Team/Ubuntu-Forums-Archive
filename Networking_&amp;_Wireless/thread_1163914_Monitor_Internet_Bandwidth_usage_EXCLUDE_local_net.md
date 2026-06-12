---
title: "Monitor Internet Bandwidth usage EXCLUDE local network"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by Xiviliai on 2009-05-19
Hi there,

I've been searching around for a long time now, and im having a lot of trouble setting up some form of bandwidth monitoring / internet usage system.

vnstat looked like a useful solution, however it only seems to log all traffic, which doesnt help me out much. Everything i have found so far always includes local network traffic as part of its calculations.

I have a small home network of 5 computers, and one user in particular is using the internet excessively (downloading torrents constatly, streaming videos / music constantly), and im hitting my monthly cap (50gb during daytime, unlimited at night). I have asked this person are they downloading, if so how much, and why cant they stick to night time, to which they deny, but i am convinced they are, i have taken a look at transmission statistics and its showing signs of usage, but it seems the stats are being reset regularly. 

I would like to be able to log statistics on this machine so i will have a simple "upload total" and "download total" but only of internet usage, completely disregarding local traffic. im not concerned about how much the local network is being used.

this machine is a laptop, and uses both wireless, and wired connections. there is a lot of local traffic due to storing all of my music / videos / software on a server that all the other machines connect too. so most of the bandwidth monitoring solutions i have come across wont help me out much.

The laptop in question is using Ubuntu Jaunty 9.04

My router is a netgear DG834G v3

I also would like this to run in the background, so that the user cant just reset the statistics, or shut down the logging.

Im open to any suggestions to fix this problem, i'll even buy a new router / modem if i thought it would give me the control that i needed. because as its going, i will have to find a way to block this person entirely from the network.

It would be nice to have logs of daily / monthly internet  usage.

The best looking solution i have found through searching so far is:
[http://duckzland.ismywebsite.com/2009/02/vnstat-checking-your-internet-bandwidth-from-the-web/](http://duckzland.ismywebsite.com/2009/02/vnstat-checking-your-internet-bandwidth-from-the-web/)
[http://ubuntuforums.org/showthread.php?t=932904](http://ubuntuforums.org/showthread.php?t=932904)

however, i dont know how to set this up, and i dont know what to do with the code provided. but i would like that, without the internal 

Thanks in advance for any help!

---

