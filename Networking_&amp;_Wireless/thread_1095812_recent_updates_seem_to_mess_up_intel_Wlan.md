---
title: "recent updates seem to mess up intel Wlan"
date: 2009-03-14
forum: Networking &amp; Wireless
---

### Post by dgrafix on 2009-03-14
"Intel Corporation PRO/Wireless 3945ABG [Golan]"

According to the hardware testing. Was working fine up to a few updates ago on 8.04. I re-installed 8.10 hoping the issue was gone but its the same so some common update seems to have broken proper support for it..

It works but its got very slow access. When i check the connection information in network manager it says 1Mb (rather than 54/100) but the signal is 80-100%
Its almost as if ubuntu thinks its a 1Mb card.

Also nautilus seems to be playing up recently, but could be related to this issue as i use NFS drives a lot.

---

### Post by chili555 on 2009-03-14
Please open up a terminal and do:```
sudo iwconfig wlan0 rate 54M auto
iwconfig wlan0
```Does *iwconfig* now show 54M?> IEEE 802.11abg  ESSID:"mylilrouter"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:9F:CC:E6:EA:7C   
          Bit Rate=**54 Mb/s**   Tx-Power=14 dBm If that fixes it, we can make it automatic.

---

### Post by dgrafix on 2009-03-15
Unfortunately not. In fact, i had a strange error when shutting down last night after several network drop-outs, a message flashed on the screen in textmode about "dazed and confused" and the screen went red before i could read it.

anyway, here is the result of that line:

```
dan@amilo:~$ sudo iwconfig wlan0 rate 54M auto
dan@amilo:~$ iwconfig wlan0
wlan0     IEEE 802.11abg  ESSID:"dansnet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:22:FA:48   
          Bit Rate=2 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=86/100  Signal level:-47 dBm  Noise level=-80 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by chili555 on 2009-03-15
> a message flashed on the screen in textmodeYou might check in */var/log/messages* like this:```
sudo less /var/log/messages
```The 'less' part will allow you to scroll back and forth in the log with the arrow keys to look for unusual messages. You will want to page down until you get to the last several posts before the shutdown, like mine:> Mar 14 21:41:51 LAPTOP60 -- MARK --
Mar 14 21:54:10 LAPTOP60 kernel: [51165.950527] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Mar 15 08:20:00 LAPTOP60 syslogd 1.5.0#2ubuntu6: restart.
Mar 15 08:20:00 LAPTOP60 kernel: Inspecting /boot/System.map-2.6.27-11-genericIf you are pretty sure it actually said 'dazed', you can do:```
sudo cat /var/log/messages | grep dazed
```This sounds very weird! Let's track it down and solve it with the hope that it will solve your speed issue.

---

