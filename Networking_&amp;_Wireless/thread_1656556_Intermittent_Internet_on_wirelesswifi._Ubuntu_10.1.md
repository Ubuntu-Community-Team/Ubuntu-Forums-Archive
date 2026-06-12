---
title: "Intermittent Internet on wireless/wifi. Ubuntu 10.10. Disconnects repeatedly."
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by okdone on 2010-12-31
Hi,

I just upgraded to Ubuntu 10.10 because I was facing internet problems with previous Ubuntu 9.04 after I upgraded it with downloaded software.

And now, 10.10 connects to wireless, but shows web-page some-times and repeatedly disconnects.

Earlier it wasn't reaching Internet at all. Some of the topics here helped a lot. But this intermittent internet seems not going anywhere.

Wired Internet connects easily though.

I've tried :-

-disabling ipv6..... first in Firefox, then in Kernel also
-Setting DNS.....System> Preferences> Network Connections
-setting static Ip

The system still gives trouble. 

My system is Asus UL20A. 
Wireless:-Atheros AR9285

Thanks a lot for the Help!!!

---

### Post by PatchesTheCaveman on 2010-12-31
Try installing updated drivers for your wireless card.  

To do so, go to Applications > Accessories > Terminal in your top panel.  In the black box that appears, type the following two commands, pressing Enter after each one:
```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

You'll need to reboot for the new drivers to take effect.

---

### Post by okdone on 2011-01-14
Hi,

Thanks a lot for the reply.  This solution really seems to work.  Its been a very long time that I returned to linux and thanks to you I'm browsing Net comfortably.

Though after half and hour or so the connection goes barren now. But it is none like earlier it disconnected too early.

Also the kernel 2.6.35.22 didn't connect to internet over wifi. The current kernel version I'm using is 24 and seems rather better. 

So thanks a lot for the solution. I'm sure this goes a long way. Thanks

---

### Post by okdone on 2011-01-14
Hi,

Thanks a lot for the reply.  This solution really seems to work.  Its been a very long time that I returned to linux and thanks to you I'm browsing Net comfortably.

The earlier frequent disconnection is much better.  I am sure now it is some issue with settings which makes the internet inactive after some time.

Also the kernel 2.6.35.22 never connect to internet over wifi. The current kernel version I'm using is 24 and seems rather better. 

So thanks a lot for the solution. I'm sure this goes a long way ahead. Thanks :-)

---

### Post by okdone on 2011-01-14
Hi,

Thanks a lot for the reply.  This solution really seems to work.  Its been a very long time that I returned to linux and thanks to you I'm browsing Net comfortably.

The earlier frequent disconnection is much better.  I am sure now it is some issue with settings which makes the internet inactive after some time.

Also the kernel 2.6.35.22 never connect to internet over wifi. The current kernel version I'm using is 24 and seems rather better. 

So thanks a lot for the solution. I'm sure this goes a long way ahead. Thanks :-)

---

### Post by okdone on 2011-01-14
Hi PatchesTheCaveman,

Thanks a lot for the reply.  This solution really seems to work.  Its been a very long time that I returned to linux and thanks to you I'm browsing Net comfortably.

The earlier frequent disconnection is much better.  I am sure now it is some issue with settings which makes the internet inactive after some time.

Also the kernel 2.6.35.22 never connect to internet over wifi. The current kernel version I'm using is 24 and seems rather better. 

So thanks a lot for the solution. I'm sure this goes a long way ahead. Thanks :-)

---

### Post by okdone on 2011-01-14
Hi PatchesTheCaveman,

Thanks a lot for the reply.  This solution really seems to work.  Its been a very long time that I returned to linux and thanks to you I'm browsing Net comfortably.

The earlier frequent disconnection is much better.  I am sure now it is some issue with settings which makes the internet inactive after some time.

Also the kernel 2.6.35.22 never connect to internet over wifi. The current kernel version I'm using is 24 and seems rather better. 

So thanks a lot for the solution. I'm sure this goes a long way ahead. Thanks :-)

---

### Post by Sam Lars on 2011-01-25
Is that package mainly for Atheros chipsets? I have a BCM4312, and it's been randomly refusing to work for a minute or so at a time.

---

### Post by conualfy on 2011-04-24
I just upgraded to Ubuntu 11.4 and the problem is still here. It's one of the bugs that makes you switch to another OS.

As I think people working on this are having hard time to reproduce the bug, I can allow some Ubuntu/Linux specialist to connect to my computer to debug it on this machine. If there is anyone interested, please email me personally on   florin [at] drumliber [dot] ro

---

### Post by ethos_dacapo on 2011-04-24
> **conualfy said:**
> I just upgraded to Ubuntu 11.4 and the problem is still here. It's one of the bugs that makes you switch to another OS.

As I think people working on this are having hard time to reproduce the bug, I can allow some Ubuntu/Linux specialist to connect to my computer to debug it on this machine. If there is anyone interested, please email me personally on   florin [at] drumliber [dot] ro

Yeah i've got the same problem. Wish i knew what a smooth upgrade was like. lol

---

### Post by conualfy on 2011-05-01
It's been a while since the upgrade to 11.4 and it's not so nice to know that something basic as a wifi connection that should just work out of the box it's not actually working.
Reconnecting the wifi connection makes the internet work again, but it's just a matter of minutes or seconds before I have to do this operation again.

I have changed the router encryption to none (I've lowered security by using only the MAC filter) and there is no difference, it's showing that I'm connected to the router, but the internet is not working at all.

I've just tried disabling the IPv6 and the bug is still here.

I tested the connection with this script:
[http://sourceforge.net/projects/wirelessscript/files/](http://sourceforge.net/projects/wirelessscript/files/)
The results for both the working wifi and the one not working (but showed by the network manager as connected) here:
[http://goo.gl/hyrZg](http://goo.gl/hyrZg) (reconnected, wifi working)
[http://goo.gl/sdgwL](http://goo.gl/sdgwL) (wifi not working)

I would allow some good willing specialist to debug this on my computer or any other way he/she suggests. If there is anyone interested in fixing this nasty bug, please send me an email on florin [at] drumliber [dot] ro


PS: I'm using a laptop (Toshiba Satellite C650 with Atheros wifi card and wifi under Windows 7 work perfectly.

---

### Post by ethos_dacapo on 2011-05-02
> **conualfy said:**
> It's been a while since the upgrade to 11.4 and it's not so nice to know that something basic as a wifi connection that should just work out of the box it's not actually working.
Reconnecting the wifi connection makes the internet work again, but it's just a matter of minutes or seconds before I have to do this operation again.

I have changed the router encryption to none (I've lowered security by using only the MAC filter) and there is no difference, it's showing that I'm connected to the router, but the internet is not working at all.

I've just tried disabling the IPv6 and the bug is still here.

I tested the connection with this script:
[http://sourceforge.net/projects/wirelessscript/files/](http://sourceforge.net/projects/wirelessscript/files/)
The results for both the working wifi and the one not working (but showed by the network manager as connected) here:
[http://goo.gl/hyrZg](http://goo.gl/hyrZg) (reconnected, wifi working)
[http://goo.gl/sdgwL](http://goo.gl/sdgwL) (wifi not working)

I would allow some good willing specialist to debug this on my computer or any other way he/she suggests. If there is anyone interested in fixing this nasty bug, please send me an email on florin [at] drumliber [dot] ro


PS: I'm using a laptop (Toshiba Satellite C650 with Atheros wifi card and wifi under Windows 7 work perfectly.

I went back and done a fresh install on an Acer Aspire ZG5 even after [this committed fix]("https://bugs.launchpad.net/ubuntu/natty/+source/linux/+bug/735171?comments=all") and it still doesn't work. The madwifi package fails to make with error code 2 so i'm still tethered.

---

### Post by atulkakrana on 2011-06-04
> **conualfy said:**
> I just upgraded to Ubuntu 11.4 and the problem is still here. It's one of the bugs that makes you switch to another OS.

As I think people working on this are having hard time to reproduce the bug, I can allow some Ubuntu/Linux specialist to connect to my computer to debug it on this machine. If there is anyone interested, please email me personally on   florin [at] drumliber [dot] ro

I tried to fix this problem in 10.04 and lost the battle...updated to 10.10 with belief that it must have been fixed...no luck

You can't live with this bug. After many wonderful years of linux  experience I was forced to switch to windows. 

I was a hardcord linux user and proponent but I realize my mistake coz many people came to me with this problem. People whom I encouraged and helped for years and made them to switch to linux. I didn't had any solution for this problem.

I am happy now with windows7 its way better then not just ubuntu but any linux out there. Internet is fast and realiable on this side and operating system is a rock...

---

