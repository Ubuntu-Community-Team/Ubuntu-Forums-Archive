---
title: "Wifi won't turn on after a suspend mode :("
date: 2013-04-25
forum: Networking &amp; Wireless
---

### Post by Macoy Villalobos on 2013-04-25
I have problem  with my wifi after resuming from suspend mode. It says "wireless is  disabled by hardware switch". In my normal boot I just press F3, the  Wifi led light turns on and my laptop starts searching for signals. But resuming from suspension, I press F3, Wifi led light turns on but no  Wifi signals detected. the message "wireless is disabled by hardware  switch" won't change at all. :sad: I'm new in Ubuntu. and excuse my grammar.. but my bluetooth seems fine even resuming from suspend mode.
 
02:00.0 Network controller [0280]: Broadcom Corporation BCM43227 802.11b/g/n [14e4:4358]
03:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
03:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 10)
03:00.2 System peripheral [0880]: Broadcom Corporation Device [14e4:16be] (rev 10)
03:00.3 System peripheral [0880]: Broadcom Corporation Device [14e4:16bf] (rev 10)

HELP...

---

### Post by chili555 on 2013-04-25
Please suspend, wait a few moments and resume. Then please open a terminal and run and post:```
lsmod | grep wl
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

Your grammer and English are just fine; no worries.

---

### Post by Macoy Villalobos on 2013-04-27
macoychristian@macoychristian-ENNS11HR:~$ lsmod | grep wl
wl                   3074942  0 
cfg80211              208382  1 wl
lib80211               14382  2 lib80211_crypt_tkip,wl
macoychristian@macoychristian-ENNS11HR:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
macoychristian@macoychristian-ENNS11HR:~$ 


Here it is sir.. it's weird but when I read your reply, suspend my laptop for a few minutes, resume. for some reason my wifi works fine without doing what you suggested. hmmm. . so maybe I thought It's just luck. Well it is luck. I reproduce the bug by shutting down my laptop and pull out my battery, count 1 - 10 (hehe) return the battery, turn on, login, close the lid, wait for a few seconds, resume and voila. the bug is back!! :D then I do what you told me. Restart (to reconnect). Reply thread. :D

---

### Post by chili555 on 2013-04-27
The commands I suggested you run aren't designed to fix anything. They are designed to gather diagnostics, to see the state of the machine when things *aren't* working. I assume the diagnostics you posted are the result of:> close the lid, wait for a few seconds, resume and voila. *the bug is back*!! then I do what you told me.We see the result here:> 1: brcmwl-0: Wireless LAN
Soft blocked: no
[COLOR="#FF0000"]Hard blocked: yes[/COLOR]Here is a technique that often helps. 
```
gksudo gedit /etc/pm/config.d/config
```

It will probably be a new file. Add a single line:
```
SUSPEND_MODULES="wl"
```Proofread carefully, save and close gedit. After a reboot, try to suspend and resume. If the wireless is not working, please run and post:```
lsmod | grep wl
rfkill list all
```

---

### Post by Macoy Villalobos on 2013-04-27
It will probably be a new file. Add a single line:
```
SUSPEND_MODULES="wl"
```Proofread carefully, save and close gedit. After a reboot, try to suspend and resume. If the wireless is not working, please run and post:```
lsmod | grep wl
rfkill list all
```[/QUOTE]

It works!! I knew you can help.. thanks doc Chili55 :D.. after I followed the first set of instruction. after resume for just 1 minute it works.. Thank you very much! Your awesome!=D>

---

### Post by chili555 on 2013-04-27
Glad it's working! Please mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Stephen_Sykes on 2013-09-13
Thanks chili555. Found this thread through google because Ubuntu 13.04 version had the same issue on my laptop and your solution works like a charm, so far. ;)

Edit: Well crap, spoke too soon. It's still taking a minute or two for the wifi to come back on after waking. How annoying!

---

### Post by neau84 on 2014-05-28
This bug appears to be on the 14.04 LTS as well. The solution was very helpful. Thanks

---

### Post by luis-rosety on 2015-01-10
> **Macoy Villalobos said:**
> It will probably be a new file. Add a single line:
```
SUSPEND_MODULES="wl"
```Proofread carefully, save and close gedit. After a reboot, try to suspend and resume. If the wireless is not working, please run and post:```
lsmod | grep wl
rfkill list all
```

It works!! I knew you can help.. thanks doc Chili55 :D.. after I followed the first set of instruction. after resume for just 1 minute it works.. Thank you very much! Your awesome!=D>[/QUOTE]

Great!
I found this post although I have been loking for a solution since some time ago.
It works and I confirm that Ubuntu 14.04 sitll has the bug.
Thanks!

---

### Post by aloiece on 2015-07-18
Hello, unfortunately this doesn't work for me. I did:  ~$ lsmod | grep wl wl                   6369280  0  cfg80211              552960  1 wl   ~$ rfkill list all 0: hci0: Bluetooth 	Soft blocked: no 	Hard blocked: no 1: phy0: Wireless LAN 	Soft blocked: no 	Hard blocked: no 2: brcmwl-0: Wireless LAN 	Soft blocked: no 	Hard blocked: no   does anyone know what to do now?

---

### Post by chili555 on 2015-07-18
> **aloiece said:**
> Hello, unfortunately this doesn't work for me. I did:  ~$ lsmod | grep wl wl                   6369280  0  cfg80211              552960  1 wl   ~$ rfkill list all 0: hci0: Bluetooth 	Soft blocked: no 	Hard blocked: no 1: phy0: Wireless LAN 	Soft blocked: no 	Hard blocked: no 2: brcmwl-0: Wireless LAN 	Soft blocked: no 	Hard blocked: no   does anyone know what to do now?May we please see:```
cat  /etc/pm/config.d/config
```Thanks.

---

### Post by nautiman on 2015-08-14
This doesn't work for me either - Lenovo G50 with 15.04 installed yesterday replacing windows 8....wifi hard blocked.   Tried the gksudo gedit command as above to access the config file but, after asking for the admin password it simply went back to the standard prompt without opening the file.....?    All ideas welcome -----should I open a new thread ?

---

### Post by chili555 on 2015-08-14
> **nautiman said:**
> This doesn't work for me either - Lenovo G50 with 15.04 installed yesterday replacing windows 8....wifi hard blocked.   Tried the gksudo gedit command as above to access the config file but, after asking for the admin password it simply went back to the standard prompt without opening the file.....?    All ideas welcome -----should I open a new thread ?Unless I am misreading your post, I think you have a different problem; that is, your wireless is hard-blocked after installation and at every reboot.

The original post was about *working* wireless that didn't work after suspend. If I am correct, then you have a different problem that deserves its own new thread.

---

