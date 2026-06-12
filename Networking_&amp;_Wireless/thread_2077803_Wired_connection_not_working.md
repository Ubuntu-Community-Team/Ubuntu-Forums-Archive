---
title: "Wired connection not working"
date: 2012-10-29
forum: Networking &amp; Wireless
---

### Post by Sowndefex on 2012-10-29
HI again all.

Sorry about getting my posts mixed up. I will try again.

Currently I have a laptop with windows and my main comp with Ubuntu. My laptop will connect to the internet with wire or wireless. But my computer will not connect. 

If I left click on the internet icon it states that enable networks and notification have ticks by them. then if I right click on the icon it states that I am disconnected. When I turn the computer on it tries a few times to connect to the internet but always gives me the not connected window with the red x.  

I havent done anything to change settings just looked at it all. 

I have looked about a maybe I need to activate drivers? So I went into system admin and then hardware drivers but it only talks about graphics card.

Please may you help me. I am happy to enter code and give screen shots if you can tell me what to do. 

Again many thanks in advance.

Regards

---

### Post by chili555 on 2012-10-29
Please open a terminal and run and post:```
lspci -nn | grep 0200
nm-tool
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Sowndefex on 2012-10-29
wow thanks!

---

### Post by Sowndefex on 2012-10-29
just saw my mistake. will send another screen shot.  I am such a div!

---

### Post by Sowndefex on 2012-10-29
ok got it right this time.

---

### Post by chili555 on 2012-10-29
You have an apparently working and healthy driver. Let's dig deeper:```
cat /etc/network/interfaces
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by Sowndefex on 2012-10-29
ok next screen shot. I hope I got it right as not much happened.

---

### Post by chili555 on 2012-10-29
No activity from Network Manager??? Wha..? Is NM even running?```
ps aux | grep -i network
```If not, let's start it:```
sudo service network-manager start
```Any improvement?

---

### Post by Sowndefex on 2012-10-29
still no luck :-(

---

### Post by chili555 on 2012-10-29
Let's check an earlier log:```
sudo cat /var/log/syslog[COLOR="Red"].1[/COLOR] | grep etwork | tail -n20
```

---

### Post by Sowndefex on 2012-10-29
OK here is the latest.  hope this helps.

---

### Post by chili555 on 2012-10-29
I noticed it marked Wired Connection 2 invalid. Let's clear out all the prior connection settings if any:```
sudo rm -rf /etc/NetworkManager/system-connections/*
```The command 'rm -rf' is powerful and dangerous if used improperly. Proofread carefully before you pull the trigger, er, uh, press Enter.

Next, be sure Network Manager has no settings at all added by you. It ought to look clean like attached.

Next, reboot. Any change?```
sudo cat /var/log/syslog | grep etwork | tail -n20
```If there is little or no output, try syslog.1 as above.

---

### Post by Sowndefex on 2012-10-29
Hithis was the output. Still no change.

---

### Post by chili555 on 2012-10-30
Let's try a couple of driver parameters:```
sudo modprobe -r forcedeth
sudo modprobe forcedeth msi=0 msix=0
```If it helps, we can write one file to make it persistent.

Now can you connect?

---

### Post by Sowndefex on 2012-10-30
I tried it and nothing happend. I am getting really depressed now. Maybe I should just get a new computer. I really dont understand this. :-(

---

### Post by chili555 on 2012-10-30
I can see that nothing happened in the terminal. What happened to your ability to connect?```
sudo cat /var/log/syslog | grep etwork | tail -n20
sudo cat /var/log/syslog | grep forcedeth | tail -n20
```

---

### Post by Sowndefex on 2012-10-30
maybe this helps?

---

### Post by chili555 on 2012-10-30
It looks very much like the previous logs: everything is normal except it just won't quite make the final step and connect. It is my most and yet least favorite kind of problem. Everything looks perfect except it doesn't start and run. 

If you have checked the CAT5/6 cable and know it's good; if you've checked to see that the cable is plugged in correctly at both the computer and router; if you've checked the router to make sure there is no restriction such as MAC address filtering; if you are using DSL and are supplying correct username and password details in either the router or NM in the computer; if all those details are checked and correct, then I have no more suggestions.

I'm very sorry.

Do you have wireless capability?

---

