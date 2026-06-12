---
title: "Slow DNS Lookup?"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by moore.bryan on 2010-10-13
On a fresh install of 10.10, I'm seeing ridiculously slow DNS lookups; can anyone else confirm the same on their systems?

---

### Post by kreggz on 2010-10-13
Try this in a terminal window:

cat /etc/resolv.conf

then ping the IP address displayed and see how much latency you get.

There may be an issue with the network connection itself. What makes you think it is just DNS lookups?

---

### Post by moore.bryan on 2010-10-14
I mainly think it's DNS because when I ran the [namebench]("http://code.google.com/p/namebench/") utility, the default servers assigned were unfathomably slow; however, after changing the DNS servers to those suggested by namebench, I'm still getting intermittent "blockages," for lack of a better term. Basically, I'll be surfing and, randomly, Chromium will tell me it is "Sending request..." and then just hangs for a while. If I wait a bit, I can reload the page and everything's fine. I can also reset my network connection and that cures it for a little while. The same is true of either Firefox or Opera. None of these issues existed on my Lucid install nor did they exist in my Maverick beta install.

Any other ideas?

---

### Post by kreggz on 2010-10-14
You could try:
Chrome Stable or Firefox
disabling ipv6

also - I am using 10.10 and DNS lookups are excellent

---

### Post by moore.bryan on 2010-10-15
Tried both; in fact, I've tried three versions of Chrome/Chromium, two Operas, and three Firefoxes. IPv6 is disabled both at the kernel, the network-manager, and browser levels.

I'm beginning to think this may be related to the ath9k module shipped with 10.10... there's some chatter on Launchpad about a possible bug.

---

### Post by SeijiSensei on 2010-10-15
Try using 4.4.4.4 and 8.8.8.8 as your nameservers in /etc/resolv.conf.  (These are Google's public nameservers.)  Does that help?

---

### Post by kreggz on 2010-10-15
I have noticed alot of people talking about slow dns lookups on these forums in regards to 10.10

A bug report would be a good idea, sounds like you have done everything you can.

---

### Post by mbott on 2010-10-15
> **SeijiSensei said:**
> Try using 4.4.4.4 and 8.8.8.8 as your nameservers in /etc/resolv.conf.  (These are Google's public nameservers.)  Does that help?

This appears to have fixed my issue with 10.10.  :)

-- 
Mike

---

### Post by PC_load_letter on 2010-10-19
I have been experiencing this problem on my wired connection for a couple of months now. It was driving me insane! So, I followed the instructions here:
[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

and changed to OpenDNS, don't have any problems now. I'm running Karmic 64bit. The Google public DNS option is also great.

---

### Post by moore.bryan on 2010-10-19
> **SeijiSensei said:**
> Try using 4.4.4.4 and 8.8.8.8 as your nameservers in /etc/resolv.conf.  (These are Google's public nameservers.)  Does that help?
These are my defaults, to no avail. Like I posted, running the namebench utility found three DNS servers faster than Google's. I read a couple of Google blog posts about them having some slow response times.

> **kreggz said:**
> I have noticed alot of people talking about slow dns lookups on these forums in regards to 10.10

A bug report would be a good idea, sounds like you have done everything you can.
There's already a bug open about the possible kernel issue: [https://bugs.launchpad.net/linux/+bug/518818]("https://bugs.launchpad.net/linux/+bug/518818").

> **PC_load_letter said:**
> I have been experiencing this problem on my wired connection for a couple of months now. It was driving me insane! So, I followed the instructions here:
[https://store.opendns.com/setup/device/ubuntu/](https://store.opendns.com/setup/device/ubuntu/)

and changed to OpenDNS, don't have any problems now. I'm running Karmic 64bit. The Google public DNS option is also great.
No dice here.

---

### Post by Perseverance on 2010-10-24
Had the same problem gere.

I was not able to use OpenDNS because my connection is limited to one particular IP only , so the option of leaving to authomatic fails.

I disabled all my IPv6 settings and for my DNS i set the first hit for my ip from [http://www.dnsserverlist.org/](http://www.dnsserverlist.org/) .Everything is fine now. Maybe you should try this too.

---

### Post by moore.bryan on 2010-10-24
It's so strange... using either namebench or dnsserverlist.org, I continually get different suggestions. I expect *some* variance, but this is a little crazy.

---

### Post by Perseverance on 2010-10-25
Getting different best DNS Servers makes me thing you might have issue with your IP Address because they use it to calculate the DNS. Is it possible that this is issue with your provider and the way your IP is obtained when you are in the global network? Maybe every connection you do is made from different IP address and that is why your DNS works perfect now and fails after short period. It is just my opinion.

---

### Post by moore.bryan on 2010-10-25
> **Perseverance said:**
> Getting different best DNS Servers makes me thing you might have issue with your IP Address because they use it to calculate the DNS. Is it possible that this is issue with your provider and the way your IP is obtained when you are in the global network? Maybe every connection you do is made from different IP address and that is why your DNS works perfect now and fails after short period. It is just my opinion.
Hmm... interesting thought. I double-checked and found Verizon hadn't change my global IP in some time, so I don't think that's the issue.

I've come to believe this is more a driver (ath9k) issue than a DNS one. I think we can now consider this thread irrelevant/dead. I'm leery to mark it "Solved," because it isn't, but hope a mod can come along and kill it.

---

### Post by cardy_c on 2010-10-29
I am lumbered with a similar problem though I am running a windows 2003 domain where the Windows machines are all perfect, but when I dual boot into any of them into 10.10, 10.4 or MAC OSX 86  the DNS is really slow. 

They are pulling DHCP from the 2003 Domain Controller which assigns itself  as the primary DNS server and my ISP DNS servers as the secondary etc.

I have not been able to determine why the DNS lookup is so slow on the non windows PCs and yet perfect on the Windows machines. (XP or 7 or 2003)

If I manually populate them with my ISPs DNS they are all  lightening fast but then I cannot browse to my Windows servers!!!

I wish I could find a fix for this -  (The IPV6 is off on them all)

-----------------------------------------------------------------------------------------------------------------------------------------------------

OK I just spent another evening working on this and I have it resolved AT LAST!!!

What I did was - in my Domain Controller / DNS server I removed my ISP DNS servers from the Forwarders and added the OpenDNS servers addresses** ([B]208.67.222.222 & ****208.67.220.220**)[/B]

Then in the DHCP Server Options I made my Domain Controller the first DNS server and added the OpenDNS addresses as 2 and 3. This has made all my Linux and Mac OSX machines every bit as fast resolving now as my Windows machines - I cannot understand why but the results are incredible.

By the way - turning IPV6 back on now seems to have no effect on any of the operating systems DNS performance.

Hope this helps someone.

---

### Post by SkepticalHippo on 2010-11-19
Hi, I have another possible fix for this...

I just updated 10.10 and noticed that both firefox and chrome were taking a long time to resolve URLs. I tried disabling ipv6 and changing DNS servers but to no avail. Then I found this old thread:

[http://www.chromeboard.com/showthread.php?p=130628](http://www.chromeboard.com/showthread.php?p=130628)

and followed the advice to edit /etc/nsswitch.conf changing the "hosts" line order by putting files and dns first and leaving the rest. Mine now looks like this:

hosts: files dns wins mdns4_minimal [NOTFOUND=return] mdns4

All browsers are now working fine :D

Hope that helps anyone else having this problem. Now I just need to fix Compiz... ;)

---

### Post by moore.bryan on 2010-11-19
Hmm... I *totally* forgot about this old "fix." I'm building compat-wireless from source nowadays for the bleeding-edge ath9k driver, but giving this a shot can't hurt.

Thanks, SkepticalHippo!

---

### Post by ImpressMe on 2010-11-29
I have the same problem, hopelessly slow dns resolving, which is blazing fast on Windows, so its a Ubuntu problem.

---

### Post by moore.bryan on 2010-12-01
Unfortunately, I would agree this is not solved. Bleeding-edge ath9k makes things *better*, but does not provide a permanent solution. I now believe it has something to do with Atheros AR9285 chipset.

---

### Post by bockman on 2010-12-07
Is anyone having this problem with an Intel ethernet card? I have this problem on an HP Pavilion dv1000, and none of the solutions in this thread work. Google public DNS, no IPv6, changing /etc/nsswitch.conf, all did nothing.

Just to show everyone how serious this "slowness" is, here is me and wget trying to test it on google.com:

```
user@host:~$ wget --dns-timeout=4 http://www.google.com
--2010-12-07 20:18:31--  http://www.google.com/
Resolving www.google.com... failed: Connection timed out.
wget: unable to resolve host address `www.google.com'
user@host:~$ wget --dns-timeout=5 http://www.google.com
--2010-12-07 20:18:38--  http://www.google.com/
Resolving www.google.com... failed: Connection timed out.
wget: unable to resolve host address `www.google.com'
user@host:~$ wget --dns-timeout=10 http://www.google.com
--2010-12-07 20:18:46--  http://www.google.com/
Resolving www.google.com... failed: Connection timed out.
user@host:~$ wget --dns-timeout=14 http://www.google.com
--2010-12-07 20:18:46--  http://www.google.com/
Resolving www.google.com... failed: Connection timed out.
user@host:~$ wget --dns-timeout=15 http://www.google.com
--2010-12-07 20:19:16--  http://www.google.com/
Resolving www.google.com... 72.14.204.99, 72.14.204.147, 72.14.204.104, ...
Connecting to www.google.com|72.14.204.99|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                   ] 8,769       --.-K/s   in 0.05s   

2010-12-07 20:19:26 (164 KB/s) - `index.html' saved [8769]

```

15 seconds! And this happens every single time on Firefox as well. And yes, each call to wget did take as long as --dns-timeout specified. Let's test it with dig, just in case.

```
user@host:~$ dig yahoo.com

; <<>> DiG 9.7.1-P2 <<>> yahoo.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 33795
;; flags: qr rd ra; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 0

SNIP!

;; Query time: 47 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Tue Dec  7 20:22:22 2010
;; MSG SIZE  rcvd: 107
```

What? 47 ms? This is a lot less. And no, this isn't a case of domain caching, it works for every single domain I've tried. Wget/firefox/ssh all take a very long time to resolve, but dig can do it no problem, very quickly.

Any ideas?

---

### Post by utilitarian on 2010-12-07
Also still having the problem tried open-dns,google dns, and changing order of nsswitch.conf. I eventually get a name resolved but it is incredibly slow. I am typing this on a 9.10 netbook and it seems to work fine with the same dns servers that my other machine is failing on. My bad machine is a thinkpad r-61 laptop.

---

### Post by moore.bryan on 2010-12-08
@bockman, @utilitarian: have you tried compiling the bleeding-edge compat-wireless package and seeing those results?

---

### Post by utilitarian on 2010-12-08
I do not know how to get the driver. Can you give me instructions? Also would a driver change really be the cause of a like 20 second dns look up time?

Anyway thanks for your help

---

### Post by moore.bryan on 2010-12-09
> **utilitarian said:**
> I do not know how to get the driver. Can you give me instructions? Also would a driver change really be the cause of a like 20 second dns look up time?

Anyway thanks for your help
Changing my driver decreased both my drop problems and look-up times; I can only anecdotally say that, though.

If you head-over to the LinuxWireless page for [compat-wireless]("http://linuxwireless.org/en/users/Download"), you can find the directions.

Basically, you're going to download the tarball, extract it, build your driver, make & sudo make install it, and enjoy. The build process is "neat" because it's set-up where you can revert back to your vanilla driver simply.

---

### Post by utilitarian on 2010-12-10
Tried it following the Ubuntu instructions on that page. Still no luck. Might just reinstall

---

### Post by utilitarian on 2010-12-11
Did a complete reinstall. Still same problem. Then I tried the compat-wireless again. This time manually not using the ubuntu packages. Not sure if its any different this way but. I got compile errors.

fatal error: net/bluetooth/mgt.h: No such file or directory

Then I tried changing the dns servers again. Also no luck.

Thinking about reverting to an earlier ubuntu release. Is there anything else I can try or info I can give to help trouble shoot this.

---

### Post by cariocap on 2010-12-11
for slow DNS read:

[http://ubuntuforums.org/showthread.php?t=1533796](http://ubuntuforums.org/showthread.php?t=1533796)

---

### Post by crucialhoax on 2010-12-11
Im using the ath9k wireless module and have very fast dns queries. I am using OpenDNS name servers:

208.67.222.222 208.67.220.220

Hope this helps :)

Also, might want to check the `rate` of your wireless card during those times(right click the signal icon and choose connection information then look for the word `Speed:`, if it is anything but 54mb then youll want to make a script for that network interface so when it comes `up` it sets the rate. My script sets the rate to 54mb at interface `up` and I h  never had a problem since. Lmk if you want the script lol :D

---

### Post by utilitarian on 2010-12-11
Thanks for the responses. Everything seems to work fine when I am plugged in to ethernet to the same router I am using for wireless. Not sure if this is useful but the connecting time seems very non-uniform between sites.  Somethimes sites will connect instantly other times they will time out. Even within sites it seems highly non uniform. Like I can connect to yahoo very fast. But l.yimg.com is very slow.

@crucialhoax
I am for sure using opendns because their welcome page says I am. Not sure what wireless module I am using. The connection information is the following.

driver:iwl3945
speed: seems to fluctuate based on if I am trying to load a page from 54 to 1 Mb/s
IP: 192.168.101
Primary DNS: 208.67.222.222

@cariocap
changed the nsswitch file and the dhclient file but no luck either before or after restart

---

### Post by uncaspi on 2010-12-11
Hi.
I don't know if this helps, but I saw a thread yesterday that there is a problem with the driver iwl3945. The thread said the driver is old and will not be implementet in the newer versions of ubuntu. In the thread he had no wireless at all until he removed the folder
/etc/modprobe.d/iwl3945
The system then found a new driver.
Anyway make a backup before you remove it.

The thread is [http://ubuntuforums.org/showthread.php?t=1640742](http://ubuntuforums.org/showthread.php?t=1640742)

---

### Post by utilitarian on 2010-12-11
ok so the connection information I get from right clicking on the network information icon on the top right of my desktop says I have iwl3945 as my driver. But in etc/modprobe.d there is no iwl3945 folder or anyother folder for that matter. There are a whole bunch of black list files and a intel-5300-iwlagn-disable11n.cong file and alsa-base.conf file.

Sorry for not pasting in the actual output. To much of a pain to use the broken computer to reach the forums.

---

### Post by utilitarian on 2010-12-11
Maybe the reason its not there is trying to install the compat-wireless thing from earlier in the thread. But that seemed to fail out and not complete

---

### Post by uncaspi on 2010-12-11
You could try to run modinfo iwl3945 and find out which depentencies
it use and blacklist them together with the driver and then reboot.

---

### Post by utilitarian on 2010-12-12
Here is the output of modinfo. Not sure how to blacklist things. Can you give me more detailed instructions?


filename:       /lib/modules/2.6.35-23-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     1CB3CFE4565C9577EFA451C
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlcore,cfg80211,mac80211
vermagic:       2.6.35-23-generic SMP mod_unload modversions 686 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software])
 (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           fw_restart3945:restart firmware in case of error (int)

---

### Post by utilitarian on 2010-12-12
ok so in /etc/modprobe.d/blacklist.conf I first added iwl3945. When a rebooted my wireless was gone completely. The network indicator icon thing just lost its wireless options. 

Then I tried just adding the dependencies from modprobe.(iwlcore,cfg80211,mac80211). After reboot I still had wireless the problem stays the same.

Not sure if this is what you wanted me to try.

---

### Post by uncaspi on 2010-12-12
Yes that was what I suggested. You should blacklist iwl3945 and the depends, and reboot. According to the thread I found Ubuntu should now find a new driver. But if it doesn't work at least you've tried it.

---

### Post by crucialhoax on 2010-12-12
> **utilitarian said:**
> Thanks for the responses. Everything seems to work fine when I am plugged in to ethernet to the same router I am using for wireless. Not sure if this is useful but the connecting time seems very non-uniform between sites.  Somethimes sites will connect instantly other times they will time out. Even within sites it seems highly non uniform. Like I can connect to yahoo very fast. But l.yimg.com is very slow.

@crucialhoax
I am for sure using opendns because their welcome page says I am. Not sure what wireless module I am using. The connection information is the following.

driver:iwl3945
speed: seems to fluctuate based on if I am trying to load a page from 54 to 1 Mb/s
IP: 192.168.101
Primary DNS: 208.67.222.222


@cariocap
changed the nsswitch file and the dhclient file but no luck either before or after restart

Try this, make a file in your home folder or where ever you can easily access it. Name it `iwl-set-rate`

copy and paste this into the document using your favorite editor

```

#!/bin/bash
# This script sets the rate of the wlan0 interface before it comes up so it does not fluctuate

if [ "$IFACE" = "wlan0" ]; then
    for direc in /etc/network/if-pre-up.d
    do
        iwconfig wlan0 rate 54M
        # Sets the rate before interface is brought up
    done
    
    for direc in /etc/network/if-up.d
    do
        iwconfig wlan0 rate 54M
        # Sets rate once interface is up
    done
fi

```

Make sure that `wlan0` is your interface, if it differs, just change the script. Save the file and then do a 
```
chmod +x `file path here/iwl-set-rate`
```
 then do a: 
```

sudo chown root iwl-set-rate

```

then 
```

sudo mv `path/to/iwl-set-rate /etc/network/if-up.d

```

Hope this helps!

---

### Post by utilitarian on 2010-12-12
@crucialhoax seemed to work in the sense that my connection information always says 54Mb/s. But dns is just a slow as before.

@uncaspi ya I also tried putting both the depends and the driver in the blacklists at the same time. That also just made my wireless connections disappear. There are several other blacklist files in the same folder should I try those?

bla back to the drawing board. Any other ideas? 

Thanks

---

### Post by uncaspi on 2010-12-13
No my  idea was to blacklist iwl3945 and the deps. If this not works there  are nothing else to blacklist as I could think of.

---

### Post by crucialhoax on 2010-12-13
Are you using network manager? if so try Wicd that sometimes works better.

---

### Post by utilitarian on 2010-12-13
It works. Although I am not sure why? I did not switch network managers. Last night my DNS was still slow despite trying all the other suggestions and doing multiple reboots.. I took it to school this morning and the DNS suddenly worked on the other network. 

This led me to believe it was some sort of issue that required both my specific computer set up and a specific network setup(other ubuntu computers worked on my home network). 

Anyway then I took my computer back home and it just kept on working. So unless I am missing something the solution was just to boot the computer on a different wireless network and then return to the old one.

Thanks so much for all the help.

---

### Post by utilitarian on 2010-12-13
Never mind the speed up only seemed to last about 10 mins. I think I am going to try a new router next.

---

### Post by crucialhoax on 2010-12-14
> **utilitarian said:**
> Never mind the speed up only seemed to last about 10 mins. I think I am going to try a new router next.

I dont believe the router is the problem. If it was then it would also occur during wired connectivity. Ill do some research and see what I can find for you. It might be a bit but I will find a solution (hopefully) 8-)

---

### Post by crucialhoax on 2010-12-14
Please read comment **#40**:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/340418](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/340418)

Also please try this as well:
```

sudo iwconfig wlan0 power off

```

Post results as soon as convenient.  :)

---

### Post by titere05 on 2011-01-08
I'm replying to this thread not to shed light on the matter, but a little more shadow. I'm using a *wired* connection (the onboard NIC of an ASUS M2N32-SLI Deluxe, it's a Realtek model but can't remember which one) and I'm having the exact same issue. I dual boot ubuntu 10.10 x64 and windows 7 x64. In the former, DNS is painfully slow, while the latter works blazingly fast.

I've tried disabling IPv6 at kernel level and within Firefox, and it made absolutely no difference. Chrome is also affected, although it's slightly faster than Firefox (at least it never times out, but still takes its sweet time). Loading times remain the same when I try different DNS addresses (those of my provider, Google, OpenDNS, etc).

This never happened to me with previous versions of Ubuntu, and it'd be weird to have a number of network drivers just go bonkers from one update to the next. My guess? The problem is related to some architectural change in Ubuntu itself. Haven't tried other distros so I can't verify.

I'm about to try the suggestion in post #2 from [http://ubuntuforums.org/showthread.php?t=1533796](http://ubuntuforums.org/showthread.php?t=1533796). I'll see what happens and report back.

EDIT: I don't want to jinx it, but pages are loading up just fine now. Hope the magic lasts more than 10-15 minutes... I'll check back later.

EDIT #2: Still works great. That was the solution for me.

---

