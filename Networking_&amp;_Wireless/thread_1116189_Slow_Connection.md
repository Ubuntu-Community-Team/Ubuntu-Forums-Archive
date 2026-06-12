---
title: "Slow Connection"
date: 2009-04-04
forum: Networking &amp; Wireless
---

### Post by Grimble Gromble on 2009-04-04
I am new to Linux and decided to go with Ubuntu 8.10. One of the things I've noticed, my connection speed is now slower than molasses and ridiculously slow when using Transmission.

My wireless card is this one: [http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=285](http://www.encore-usa.com/product_item.php?region=us&bid=2&pgid=81_4&pid=285)

Here is further info:
  
*-network               
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:04:09.0
       logical name: wmaster0
       version: 20
       serial: 00:18:e7:1e:43:d5
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.1.100 latency=32 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 72:0e:ab:ee:1e:09
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I'm not sure if the drivers need to be updated or if something else needs to be done. Suggestions?

---

### Post by Mr Henderson on 2009-04-04
I don't suppose this is much consolation but as far as I can make out you're lucky it's working at all. (Writing this on a Windows machine.)

---

### Post by kreggz on 2009-04-04
What speed is your Internet Connection? You may find that you are uploading at such a high speed that it is affecting your web browsing.

Also
- Mr Henderson, your reply doesn't offer any value to this thread.

---

### Post by linuxuser21 on 2009-04-04
I notice this when I use Transmission as well.  Especially if I have it resume from when it left off.  I'm not sure Transmission is quite the best torrent handler.

---

### Post by Mr Henderson on 2009-04-04
Kept it near the top of the list, though, didn't it?

---

### Post by lisati on 2009-04-04
If you're using ADSL and the connection is slow on Windows as well, you might want to check the filter(s) on your line.
I recently had internet speed and connection problems, and as part of the troubleshooting process I hooked up my first ADSL modem (a "freebie" from my ISP) and got better a better connection than on the newer modem/router (another "freebie" from my ISP). After much muttering and cussing I discovered that using the filter I was using with the older modem seemed to work better with the newer one.

Just a thought......

---

### Post by kreggz on 2009-04-04
try Vuze and lower the download and upload speed as much as you can, then adjust as necessary, otherwise the torrenting will chew all your bandwidth.

The other thing you could do is let the torrent run only when you aren't using the computer.

---

### Post by Grimble Gromble on 2009-04-04
If I do a speed test online, it says the download rate is 6.50 Mb/S and upload is 0.24 Mb/s. I have Brighthouse's "High Speed Internet" for my ISP.

I am connected to a wireless connection and the connection fluctuates, usually staying around 10%. This happens without downloading or uploading anything.

I was using Windows XP before and the Internet was faster. I first noticed this when websites took longer to load with Linux. So it's not just an issue with torrents being slow because it appears to be related with the wireless network.

---

### Post by JK3mp on 2009-04-04
*note: i am not an expert..some of this is assumptions, LOL*
I have the SAME problem with mine but only when i get onto a wireless network that is protected..such as a WPA protected router etc. Im thinking it has something to do with that or the fact that something in it filters out those  ports causing the slower speeds. Again...not expert..but just going on a limb. If you didn't have to install the wireless drivers for you wireless card and it already worked..i would try maybe unloading the current ones,..downloading ones and install manually, may prove best, when i had 8.04 i had to load the drivers myself and it worked fine on any network, but when i switched to 8.10 it all worked fine out of box on free wifi networks, but when i get to a WPA protected router (running from charter cable if that makes diff) than i got horrible dial up downloads and slightly slower browsing. Know that might not help but maybe some of the info i provided will help someone else come to a conclusion. Good luck and i'll keep searching for answers.

UPDATE: Seems to run fine from protected router thats routing from a mobile broadband card on a desktop. hmmm...odd.

---

### Post by lisati on 2009-04-04
Another possibility: is there any clash or conflict with another wireless network in your area that Windows copes with better than Ubuntu?

---

### Post by Grimble Gromble on 2009-04-04
The wireless network is secure and it recognized everything which I thought was impressive. The next thing for me to try is a direct connection, but unable to do that at the moment.

Not sure if there is a clash but it does pick up another network. I deleted it thinking that might of been the cause.

---

### Post by kreggz on 2009-04-04
You could try disabling ipv6 - 
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)


it worked for me

---

### Post by Grimble Gromble on 2009-04-04
This will sound like a very dumb question. Would those commands be typed into the Terminal by going to Applications>Accessories>Terminal? As I said, completely new to this. I am some what hesitant to type something given the struggle to get this installed at 100%. If it will fix the problem I'll try it out.

---

### Post by kreggz on 2009-04-04
Yes, and if not done correctly could cause your system damage.

There are actually two ways of disabling ipv6, here is an easier way.

1. Go to your Terminal

type:

gksu gedit /etc/modprobe.d/blacklist

2. It will open the text editor. At the bottom of the text file press enter for a new line, keeping in mind that you don't delete or modify any text.

Type:
blacklist ipv6

3. Save the file and reboot your PC.

---

### Post by Grimble Gromble on 2009-04-04
I must be doing something wrong because nothing opens when I type the first command you mentioned. I'll have to read more about how to use this and thanks for the suggestions.

---

### Post by Grimble Gromble on 2009-04-05
The suggestion of typing the command in Terminal worked this time but I don't see an improvement of internet speed. Should my wireless connection to 'linksys' be at 100%? It feels like I am on dial-up when browsing the internet. If there is anything else I can do, I'd love to hear more.

---

### Post by kreggz on 2009-04-05
What is telling you that your network card is working out 100%?

Can you post the output of this command in a terminal:

ping google.com

---

### Post by Grimble Gromble on 2009-04-05
The NetworkManager on the upper right by the clock.

Here is part of it:

PING google.com (74.125.67.100) 56(84) bytes of data.
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=1 ttl=245 time=23.0 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=2 ttl=245 time=19.4 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=3 ttl=245 time=27.2 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=4 ttl=245 time=22.9 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=5 ttl=245 time=22.2 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=6 ttl=245 time=21.6 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=7 ttl=245 time=21.6 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=9 ttl=245 time=20.9 ms
64 bytes from gw-in-f100.google.com (74.125.67.100): icmp_seq=10 ttl=245 time=32.2 ms

This continues for quite awhile and the time is around 18-35 ms for 64 bytes.

---

### Post by Grimble Gromble on 2009-04-05
When typing this command: ping -c 4 google.com

I get this:

PING google.com (74.125.45.100) 56(84) bytes of data.
64 bytes from yx-in-f100.google.com (74.125.45.100): icmp_seq=4 ttl=245 time=20.8 ms

--- google.com ping statistics ---
4 packets transmitted, 1 received, 75% packet loss, time 3011ms
rtt min/avg/max/mdev = 20.879/20.879/20.879/0.000 ms

---

### Post by kreggz on 2009-04-05
Are you still running bittorrent? If so then disable it and try web browsing again.

---

### Post by Grimble Gromble on 2009-04-05
Nope. I gave up on that after it said it would take around 23 days to download something. I am only browsing on one site and nothing else is open.

---

### Post by kreggz on 2009-04-05
So is it still slow? What is slow in particular?

---

### Post by Grimble Gromble on 2009-04-05
Yeah, unfortunately. Browsing sites can take 5-15 seconds to load. I never had this issue when using Windows. I would think it has to do with the signal being so low and possibly the drivers it detected automatically.

---

### Post by kreggz on 2009-04-06
You could try and see if it works better with a hard wired connection... Other than that I dunno :?

---

### Post by Grimble Gromble on 2009-04-06
That's the next thing I am going to try and maybe the next release won't have this issue.

---

### Post by c-shadow on 2009-06-26
Did you try using ndiswrapper and WinXP drivers?
My PCI card is Micronet SP906GK with RTL8185 chipset:
[http://www.micronet.com.tw/product_model.aspx?series_no=4&category_no=0#WLAN%20Adapter](http://www.micronet.com.tw/product_model.aspx?series_no=4&category_no=0#WLAN%20Adapter)

It is working fine for quite a while in 8.10 32-bit. 
With native linux drivers (rtl8180 module) I have the same problems (slow connection, weak signal,...), tested in 8.10 32-bit and 9.04 64-bit. In jaunty 64 ndiswrapper doesn't work with WinXP 64 bit drivers. I think there are some bugs reported on launchpad. 
IMHO, native linux drivers for these cards are just pain in the ...

---

### Post by Charles Kerr on 2009-06-28
This sounds a lot like a router issue.  BitTorrent clients cycle through a *lot* of short-lived socket connections as they churn through the tracker-provided list of peers in search of the fasted connections.  This can often cause problems for cheap and/or misconfigured routers.  Problems caused by filling up the router's tables can persist for an hour (or more) *after* the BitTorrent client's been closed.

If this is the problem, the simplest workaround is to edit Transmission's preferences s.t. the maximum number of peers, both global and per-torrent, are much lower.  And, if the router is clogged, it should be rebooted in order to test things out properly.

If your router is tweakable, it's a good idea to increase its connection limit and to shorten the period for closing inactive connections.  If you're going to do a *lot* of p2p, it's probably a good idea to go wired (instead of wireless) and get a good router and/or install a good firmware such as DD-WRT or Tomato.

...but, that's more of a brain dump than an answer.  First thing to test is reboot the router and lower the maximum number of peers in your BitTorrent client. :)

---

