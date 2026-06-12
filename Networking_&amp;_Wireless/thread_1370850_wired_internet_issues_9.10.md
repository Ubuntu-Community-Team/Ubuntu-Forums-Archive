---
title: "wired internet issues 9.10"
date: 2010-01-02
forum: Networking &amp; Wireless
---

### Post by rottenart on 2010-01-02
Hey all,

I'm trying to get my folks' internet issues sorted out. I just did a fresh install of 9.10 and a fresh update of firefox to 3.5

They've been having issues with the wired connection through a Belkin Wireless G router for some time. My son's macbook connects no problem through the wireless signal and he has fast speed, but the wired connection is really, really slow. When I swicth to a direct connection without the router, it's as fast as it should be.

I tried disabling IPv6 as per another thread, but that didn't seem to make a difference. It seems there might just be a configuration problem with the router. 

I'm not a novice, but certainly no expert either. Any ideas?

---

### Post by sgosnell on 2010-01-02
The easiest way to check it is to reset the router to factory defaults, by pressing and holding the reset button for ~30 seconds.  You'll have to reset everything afterwards, but it shouldn't be too painful.  The main things you'll need to change are the password and the wireless security settings.  It might be a faulty router, but it's impossible to diagnose without more information.  The default username and password for Belkin routers is freely available on the internet.

---

### Post by rottenart on 2010-01-02
I tried that numerous times and it hasn't worked yet. I have to keep plugging in directly to check the forums. I thought that by typing in the IP address into the browser window would allow me to look at the configuration of the router when it's plugged in, but that doesn't seem to work, either.

what additional information would you need? If the router were faulty, wouldn't that impede the wireless signal too?

---

### Post by rottenart on 2010-01-03
Ok, so, I have been working with this all day and I think I have some solutions and I also have some new questions.

First of all, I was able to get the original connections restored. I now have internet access through the router, with the same page-loading issues that I had before. I haven't been able to check it yet, but I assume the wireless has the speed it should have. The speakeasy.net speed test still shows the connection to be as fast as it should. I am seemingly back to square one.

After talking with a network-savvy friend of mine, I thought it might be an issue with Firefox. I noticed a lot of similar problems in the forums after upgrades to 3.5, or when they upgraded the OS to Karmic (both of which I have done). I tried some of the fixes that were mentioned in the Troubleshooting thread (i.e. the .pipelining changes). I also tried renaming the hidden .mozilla file, but it turns out that's not necessary and only served to delete all my bookmarks when restarting FF.

So, after much frustration, I decided to try Google Chrome. People on the forums seemed to be happy and it sounded like the loading/speed issue was not a problem. Hey, Mozilla's not infallible, so might as well try an alternative while I wait for a fix, right?

Unfortunately, the problem persists with Chrome. I get a really long "resolving host" before the page loads. It is almost the same problem to a tee.

All this leads me to some questions that might actually be suited to another forum:

Why the change between the router and modem? Shouldn't the router just be a gate for the data flow on the way to the box? 

Is there something I'm missing that *IS* FF related? There definitely seems to be issues involving 3.5 and load-times, so at least I'm not the only one.

If it's a FF issues, then why would Chrome be doing the same thing? Again, the speed tests all show a 25mbps connection, so it's SOMETHING on my end.

Would a switch solve the problem? It seems that if I have a problem with the router, I'd have similar troubles with the switch, and I would really rather pinpoint the problem and (hopefully) fix it w/out spending money.

Some of these are probably easy answers and some might require other info, but I'll provide whatever anyone needs...

---

### Post by sgosnell on 2010-01-04
That's a Karmic bug, and is resolved by disabling ipv6.  There are numerous threads here with detailed instructions for doing that.

---

### Post by pricetech on 2010-01-04
You may have a bad router.  I"ve encountered a couple of belkin devices and they were pretty junky.

Try another computer connected to the same wired connection and see how it responds.

If it seems to be taking forever to resolve IPs, then change the DNS entries in the router or use manual DNS entries on your computer.

---

### Post by adam814 on 2010-01-04
You could always use Google DNS or run your own DNS server (I like dnsmasq and it's in the repos).

---

### Post by Ubunt2u on 2010-01-05
> **adam814 said:**
> You could always use Google DNS or run your own DNS server (I like dnsmasq and it's in the repos).

Yes.  Seems either it's a faulty router or dns problem.  Try using opendns.com instead and see if it helps.  Put the addresses listed below into your router's configuration settings for DNS.

Addresses for opendns

208.67.222.222
208.67.220.220

---

### Post by rottenart on 2010-01-05
> **sgosnell said:**
> That's a Karmic bug, and is resolved by disabling ipv6.  There are numerous threads here with detailed instructions for doing that.

You nailed it. Right before I left, I disabled IPv6 and it seemed to clear the whole thing up.

Thanks for the help!

---

