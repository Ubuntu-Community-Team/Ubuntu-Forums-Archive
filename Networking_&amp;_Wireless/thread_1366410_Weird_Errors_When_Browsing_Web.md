---
title: "Weird Errors When Browsing Web"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by jdorenbush on 2009-12-28
I occasionally get very strange errors when browsing the Internet, and it only seems to happen on Ubuntu. This has happened through multiple versions and re-installs of Ubuntu. Errors happen both in Firefox and Google Chrome.

It usually happens when trying to browse my companies website, [www.mutineermagazine.com](www.mutineermagazine.com), but I believe it has happened on other sites I visit frequently, i.e. [www.gmail.com](www.gmail.com). When I receive the errors I have others test the sites, and the sites work fine for them, so it appears to be a problem only I am experiencing. Even stranger is that when I launch the site in question on a different computer on my network (a Windows XP machine) and then come back to my Ubuntu machine and refresh the site, it starts working again.

Some random errors I receive:

**Example Error 1**
> Server Error

404 - File or directory not found.

The resource you are looking for might have been removed, had its name changed, or is temporarily unavailable

**Example Error 2**
> 404 Error - SimpleCDN Mirror Bucket

**Example Error 3**
> Invalid URL

The requested URL "*(WEBSITE URL HERE)*", is invalid.
Reference #9.46b1160.1259175976.28ae33f*(THIS # CHANGES EACH TIME)*

**Example Error 4**
> 413 Request Entity Too Large 
marbles

**Other Errors**
- Sometimes websites will redirect me to Myspace.com or Google.com for no apparent reason.

- Sometimes jQuery plugins on my site will just stop working and then start again.

Any idea what might be causing this?

**Update:**
This is a new one, when trying to access PayPal.com
> This webpage is not available.

The webpage at [https://www.paypal.com/](https://www.paypal.com/) might be temporarily down or it may have moved permanently to a new web address.

---

### Post by Rhemat on 2010-01-25
I'm having the same problem, but it happened in openSuSE 11.2 for me as well, and on my laptop.  I think that the problem might lay with something else.  Could be a modem, router, Networking card, or even ISP problem.
Any suggestions are welcome.

---

### Post by seismicmike on 2010-03-16
I too am having this issue.... this couldn't possibly be the unthinkable could it? Linux is immune to malware, but this behavior reminds me so much of how really bad spyware and trojan attacks would act on Windows PC's..... don't tell me that's it!

Usually what I get is the "Invalid Url.... Reference #", but I also have problems using stumble upon. Sometimes I'll click it and it'll tell me that Stumble Upon's server is down and give me a blank page.

I've also had almost every other error listed here - including being directed to myspace - I NEVER use myspace. By and large, the one I have the highest percent of the time is the "Invalid URL" one, though.

Any and all help would be wonderful. Is it possible to have malware on routers/modems? Is there a way to check that? I'm on AT&T DSL and I have a 2Wire modem, but I also have a Linksys router, too.

---

### Post by Scruffynerf on 2010-03-21
I'm getting this as well.

It's not the ISP, or the router.

I dualboot - in windows, Firefox / Opera work as expected. In Linux, all of the errors in the OP are present.

Lucid Beta at the moment, Firefox from the base repos. Chromium however, seems to work ok.

I think that the fault lies with the Firefox or related (XUL-runner?) packages in the repo.

---

### Post by n0dix on 2010-04-04
A read that someone has the same thing on Arch Linux, but unfortunately not a solution yet.

---

### Post by trusktr on 2010-04-09
Yup, i have Arch Linux and i am having these wierd problems too with Google Chrome (Dev).

When i access gmail, first it says "This webpage is not available" with a long string below it.

Then hit refresh and it says the same thing with a short string.

On the third or fourth refresh, it'll actually work and gmail will load, although it will look horribly funny.

This is also happening with other google services.

Jdorenbush, try hitting refresh multiple times and see if it finally loads. What happens?

---

### Post by jdorenbush on 2010-04-14
> **trusktr said:**
> Yup, i have Arch Linux and i am having these wierd problems too with Google Chrome (Dev).

When i access gmail, first it says "This webpage is not available" with a long string below it.

Then hit refresh and it says the same thing with a short string.

On the third or fourth refresh, it'll actually work and gmail will load, although it will look horribly funny.

This is also happening with other google services.

Jdorenbush, try hitting refresh multiple times and see if it finally loads. What happens?

I tried refreshing a bunch, clearing all cache/cookies/history, restarting the browser. Nothing works. It seems like it just randomly decides to start working whenever it wants.

I get these errors in both Firefox and Chrome. Right now I am getting an error for a site saying "Reported Attack Page!" as if it is a bad page or something, which I know it isn't. I checked it in Chrome and it is working fine for the moment, not in firefox though. When I hit "Ignore this warning" it takes me to the site but it looks like styling is turned off, because there is no CSS.

Last week on Firefox/Chrome I was getting Google 404 errors for pages that weren't even Google's.

---

### Post by negativ on 2010-04-15
> **jdorenbush said:**
> I tried refreshing a bunch, clearing all cache/cookies/history, restarting the browser. Nothing works. It seems like it just randomly decides to start working whenever it wants.

I get these errors in both Firefox and Chrome. Right now I am getting an error for a site saying "Reported Attack Page!" as if it is a bad page or something, which I know it isn't. I checked it in Chrome and it is working fine for the moment, not in firefox though. When I hit "Ignore this warning" it takes me to the site but it looks like styling is turned off, because there is no CSS.

Last week on Firefox/Chrome I was getting Google 404 errors for pages that weren't even Google's.



I'm also on Arch, having exactly the same problems listed in this thread.  It always seems to happen on exactly the same couple of websites, too.  I can usually reproduce it (only on those websites) by hitting ESC while the page is loading, then F5 to refresh... and boom, Invalid URL, or Google 404 (have seen Yahoo 404, and I NEVER use Yahoo).  Once it happens in one browser, all other browsers are similarly affected.

I have no idea why this would matter, especially since no other machine on the network has this problem, but I'm behind a Linksys WRT160Nv3.  It seems like some DNS shenanigans or something.  Bleh.

---

### Post by jdorenbush on 2010-05-05
Bump... Still having problems with this. Very frustrating. It seems to happen randomly on both Firefox and Chrome, but not simultaneously. For example: If a page isn't working in Firefox, it'll usually be working fine in Chrome.

---

### Post by jdorenbush on 2010-06-04
Still trying to figure out what is causing this... Anyone have any ideas?

---

### Post by Devpaul on 2010-06-04
I'm having this problem as well.

It seems consistent, though.

for instance, one of my favorite tech websites [www.boygeniusreport.com](www.boygeniusreport.com) never comes up

---

### Post by lisati on 2010-06-04
It almost sounds like some DNS problem to me too.

The Paypal and BGR sites opened OK for me.

Random musing, which could turn out to be irrelevant: I wonder if the common factor is some kind of DNSBL blocking on the DNS lookup. Places to check include [http://blacklist.org](http://blacklist.org) and [http://debouncer.com](http://debouncer.com)

---

### Post by jrodimusprime on 2010-06-05
I had the same problem with new lynx install. It was an IPV6 issue - disable it.

[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)


Also clear cache and clear dns cache in FF afterwards.

---

### Post by jdorenbush on 2010-06-09
I disabled IPV6 in Ubuntu and Firefox and am still experiencing some problems with image loading. Now I'm just waiting on webpages to start displaying errors. :\ I'll keep you all posted.

---

### Post by trusktr on 2010-06-09
well, good news is Chrome is officially released for Linux now. Problem solved. :)

---

### Post by jdorenbush on 2010-06-09
> **trusktr said:**
> well, good news is Chrome is officially released for Linux now. Problem solved. :)

I think it is a router problem.

I stumbled upon this: [http://homecommunity.cisco.com/t5/Wireless-Routers/WRT310Nv2-Sporadically-pointing-domains-to-different-websites/td-p/285318](http://homecommunity.cisco.com/t5/Wireless-Routers/WRT310Nv2-Sporadically-pointing-domains-to-different-websites/td-p/285318)

---

### Post by trusktr on 2010-06-09
Well it's interesting to note that I was having this problem only in Google Chrome Beta and Dev. Now that Chrome has moved out of Beta, the problem has disappeared.

Are you experiencing this in other browsers?

---

### Post by jdorenbush on 2010-06-09
> **trusktr said:**
> Well it's interesting to note that I was having this problem only in Google Chrome Beta and Dev. Now that Chrome has moved out of Beta, the problem has disappeared.

Are you experiencing this in other browsers?

Yes, in Firefox and Chrome.

---

### Post by jrodimusprime on 2010-06-09
try this one

[https://addons.mozilla.org/en-US/firefox/addon/5914/](https://addons.mozilla.org/en-US/firefox/addon/5914/)

also, if your router has a DNS cache, clear it.

---

### Post by jrodimusprime on 2010-06-09
also, you can force your DNS server to your ISPs in your IP settings to bypass your router.

---

### Post by jdorenbush on 2010-06-09
I'm so frustrated right now because I put together this detailed post last night regarding this issue and how I thought I finally solved it. Then I go to click "Submit Reply" and ubuntuforums.org errors on me. #FAIL... I've been having off and on problems ever since.

1. I've disabled IPv6 in Ubuntu and Firefox.
2. I've installed and tried this: [https://addons.mozilla.org/en-US/firefox/addon/5914/](https://addons.mozilla.org/en-US/firefox/addon/5914/)
3. I'm using Google's public DNS.
4. I setup a static IP on my system.

After all that I thought for sure it was fixed, but apparently I was wrong.

FYI: I've never adjusted IP and DNS settings on Ubuntu before. Just in case I maybe did something wrong, here are the steps I took, so if anyone sees any mistakes please let me know:

[SIZE="1"]1. System > Preferences > Network Connections
2. Click "Edit"
3. Under the "IPv4 Settings" tab I changed the following information:
Method: Manual
Address: 192.168.1.1 
Netmask: 255.255.255.0
Gateway: 192.168.1.255
DNS Servers: 8.8.8.8, 8.8.4.4

To get my Address, Netmask and Gateway I used "ifconfig", which produced the following results:
inet addr:192.168.1.1
Bcast:192.168.1.255
Mask:255.255.255.0[/SIZE]

> **jrodimusprime said:**
> also, you can force your DNS server to your ISPs in your IP settings to bypass your router.

Can you elaborate on that? Not sure exactly what you mean. Thanks!

---

### Post by trusktr on 2010-06-10
Hmmm, what a wierd problem! I only had it in Chrome but it went away as soon as I upgraded to the new release.

I have firefox (namoroka) 3.6.3 with no problems.

Hope you get it fixed!

---

### Post by jrodimusprime on 2010-06-10
i think "sudo ip route flush table main" might clear up your routes if ipv6 screwed them up. you'll need to restart afterwards.

clearing your ff cache after each troubleshooting step will help.

---

### Post by jrodimusprime on 2010-06-10
if you entered the dns into the gui it might not have been the default gateway. you might want to try to add a default gateway in terminal. lots of how-tos on that.

---

### Post by jdorenbush on 2010-06-10
@jrodimusprime I am going to try and reconfig dns info via Terminal and see if that helps.

There is lots of discussion regarding this on the Linksys support forums.
[http://homecommunity.cisco.com/t5/Wireless-Routers/WRT310Nv2-Sporadically-pointing-domains-to-different-websites/td-p/285318](http://homecommunity.cisco.com/t5/Wireless-Routers/WRT310Nv2-Sporadically-pointing-domains-to-different-websites/td-p/285318)
[http://homecommunity.cisco.com/t5/Wireless-Routers/WRT160N-V3-has-serioius-DNS-issues/m-p/280327](http://homecommunity.cisco.com/t5/Wireless-Routers/WRT160N-V3-has-serioius-DNS-issues/m-p/280327)
[http://homecommunity.cisco.com/t5/Wireless-Routers/WRT320N-randomises-destination-IP-adress/m-p/315112](http://homecommunity.cisco.com/t5/Wireless-Routers/WRT320N-randomises-destination-IP-adress/m-p/315112)
[http://homecommunity.cisco.com/t5/Wireless-Routers/Wireless-Router-redirects-to-Google-es/m-p/196629](http://homecommunity.cisco.com/t5/Wireless-Routers/Wireless-Router-redirects-to-Google-es/m-p/196629)

I spoke to Linksys support yesterday and there was a firmware upgrade that was released in April 2010 that was supposedly going to fix this. He walked me through the exact step by step procedure for a successful firmware upgrade. Everything was working fine until about an hour ago when flickr.com started acting up. Just a few minutes ago my music suddenly stopped playing on Pandora.com and I hit refresh only to end up at the infamous "Invalid URL" page. Ubuntu Forums was giving me errors too.

---

### Post by jdorenbush on 2010-06-10
> **jrodimusprime said:**
> if you entered the dns into the gui it might not have been the default gateway. you might want to try to add a default gateway in terminal. lots of how-tos on that.

I followed these steps to setup static IP address:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Set_a_static_IP_address](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Set_a_static_IP_address)

I think everything is setup correctly now. What is the best way to confirm that you are using the correct addresses in each of the different fields, i.e. netmask, network, broadcast, etc.?

Also, what is the best way to check that my changes are actually in affect and ubuntu is using the static addresses?

---

### Post by jrodimusprime on 2010-06-10
it will also show you your dns and it's resolution.

```
jrod@jrod-desktop:~$ nslookup google.com
Server:        8.8.8.8
Address:    8.8.8.8#53

Non-authoritative answer:
Name:    google.com
Address: 66.102.11.104

```

---

### Post by jdorenbush on 2010-06-10
```
jeff@jeff-desktop:~$ nslookup google.com
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
Name:	google.com
Address: 74.125.127.106
Name:	google.com
Address: 74.125.127.103
Name:	google.com
Address: 74.125.127.105
Name:	google.com
Address: 74.125.127.104
Name:	google.com
Address: 74.125.127.99
Name:	google.com
Address: 74.125.127.147
```

Do you know why mine has so many as opposed to just one on yours?

---

### Post by jrodimusprime on 2010-06-12
did you add this line > "ipv6.disable=1" to the line containing "GRUB_CMDLINE_LINUX_DEFAULT=" in  /etc/default/grub

and of course reboot and clear cache.

---

### Post by jdorenbush on 2010-06-14
> **jrodimusprime said:**
> did you add this line 

and of course reboot and clear cache.

This is what my GRUB file looks like right now:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="ipv6.disable=1"
```

After setting up the static IP via [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Set_a_static_IP_address](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Set_a_static_IP_address) my Internet has been working perfectly -- until today.

I had problems connecting my desktop to Ubuntu One and connecting to my network printer. I think the issue had something to do with not being able to connect to "localhost". I couldn't seem to resolve the issue with my static IP settings, so I reinstalled Network Manager and used DHCP, which solved problems with local network. 

Then I tried setting up the static IP again. I noticed that the first time I set it up I removed two lines of code in /etc/network/interfaces. Maybe that was the problem with local network? So I left them in this time:
```
auto lo
iface lo inet loopback
```

Somehow that resolved issues with static IP and localhost, but deviantart.com just gave me the "Invalid URL" error. :(

**UPDATE:** Just checked my /etc/resolv.conf file, and NetworkManager somehow reset it. I changed this back to Google's Public DNS. It has my "gateway" address from etc/network/interfaces listed as a "nameserver" address though...Not sure why, is this needed? Below are my current settings:

_/etc/network/interfaces_
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.102
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

_/etc/resolv.conf_
```
# Google Public DNS
nameserver 192.168.1.1
nameserver 8.8.8.8
nameserver 8.8.4.4
```

---

### Post by jrodimusprime on 2010-06-15
network manager is probably putting your default dns in /etc/resolv.conf

you might in NetworkConnections->IPV4 Settings select Automatic (DHCP) addresses only and enter the two google DNS servers (unless you really need a manual static addr). reboot and your resolv.conf should only have the google domains and should be resolving properly.

an interesting one.

---

### Post by jdorenbush on 2010-06-17
I believe I've successfully setup my static IP/Google DNS config.

And I've been browsing error-free for a couple days now. I'll give it a week or so and if I've still had no errors I'll mark this as "solved".

=D>

---

### Post by jdorenbush on 2010-07-12
Using a static IP has solved this problem for me.

---

