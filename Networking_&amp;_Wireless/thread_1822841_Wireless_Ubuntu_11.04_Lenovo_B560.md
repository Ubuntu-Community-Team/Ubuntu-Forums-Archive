---
title: "Wireless Ubuntu 11.04 Lenovo B560"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by AimpliesB on 2011-08-11
Hello!

I just installed ubuntu on my lenovo B560 notebook and have some trouble to get the wireless to work.

I googled my problem and stumbled over this thread: [http://ubuntuforums.org/showthread.php?t=1791389](http://ubuntuforums.org/showthread.php?t=1791389)

So I followed the wireless troubleshooting guide and found out, that the  problem seems to be caused by the "activate wireless" button of the  notebook:

 ```

rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```However, I cannot fix this problem. If I proceed with 

 ```

sudo rfkill unblock all 

```my computer freezes!
(The same result I get, if I actually hit the "activate wireless"  (Fn+F5) button, which was the first naive attempt of mine to this  problem.)

Any ideas, what might cause this strange behaviour and how to get my  wireless up and running?

Thank you very much!

A => B

---

### Post by chili555 on 2011-08-11
Please try this:```
sudo rmmod -f acer-wmi
```Now does your wireless work as expected? If so, blacklist it:```
sudo su
echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf
exit
```It's a known bug, for the benefit of all you searchers!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668234](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/668234)

---

### Post by AimpliesB on 2011-08-11
Hello chili,

thank you for your quick answer. I already tried that (due to your post in this thread: [http://ubuntuforums.org/showthread.php?t=1745317&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1745317&highlight=acer-wmi)) but it didn't change anything.

A => B

---

### Post by chili555 on 2011-08-11
Please run and post:```
sudo rmmod -f acer-wmi
rfkill list all
sudo rfkill unblock all
rfkill list all
```

---

### Post by AimpliesB on 2011-08-11
Hello again,

```

sudo rmmod -f acer-wmi rfkill list all

```
gives the same output as I posted above.

As soon as I run

```

sudo rfkill unblock all

```

my compuer freezes. I cannot do anything anymore, except switching it off.

---

### Post by pikamoku on 2011-08-11
I own the same laptop and had the same problems with wifi, but solved when log into windows partition, disabled and reenabled wifi from "control panel" (or something similar), then back to linux a verify everything worked.
My wifi device is:
> 04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
and I'm using "brcm80211" driver with no problems to connect on wpa/wep/open networks

edit: this thread could be useful [http://ubuntuforums.org/showthread.php?t=1617380](http://ubuntuforums.org/showthread.php?t=1617380)

---

### Post by chili555 on 2011-08-11
> **AimpliesB said:**
> Hello again,

```

sudo rmmod -f acer-wmi rfkill list all

```
gives the same output as I posted above.

As soon as I run

```

sudo rfkill unblock all

```

my compuer freezes. I cannot do anything anymore, except switching it off.Let's dig a little deeper. Please post:```
lspci -nn | grep 0280
```

---

### Post by AimpliesB on 2011-08-12
Good morning you two.

pikamoku, switching off and on doesn't help...

Chili:
```

lspci -nn | grep 0280
04:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

Thank  you,

A => B

---

### Post by chili555 on 2011-08-12
It looks like you actually need a wireless driver! Can you hook up to an ethernet connection and open a terminal and do:```
sudo apt-get install bcmwl-kernel-source
```That will install the correct driver and after you detach the cable and reboot, your wireless should be working.

---

### Post by AimpliesB on 2011-08-12
Chili,

this did it. Thank you so much!
I was convinced, the drivers were ok, because I activated it in the "additional drivers" window...
Anyhow, the wireless works  since then.

But something mysterious happened then. I tried to connect to my wireless, entered the password and saved and at that moment, both wlan and ethernet died. 
Eversince, my router (2wire) boots (flashing green power light), the green power light runs stable for like 2 seconds, then the router makes a clicking noise. Then the "ethernet" light flashes up for about one second and then the power lights turn red. Then the whole cycle starts again.
I cant have access to the internet over my router now, neither over ethernet nor wireless.
Normally I would say this is only a router problem, but it is a weird coincidence, that it occurs at the same time, that I tried to connect. 

So my last (stupid) question: Is this just bad luck or can there be a connection?

Thank you again for your help.

A => B

---

### Post by chili555 on 2011-08-12
> Eversince, my router (2wire) boots (flashing green power light), the green power light runs stable for like 2 seconds, then the router makes a clicking noise. Then the "ethernet" light flashes up for about one second and then the power lights turn red. Then the whole cycle starts again.
I cant have access to the internet over my router now, neither over ethernet nor wireless.You shouldn't really have both wired and wireless connected at once. Ordinarily, Network Manager disables wireless if wired is available.

I'd shut down my computer, detach all ethernet cables from the router and plug it in and start it up. If the power light still turns red and it clicks, I'd try to reset it by holding down the reset button for 15 seconds; usually the reset button is on the back. Some routers have unique reset procedures; please check your users manual. If it still acts strangely, even after a reset, I'd believe it is defective.

---

### Post by AimpliesB on 2011-08-24
Finally- Internet again. It was actually an unfortunate coincidence.

Thank you again for all your help!

A => B

---

