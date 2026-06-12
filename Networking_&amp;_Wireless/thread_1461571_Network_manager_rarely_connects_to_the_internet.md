---
title: "Network manager rarely connects to the internet"
date: 2010-04-24
forum: Networking &amp; Wireless
---

### Post by AKG_8 on 2010-04-24
Hi folks,

I am using Ubuntu 9.10 and HP laptop dv6000 pavilion.

I use network manager and the wired connection is fine, but the wireless very rarely connects to the internet .. sometimes in one click it connects, sometimes it never connects .. and displays the message " wireless network disconneted".

Please suggest what to do .. I am new to linux and don't know much about it ..

Thanks

AG

---

### Post by mr clark25 on 2010-04-24
sounds like the connection might be weak. if you just hover over the network icon, it should give you the signal strength in %.

you could also get a wifi scanner from the software center that should display the strength of all networks available.

how strong is the signal when it wont connect?

---

### Post by kindred7 on 2010-04-24
1. Do you have windows dual booted? If so you can see how windows fairs in connecting. If both have an issue u may want to take a look at ur router settings.

2. If you have another laptop u can see how it compares to connecting and go from there.

3. Try connecting to ur wifi network by being as close to the router as possible. Try to connect, if u still have an issue it may be the router. Or you can try to use wicd instead of network manager. I had several "random disconnecting" issues with network manager and wicd fixed them.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php) scroll down to installing on ubuntu

hope that helps

---

### Post by AKG_8 on 2010-04-24
Hi folks ..

Many thanks for the replies

My roomie has windows xp and he never has a problem using the wireless .. I have tried to connect being close to the router but that also does not help ..

Signal strength also did not show a pattern ..sometimes even at weak signals it connects .. sometimes even at strong signals it does not ..

I had wicd before and using that I was never able to connect .. atleast using network manager it connects some times ..

I ran this command while searching this forum
dmesg | grep -e ndis -e wlan


and the results were

ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   18.935453] usbcore: registered new interface driver ndiswrapper
[   19.666595] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   49.267420] wlan0: authenticate with AP 00:22:3f:96:ff:06
[   49.269209] wlan0: authenticated
[   49.269213] wlan0: associate with AP 00:22:3f:96:ff:06
[   49.272374] wlan0: RX AssocResp from 00:22:3f:96:ff:06 (capab=0x421 status=0 aid=3)
[   49.272378] wlan0: associated
[   49.274164] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   60.028097] wlan0: no IPv6 routers present
[   94.811621] wlan0: disassociating by local choice (reason=3)
[  103.957552] wlan0: authenticate with AP 00:22:3f:96:ff:06
[  103.959368] wlan0: authenticated
[  103.959374] wlan0: associate with AP 00:22:3f:96:ff:06
[  103.962451] wlan0: RX AssocResp from 00:22:3f:96:ff:06 (capab=0x421 status=0 aid=3)
[  103.962457] wlan0: associated
[  149.809108] wlan0: disassociating by local choice (reason=3)


Perhaps this can give a hint to the problem

Please advise

Thanks

A

---

### Post by kindred7 on 2010-04-24
The problem seems to be this line here:
"disassociating by local choice (reason=3)"

Not sure what reason three is. But doing some more searching:
[http://ubuntuforums.org/showthread.php?t=1123627](http://ubuntuforums.org/showthread.php?t=1123627)
Which lead me to this:
[https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/361461](https://bugs.launchpad.net/ubuntu/+source/wicd/+bug/361461)

(Yes I know that thread is specifically for wicd)

Someone here had the same problem and it worked with wicd, the latest version. How long ago did u try wicd? Because the problem I am talking about was solved this morning. Depending on how long ago u tried wicd it might work now. Perhaps u could give it another go?
Be sure all of network manager is uninstalled after installing wicd.

EDIT: 

Disassociating by local choice (reason=3 seems to means Radio Kill Switch=ON. so naturally your wifi wont work if its set to ON. I'm unsure how to get it to =OFF. For now try wicd and we'll go from there

EDIT2:

If all else fails you may have to build your own drivers from the latest source. 
[http://wireless.kernel.org/en/users/Drivers](http://wireless.kernel.org/en/users/Drivers)

---

### Post by AKG_8 on 2010-04-25
Hi kindrer7 .. Thanks for the suggestions .. I really appreciate it .. 

i installed the latest wicd but it did not help .. also tried to find how to toggle radio kill switch = ON .. could not find any thing ..

my wireless card is iwl3945 .. I don't know how to find and install the drivers . please help .. 

AG

---

