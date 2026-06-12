---
title: "Wireless drops repeatedly - Linksys E1000, Realtek RTL8191SEvB"
date: 2011-04-09
forum: Networking &amp; Wireless
---

### Post by aman_cc on 2011-04-09
I have
- Ubuntu 10.10 64 bit
- Kernel 2.6.35-28-generic
- Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
- Linksys E1000 wireless router
 
Problem - Wireless keeps dropping. It doesn't disconnect but I can't ping any site. Dis-connecting / re-connecting makes it work fine, but it drops again.
I have Windows 7 on the same computer - I face no problem there.
 
What all I have done so far
1. Un-installed Network Manager and installed wicd - no success
2. Reading some threads and sites - but no success
3. Tried contacting Linksys support - but no success
 
My linux skills - very basic.
 
 
Output of some commands I ran - 
**lspci | grep Network**
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
 
**nm-tool**
- Device: wlan0 [cc] ----------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl819xSE
State: connected
Default: yes
HW Address: F0:7B:CB:A6:03: DB
 
 
Any help / pointers will be much appreciated. This problem is making me think of stop using Ubuntu.
 
Thanks

---

### Post by aman_cc on 2011-04-09
This what I could see in the messages log

Apr 10 08:21:30 T410 kernel: [ 3942.345797] NVRM: os_raise_smp_barrier(), invalid context!
Apr 10 08:21:30 T410 kernel: [ 3942.362527] NVRM: os_raise_smp_barrier(), invalid context!
Apr 10 08:21:35 T410 kernel: [ 3947.338748] NVRM: os_raise_smp_barrier(), invalid context!
Apr 10 08:21:35 T410 kernel: [ 3947.353585] NVRM: os_raise_smp_barrier(), invalid context!
Apr 10 08:21:39 T410 kernel: [ 3951.321680] ===>rtl8192se_link_change():ieee->iw_mode is 2
Apr 10 08:21:39 T410 kernel: [ 3951.374472] =====>rtl8192_set_chan()====ch:1
Apr 10 08:21:39 T410 kernel: [ 3951.495351] =====>rtl8192_set_chan()====ch:2
Apr 10 08:21:39 T410 kernel: [ 3951.613942] =====>rtl8192_set_chan()====ch:3
Apr 10 08:21:39 T410 kernel: [ 3951.723790] =====>rtl8192_set_chan()====ch:4
Apr 10 08:21:39 T410 kernel: [ 3951.834860] =====>rtl8192_set_chan()====ch:5
Apr 10 08:21:39 T410 kernel: [ 3951.953412] =====>rtl8192_set_chan()====ch:6
Apr 10 08:21:39 T410 kernel: [ 3952.063224] =====>rtl8192_set_chan()====ch:7
Apr 10 08:21:39 T410 kernel: [ 3952.174286] =====>rtl8192_set_chan()====ch:8
Apr 10 08:21:39 T410 kernel: [ 3952.292871] =====>rtl8192_set_chan()====ch:9
Apr 10 08:21:40 T410 kernel: [ 3952.403710] =====>rtl8192_set_chan()====ch:10
Apr 10 08:21:40 T410 kernel: [ 3952.512493] =====>rtl8192_set_chan()====ch:11
Apr 10 08:21:40 T410 kernel: [ 3952.622354] =====>rtl8192_set_chan()====ch:12
Apr 10 08:21:40 T410 kernel: [ 3952.732161] =====>rtl8192_set_chan()====ch:13
Apr 10 08:21:40 T410 kernel: [ 3952.843246] =====>rtl8192_set_chan()====ch:9
Apr 10 08:21:40 T410 kernel: [ 3952.853473] ===>rtl8192se_link_change():ieee->iw_mode is 2
Apr 10 08:21:40 T410 kernel: [ 3952.853482] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE

Any help please ?

---

### Post by aman_cc on 2011-04-11
Another thing I noticed, the connection drops lot more frequently when using applications like
- Update Manager
- BitTorrent
etc (maybe because of higher traffic ??)

---

### Post by aman_cc on 2011-04-12
@[[SIZE=5][COLOR=#000000]ashily24dee[/COLOR][/SIZE]]("http://ubuntuforums.org/member.php?u=1249487")   hi - if you could please share what did u do to make the wireless work for you plz
 
thanks

---

### Post by aman_cc on 2011-04-14
There is this thread
[http://ubuntuforums.org/showthread.php?t=1653157](http://ubuntuforums.org/showthread.php?t=1653157)
 
which seems to suggest a solution - but hasn't worked yet for me.
 
Can anyone please help?

---

### Post by aman_cc on 2011-04-27
Bumping !
 
Anyone has any experience on this with Natty? Is the problem still there with Natty?

---

### Post by aman_cc on 2011-05-03
bump plz
 
 
One clarification - The wifi doen't drop. It just freezes ! For any browser request / download, it gives a time-out. Even ping times out.
 
 
I have been banging my head on this for past 2 weeks. No success. Can anyone please help?

---

### Post by yungballla6 on 2011-05-04
Hi, I'm having this same problem and have noticed that it cannot be the router. Since I have tried my connection on many other sources. And the problem happens each time no matter what connection. I have a realtek card also. Just putting in my two cents.

---

### Post by aman_cc on 2011-05-06
> **yungballla6 said:**
> Hi, I'm having this same problem and have noticed that it cannot be the router. Since I have tried my connection on many other sources. And the problem happens each time no matter what connection. I have a realtek card also. Just putting in my two cents.
 
 
Yes doesn't seem to be a router problem. I have a dual boot with Win 7 64 bit and face no problem with that OS. Thanks

---

### Post by JVP3122 on 2011-05-06
I'm having the same problem.  Another proof it's not the router is that my wife uses the same router at the same time and she never has this problem.

---

### Post by conualfy on 2011-05-06
I've posted about this bun in a dozen threads but I still have no solution for this on my Toshiba laptop.

Wifi chipset: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express)

I've had it in Ubuntu 10.10 (64bit), upgraded to 11.4 and it's still there. I've tried different routers, so it's not the router. Win 7 works ok. It seems to be a problem with all wifi chipsets, it's very frustrating nobody can fix it.

As someone else said, it seems to happen on high speed downloading / uploading. I've offered to allow connection to my ubuntu (teamviewer, etc.) so a specialist / guru / linux experienced  can find the source of this bug (email me at      florin [at] drumliber [dott] ro).

---

### Post by axioma on 2011-05-06
I have the same problem. I tried Ubuntu and Kubuntu both with the same result. On the first boot the wireless seems to work fine for 5 to 30 minutes but than fails to connect again. Network-manager seems to be able to find the router because it lists it correctly in the list but can not connect to the net anymore. 
Seems to be a fundamental problem in the 11.04 set-up(?)

Had no problems in 9.04 and 10.10. Also router works perfect in windows.

I think some of the experts of the Network-managers have to have a look at it.
:(

---

### Post by Gr!MM^ on 2011-05-06
Having the same problem with my 11.04 desktop.
Connection freezes from time to time.

The other machines in this network are running Ubuntu 10.10, Windows XP and Arch Linux, they dont display any of these problems and downgrading to 10.10 solves the issue.

Oh, also, this happens more frequently when using SAMBA or BitTorrent

I'm assuming this is a problem between my machine and Natty. :(

```
$ lsusb | grep Wireless
Bus 001 Device 003: ID 07d1:3c0f D-Link System AirPlus G DWL-G122 Wireless Adapter(rev.E) [Ralink RT2870]
``````
$ iwconfig
wlan0     IEEE 802.11bg  ESSID:"gateway"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:9F:07:3B:45   
          Bit Rate=12 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:944  Invalid misc:81   Missed beacon:0
``````
$ uname -a
Linux desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by yungballla6 on 2011-05-06
its crazy how no one has a fix for this, i heard that a wipe of your system including windows. then the reinstall of windows then to again set up dual boot with Ubuntu will solve the issue.....but im a noob and am not about to break my whole lappy. Just my 2 cents

---

### Post by aman_cc on 2011-05-07
> **yungballla6 said:**
> its crazy how no one has a fix for this, i heard that a wipe of your system including windows. then the reinstall of windows then to again set up dual boot with Ubuntu will solve the issue.....but im a noob and am not about to break my whole lappy. Just my 2 cents
 
 
an update here - i have got a new driver for this card. (if someone know where i can upload it - i will be happy to do that). seems promising - normal browsing is fine. but when i try to donload files - like when running update manager it goes for a toss.

---

### Post by juliobahar on 2011-12-04
Refer to my thread [here]("http://ubuntuforums.org/showpost.php?p=11511359&postcount=11"). Wireless adapter seems more sane now.

---

### Post by aryangor on 2012-05-05
> **juliobahar said:**
> Refer to my thread [here]("http://ubuntuforums.org/showpost.php?p=11511359&postcount=11"). Wireless adapter seems more sane now.

Worked for me, thank you very very much!! ;)

---

