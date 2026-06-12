---
title: "NetworkManager can't find my wifi"
date: 2011-07-01
forum: Networking &amp; Wireless
---

### Post by bhalkitt on 2011-07-01
A couple of months ago networkmanager "lost" my wifi at home. It had worked flawlessly previously, for more than a year. Now, networkmanager can see the wifi signals from all my neighbors but not my own right in the same apartment! Needless to say, it's not possible to connect to the internet. This is a dual boot machine, running Ubuntu Hardy and Vista. Connection to my wifi works just fine under Vista, so something has gone awry in the ubuntu configuration, I suppose. I have tried setting up my wifi as a hidden network, but to no avail. Any ideas are welcome!

---

### Post by bhalkitt on 2011-09-03
Nobody replied to this during the summer, so I'll try again. If no one here has any advice, perhaps there's somewhere else I could look? I'm getting really tired of slogging thru with Vista to get online!

---

### Post by josephmills on 2011-09-03
hi there maybe when you updated it changed something. have you tryed the "quick fix" of installing wicd ? also do you see it with the command ```
iwlist scan 
``` ?

---

### Post by northd_tech on 2011-09-03
Let's see the output of the following terminal commands (copy/paste under Ubuntu and post here):

```
sudo lshw -C network
ifconfig
iwconfig
lsmod
lspci | egrep 'net|ireless|etwork'
nm-tool
rfkill list all
tail /var/log/wicd/wicd.log

```

I suspect you've got some Network Manager and/or authentication issues (which Wicd might possibly cure pretty easily from my experience).

---

### Post by northd_tech on 2011-09-03
> **bhalkitt said:**
> Connection to my wifi works just fine under Vista, so something has gone awry in the ubuntu configuration, I suppose. I have tried setting up my wifi as a hidden network, but to no avail. Any ideas are welcome!
After you get done posting that terminal output (with josephmills' [**sudo] iwlist scan** output here too), can you reboot into Vista (or else Ethernet cable into your router under Ubuntu) and undo all that hidden network business?  That WILL NOT help you get Ubuntu connected wirelessly (and it really doesn't add all that much security IMHO)

---

### Post by josephmills on 2011-09-03
> **northd_tech said:**
> After you get done posting that terminal output (with josephmills' **sudo iwlist scan** output here too), can you reboot into Vista (or else Ethernet cable into your router under Ubuntu) and undo all that hidden network business?  That WILL NOT help you get Ubuntu connected wirelessly (and it really doesn't add all that much security IMHO)


Please do NOT put the out put here as I DO NOT want to see you mac address or ip address 
Just wondering if you can see your network

---

### Post by northd_tech on 2011-09-03
> **josephmills said:**
> Please do NOT put the out put here as I DO NOT want to see you mac address or ip address 
Just wondering if you can see your network
Well, my **working** wireless tells me this if I don't use **sudo** with **iwlist**:

> **iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

**eth1      Interface doesn't support scanning.**

vboxnet0  Interface doesn't support scanning.
Of course, my Broadcom STA driver doesn't work with **rfkill** at all either:

> xx@-laptop:~$ **rfkill list all**
xx@-laptop:~$ **sudo** **rfkill list all**
:(

---

### Post by josephmills on 2011-09-03
Broadcom you say ehhhh (look ma Im candian :) )

lets see a ```
lspci -nn 
``` 
thanks

---

### Post by northd_tech on 2011-09-03
> lspci -vvnn | egrep 'net|ireless|etwork'
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
03:00.0 Network controller [0280]: Broadcom Corporation **BCM4328** 802.11a/b/g/n [14e4:**4328] (rev 03)**

The "STA" driver works great for me, as long as I don't try to force the "b43" driver for monitor mode- that created all kinds of firmware issues (that I couldn't seem to get fixed but I have 'found' very intermittent wireless access this past year).  Honestly, I could swear that used to say   "...[COLOR=Blue][14e4:**4328] (rev 01)**[/COLOR]" for my Broadcom "4328" wireless (which Vista calls a "Broadcom 4321AG")- could Windows Vista have somehow updated my Broadcom firmware without me noticing/asking it to?  Maybe I'm just getting it confused with someone else's wireless card though (I have looked at a LOT of **lspci** output on this forum and elsewhere ;) ).

I had no end of wrinkled forehead trying to figure out the **rfkill** thing and I finally just gave up trying- there is an older thread here at Ubuntufourms where that played out.

---

### Post by bhalkitt on 2011-09-05
Thanks for all the advice. My apologies for not answering quicker - too much travel in a different time zone. 
I just sat down to run the commands you asked for and lo and behold, the wifi connection came up normally! Earlier this summer I made repeated attempts over several weeks, to no avail. And now - once there's some competent help available - the problem goes away (seemingly). Spooky. 
I have no idea what could cause this behavior, but it's useless to try to diagnose a problem that disappears. For the time being I'll just pretend nothing ever happened, but I'll keep your suggestions just in case. Anyway, one of the first things on my list is to upgrade to lucid. 
Thanks again, and I hope you don't hear from me again on this subject.

---

