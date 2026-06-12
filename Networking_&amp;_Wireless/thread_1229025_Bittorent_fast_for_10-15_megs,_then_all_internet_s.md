---
title: "Bittorent fast for 10-15 megs, then all internet slows down..."
date: 2009-08-01
forum: Networking &amp; Wireless
---

### Post by Raider007 on 2009-08-01
Hello all,

I'm new to Ubuntu, been working great for the past week except for this little issue...

When I use Bittorrent (Tranmission), it works great for the first 10-15 megs, maxing out my speed, then it hits a wall and drops downloading to 10% of what's capable... besides that, it slows my overall internet experience even if i close down the bittorrent client... 

if i turn off my wireless connection, then turn it back on through the network manager, my internet is back to normal speeds as long as I don't use bittorrent... start downloading a torrent files then the same thing happens...

I've setup my port correctly in the client, i've opened them up in FireStarter, and I've used the following code to make sure everything is fine..

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

anyone have ideas why my internet slows down so much after laucnhing bittorrent?

it's not that it's a seeding issue, because like i said before, even after i close my client down the internet is slow till i disable & enable my wireless..


edit: other points of interest...
I use Transmission on my mac, so i've put in the exact same settings...
router is a WRT54GL running Tomato firmware
speed test before running bittorrent: 17Mbs/2Mbs (speed boost through comcast, otherwise my connection is 8Mbs)
speed test after running bittorent (after closing software): 1.1Mbs

---

### Post by keith.newell on 2009-08-01
not sure if this well help or not, but i have found that using deluge instead of transmission greatly increases both my transmit and receiving speeds.  im not sure why though.  :)

---

### Post by Raider007 on 2009-08-01
> **keith.newell said:**
> not sure if this well help or not, but i have found that using deluge instead of transmission greatly increases both my transmit and receiving speeds.  im not sure why though.  :)

I tried Deluge as well... same issues... i get a good speed going, then everything drops...

---

### Post by darco on 2009-08-01
Could be your ISP...I know comcast throttles users after you eat up bandwidth in a pre determined amount of time...

darco

---

### Post by Raider007 on 2009-08-02
> **darco said:**
> Could be your ISP...I know comcast throttles users after you eat up bandwidth in a pre determined amount of time...
darco

I swapped over to my mac to make sure it wasn't a seeder/bandwidth issue...
maxed out my speed the whole download without issue...

try again on the ubuntu system... same thing, get a good speed going for about 30 seconds then my internet drops to a slow speed and stays that way till i disable the wireless connection, as soon as i turn the wireless back on, my speeds are maxed out again until I start using bittorrent...

rinse and repeat...

---

### Post by Raider007 on 2009-08-02
Here is an example of what i mean...

Fresh boot, cleared cache + history
[IMG]http://www.speedtest.net/result/530576498.png[/IMG]

Restarted computer

Opened transmission, got to about 20 megs out of a 375 meg torrent file, then my internet speed dropped, quit transmission.

Opened firefox, cleared cache + history
[IMG]http://www.speedtest.net/result/530577457.png[/IMG]

go to network manager, disable wireless, then immediately enable it again and my speeds are back to normal...

---

### Post by Raider007 on 2009-08-02
:)

---

### Post by Raider007 on 2009-08-04
in case this ever comes up and someone is wondering how to fix...
I narrowed down my issue to the built in Network Manager... I replaced it by installing Wicd ([http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)) and redoing my internet connection...

no more bittorrent issues, i can download and upload max speed...

---

### Post by darco on 2009-08-04
Good job....mark it "solved"

darco

---

### Post by Kaineward on 2009-11-23
I actually downloaded Wicd as well after experiencing the same problems. It didn't fix the problem. 

Not only do the speeds drop while using deluge, but if I do a speed test it shoots all the way to 11mibs and then drops slowly to 8mibs, then 6mibs... and so on. 

Then my net connection is completely shot. 

If anyone has any clues let me in on it. 

Thanks.

---

### Post by MikeFlint on 2010-11-02
Just like to add a "me too".

I have tried replacing Network-Manager with WICD, and also disabling IP6 in the OS. Neither really works.

Downloads are fine for a while, then speed gradually slows to about 1M.  Dropping the wifi connection and re-connecting fixes it for a while then dies again.

Have the feeling it's buffering somewhere.  If I get chance I'll try the various other drivers WICD offers to see if that helps. Am using 'wext' at the moment, whatever that is!

---

### Post by ProZac83 on 2010-11-17
Throw my hat in the ring here aswell. Trying to get a torrent going in any torrent software I;ve so far tried has the same results... Destroys my internet connection.

Any ideas?

---

### Post by slash070 on 2012-02-14
Im experience the same issue, the internet slow down in whole computer after downloading some torrent. It start downloading fine with max speed than and everything its good, but after a minute it stops. This thing getting me crazy, i tried everything from firewall, disable ipv6, open ports, change to wicd, bla bla bla.. In windows its OK.

Please help because i dont want back to Bindows... :D

---

### Post by DrMilo on 2012-03-05
I've tire transmission and deluge, about the same. I can't even load most webpages before I get a timeout error while a torrent is running.

 Looks to me like there's no bandwidth management at all; the torrent grabs everything and leaves nothing for the browser. 

Surprise! This started when I upgraded to 11.04!

---

