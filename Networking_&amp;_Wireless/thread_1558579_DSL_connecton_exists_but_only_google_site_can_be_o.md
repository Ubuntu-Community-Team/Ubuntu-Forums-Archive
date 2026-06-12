---
title: "DSL connecton exists but only google site can be opened"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by niziris on 2010-08-22
Hello! 
I am new to Ubuntu...and so far I am in love :)...
only problem in my path to install Ubuntu at all my machines is [B]network connection

[/B]wireless connection works like charm 

but DSL connection is making problems, network connection show successful connection but I can only open 
[www.google.com]("http://www.google.com") and gmail ... when I try to go to one of the search results it all stops at loading screen ...

so far I have:
disabled ipv6 in sysctl.conf (this made some problems so I had to reinstall ubuntu completely)

disabled ipv6 in firefox

tried chromium WB (same problem nothing changed)

put [opendns]("https://store.opendns.com/setup/device/ubuntu/")  address as someone here suggested

so far I had no luck

if someone knows how can I fix this pleeease help!!

---

### Post by prshah on 2010-08-22
> **niziris said:**
> I can only open 
[www.google.com]("http://www.google.com") and gmail

Hi, I had a similar problem, you can take a look at my [(solved) post]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") on this; you could also [review the entire thread]("http://ubuntuforums.org/showpost.php?p=4514356").

Hope it helps:

---

### Post by niziris on 2010-08-22
> **prshah said:**
> Hi, I had a similar problem, you can take a look at my [(solved) post]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12") on this; you could also [review the entire thread]("http://ubuntuforums.org/showpost.php?p=4514356").

Hope it helps:

Thanks for fast reply! 

I tried couple of things 

#/sbin/ifconfig eth0 mtu 1492 

and

sudo ping -M do -s 1492 192.168.0.1

what did I do wrong because now I cant connect even to the google?

also my address is not static 

how should I fix MTU in Ubuntu 10.04?

---

### Post by dineshs on 2010-08-22
Can you explain the setup?Is your DSL modem programmed in PPPoE mode?
Which ubuntu version are you using?Are you using Network manager ?Can you post the results of
```
ifconfig -a
```
Note: MTU can be set in Network manager (right click NM -select the connection-edit
Have you tried DNS 4.2.2.1?

---

### Post by niziris on 2010-08-23
Thank you good people for yours replays! 

I FIXED THE PROBLEM!!!! FIrefox is working like charm! :KS :KS :KS :KS :KS


Solution was to fix MTU as prshah suggest and thank you man for that!

first I fix MTU in network connection: DSL tab/wired
that didn't do anything

BUT THEN

[B]I edited file in system-connection
address:   etc/NetworkManager/system-connections/kbc 
(kbc is the name of my DSL connection)
I edited by entering
[COLOR=DarkRed]sudo gedit/etc/NetworkManager/system-connections/KBC[/COLOR]
in terminal

after entering pass, gedit open editable file, there under [COLOR=DarkRed]"ppp" I found mtu=something[/COLOR] and I enter the values that I like ( for me it was 1480) and net works[/B]

the thing that I noticed: changing MTU in NetworkManager application in System/Preferences/Network Connections 
edited the end of  KBC file under "802-3-ethernet"...and that did not help

I put step by step explanation for the newbe (like myself) can follow easily

---

### Post by prshah on 2010-08-23
> **niziris said:**
> Solution was to fix MTU 

Just one minor point; in my suggestion, I recommended changing it in the router's settings, so that you will not have difficulties with other linux clients connecting; by changing it only on your machine, please remember that you will have to do it to every (wired) machine that you add to the network.

---

### Post by niziris on 2010-08-23
> **prshah said:**
> Just one minor point; in my suggestion, I recommended changing it in the router's settings, so that you will not have difficulties with other linux clients connecting; by changing it only on your machine, please remember that you will have to do it to every (wired) machine that you add to the network.
Thanks for your help one more time :D....yep, I will do that

---

### Post by srpsinu on 2010-09-24
> **niziris said:**
> Thank you good people for yours replays! 

I FIXED THE PROBLEM!!!! FIrefox is working like charm! :KS :KS :KS :KS :KS


Solution was to fix MTU as prshah suggest and thank you man for that!

first I fix MTU in network connection: DSL tab/wired
that didn't do anything

BUT THEN

[B]I edited file in system-connection
address:   etc/NetworkManager/system-connections/kbc 
(kbc is the name of my DSL connection)
I edited by entering
[COLOR=DarkRed]sudo gedit/etc/NetworkManager/system-connections/KBC[/COLOR]
in terminal

after entering pass, gedit open editable file, there under [COLOR=DarkRed]"ppp" I found mtu=something[/COLOR] and I enter the values that I like ( for me it was 1480) and net works[/B]

the thing that I noticed: changing MTU in NetworkManager application in System/Preferences/Network Connections 
edited the end of  KBC file under "802-3-ethernet"...and that did not help

I put step by step explanation for the newbe (like myself) can follow easily


Thanks I was having the same problem & your advice worked. Seems like network manager is running the show in new distros.

---

