---
title: "BCM4312 drops wireless connection"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by daniel.p on 2011-09-27
I have an HP Mini netbook dual booting Ubuntu Netbook Remix and BackTrack 5. I know this isn't the BackTrack forums, but I've asked for help there and 48 hours later still have no replies. I searched Google for a few hours before asking on their forums, and have spent countless hours searching for help since posting on their forums. Knowing that BackTrack is based off Ubuntu, I figured I would try looking for help here.

I originally thought my issue was with Wicd. I kept getting the "bad password" problem when trying to connect to my home network secured with WPA. I tried the solution of downgrading Wicd but had no luck. Finally I disabled security on my router and was able to connect, or so I thought. According to Wicd I was connected but I was unable to load a page in Firefox. Looking back at Wicd it said I was not connected. I connected again and the same thing happened. Finally I decided to connect and try to ping Google, no response. I decided to reboot and manually connect to my wireless and got the expect response in the terminal window showing that I had connected. When I tried to ping Google again, same result happened. I'm not really sure what to do here. Basically it's not really connecting at all, just thinking it is or it's dropping the connection as soon  as it's used.

Like I said, I know this isn't the BackTrack forums, but I got no help there and I know this community is more populated and extremely helpful. Any help or advice would be greatly appreciated.

---

### Post by daniel.p on 2011-09-28
Nobody has any ideas? I'd really like to get this issue solved.

---

### Post by chili555 on 2011-09-28
I'll take a run at it. Please post:```
lspci -nn | grep 0280
lsmod | grep -e b43 -e wl -e ndis
```Thanks.

---

### Post by paddy101 on 2011-09-28
I'm having a similar problem with a Ubuntu 10.04 and a BCM4311 which has started constantly dropping off.  I had an earlier thread which, also, nobody replied to.  Is it acceptable for me to post my diagnostics to this thread?  Thanks

---

### Post by chili555 on 2011-09-28
> **paddy101 said:**
> I'm having a similar problem with a Ubuntu 10.04 and a BCM4311 which has started constantly dropping off.  I had an earlier thread which, also, nobody replied to.  Is it acceptable for me to post my diagnostics to this thread?  ThanksSure. Bear in mind, as I will, too, that you have a 4311 and that daniel.p has a 4312. The fixes may be different.

---

### Post by paddy101 on 2011-09-28
Thank you, at this point I will take what I can get.  I do appreciate the help.

lspci -nn | grep 0280

03:03.0 Network controller [0280]: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)


lsmod | grep -e b43 -e wl -e ndis

b43                   163556  0 
mac80211              205402  1 b43
cfg80211              126144  2 b43,mac80211
led_class               2864  1 b43
ssb                    38934  1 b43

If you need anything else, please let me know.

---

### Post by chili555 on 2011-09-28
Good news so far; b43 and ssb are correct for your device. Let's see if there are any kernel messages about this:```
dmesg | grep b43
rfkill list all
```Thanks.

---

### Post by daniel.p on 2011-09-28
> **chili555 said:**
> I'll take a run at it. Please post:```
lspci -nn | grep 0280
lsmod | grep -e b43 -e wl -e ndis
```Thanks.

 "lspci -nn | grep 0280" produces:
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```"lsmod | grep -e b43 -e wl -e ndis" gives me:
```
b43                   312342  0 
mac80211              255996  1 b43
cfg80211              153414  2 b43,mac80211
ssb                    37936  1 b43

```

EDIT: If you look at this [link]("http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers#Tested_and_working_cards") to the BackTrack Wiki, it lists BCM4312 as working with mac80211 b43

---

### Post by paddy101 on 2011-09-28
Thanks again.  

dmesg | grep b43

[88639.456060] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[88799.308197] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89005.852198] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89006.432197] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89047.464202] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89207.308198] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89408.872199] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89409.468199] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89450.472199] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89610.312067] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89816.836059] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89817.404199] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89858.488198] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[90018.308201] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[90219.868174] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[90220.448172] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[90261.440062] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[90421.308196] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[90622.852197] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[90623.364198] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[90664.476198] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[90824.312061] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[91025.896099] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[91026.416065] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[91067.488063] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[91227.312084] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[91267.012087] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[95862.668143] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[95877.868152] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[95878.400135] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[95959.876206] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[95960.492197] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[95961.488201] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

rfkill list all

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2011-09-28
> **daniel.p said:**
> "lspci -nn | grep 0280" produces:
```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```"lsmod | grep -e b43 -e wl -e ndis" gives me:
```
b43                   312342  0 
mac80211              255996  1 b43
cfg80211              153414  2 b43,mac80211
ssb                    37936  1 b43

```

EDIT: If you look at this [link]("http://www.backtrack-linux.org/wiki/index.php/Wireless_Drivers#Tested_and_working_cards") to the BackTrack Wiki, it lists BCM4312 as working with mac80211 b43@daniel.p--

Please hook up the ethernet cable and do:```
sudo apt-get install firmware-b43-lpphy-installer
```After a reboot, you should be working properly.

---

### Post by chili555 on 2011-09-28
I am quite mystified:> [88639.456060] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[88799.308197] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89005.852198] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89006.432197] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[89047.464202] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)May I see:```
ls /lib/firmware | grep b43
ls -al /lib/firmware/b43
dmesg | grep firmware | tail -n10
```Thanks.

---

### Post by daniel.p on 2011-09-28
> **chili555 said:**
> @daniel.p--

Please hook up the ethernet cable and do:```
sudo apt-get install firmware-b43-lpphy-installer
```After a reboot, you should be working properly.

This is what I got:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firmware-b43-lpphy-installer

```
My guess is it's not in the BackTrack repo. I searched in Synaptic for b43 and all that came up was b43-fwcutter. On a side note, I know Wicd 1.7 (the network manager that comes with BT) has an issue with connecting to WPA secured networks. If I can at least get a connection manually then the Wicd thing is an easy fix from there.


EDIT: So, I just upgraded from Netbook Remix to 11.04 and can no longer connect to wireless. It was working fine prior to updating though. Wireless is actually what I used to get the update/upgrade. Wired still works fine though.

---

### Post by paddy101 on 2011-09-28
> **chili555 said:**
> I am quite mystified:May I see:```
ls /lib/firmware | grep b43
ls -al /lib/firmware/b43
dmesg | grep firmware | tail -n10
```Thanks.


ls /lib/firmware | grep b43 shows

```
b43
b43legacy
```ls -al /lib/firmware/b43 shows

```
total 308
drwxr-xr-x  2 root root  4096 2010-09-28 07:48 .
drwxr-xr-x 52 root root 20480 2011-07-16 07:58 ..
-rw-r--r--  1 root root   158 2010-09-28 07:48 a0g0bsinitvals5.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 a0g0bsinitvals9.fw
-rw-r--r--  1 root root  1840 2010-09-28 07:48 a0g0initvals5.fw
-rw-r--r--  1 root root  2002 2010-09-28 07:48 a0g0initvals9.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 a0g1bsinitvals13.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 a0g1bsinitvals5.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 a0g1bsinitvals9.fw
-rw-r--r--  1 root root  2080 2010-09-28 07:48 a0g1initvals13.fw
-rw-r--r--  1 root root  1840 2010-09-28 07:48 a0g1initvals5.fw
-rw-r--r--  1 root root  2002 2010-09-28 07:48 a0g1initvals9.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 b0g0bsinitvals13.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 b0g0bsinitvals5.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 b0g0bsinitvals9.fw
-rw-r--r--  1 root root  2080 2010-09-28 07:48 b0g0initvals13.fw
-rw-r--r--  1 root root  1840 2010-09-28 07:48 b0g0initvals5.fw
-rw-r--r--  1 root root  2002 2010-09-28 07:48 b0g0initvals9.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 lp0bsinitvals13.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 lp0bsinitvals14.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 lp0bsinitvals15.fw
-rw-r--r--  1 root root  3618 2010-09-28 07:48 lp0initvals13.fw
-rw-r--r--  1 root root  2064 2010-09-28 07:48 lp0initvals14.fw
-rw-r--r--  1 root root  2052 2010-09-28 07:48 lp0initvals15.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 n0absinitvals11.fw
-rw-r--r--  1 root root   158 2010-09-28 07:48 n0bsinitvals11.fw
-rw-r--r--  1 root root  2100 2010-09-28 07:48 n0initvals11.fw
-rw-r--r--  1 root root  1320 2010-09-28 07:48 pcm5.fw
-rw-r--r--  1 root root 29864 2010-09-28 07:48 ucode11.fw
-rw-r--r--  1 root root 32232 2010-09-28 07:48 ucode13.fw
-rw-r--r--  1 root root 31384 2010-09-28 07:48 ucode14.fw
-rw-r--r--  1 root root 30488 2010-09-28 07:48 ucode15.fw
-rw-r--r--  1 root root 22384 2010-09-28 07:48 ucode5.fw
-rw-r--r--  1 root root 25160 2010-09-28 07:48 ucode9.fw

```]
dmesg | grep firmware | tail -n10 gives me

```

[110394.496201] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[110554.308200] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[110760.848194] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[110761.484199] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[110802.496191] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[110962.308204] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[111163.828202] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[111164.372213] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[111205.432199] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[111323.592212] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```Thanks

---

### Post by daniel.p on 2011-09-29
I'm really starting to get curious about my wireless issue(s). Since upgrading to Ubuntu 11.04 from the Netbook Remix I'm having the same issue I've been having with BackTrack. For example, right now I booted up my netbook and my wireless connection was established (according to the tray icon), but as soon as I opened up Firefox and tried to search something the connection dropped.

It tried to automatically reconnect and after about 5 minutes it stops trying and just gives me a disconnected notification, which is pretty much what BackTrack 5 is doing.

---

### Post by paddy101 on 2011-09-30
> **chili555 said:**
> I am quite mystified:May I see:```
ls /lib/firmware | grep b43
ls -al /lib/firmware/b43
dmesg | grep firmware | tail -n10
```Thanks.


I ran all these diags after manually reconnecting the wireless.  Should they have been run while the wireless was down?  Would the results possibly have been different?

---

### Post by chili555 on 2011-10-01
> **paddy101 said:**
> I ran all these diags after manually reconnecting the wireless.  Should they have been run while the wireless was down?  Would the results possibly have been different?They would have likely been the same either way. I am still mystified! I don't understand why it repeatedly reloads the firmware. Maybe there is a clue here:```
sudo cat /var/log/syslog | grep -e b43 -e firmware | tail -n25
```

---

### Post by paddy101 on 2011-10-01
sudo cat /var/log/syslog | grep -e b43 -e firmware | tail -n25 produces

```
Oct  1 08:16:29 family-laptop kernel: [66928.368650] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

```

I do appreciate the effort.

---

### Post by paddy101 on 2011-10-07
Anybody have any more recommendations?  Ideas?

---

### Post by tp11235 on 2012-07-07
I came here with the same problem. However, I put Ubuntu onto the HP Mini 210 because it was getting exactly this problem with Windows 7. I am fairly sure this problem is very close to the hardware.

I am new to Ubuntu having spent many years building Gentoo servers. I once got a wireless connection working in Gentoo! I was amazed at how easy Ubuntu has made it!

I am trying to modify the diagnostics here to find out what is happening on my machine.

---

