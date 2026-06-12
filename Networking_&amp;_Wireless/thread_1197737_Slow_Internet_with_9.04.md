---
title: "Slow Internet with 9.04"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by Talon2 on 2009-06-26
I recently installed Ubuntu 9.04 on my Dell 530n.  It is a dual boot with the Ubuntu 8.04 that came pre-loaded.  I do not share /home.  Both installations are totally separate.

I noticed that my dsl internet connectivity seemed to be far slower with 9.04 so I downloaded tcpTest v3 and ran some tests.  Here are the results:

Ubuntu 8.04:

Best tcp send rate 532.85 kbit/s
Best tcp receive rate: 1.42 Mbit/s
Send efficiency: 94.7%
Receive efficiency: 89.6%

Ubuntu 9.04:

Best tcp send rate 172.64 kbit/s
Best tcp receive rate: 267.06 kbit/s
Send efficiency: 30.9%
Receive efficiency: 18.3%

Something is wrong with 9.04.  I'd like to see if anyone else is seeing this before I investigate filing a bug.

---

### Post by sockmoney on 2009-07-05
I am seeing the same problem.  Ever since I loaded 9.04 last week my internet speed has been horrendous.  It is constantly "looking up" dns entries for like 4-5 seconds before even trying to load pages.

I disabled ipv6 in firefox, and I even went as far as re-compiling the kernel to modularize the ipv6 code so I could disable it.  That still didn't resolve the problem.

I switch back over to XP (dual boot) and internet works fine... lightening fast... never slow.

On Ubuntu, I get very slow response times.  Even when using things like telnet, my commands take many seconds to appear after I type them.  Very frustrating.  

Unfortunately I cannot work like this, and have to switch back to XP for now until they fix this problem.

---

### Post by darco on 2009-07-05
which kernel are you running?

darco

---

### Post by Spike1158 on 2009-07-05
I had the same problem, and what worked for me is Ndiswrapper...not through the GUI though, but through the terminal. [http://ubuntuforums.org/showthread.php?t=1078715&highlight=wmp54g](http://ubuntuforums.org/showthread.php?t=1078715&highlight=wmp54g) 2nd post down
If you are on a wireless setup-try out that guide...if not, try disabling/blacklisting IPV6, if you can find a good guide for it.

---

### Post by elnur on 2009-08-12
I solved this problem by setting **OpenDNS** as DNS.

Open the file:
```
sudo nano /etc/dhcp3/dhclient.conf
```
And add this to the end of the file:
```
prepend domain-name-servers 208.67.222.222, 208.67.220.220;
```

More info [here]("http://ubuntuforums.org/showthread.php?t=878694").

---

