---
title: "How To Get Your Atheros 802.11n wireless working in 9.1"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by jackthe7th on 2010-01-11
I spent days trying to figure out how to get my atheros AR928x 802.11n wireless card to work in Ubuntu.  The card worked perfect in Windows 7 but the connection kept dropping in Ubuntu.  It would find my router and connect with 60% signal for about 5 seconds, then fall down to about 25% signal and then cut out altogether.  After searching for days to find a solution, I finally figured it out and figured Id post it here to let everyone else in the same boat have a working wireless too!

I found this solution from:
[http://quefyx.com/2009/05/23/installing-ubuntu-9-04-jaunty-on-asus-eee-pc-1008ha/](http://quefyx.com/2009/05/23/installing-ubuntu-9-04-jaunty-on-asus-eee-pc-1008ha/)

This solution is for JAUNTY (Ubuntu 9.04), so if you are running Jaunty, you can just follow that post.

If you are using Karmic (Ubuntu 9.1), you can follow this tutorial I'm posting.  It's pretty simple:

First, make sure you got all your files up to date. Type in a terminal:

sudo apt-get update

Let that run, and once its done, type into terminal:

sudo apt-get upgrade

Once that finished, restart your computer.  Again open up terminal and type:


sudo apt-get install linux-backports-modules-karmic


If you are using Jaunty, instead of karmic type in jaunty, if you use another version of ubuntu, you can find a list of versions and their names here:


[http://en.wikipedia.org/wiki/Ubuntu_(operating_system]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system"))

Restart your computer one more time, and you should be good to go!

This has been tested and confirmed to work on:
 -Ubuntu 9.1(karmic) with an Atheros 928x 802.11n wireless card, using the Ubuntu installed network software, in a Gateway NV53 laptop connected to a belkin 802.11n wireless router.

-HP base station / 802.11g airport express



This has been tested and does not work/has issues with:

-airport extreme


  I hope this works for you too, and if it does, please let me know with your hardware and Ubuntu version so I can post here what other setups have been confirmed to let this work.




Share and enjoy!

JackThe7th

---

### Post by kamina on 2010-01-11
Using these instructions I get it to work fine at .g speeds connecting to an HP base station / Apple Airport Express (old .g version).

However it still does not work well with an Airport Extreme, even when forced to .g speeds. It will stop transferring all the time.

Updating to a 2.31.2 kernel makes things a bit better (even with the other base stations), but still not very good with the Airport Extreme (.g speeds and transfers slower then 1MB/s and very slow to respond to input over ssh).

I think the Airport Extreme also has a Atheros radio.

---

### Post by jackthe7th on 2010-01-11
when you say it will stop transferring all the time, you mean that it does connect, but cuts out?

Thats strange that it would work with airport express but not airport extreme.  I am not totally familiar with those products, but Im going to assume the two products are not affected by the process I described.  The way I understand it, the process in this post is for installing the compat-wireless package which includes the atheros ath9k drivers needed for the wireless card inside your computer.  Don't quote me on that, but thats the way Ive come to understand it.  Therefore the external airport products would not be affected by installing these drivers.  However it could be that the drivers are not perfect and for some reason are not stable with the airport extreme.

The airport products come with an install disc for the airport utility correct?  It might be possible to use the windows install file in linux through wine or something, Im not sure but that would be a guess to why the airport extreme is not running properly.  It may need that airport utility.

Also the ath9k drivers are intended for atheros wireless 802.11n PCI cards and AHB wireless chipsets:

[http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

A process provided on that website also explains a way to install the ath9k driver, but I did not have any luck with it.

If you are using products and a wireless card that are 802.11g based, they may not be the right drivers for you because ath9k is meant for 802.11n, but again I am unsure.

---

### Post by kamina on 2010-01-12
The airport express / extreme are Apple made wifi accesspoints. They don't require drivers any more then other accesspoints.

My computer is an Asus EB1501 "eeebox" with the Atheros 9285 (I recollect) wifi chipset on a mini-pci card.

My conclusion is that the Atheros driver has compatibility problems with certain accesspoints, but works fine with others (at least after these workarounds). Funny thing of course is if the compatibility problems affect accesspoints with an Atheros radio (I don't know if it's just the airport extreme or others too).

My testing with the airport extreme has gone in the following way:

- Default ubuntu installation and AP settings (WPA2-PSK): Works bearably for a moment and then starts cutting. Transfers at 2-3MB/s for 5-10 seconds then dies completely for 60-90 seconds. Works again for a moment and then dies. This get's worse the more data is transferred.

- Default ubuntu installation and AP settings (no encryption): Cuts are shorter but still exist. Transfer speeds fluctuate between 100KB/s - 3MB/s

- Installing linux-backports-modules-karmic, default AP settings (WPA-PSK): Terrible lag, transfers fluctuate between 300-500KB/s but does not cut as much. Adding debugging options to the kernel causes the machine to crash.

Anyway, I find this might be important information for somebody, as while trying to solve my problems I noticed this "fix" solves the problems for most people, but not everyone. I think it could be interesting to see what kind of access points the people who this fix does not work for have, as it could be the key.

If somebody actually get's decent speeds from a .N network I would love to hear what accesspoint they are using and what their typical throughput is.

---

### Post by SiliconS on 2010-02-03
> **jackthe7th said:**
> I spent days trying to figure out how to get my atheros AR928x 802.11n wireless card to work in Ubuntu. The card worked perfect in Windows 7 but the connection kept dropping in Ubuntu. It would find my router and connect with 60% signal for about 5 seconds, then fall down to about 25% signal and then cut out altogether. After searching for days to find a solution, I finally figured it out and figured Id post it here to let everyone else in the same boat have a working wireless too!
Jack, you are a star. Thank you so much for posting your instructions. Yours was the one forum post I needed to find.

I've just bought an Acer Aspire Revo R3610 with the same Atheros AR928X mini PCI wifi plug-in. I've installed Karmic and the wifi was very poor, with low signal strength and frequent drop-outs, even when my access point was in the same room as the Revo. Wired ethernet worked perfectly.

I followed your instructions and the wifi is now almost perfect. It's had a couple of drop-outs when running XBMC at the same time as copying large video files over the air, but that might be an XMBC problem. (The error message is "error allocating memory".)

For the record, without me changing anything my system is using the default ath9x driver and I had already run the update manager several times before finding this thread. My access point is a LinkSys WRT54GS.

(Oh, and 9.1 isn't the same as 9.10 ;) )

Thanks again, jackthe7th. You saved me a lot of frustration.

---

### Post by MontyMeigs on 2010-02-22
Just to let you know that your fix worked a treat for me too. Many thanks. My access point is BT Home Hub (Original version) and the laptop I'm using is an Acer Aspire 5536. 

I'm a complete Ubuntu/Unix novice so if you ever get the time it would be good to know what the commands I ran actually did. Although I'm reading up on Ubuntu so I guess I'll discover for myself eventually.

---

### Post by Everybody Loves Hypnotoad on 2010-02-23
Dlink dwa-645 cardbus (atheros ar5008, bgn), dlink dir-655 router. I installed linux-backports-modules-karmic and I now get approximately the same speeds as what the intel 3945 (abg card) is capable of, 15/5 (less than half of what the wired NIC gives me).

iwlist wlan1 scan throws me a pretty lie about the network being able to handle only speeds up to 54Mb/s, the same as a scan with the 3945 does. Maybe I should try forcing n in the router ... I will try that.

---

### Post by rfbeck on 2010-02-24
I have a Sony VAIO with an Atheros AR9287 internal wireless and I installed Karmic in early February, without the Atheros working. I then connected to an Ethernet connection and updated my installation and still my Atheros didn't work. Do I have to specifically go to "compat-wireless package" to get the update?
______
Robert

---

### Post by alfal on 2010-02-25
Install backports in terminal as shown in post 1 and then install wicd from Ubuntu Software Center ...

---

### Post by rfbeck on 2010-02-28
Okay. That was certainly easy enough. Not to mention entertaining!
Thanks.
______
Robert

---

### Post by shawn.parrish on 2010-03-02
Seems to have fixed my intermittent problems with wifi on my Acer Ferrari one 200 series netbook (N214 zh6).  Wireless is labeled as an 'Acer Nplify 802.11b/g/n'.

Yes, that's 'Nplify'.  I don't understand marketing people...  Vanna, I'd like to buy a vowel.

Thanks,
Shawn

---

### Post by mikefreeman on 2010-03-04
Any idea how to activate wireless-n mode? I've got a wireless-n router (Linksys, but not near it to get the exact model). We have it set to mixed g/n mode because my laptop (Gateway NV53) is capable of wireless-n (Atheros AR928X), but my wife's older laptop is only wireless-g.

With Mint 8 (=Ubuntu 9.10) I cannot connect at wireless-n speeds with the ath9k driver, even after following this howto. Also, I'm still seeing broad fluctuations in connection speed, from 54mb/s all the way down to 1mb/s, and everywhere in between at random.

I can get wireless-n speeds if I switch into Windows 7, but why would I want to do that? ;) Any ideas how to activate 802.11n compatibility on this laptop? Thanks!

---

### Post by BrucePatrick on 2010-03-07
> **jackthe7th said:**
> I spent days trying to figure out how to get my atheros AR928x 802.11n wireless card to work in Ubuntu.  The card worked perfect in Windows 7 but the connection kept dropping in Ubuntu.  It would find my router and connect with 60% signal for about 5 seconds, then fall down to about 25% signal and then cut out altogether.  After searching for days to find a solution, I finally figured it out and figured Id post it here to let everyone else in the same boat have a working wireless too!

I found this solution from:
[http://quefyx.com/2009/05/23/installing-ubuntu-9-04-jaunty-on-asus-eee-pc-1008ha/](http://quefyx.com/2009/05/23/installing-ubuntu-9-04-jaunty-on-asus-eee-pc-1008ha/)

This solution is for JAUNTY (Ubuntu 9.04), so if you are running Jaunty, you can just follow that post.

If you are using Karmic (Ubuntu 9.1), you can follow this tutorial I'm posting.  It's pretty simple:

First, make sure you got all your files up to date. Type in a terminal:

sudo apt-get update

Let that run, and once its done, type into terminal:

sudo apt-get upgrade

Once that finished, restart your computer.  Again open up terminal and type:


sudo apt-get install linux-backports-modules-karmic


If you are using Jaunty, instead of karmic type in jaunty, if you use another version of ubuntu, you can find a list of versions and their names here:


[http://en.wikipedia.org/wiki/Ubuntu_(operating_system]("http://en.wikipedia.org/wiki/Ubuntu_%28operating_system"))

Restart your computer one more time, and you should be good to go!

This has been tested and confirmed to work on:
 -Ubuntu 9.1(karmic) with an Atheros 928x 802.11n wireless card, using the Ubuntu installed network software, in a Gateway NV53 laptop connected to a belkin 802.11n wireless router.

-HP base station / 802.11g airport express



This has been tested and does not work/has issues with:

-airport extreme


  I hope this works for you too, and if it does, please let me know with your hardware and Ubuntu version so I can post here what other setups have been confirmed to let this work.




Share and enjoy!

JackThe7th

Thank you so much. I was getting dropped connections every 30 seconds and was about to give up but this fixed the problem. :p

---

### Post by Paulnug on 2010-03-09
Hi,

I am a complete linux novice. 

I have an Acer Revo 3600 - no idea what the Wifi Card is and not sure how to find out.
Router is a Lynksys WR54 running 802.11bg but not n - according to iwconfig

I ran the instruction, note to other 3600 users, you will have to reinstall the Graphics drivers.

The Wifi speed is 3Mbps   which sounds great but on my Mac book, sitting 1 foot away I get speeds of 15Mbps and I can't figure out why the discrepancy.

Any idea or suggestions greatly appreciated.

Is there a way I can measure speed between the Revo and the Router so I can rule out any external factors?

---

### Post by AComplex on 2010-03-09
Hey, I just want to thank you again for this tutorial. It's seems be working good on a Toshiba Satellite a500.

---

### Post by erktheerk on 2010-04-21
Worked on my HP Pavilion Elite e9120f....thanx

---

### Post by edthemlb on 2010-09-06
Worked on my el cheap-o eMachines, AMD64 A5001, Karmic 9.10.  Thanks for posting

---

### Post by z987k on 2010-10-23
Is there a fix for 10.10?

Installing linux-backports-modules-wireless-maveric-generic did nothing for it.

---

