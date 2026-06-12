---
title: "installing  ipw2200 and ieee80211 problem"
date: 2010-02-17
forum: Networking &amp; Wireless
---

### Post by abdelhadim on 2010-02-17
Hi guys,
I recently switched to Linux ubuntu 9.10
the olny problem i have now is my wireless. i have IBM THINKPAD t43
looked online, the best thing is to install ipw2200. Which needs ieee80211
I downloaded ieee80211-1.2.18
but when i run "make" it gives me this:
```
Checking in /lib/modules/2.6.31-19-generic for ieee80211 components...
make -C /lib/modules/2.6.31-19-generic/build M=/home/mohammad/Desktop/ieee80211-1.2.18 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-19-generic'
  CC [M]  /home/mohammad/Desktop/ieee80211-1.2.18/ieee80211_module.o
/home/mohammad/Desktop/ieee80211-1.2.18/ieee80211_module.c: In function ‘alloc_ieee80211’:
/home/mohammad/Desktop/ieee80211-1.2.18/ieee80211_module.c:148: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/mohammad/Desktop/ieee80211-1.2.18/ieee80211_module.c:149: error: ‘struct net_device’ has no member named ‘change_mtu’
/home/mohammad/Desktop/ieee80211-1.2.18/ieee80211_module.c:153: error: ‘struct net_device’ has no member named ‘get_stats’
make[2]: *** [/home/mohammad/Desktop/ieee80211-1.2.18/ieee80211_module.o] Error 1
make[1]: *** [_module_/home/mohammad/Desktop/ieee80211-1.2.18] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-19-generic'
make: *** [modules] Error 2

```I'm  a root when i run the command
from my understaning the prblem is that there is a compiling error in [COLOR=Red]ieee80211_module.c[/COLOR]
but i might be wrong!
i searched here for an answer and some people having the same problem but i did not find any solution.
If anyone knows what is going on, please let me know

Thank you guys for providing such a forum!!

---

### Post by chili555 on 2010-02-17
I don't know where you downloaded the ipw2200 package, or more pointedly, how old it is, but ipw2200 has been in the mainline kernel for some time now. As coincidence would have it, I answering this post on an ancient T40 using the mainline ipw2200 which works perfectly for me.

There is a newer, presumably better version in linux-backports-modules, as well. On boot, your device should grab the module automatically and create an interface, usually eth1, and be available in Network Manager.

If it's not working as expected, installing an *older* driver is very seldom useful.

If you'd like to troubleshoot, please post:```
lspci -nn | grep Network
dmesg | grep ipw
rfkill list
```Thanks.

---

### Post by abdelhadim on 2010-02-17
```
###########-laptop:~$ lspci -nn | grep Network
0b:02.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
###@###-laptop:~$ dmesg | grep ipw
[   14.065076] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   14.065080] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   14.065167] ipw2200 0000:0b:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.065235] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   14.065282] ipw2200 0000:0b:02.0: firmware: requesting ipw2200-bss.fw
[   14.644081] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
```
and the thing is that with fedora 12 it the wireless works out of the box!!
i tried debian no luck and now the ubuntu
and about where i downloaded the packages from the official websites
  [http://prdownloads.sourceforge.net/ieee80211/](http://prdownloads.sourceforge.net/ieee80211/)
[http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.6.tgz?download](http://prdownloads.sourceforge.net/ipw2200/ipw2200-1.0.6.tgz?download)

actually when i got these compiler error, the first thing that got to my mind is the code is not running, then the file is not legit. Downloaded the file some were else, no luck, i even tried an older one

thank you for the response

---

### Post by chili555 on 2010-02-17
It actually looks pretty fine. How did this look?```
rfkill list
```Also, please let us see these:```
iwconfig
sudo iwlist eth1 scan
```Thanks.

---

### Post by abdelhadim on 2010-02-17
Hey man;
here is the the result of the commands you wanted me to try:
```
mohammad@mohammad-laptop:~$ rfkill list
mohammad@mohammad-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

mohammad@mohammad-laptop:~$ sudo iwlist eth1 scan
[sudo] password for mohammad: 
eth1      Interface doesn't support scanning.

mohammad@mohammad-laptop:~$ 




```
if there is anything else you want me to do let me know


Thank you man for the fast response

---

### Post by abdelhadim on 2010-02-19
will some body please help

---

### Post by chili555 on 2010-02-19
We have a real mystery here. the driver module ipw2200 recognizes your card and loads and *dmesg* doesn't show us any errors. However, as *iwconfig* shows, no wireless interface is created. *rfkill* doesn't cause an error, but also doesn't tell us any information at all. Something perplexing is going on under the hood. Is the wireless LED on your T43 on, off or flickering? Do repeated presses of Fn+F5 change it? Will you please do:```
dmesg >dmesg.txt
zip dmesg.zip dmesg.txt
```You will now find a file named dmesg.zip that  you can transfer on a USB key or similar to another computer to post here as an attachment to your reply.

Thanks.

---

### Post by Dr Nick^ on 2010-04-11
hey there,

i got the same problem here, well, not totally the same but looks like it.

Freshly installed the latest ubuntu, did networking with cable, np at all.
and wanted to do some wireless too, but ran into problems with that.

some years ago i did ubuntu too on this same laptop, i know i had some issue with the power switch not functioning on my wireless.

so i checked:
ifconfig, 3 interface (lo,eth0,eth1)
iwconfig, 3 interdace, 1 wireless (eth1)

checked your posts about dmesg etc, all seemed good aswell (same results)

but when i try to power up my wireless i get this:
```
nick@Drnick:~/Downloads/$ sudo iwconfig eth1 p on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device eth1 ; Input/output error.
nick@Drnick:~/Downloads/$ 

```
ans scan gives this:
```
nick@Drnick:~/Downloads/$ sudo iwconfig eth1 scan
iwconfig: unknown command "scan"
nick@Drnick:~/Downloads/$
```

so also fiddling in the dark here :)

---

### Post by chili555 on 2010-04-11
```
sudo [COLOR="Red"]iwlist[/COLOR] eth1 scan
```Let's see, also:```
rfkill list
dmesg | grep -i kill
```Thanks.

---

### Post by Dr Nick^ on 2010-04-11
more notes:
```
nick@Drnick:~/Downloads$ iwconfig eth1 
eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

nick@Drnick:~/Downloads$ 
```

```
nick@Drnick:~/Downloads$ iwlist eth1 power
eth1      Current mode:on

nick@Drnick:~/Downloads$ 
```

```
nick@Drnick:~/Downloads$ iwlist eth1 scan
eth1      No scan results

nick@Drnick:~/Downloads$ 
```

---

### Post by Dr Nick^ on 2010-04-11
```
nick@Drnick:~/Downloads$ dmesg | grep -i kill
[    8.478198] ipw2200: Radio Frequency Kill Switch is On:
[    8.478202] Kill switch must be turned off for wireless networking to work.
nick@Drnick:~/Downloads$ 
```

```
nick@Drnick:~/Downloads$ rfkill list
nick@Drnick:~/Downloads$ 
```

---

### Post by chili555 on 2010-04-11
> eth1      *radio off*  ESSID:off/any 

> Kill switch must be turned off for wireless networking to work.Looks like the wireless switch is nudged over to Off. Nudge it back over to On and your wireless should spring to life.

---

### Post by Dr Nick^ on 2010-04-11
thats where the problem is with me,
he doesnt listen to turn 'on' :P

cant seem to find my old posts some where to watch it back :(

---

### Post by chili555 on 2010-04-11
Is this an ipw2200 driver? What kind of laptop is it?

---

### Post by U-russia on 2011-05-06
Ok, this is an old topic but somebody could find it through search  so, the solution can be not easy  i had such problem and it`s not OS question, because i got it on Linux as on Win systems.  i just had to disassemble laptop and made hard reset(battery) for BIOS, but may be load setup defaults could help or reinstall just the WIFI card.  other solution not worked for me ; hope this can help!   ps: it was about &quot;Radio Frequency Kill Switch is On

---

