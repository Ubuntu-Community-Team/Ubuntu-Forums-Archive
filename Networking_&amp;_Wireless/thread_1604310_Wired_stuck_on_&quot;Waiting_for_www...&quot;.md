---
title: "Wired stuck on &quot;Waiting for www...&quot;"
date: 2010-10-23
forum: Networking &amp; Wireless
---

### Post by yipyip123 on 2010-10-23
Hi,

I am on an Asus laptop. My wireless connection works fine. But when I connect to Auto etho, I only can open google or youtube, but nothing ever loads or anything. I can search terms on google, which gives results, but I can't open any web pages.

My wired connection worked until I opened my windows partition. Then it started to work again after an update. then I went into windows again and the wired connection stopped working again. But now it hasn't worked for a couple weeks. Help?

Also, can someone explain or provide a noob-friendly link on how to install/get the statistical program "R"?

---

### Post by relay_man on 2010-10-24
I'm not positive, but it appears the package "R" you are looking for is available in the repositories.

If you will use the synaptic package manager, the correct package and any dependencies should be installed automatically.

To get to the package manager:

System>Administration>Synaptic Package Manger

enter your password at the prompt.

When the package manager window opens, there will be a small search box in the center at the top.  If you will enter "r-base" (no quotes) I think the package you are interested will be listed.

Click the check box next to the r-base package and choose "mark for installation".  At top of the window in the toolbar, choose "Apply"


Now, with your cable connected to your laptop and the eth0 connection chosen as the active connection in network manager,
open terminal and at the command line enter "ifconfig".(no quotes)
Post the results and I'll try to help with the wired network connection problem.

---

### Post by yipyip123 on 2010-10-24
Ok, I clicked "Apply" for r-base, but I still don't see anything like a program anywhere.

```

eth0      Link encap:Ethernet  HWaddr 00:24:8c:75:e0:ee  
          inet addr:172.30.163.234  Bcast:172.30.167.255  Mask:255.255.248.0
          inet6 addr: fe80::224:8cff:fe75:e0ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17521 errors:558 dropped:0 overruns:0 frame:558
          TX packets:3271 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4030879 (4.0 MB)  TX bytes:665436 (665.4 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8163 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:888691 (888.6 KB)  TX bytes:888691 (888.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:85:ad:03  
          inet6 addr: fe80::222:43ff:fe85:ad03/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3412536 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1138363 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2086582733 (2.0 GB)  TX bytes:185613581 (185.6 MB)

```

---

### Post by wojox on 2010-10-24
When you open Network Connections click on eth0 and Edit and see if it's set to connect automatically.

---

### Post by yipyip123 on 2010-10-24
Yes, auto eth0 is set to connect automatically.

---

### Post by relay_man on 2010-10-25
It looks like getting the entire "R" package is best done from the command line.  If you will open terminal and type:

sudo apt-get install littler

there will be quite a listing of packages.

I have not used "R". You may have to  search a little to find out how it works.

As for your wired connection, your ip address and mask looked curious to me, but I checked and it should work o.k.

Did you set this network up or is it a business/school administered by others?

You said you can see and use Google.  To make sure you aren't seeing cached pages, open your browser and choose

 tools>clear recent history>clear now

make sure at the top you've chosen "everything" and that all of the boxes are checked.

Close your browser and then restart it.

Let us know if google and youtube still work.

---

### Post by yipyip123 on 2010-10-25
ok, the terminal result ends in 
"Processing triggers for man-db ...
Setting up littler (0.1.3-1) ...
"

Is that right? I still don't see anything..

I'm on my school's network

I cleared everything except for "site preferences" and can still see  Google and search terms, while on auto eth0, but websites such as  facebook and youtube videos will not load. It just gets stuck at  "Waiting for..." or "Looking up..."

---

### Post by wojox on 2010-10-26
Open Firefox and type

```
about:config
```

Search for ipv6 and click it to true value.

---

### Post by yipyip123 on 2010-10-26
I clicked it to true, connected to auto eth0, closed/opened browser. It still doesn't work :(

---

### Post by wojox on 2010-10-26
Are you the only one with this problem at your school?

Does everything work in Windows?

---

### Post by relay_man on 2010-10-26
Sounds like "R" is installed.  The apt system is excellent.
I've not used R.  It may run only from the command line.
If you can search using google, it would be good idea to do so.
I see that you are using the school network.  That would explain 
the 2000+ hosts available...

Have you tried any other websites besides youtube and facebook?

---

### Post by yipyip123 on 2010-10-27
I haven't met anyone else with this problem. I don't know why I'm having this problem. It was working fine earlier, until I went into windows and then it stopped.

I've been trying to avoid using windows because 
1) it seems that it makes auto eth0 not work
2) the windows partition seems to take 10 times longer to boot up now that ubuntu is installed, even though the ubuntu partition is only 40 gigs

I dunno. All of my friends seem to have such ease with dual booting.

No websites load when I am connected to auto eth0. However, a small level of connection must be available for me to search on google. It brings up search results, but I cannot load any websites.

I just have no idea what's going on anymore. I still don't know how to access R

---

### Post by EMulligan on 2010-10-28
Waiting for wwww.. sounds like a possible address resolution problem. Have you checked your DNS settings?  Resolv.conf.  Are you using network manager?  It generates resolv.conf each time you start up a connection.  In network manager you specify each wireless connection you use including DNS settings. Auto eth0 is specified only once and you may need to specify it differently between home and school/work.  You could check to see is resolv.conf different when you are on the wire and on the wireless.

---

### Post by yipyip123 on 2010-10-29
I went onto the windows partition. The wired connection works on the windows partition. I got an error telling me to run Chkdsk. I did windows startup repair at boot-up using a CD. Wired connection still does not work in Ubuntu (lucid lynx)

:frown:

---

### Post by yipyip123 on 2010-11-16
Damnit, it (wired connection) started working again. then I had to go into Windows to print something because printing scanned PDF's apparently doesn't work with ubuntu...

and then now I'm back in ubuntu. and it stopped working. does anyone have ANY idea why this is happening or how to fix it? I don't want to have to rely on wireless connections when I have to do my college finals.

PLEASE HELP

---

### Post by RJARRRPCGP on 2010-11-16
"Waiting for x..." AFAIK is a script not responding.

Or the browser received all the data, but still thinks it's not ready, even when the scripts are fine. 
Just like if you keep getting the dreaded spinning mouse pointer. Seems to indicate a browser engine hang.

---

### Post by red91sit on 2010-12-25
Hi,

I was wondering if a solution was ever found for this?  I am having the exact same problem on my Toshiba Satellite, L35.  The only difference is it's my wireless that doesn't work, wired works fine.  I have tried; 


[LIST=1]
[*]1.Various browsers, chromium, chrome, firefox, all with same results,
[*]Adjusted MTU using pinging, this seemed to help a little, but then I'd have to lower the MTU again,  Initially 1475 worked for a short period of time, then I had to drop it down to below 1440 for the internet to work again, but after a short while, this stopped working as well.
[*]I adjusted pipelining settings as other threads have suggested,
[*]Used DSN server, and adjusted several settings for this
[*]Disabled IPV6 in the browser,
[*]Disabled IPV6 on the whole computer
[*]Tried a different version of Ubuntu (10.10 and Mint 9)
[/LIST]
It seems like if some sites work, that it shouldn't be that much more difficult to get them all working?

---

