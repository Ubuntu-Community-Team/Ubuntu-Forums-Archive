---
title: "Updated to 9.10 and wireless is working but not internet"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by Laminebean on 2009-10-30
Dear fellow Ubuntites,

I recently upgraded to 9.10 and I am having some strange problems with my internet connection:

1. I am connected to my wireless but can only access internet via Empathy and similar application (Skype, Dropbox).

2. Firefox and other web browsers do not seem to connect at all.

3. I also have Mandriva on dual boot, and now that is experiencing the same issues.

4. I can access the internet on Windows XP via Virtualbox

5. Update manager cannot connect unless I first rechoose my server from software sources.


From reading about similar problems from others, I think its probably a DNS issue, but I dont really know too much about that. If anyone can help me with this most bizarre problem it would be most highly appreciated...it is now driving me nuts.

---

### Post by dasris on 2009-10-30
I believe that I have the same problem (Empathy works, Firefox does not).  

Some more data from my case: 

- Clean install of netbook remix (ubuntu karmic) on a eeePC 1005HA. 
Dual boot with the originally installed Windows XP Home.  
Nothing modified at all, I just entered the WPA key.   

- On Windows: WiFi works perfect. 
- On Ubuntu, wired works perfect. 

- On Ubuntu & WiFi: Empathy works (chat), ping works well including name resolution (DNS). Firefox will not access internet. Software update will not work. 

I could read a page from internet through WiFi ocasionally. When disconnecting the network cable, ubuntu switches over to WiFi, being very close to the antenna of the presence point, I could read a page (a new page, I am sure it was not from cache). Then no more access possible. This worked 2 times only, most of the attempts to repeat it did not work at all.  

Running system update (on wired) did not affect this problem.

---

### Post by Laminebean on 2009-10-30
Well, at least im not the only one. I havent tried a wired connection yet, because I dont have one (my wireless is shared between 2 other flats in our building).

I also made the mistake of doing a clean install afterwards, so now I dont even have Skype or Virtualbox...just empathy.

---

### Post by Laminebean on 2009-10-30
Ok, so I disabled the IP6V settings on Firefox and now Firefox can access the internet no problem...Thank god!

I still have problems with other applications and in particular the update manager and software manager...so still needs work.

Any ideas?

---

### Post by dietsche on 2009-10-30
I have the exact same problem - wireless worked before I upgraded to 9.10. It also works in windows.

I did a fresh install of 9.10 (x64) and still have the problem. It looks like everything gets stuck doing DNS lookups. I have 802.11n deployed if that makes any difference...

If I plug my computer directly in to the router with cat5, the internet works just fine. When I switch back to the wifi, things stop working again.

I also have windows 7 on this laptop, and wifi works just fine there.

In any case, this is very uncool :( Windows 7 doesn't recognise my sound card, and ubuntu doesn't work with my wifi! I'd prefer to use ubuntu, but I'm pretty much stuck in win 7 for now. Makes wireless hulu sessions impossible :(

Incidentally, I tried disabling ipv6 in firefox by toggling the "network.dns.disableIPv6" setting in about:config to true, but it didn't seem to help. Is there more than one setting to set?

---

### Post by samtihen on 2009-10-30
Hi, I think I'm having the same issue.

I just did a clean install of Ubuntu 9.10 from my previous 9.04 install which was working.

I can connect wirelessly to my router (Netgear WGR614) without a problem, using WEP. I have an Intel 802.11 pre-n card on a Thinkpad T61.

However, once I try to connect to a website using Firefox I time out. I also time out when I try to use apt-get. I didn't test Empathy, but I have a feeling it might work (just because everyone else says it did).

I checked to see if I could ping anything, and I am able to ping pretty much anything with no issues (google.com works, etc) If I take the IP address from those successful pings, I can connect to the sites.

So, I know I am connected to the internet. I know DNS resolution works for ping. I also know Firefox can connect via IP address. So, based on that, I assume Firefox/apt-get/other utilities use some sort of library/wrapper for DNS resolution that has a configuration issue of some sort. I could be wrong, but that's what it feels like to me.

Thoughts/Suggestions?

---

### Post by spotrick on 2009-10-30
Me too! (Thank ceiling cat I'm not alone!)

Running Dell XPS M1330. I upgraded yesterday at work on a wired lan, no problems. Last night tried at home on WiFi and got this problem. It's a little weird because when I start Firefox, I get as far as Facebook home loading, with a few broken images, but latest wall posts. Then any further attempts to connect anywhere fail.

Also fails if I connect through cable to our wireless router, so maybe this is not simply a wireless issue? ADSL? Router is a D-Link DSL604-T.

I've had an issue with VPN access since 8.10, which feels similar -- you get a connection, but get dropped after 30 seconds or so. Never did resolve that one.

Hope this resolves soon, 'cause I'm currently using Vista :/

---

### Post by samtihen on 2009-10-30
Well, after a bit more research, it looks like the problem is more related to my router's ipv6 compatibility than anything else.

I have a partial fix for people who have this problem, but it needs a better solution.

First, disable your networking. To do this, right click on your Network Manager icon in the notification area, and un-tick the "Enable Networking" box. You will be disconnected from all networks.

Now, open up a terminal and run the following: 

```

sudo su
echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6

```

Additionally, (this may not be needed for everyone), go to the address "about:config" in Firefox and edit the following value:

```

network.dns.disableIPv6 = true

```

Now, re-enable networking by right clicking on the same icon and re-ticking the box you un-ticked earlier.

Now, the problem I am currently having is that /proc/sys/net/ipv6/conf/all/disable_ipv6 keeps resetting itself to 0 whenever I restart my computer, so I suspect there is a better solution.

---

### Post by samtihen on 2009-10-30
Actually, scratch all that. I think the only part of the solution I posted that works is the "about:config" change in Firefox, and that only works for Firefox.

So, at the moment, Firefox works, ping works, Empathy works (probably always did).

apt-get, synaptic, update manager, etc do not work.

---

### Post by spotrick on 2009-10-31
Can confirm the Firefox fix works. (Otherwise, I wouldn't be here. :)

I also edited my Wireless connection, changing IPvv4 settings to DHCP addresses only, and adding the IP for my ISP's nameserver. (Previously, the nameserver addr. was 10.1.1.1, my wireless router.) This fixed the network problem in Thunderbird too. 

No idea why. I was just following hints from another thread.

---

### Post by dasris on 2009-10-31
I reproduced the results of samithen: disabling the parameter in about:config makes Firefox work. 
Update manager still does not work.    

Then I did what spotrick says, only that I used the OpenDNS ip address. This made Update manager work on WiFi, so I run it and I saw an update for Firefox.   
I installed this update of Firefox.  

After the update, I start Firefox again and I reverted the change in the Firefox parameter, now it says: 
 network.dns.disableIPv6 default boolean false 
 and Firefox is working well

---

### Post by dietsche on 2009-11-01
I finally got mine working... I'm not sure that IPv6 was the root problem in my case. Disabling IPV6 in firefox didn't help me.

I edited my network configuration for my access point and set it to "Automatic (DHCP) Addresses Only" Then I manually put in my DNS servers (10.0.1.1, 10.0.0.2) My settings here are unique to my situation.... 10.0.0.2 is a border router with dns and 10.0.1.1 is the access point which also happens to be providing dns.

I also set my search domain becuase I happen to care about that... I think most people won't need to do that. Also, I set the DHCP Client ID to "Vader" which is what I like to call my laptop :)

With all of that setup, things are working. I wonder if anyone's submitted a ticket to ubuntu? This is a pretty unacceptable situation. Both the previous version of ubuntu and windows 7 work fine with my setup using fully automatic dhcp configuration.

---

### Post by akilenc on 2009-11-09
Hi I have the same problem

Manage to fix my firefox with about:config. but rest of them is not working.

Please some one help me

---

### Post by deanec65 on 2009-11-09
wired connection here but no websites here. any help?

---

