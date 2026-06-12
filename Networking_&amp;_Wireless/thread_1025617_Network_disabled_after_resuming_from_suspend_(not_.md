---
title: "Network disabled after resuming from suspend (not a driver issue)"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by chiron80 on 2008-12-30
I just reformatted and installed Ubuntu 8.10 Intrepid Ibex on my Thinkpad Z60m. At first I was having trouble with the wireless card (Atheros using ath_pci) not working after resuming from suspend. However, I fixed *that* problem using the instructions in the release notes [1], and now I am experiencing another problem.

Upon resuming my networking is disabled. This happens with both wireless and wired networking. In this case the workaround is simple: I just right-click on the network manager icon and check the box labeled "Enable Networking" and everything works smoothly.

I know this is a pretty simple workaround, and that makes this a pretty minor issue. However, this is definitely a regression from behavior in previous releases, and is kind of annoying.

Anybody know how to fix this issue (how to get network manager to automatically enable itself after resuming)?

[1] [https://wiki.ubuntu.com/IntrepidReleaseNotes#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver](https://wiki.ubuntu.com/IntrepidReleaseNotes#Wireless%20doesn%27t%20work%20after%20suspend%20with%20ath_pci%20driver)

---

### Post by nukeqler on 2008-12-30
I see this too, except I think it only happens about 1 our of 5 times that I resume (I usually suspend rather than hibernate, if that makes a difference).  

It does seem to have gotten somewhat better since the last set of updates.

---

### Post by chiron80 on 2008-12-30
> **nukeqler said:**
> I see this too, except I think it only happens about 1 our of 5 times that I resume (I usually suspend rather than hibernate, if that makes a difference).

I think it fails closer to 4 out of 5 times for me, but every once in a while it seems to resume without trouble, so it is definitely intermittent.

> **nukeqler said:**
> It does seem to have gotten somewhat better since the last set of updates.

I just upgraded to Intrepid last week, so I haven't had a chance to see a difference.

---

### Post by tomakCZ on 2009-01-14
I am experiencing the same problem in like 1 of 5 rate - still no solution ?

---

### Post by chiron80 on 2009-01-14
> **tomakCZ said:**
> I am experiencing the same problem in like 1 of 5 rate - still no solution ?

I haven't found a solution yet.

---

### Post by lloydkuhnle on 2009-01-28
Hello

After all my googling, I'm finding that quite a few people, including myself, have this problem.

(On a side note, suspend only functions on every other lid closing)

As of yet, has anyone come up with a fix?

---

### Post by linux4me on 2009-01-28
> **lloydkuhnle said:**
> Hello

After all my googling, I'm finding that quite a few people, including myself, have this problem.

(On a side note, suspend only functions on every other lid closing)

As of yet, has anyone come up with a fix?

I don't think there is a fix yet. It has been reported as a [bug]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/291062") in Intrepid and it looks like it's being worked on.

I haven't tried it, but in [another post]("http://ubuntuforums.org/showthread.php?t=829869&page=3") about this, some have found that uncommenting the line:
```
# iface eth1 inet dhcp
```
in /etc/network/interfaces serves as a workaround.

---

### Post by MacKai on 2009-01-28
im having the same problem about 4 out of 5  

Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection

---

### Post by Racer-X on 2009-01-28
I had the same problems and found a script on some posting that has worked for me since.  You have to run it after resuming from a suspend (and sometimes then select again the network you're trying to connect to).  Regardless, it's worked for me.  Make sure you use sudo to run it.

e.g. sudo resumenetwork.sh

Here's the script:

```
#! /bin/sh
# This script resumes network connectivity after suspend
sudo ifconfig wifi0 down
sudo dhclient -r wifi0
sudo wpa_supplicant -Dmadwifi -iwifi0 -c/etc/wpa_supplicant.conf -dd 
sudo ifconfig wifi0 up
sudo iwconfig wifi0 mode Managed
sudo dhclient wifi0
```

Hope this helps...

---

### Post by Arcturus691 on 2009-01-30
This is a problem with kernel 2.6.27-11.
There is a bug for this see link below:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288281]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/288281")

I used the following workaround, mentioned in the above link to get my network connection to work when resuming from suspend to ram. 

edit the file in /etc/pm/config.d/00sleep_module and add the line below:

SUSPEND_MODULES="forcedeth"

now when you suspend your network connection should work.

Dont forget to comment this line out when the fix is released for this issue.

---

### Post by dissdigg on 2009-01-31
problem persists 

lspci shows:

02:08.0 Network controller: RaLink RT2561/RT61 rev B 802.11g

---

### Post by kpkethc on 2009-02-15
Does anyone know of a fix for this? It's the only thing turning me off to Ubuntu...

---

### Post by chiron80 on 2009-02-15
> **kpkethc said:**
> Does anyone know of a fix for this? It's the only thing turning me off to Ubuntu...

There are a few possible solutions listed on the [bug report [1]]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/291062"). I haven't had a chance to try any yet (there was a suggestion posted just Friday), but the problem is definitely being looked at, and hopefully should be fixed soon.

- Ben

[1] [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/291062](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/291062)

---

### Post by seamustry on 2009-02-20
i have same problem with intel 2915abg wifi..."networking disabled" after suspend resume. looking forward to bug fix.

---

### Post by BadgerKid on 2009-03-07
What's working for me currently involved three changes. I'm not sure what the minimal set of changes is, but it works.

1. /etc/pm/config.d/00sleep_module

SUSPEND_MODULES="ath_pci"

2. /etc/pm/config.d/local

SUSPEND_MODULES="ath_pci"

3. a resume script:

# 2009-03-01: below are some things I tried that helped somehow
sudo /etc/init.d/networking restart
sudo modprobe  wlan_scan_sta
sudo ifconfig eth0 down
sudo modprobe ath_pci

---

### Post by danmarycap on 2009-03-12
> **BadgerKid said:**
> What's working for me currently involved three changes. I'm not sure what the minimal set of changes is, but it works.

1. /etc/pm/config.d/00sleep_module

SUSPEND_MODULES="ath_pci"

2. /etc/pm/config.d/local

SUSPEND_MODULES="ath_pci"

3. a resume script:

# 2009-03-01: below are some things I tried that helped somehow
sudo /etc/init.d/networking restart
sudo modprobe  wlan_scan_sta
sudo ifconfig eth0 down
sudo modprobe ath_pci


A very similar fix worked for me:

1) sudo gedit /etc/pm/config.d/00sleep_module

added this text as the last line in the file and saved:

SUSPEND_MODULES="wl0"
  (note: it's a Dell mini9 with a Broadcom 43xx wireless adapter)

2) sudo gedit /etc/pm/config.d/bcmwifi
  (note: this file does not exist, but I created it)

added same text (SUSPEND_MODULES="wl0") as only entry in this file and saved.

Now when I resume from suspend, I don't need to go to terminal to issue any commands...if my wireless was connected before suspend, it automatically reconnects afterwards.

Thanks to gib2800 at this post ([http://ubuntuforums.org/showthread.php?t=779338&highlight=resume+network](http://ubuntuforums.org/showthread.php?t=779338&highlight=resume+network)) as well as a few other posts where these solutions are suggested.  I don't know which of these actions (or both?) did the trick, but it works.

-Dan

---

### Post by cottfcfan on 2009-03-16
I have an Edimax 7318usg wireless card, with a ralink chipset and rt73 driver.
I`m new to Linux. What would I need to do to get mine working after suspend?
Thanx in advance.

---

### Post by lycopenehead on 2009-04-21
hello fellas ,i have a very simple solution ,while somehow it turns to be boring for me,but at least its better than rebooting and stuff,from menu go to system>administration>hardware drives then disable the network controller and enable it again(while doing that keep the wifi enabled in the network manager)then pick up your fav. network

i really hope it works for all,cheers,

---

### Post by nickdjones on 2009-07-23
> **danmarycap said:**
> A very similar fix worked for me:

1) sudo gedit /etc/pm/config.d/00sleep_module

added this text as the last line in the file and saved:

SUSPEND_MODULES="wl0"
  (note: it's a Dell mini9 with a Broadcom 43xx wireless adapter)

2) sudo gedit /etc/pm/config.d/bcmwifi
  (note: this file does not exist, but I created it)

added same text (SUSPEND_MODULES="wl0") as only entry in this file and saved.

Now when I resume from suspend, I don't need to go to terminal to issue any commands...if my wireless was connected before suspend, it automatically reconnects afterwards.

Thanks to gib2800 at this post ([http://ubuntuforums.org/showthread.php?t=779338&highlight=resume+network](http://ubuntuforums.org/showthread.php?t=779338&highlight=resume+network)) as well as a few other posts where these solutions are suggested.  I don't know which of these actions (or both?) did the trick, but it works.

-Dan

The same fix worked for me on my Dell Optiplex gx620.

I only needed the first step, as outlined here:
[http://ubuntuforums.org/showpost.php?p=6465454&postcount=6](http://ubuntuforums.org/showpost.php?p=6465454&postcount=6)

thanks everyone

---

### Post by thedude01 on 2009-09-22
I had the same problem with my Intel PRO/Wireless 2200BG card. In order to turn the wireless radio on after a boot I have to run a script:

```

#!/bin/bash
sudo modprobe fsam7400 radio=1
exit

```I finally figured out what was needed to keep my wireless going after a suspend -- just unload and reload the driver fsam7400 via modprobe after resuming from a suspend:

```

#!/bin/bash
sudo modprobe -r fsam7400
sudo modprobe fsam7400 radio=1
exit

```This seems to work well for this particular driver.

Cheers!

---

### Post by thedude01 on 2009-09-22
actually, it seems to be sufficient to simply use

```

#!/bin/bash
sudo modprobe -r fsam7400
sudo modprobe fsam7400 radio=1
exit

```

for a wireless-load script, irrespective if after booting or resuming suspend.

---

### Post by fabricio.lemos on 2009-11-14
Is there any feature request on the bug tracking for this workaround?

---

