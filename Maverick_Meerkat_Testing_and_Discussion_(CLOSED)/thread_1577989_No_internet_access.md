---
title: "No internet access"
date: 2010-09-19
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by raziology on 2010-09-19
Hey guys,

I'm having a very weird problem with my Ubuntu 10.10 Beta. The internet was functioning properly when all of a sudden, my two browsers (Chrome and firefox) stopped connecting to the internet. After numerous tries to connect, I get internet access for around 10 seconds, and then it just stops again. I'm %100 positive that nothing is wrong with my router configuration since I have windows 7 installed on my laptop as well, and it's working perfectly in there. I can connect to the router normally using the Network Manager applet, and it shows me that it's connected. Then I'm able to access my router's firmware through both of the browsers where I get to see that my PPPOE account is connected through the router. And when trying to ping the router, I have no packets lost whatsoever. What's more interesting to mention is that my torrent client (Azureus) is able to download files normally and with the usual speed without any problems, so this looks like a browser specific problem, most likely related to port 80. I didn't install any new programs on my Ubuntu nor firewalls. It just stopped surprisingly.

Does anyone have an idea what's happening?

---

### Post by termin on 2010-09-19
well since ubuntu 10.10 is a beta release, its not that stable. you should instead install ubuntu 10.04 because i had this too just 2 hours ago and this seemed to work for me. beta releases aren't too reliable.

---

### Post by termin on 2010-09-19
i also forgot to mention that if you havn't ever downloaded the ubuntu 10.04 cd do this on the windows 7 partition.

---

### Post by mkbecker on 2010-09-19
I had a similar problem.  I could run a wired connection just fine but got no response or show of any network in wireless.  I am running Ubuntu 10.04 on a five year old Dell Inspiron 6000 laptop.  At some point in the past my wireless card must have died because it would not work under Windows XP either.  I replaced the wireless card with another older Broadcom card and got perfect wireless performance under XP but not Ubuntu.  Somebody, who's post I cannot now find,suggested using Synaptic Package Manager to remove Network Manager and gnome-network manager and install WICD.  I did that,  followed the WICD installation instructions, and lo and behold I have wireless connection under Ubuntu again.

---

### Post by shahan on 2010-09-19
As 10.10 is a Beta Release, It just a test release. You can complain about ur problem on the lunchpad.

---

### Post by raziology on 2010-09-20
> **mkbecker said:**
> I had a similar problem.  I could run a wired connection just fine but got no response or show of any network in wireless.  I am running Ubuntu 10.04 on a five year old Dell Inspiron 6000 laptop.  At some point in the past my wireless card must have died because it would not work under Windows XP either.  I replaced the wireless card with another older Broadcom card and got perfect wireless performance under XP but not Ubuntu.  Somebody, who's post I cannot now find,suggested using Synaptic Package Manager to remove Network Manager and gnome-network manager and install WICD.  I did that,  followed the WICD installation instructions, and lo and behold I have wireless connection under Ubuntu again.

My problem isn't the same as yours since both, my wired connection and my wireless connection to the router, aren't giving me internet access using my browsers. Yet I'm able to download normally using my torrent client.

---

### Post by raziology on 2010-09-20
> **termin said:**
> i also forgot to mention that if you havn't ever downloaded the ubuntu 10.04 cd do this on the windows 7 partition.

My Ubuntu OS has been upgraded from Ubuntu 9.04 Jaunty to Ubuntu 9.10 Karmic Koala, then to Ubuntu 10.04 Lucid, and now to the new beta Ubuntu 10.10 Maverick. It has been around 2 weeks since I last installed the new beta with no internet connection problem whatsoever. It all began 2 days ago, without even updating anything nor installing any new programs.

---

### Post by dineshs on 2010-09-20
Please post results for```
ping -c5 google.com
```
```
ping -c5 4.2.2.1
```

---

### Post by raziology on 2010-09-20
> **dineshs said:**
> Please post results for```
ping -c5 google.com
```
```
ping -c5 4.2.2.1
```

The result for ```
ping -c5 google.com
```:


PING google.com (173.194.37.104) 56(84) bytes of data.
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_req=1 ttl=54 time=371 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_req=2 ttl=54 time=381 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_req=3 ttl=54 time=420 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_req=4 ttl=54 time=398 ms
64 bytes from lhr14s02-in-f104.1e100.net (173.194.37.104): icmp_req=5 ttl=54 time=377 ms


The result for ```
ping -c5 4.2.2.1
```:
64 bytes from 4.2.2.1: icmp_req=1 ttl=246 time=405 ms
64 bytes from 4.2.2.1: icmp_req=2 ttl=246 time=435 ms
64 bytes from 4.2.2.1: icmp_req=3 ttl=246 time=424 ms
64 bytes from 4.2.2.1: icmp_req=4 ttl=246 time=383 ms
64 bytes from 4.2.2.1: icmp_req=5 ttl=246 time=405 ms


Both results mean that I have no problem with my DNS configuration whatsoever. Any suggestions?

---

### Post by raziology on 2010-09-21
> **raziology said:**
> Hey guys,

I'm having a very weird problem with my Ubuntu 10.10 Beta. The internet was functioning properly when all of a sudden, my two browsers (Chrome and firefox) stopped connecting to the internet. After numerous tries to connect, I get internet access for around 10 seconds, and then it just stops again. I'm %100 positive that nothing is wrong with my router configuration since I have windows 7 installed on my laptop as well, and it's working perfectly in there. I can connect to the router normally using the Network Manager applet, and it shows me that it's connected. Then I'm able to access my router's firmware through both of the browsers where I get to see that my PPPOE account is connected through the router. And when trying to ping the router, I have no packets lost whatsoever. What's more interesting to mention is that my torrent client (Azureus) is able to download files normally and with the usual speed without any problems, so this looks like a browser specific problem, most likely related to port 80. I didn't install any new programs on my Ubuntu nor firewalls. It just stopped surprisingly.

Does anyone have an idea what's happening?

Has anyone figured out a solution for my problem?

---

### Post by SeijiSensei on 2010-09-21
I have a USB device that uses a Realtek chip and the rt2500usb driver in Ubuntu.  I've had a succession of connection problems with this device that are well-known and being repaired by the kernel developers.  I actually upgraded to Maverick just to get the newer kernels with the patches for this problem.

That said, the most recent kernel update from 2.6.35-10-generic to -11 made my wireless connection unstable once again.  I've reverted back to -10, and connectivity has improved considerably, though the connection does drop out briefly from time to time.  

You can find out what chipset is being used by typing either 'lspci' or 'lsusb' at a terminal prompt.  If your adapter has the very common Realtek chip as does mine, and you've been updating your Maverick system regularly, this might be your problem as well.  At boot, if both the -11 and -10 releases are listed, select the latter and see if that helps.

For more information, read these bug reports at Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549585](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549585)

---

### Post by lovinglinux on 2010-09-21
Is probably your torrent client clogging the network. Limit the UPLOAD to 80% of your UPLOAD bandwidth limit and also put some limit in the DOWNLOAD.

---

### Post by dineshs on 2010-09-21
Have you tried disabling ipv6?
[http://support.mozilla.com/en-US/kb/server+not+found](http://support.mozilla.com/en-US/kb/server+not+found)

---

### Post by raziology on 2010-09-22
> **lovinglinux said:**
> Is probably your torrent client clogging the network. Limit the UPLOAD to 80% of your UPLOAD bandwidth limit and also put some limit in the DOWNLOAD.

Even when I'm not using any torrent clients, I still cannot access the internet. But as I said, when I try my torrent clients, they seem to be downloading normally!

---

### Post by raziology on 2010-09-22
> **dineshs said:**
> Have you tried disabling ipv6?
[http://support.mozilla.com/en-US/kb/server+not+found](http://support.mozilla.com/en-US/kb/server+not+found)


My problem isn't tied to just one browser. I have tried Firefox, Chrome, and Epiphany. Same result on the three of them.

---

### Post by Iowan on 2010-09-22
Moved to Maverick Meerkat Testing and Discussion

---

### Post by raziology on 2010-09-22
> **SeijiSensei said:**
> I have a USB device that uses a Realtek chip and the rt2500usb driver in Ubuntu.  I've had a succession of connection problems with this device that are well-known and being repaired by the kernel developers.  I actually upgraded to Maverick just to get the newer kernels with the patches for this problem.

That said, the most recent kernel update from 2.6.35-10-generic to -11 made my wireless connection unstable once again.  I've reverted back to -10, and connectivity has improved considerably, though the connection does drop out briefly from time to time.  

You can find out what chipset is being used by typing either 'lspci' or 'lsusb' at a terminal prompt.  If your adapter has the very common Realtek chip as does mine, and you've been updating your Maverick system regularly, this might be your problem as well.  At boot, if both the -11 and -10 releases are listed, select the latter and see if that helps.

For more information, read these bug reports at Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/548992)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549585](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/549585)


I have tried both of my cards:
My wireless card which happens to be an Intel(R) Wireless WiFi Link 4965AGN and my wired ethernet card (Realtek PCIe GBE Family Controller).

Both of them are giving me the same result. Could both of them have the same glitch from the kernel?

---

### Post by dineshs on 2010-09-24
You may also try setting MTU
[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)
[http://ubuntuforums.org/showthread.php?t=1558579](http://ubuntuforums.org/showthread.php?t=1558579)
Note If your modem/router in PPPoE mode you may set MTU via the wired tab in Network mngr

---

### Post by raziology on 2010-09-27
> **dineshs said:**
> You may also try setting MTU
[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)
[http://ubuntuforums.org/showthread.php?t=1558579](http://ubuntuforums.org/showthread.php?t=1558579)
Note If your modem/router in PPPoE mode you may set MTU via the wired tab in Network mngr

Not even this was my problem..

Any other suggestions guys? I've searched everywhere with no luck!

---

