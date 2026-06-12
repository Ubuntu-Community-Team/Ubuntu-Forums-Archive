---
title: "Slow wireless network"
date: 2009-06-24
forum: Networking &amp; Wireless
---

### Post by Snuzzer on 2009-06-24
Hey.

My internet on Ubuntu 9.04 has become very slow and I belive it's after doing some updates. I've tried reinstalling the system but it's still the same.

I've got no speed problems when using other PCs using Windows XP or LAN connection.

Does anyone have any suggestions?

Thanks in advance.
Simon B. Støvring
Denmark

---

### Post by pedro_orange on 2009-06-24
By slow internet what do you mean?

Is it slow opening firefox / opening web pages?
Is it slow doing an update?
Is it slow running a torrent?

I've heard lots of stories about people disabling Firefox from checking for updates to itself/add ins and things seem to be faster.

---

### Post by Snuzzer on 2009-06-24
> **pedro_orange said:**
> By slow internet what do you mean?

Is it slow opening firefox / opening web pages?
Is it slow doing an update?
Is it slow running a torrent?

It's opening web pages.

EDIT: Fixed quote.

---

### Post by pedro_orange on 2009-06-24
Could be ipV6

Try:

```
ip a | grep inet6
```

If you get anything output related to inet6, then you probably have it enabled, so disable it.

```
sudo nano -w /etc/modprobe.d/blacklist
```

Add this to the end

```
blacklist ipv6
```

Reboot, and you should be okay.

---

### Post by Snuzzer on 2009-06-24
> **pedro_orange said:**
> Could be ipV6

Try:

```
ip a | grep inet6
```

If you get anything output related to inet6, then you probably have it enabled, so disable it.

```
sudo nano -w /etc/modprobe.d/blacklist
```

Add this to the end

```
blacklist ipv6
```

Reboot, and you should be okay.

It's the same with ipv6 blacklisted.

---

### Post by pedro_orange on 2009-06-24
Have you done any testing?

Have you tried other web browsers? Is it just Firefox or all browsers? 
Have you checked your network settings? Checked the router? 
Isolate the error!

---

### Post by Snuzzer on 2009-06-24
> **pedro_orange said:**
> Have you done any testing?

Have you tried other web browsers? Is it just Firefox or all browsers? 
Have you checked your network settings? Checked the router? 
Isolate the error!

I've tried the Epiphany browser in Ubuntu - that's the same. I've used my stationary PC running Windows XP with LAN connection, which works fine. I've tried a laptop PC running Windows XP using wireless network which works fine.
I've reinstall my Ubuntu laptop and tried Firefox again and it's still slow.

---

### Post by pedro_orange on 2009-06-24
Are you sure you've disabled ipv6? 

Open Firefox, and in the address bar try

```
about:config
```

Find IPv6. Set that to off, reboot firefox and try again.

Or you could try:

/proc/sys/net/ipv6/conf/../disable_ipv6 files? 
0 is false, 1 is true. (So set it to 1 - You'll need to be su to do this)

(.. is for the various subsequent folders related to the network interface you're using)

Have you tried using Opera? That's pretty nifty.

---

### Post by mr_raider on 2009-06-24
I can confirm this. every laptop I have running 9.04 has seen degraded performance in wi fi recently. This appeared after some updates last week. I used to get steady 54mbps connections and could stream video. Now I'm lucky to get 18mbps. This on a computer running a broadcom wifi, one running a ralink chipset, and one using realtek USB adapter.

Neither PC has issues in windows, which eliminates an issue with my router.

---

### Post by Snuzzer on 2009-06-26
> **mr_raider said:**
> I can confirm this. every laptop I have running 9.04 has seen degraded performance in wi fi recently. This appeared after some updates last week. I used to get steady 54mbps connections and could stream video. Now I'm lucky to get 18mbps. This on a computer running a broadcom wifi, one running a ralink chipset, and one using realtek USB adapter.

Neither PC has issues in windows, which eliminates an issue with my router.

So another Linux distribution could be an alternative? I'm kinda new to Linux and Ubuntu is the first one I've been using so I'm open for new.

---

### Post by Snuzzer on 2009-06-26
> **pedro_orange said:**
> Are you sure you've disabled ipv6? 

Open Firefox, and in the address bar try

```
about:config
```

Find IPv6. Set that to off, reboot firefox and try again.

I've tried that without any changes.

> **pedro_orange said:**
> /proc/sys/net/ipv6/conf/../disable_ipv6 files? 
0 is false, 1 is true. (So set it to 1 - You'll need to be su to do this)

(.. is for the various subsequent folders related to the network interface you're using)

I'm not sure how to do this to be honest.

> **pedro_orange said:**
> Have you tried using Opera? That's pretty nifty.

Well, FireFox or Opera - no matter what it should be working just fine. As mentioned before, I've tried Epiphany too.

---

### Post by mr_raider on 2009-06-26
Solved my problems as follows:

Boot Jaunty with the 2.6.28-11 kernel. Us WPA2 AES encryption. Set the router to b+G mode, no N.

I get stable 54mbps connections.

---

### Post by rnschmidt on 2009-06-27
mr_raider:

How did you boot Jaunty with the 2.6.28-11 kernel?


Thanks, 
Rob

---

### Post by mr_raider on 2009-06-27
On load screen, you can choose your kernel.

---

### Post by drudogg on 2009-06-28
so has anyone found an actual solution to the speed? i was running fine until i did updates, now my wireless is dog slow. updates are slow, internet is slow, would love to tell you about epiphany, but it said it was going to take like 8 hours to download and install it.... it is all slow. not really wanting to limit things (ie lose n on my router), i did blacklist the ipv6 and it did nothing to help. also i have the weather applet on my taskbar, and it won't update itself on its own. it will if i tell it to, but it is slow as well. it is not a firefox problem... this is an hp laptop with broadcom bcm4306. i got it working finally, and then it drops to a crawl after like 2 days.

edit: network traffic is fine, just internet. shows as 54g speed, and network resources seem to respond fine. internet ones don't.

---

### Post by rnschmidt on 2009-06-28
mr_raider:

Tried all of the suggestions and this still didn't work. 


Any other ideas for a solution?  Everything else works well with the exception of the wireless, which is quite annoying!

---

### Post by Mechmechie on 2009-06-29
Mine was slow but the default speed is 1M
Trying following this thread, it helped me sort mine out
wireless very slow since 9.04
[http://ubuntuforums.org/showthread.php?t=1160972](http://ubuntuforums.org/showthread.php?t=1160972)

---

### Post by mr_raider on 2009-06-29
> **rnschmidt said:**
> mr_raider:

Tried all of the suggestions and this still didn't work. 


Any other ideas for a solution?  Everything else works well with the exception of the wireless, which is quite annoying!

Yeah. Mine started flaking out after two days. Now I'm back on the 2.6.28-13 kernel. I'm using WEP security and MAC address filters, b+G mode (n disabled in router) and seem to be getting solid 54mbps connection and can stream video. We'll see how long it lasts. I have broadcom wifi module in my HP laptop.

Some people have had success using the jaunty backports module. SOme people claim better performance on the 2.6.29 kernel, but ATI drivers won't work with that kernel.

---

### Post by drudogg on 2009-07-02
okay, i tried the backports module, nada. i also tried the newer kernel, did not function, had to switch back to 2.6.28-13.

i found something opn here that worked for a session, but did not hold through a restart, even after making it permanent.


somebody has to know how to speed this back up, please help me.

---

### Post by iamyourdemize on 2009-07-05
> **drudogg said:**
> okay, i tried the backports module, nada. i also tried the newer kernel, did not function, had to switch back to 2.6.28-13.

i found something opn here that worked for a session, but did not hold through a restart, even after making it permanent.


somebody has to know how to speed this back up, please help me.

I am having the same problem. I have 3 other wireless devices that work fine but not my Ubuntu laptop. I can even boot my laptop to Vista and it works no problem. Anybody have a solution?

---

### Post by northd_tech on 2010-02-12
Has anyone found a fix for slow network connections with Broadcom's STA ("wl") driver?  I'm at work and our connection is really slow under Ubuntu 9.04.  Gnome's Network Manager was reporting 54 MB/sec and that quickly dropped to about 14 MB/sec.  Updates and web pages run really slow, but I can ping Columbia University (basically across the continent from me) at an average of 105 milliseconds- which doesn't seem all that slow.

I had read that wicd runs faster for some people, so I just installed that and restarted (which gets rid of the Gnome and KDE WiFi managers).

According to the CNET.com Bandwidth test, I'm currently at 619-640 kbps (down in the DSL range), and it had been 1.5 Mb/sec just a little while ago.

[http://reviews.cnet.com/internet-speed-test/](http://reviews.cnet.com/internet-speed-test/)

Our ISP was down most of the day yesterday, so it could be something on Qwest's end I suppose.

I am supposed to be using 802.11-N speeds here though (not sure on the ISP bandwidth, but it should be much faster than I've been seeing lately).

I've got a Broadcom 4321AG wireless under 64-bit Ubuntu 9.04 running a 2.6.28-18-generic kernel with very current updates. **lspci **reports the WiFi as:

03:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)

I'm going to switch over to Vi$ta and see how that is running today.

---

### Post by northd_tech on 2010-02-12
I got chased out the door at work (Fri. afternoon), but I'm now at home with a differnet ISP running the same Ubuntu 9.04/wicd 1.5.9 setup with absolutely NO changes made (other than rebooting the laptop).  Now I'm getting 1756 kbps (which still seems waaaay slow for a Comcast "high speed" cable modem- allegedly the fastest consumer ISP in my area).  

I just downloaded the newest NVIDIA graphics driver (22MB), and it got up to about 700 kb/sec and averaged about 450 kb/sec in my estimation, so that CNET online test looks reasonably accurate at least.

Time to check Vi$ta's connection speed I guess...:-?

---

### Post by northd_tech on 2010-02-14
> **northd_tech said:**
> 
Time to check Vi$ta's connection speed I guess...:-?

Vista is claiming 135 Mbps and that same 22 MB NVIDIA download only took about 5-6 seconds under Vista, so it is waaay faster wireless under Vista.

Of course, Vista **also has** all those virus, trojan, worm, spyware, rootkit, cookies, Micro$oft, NSA, etc. things "going for it" so...

:-# [censored]

---

### Post by linuxguiri on 2010-02-16
Had the same problem (slow browsing/page loading with Firefox in Ubuntu but fast in Vista). Several threads have suggested pointing DNS to OpenDNS servers. That had a small effect; however, switching to Google's public DNS servers made the biggest difference:
[http://code.google.com/speed/public-dns/docs/using.html](http://code.google.com/speed/public-dns/docs/using.html)

---

