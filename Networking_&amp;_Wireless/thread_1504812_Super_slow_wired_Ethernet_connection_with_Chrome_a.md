---
title: "Super slow wired Ethernet connection with Chrome and Firefox in Xubuntu 10.04"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by adamsiddhi on 2010-06-08
Hello. 

**Bad News**
I just installed Xubuntu 10.04 yestarday and all is well except that my wired Ethernet connection is super ultra slow. It is so slow that high traffic sites will not even load and low traffic sites will take 5 minutes or longer to load. I guess any page with lots of CSS styling and scripting will have a hard time loading or not load at all. 

**Good News**
Text based pages seem to load up fairly quickly though. Google & Gmail seem to load fairly fast. Running a search is fast too. 

Xchat seems to work just fine as well as software downloading from the updater. Yesterday it wanted to download an over 80MB package of software updates. I accepted it and it downloaded the updates fairly fast. Well as fast as I am used to on my other machine with a healthy connection. 

**Solution Search**
I first tried to make my connection faster by following [[COLOR="Indigo"]**this tutorial**[/COLOR]]("http://wojox.homelinux.org/?p=46") to Disable IPv6 in GRUB. This did not help at all. 

I have read elsewhere and discovered that maybe I need to reinstall my Ethernet device driver so I ran the **dmesg |grep eth0** command in Terminal (to see info on my Ethernet connection & device) and this is what I got back:

[INDENT][    4.696577] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:c0:9f:65:4e:45
[   20.816185] b44: eth0: Link is up at 100 Mbps, full duplex.
[   20.816190] b44: eth0: Flow control is off for TX and off for RX.
[ 4575.499137] b44: eth0: powering down PHY
[ 4602.000202] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 4602.000207] b44: eth0: Flow control is off for TX and off for RX.
[/INDENT]
So a few questions....

**[COLOR="Red"]UPDATE[/COLOR]**
[COLOR="Red"]I decided to run a internet connection speed test from Chrome. First though, I had to download Flash Player. Actually I never got to downloading Flash Player since Adobe's website is not loading properly. All the CSS is missing and I do not see a download link. But while I was waiting I decided to fire up **Transmission **(torrent client) and download some audio books from ClearBits. At the same time I fired up **System Monitor** to see what was going on with my connection. 

So it turns out that as I was waiting for Adobe and three Internet speed test sites to finish loading, **System Monitor** was showing that I was only receiving around **1** to **2** KiB/s at any given moment. Then when I started downloading audio books with **Transmission**, the **Network History** section with in **System Monito**r was showing that I was downloading at a healthy speed in between **120** to **230** KiB/s. And like I said before there was no problem for **Update Manager** to quickly download that 80mb package yesterday and Xchat runs fast too. So whatever the issue is has to do with browsers in general: Firefox and Chrome.[/COLOR] 

[LIST]
[*]What should I do now? 
[*]Does the above info about my Ethernet device & connection look right and healthy?
[*]If I have to update my Ethernet driver, how would I do that?
[/LIST]

Thank you,
:adam

---

### Post by adamsiddhi on 2010-06-09
I fixed my problem by following this tutorial:

[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

YES!!:guitar:

---

