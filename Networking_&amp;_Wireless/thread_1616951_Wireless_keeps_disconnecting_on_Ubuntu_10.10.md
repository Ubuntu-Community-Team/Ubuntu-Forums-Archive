---
title: "Wireless keeps disconnecting on Ubuntu 10.10"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by bonbeeno on 2010-11-08
Hi to whoever reads this,

I have always had trouble in the past getting wireless adapters and what not to start working on Ubuntu but with each 6-month upgrade most problems are fixed while new ones are made. Since Ubuntu 10.10 just came out I thought I'd give it a go and test it with my hardware.

Before 10.10 Ubuntu could not connect with my wireless device and I had to do many things with gedit and such to get it working. After I have upgraded to 10.10 Ubuntu now recognizes my wireless device and network and I can search the web...but wait here it comes.


Literally minutes after a fresh install and first connection to my network my wireless signal will drop and prompt me to reconnect. Of course the first thing comes to mind I reconnect which doesn't work so I unplug the device and replug it making it works...Two minutes later my connection drops again and so I so reboot, and if you really want to know what happens next just restart this paragraph. 

Things you need to know
Operating System - Ubuntu 10.10 64-Bit
Wireless Adapter - Hawking HWUN3 Hi-Gain Wireless-N Network USB Adapter
Router - Apple Airport (99% sure it has all updates)

---

### Post by oak3 on 2010-11-09
If you use WPA authentication, try to change to WPA2 in router, it did solved my similar problem.

---

### Post by mvalero on 2010-11-24
Do you really want to solve your problem?
Well, assuming that, by "any" chance your problem was not a security and/or authentication with your router (WPA, WEP or nothing), here it goes:

I have always had problems with five different computers with ubuntu/wifi, I use ubuntu since v8.04, no release has ever fixed those problems and if you look in the forums (not just this one), you'll see that it's a very common problem for lots of people, many people claim that XP does well with that same hardware, well, I can say that too with mine.

I will not argue anymore, I just want to offer you a solution, so, see the image below.

[IMG]http://i54.tinypic.com/25gbi2e.jpg[/IMG]

Now, it doesn't have to be perfect, nor a parabolic surface or something equally weird, even a good reflection plane (a flat surface) would do the trick, mine is aluminium foil, but it can be anything metallic, even a metallic net, providing that the holes in the net are "tiny", no more than 1cm.

So I was just tired of this problem, it was just ridicolous, the router is in the next room, no more than 5m way, there's just a wall between the computer and the router, of course XP does just fine here and of course I like Ubuntu (and linux in several flavors) muuuuch better than winblows.

Is this criticism? Yes!
Am I being "harsh"? No!

As I said, I love Linux and I really love ubuntu, so, fix the problem with your drivers, you're not using the hardware at its real capacity, I'm an electronics engineer and believe me, you will not be more greener if you use 50mW or 100mW (or 12dB, 14dB or 19dB instead of 24dB) or whatever is the max power you use to set the wifi dongles/cards, you will just "scare" people off Linux just because of a "simple" problem like this.

By the way, I have turn many people here to Linux (and specifically to Ubuntu), some people have even found another way of earning decent money just by installing it and by teaching the basics to others, since 8.04 Ubuntu performs quite well on my five PCs, all with different hardware, including two laptops, but the wifi issue has always been a "bleeding wound".

Solutions?
Two, the first, give the user the possibilty of setting the transmit/receive power int their wifi gear, but obviously this won't be very wise...
The second, let the kernel or the network or wifi modules change the power accordingly to the needs of the connection stability (transmit/receive errors, you know, you're the programming guys).

I really hope this really gets fixed.

---

### Post by idealsceneprod on 2011-03-04
For anyone still experiencing this issue with Ubuntu 10.10, my problem was that I had nm-applet and wicd-daemon both running and conflicting.  Killall wicd solved it, then I removed wicd-daemon with apt-get  [http://valgameiro.com/linux-wireless-network-keeps-disconnecting-ubuntu-netbook-remix/](http://valgameiro.com/linux-wireless-network-keeps-disconnecting-ubuntu-netbook-remix/)  Val

---

### Post by eeverson on 2011-04-03
Tempting Fate with this but hey!

I had the same problem but it only started happening a couple of days after building my PC. So I went back and removed everything that I have added one by one to see what was the cause. 

I have just REMOVED ubuntu-restricted-extras and have been running for the last 30 mins. Before this I could get through about 3 minutes.

I hope this helps someone!

Cheers
Euge

P.S My Motherboard is a Zotac GEForce 9300 ITX Wifi

---

### Post by eeverson on 2011-04-03
Ok I spoke too soon :(

It made 45 minutes which is alot longer than before but then it failed to respond.

---

### Post by jellis2 on 2011-06-15
I think I have fixed this problem on my Ubuntu 10.10 server by turning off power management on wlan0

I had tried both network manager and wicd, separately and together, and was getting nowhere. Signal just dropped after 10 minutes or so and refused reconnection.

In the end completely removed wicd, upgraded network manager and turned off power management, and, touch wood, so far so good. Was on all day yesterday and all of this morning, which never happened before. 

```
IEEE 802.11bg  ESSID:"xxxxxx"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0D:72:71:E9:89   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by hausmusic on 2011-07-26
Excuse my ignorance, but would you be able to tell me how to execute that? I can't find anything about power management in the network tools. I am running ubuntu 11.04.
Thanks

---

### Post by thefasterblueone on 2011-07-26
Turn off power management.

```
sudo iwconfig wlan0 power off
```

---

### Post by selimhanov on 2012-06-18
I know this is an old post. But none of the solutions helped. And I found this solution...

> sudo apt-get install ntp

[http://ubuntuquestions.blogspot.com/2011/03/wireless-keeps-disconnecting-in-ubuntu.html](http://ubuntuquestions.blogspot.com/2011/03/wireless-keeps-disconnecting-in-ubuntu.html)

And it seems it worked for me. I haven't been disconnected for last 20 minutes.

---

