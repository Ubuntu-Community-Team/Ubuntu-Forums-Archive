---
title: "iwlagn issues (deep sleep, device not ready)"
date: 2012-02-10
forum: Networking &amp; Wireless
---

### Post by lejono on 2012-02-10
My wireless card, which has been working fine for ages, stopped working recently (presumably due to some automatic update).  I'm using Ubuntu 11.04.   My wireless card is an Intel(R) Centrino(R) Advanced-N 6200 AG, and I have a Lenovo X201.   The wireless device connects fine initially, but after about 10 minutes, disconnects and has trouble reconnecting.  Then it just goes dead, and network manager doesn't report any visible devices, or doesn't even show the existence of the wireless card.  After rebooting, it works fine again for another 10 minutes.  Turning on and off wireless in network manager sometimes corrects the problem once or twice, but then even this doesn't work. 

 iwlagn is reporting the following types of errors in kern.log: 

"iwlagn: Request scan called when driver not ready"
"iwlagn: MAC is in deep sleep!"
"iwlagn: Unknown hardware type"
"iwlagn: Unable to init EEPROM"
"iwlagn: probe of 0000:02:00.0 failed with error -2"

etc.

Googling reveals various people with similar problems, and a few bug reports which may be related, but just get closed, but no solution.  Any ideas???

J

---

### Post by lejono on 2012-02-15
I installed linux-backports-modules-cw-2.6.39-2.6.38-13-generic which corresponds to my kernel version.  That seems to have helped, in terms of sometimes I can go a few hours before my wireless dies and I need to reboot.

Anyone know a proper solution??

---

### Post by chili555 on 2012-02-15
> Anyone know a proper solution??*KNOW* a proper solution? No. Willing to work on it with you? Yes.

Is power management on or off?```
iwconfig
```> wlan0     IEEE 802.11abg  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:13:10:62:88:77   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [COLOR="Red"]Power Management:off[/COLOR]
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:89   Missed beacon:0Is the behavior improved with 802.11N disabled?```
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
```

---

### Post by lejono on 2012-02-19
Thanks [chili555]("http://ubuntuforums.org/member.php?u=35909"), much appreciated!  And sorry about the delay, I had given up hope and wasn't checking the forum.  Will do that now.  Power management is off.  Disabling 802.11N doesn't seem to make any difference....

---

### Post by chili555 on 2012-02-19
I'm sorry; I am out of ideas. All I can suggest is to keep Googling for "iwlagn: MAC is in deep sleep!." Like you, I have seen the complaint many times but haven't seen the solution.

---

### Post by griffjon on 2012-03-12
Bump - same problem, with an Intel 5300 and a Lenovo y550, but otherwise exact same symptoms, and in 11.04 .  modprobing does nothing, but rebooting so far always restores wifi.

This bug appears related: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/903517](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/903517)

Installing backports may help: [http://ubuntuforums.org/showthread.php?t=1783456](http://ubuntuforums.org/showthread.php?t=1783456)

---

### Post by lejono on 2012-04-08
I've upgraded to the 3.0.0-17-generic kernel, and Ubuntu 11.10, and still have the same issues.  One thing I've discovered is that the problem kicks in if the signal is weak.  It's pretty frustrating that this issue is being widely reported for some time, but with no solution...

---

### Post by Light-kun on 2012-05-18
Hi.
have similar problem with :
"iwl3945: Intel(R) PRO/Wireless 3945ABG/BG"

rmmod+modprobe did this (the interesting part):
iwl3945 0000:06:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
iwl3945 0000:06:00.0: EEPROM not found, EEPROM_GP=0xffffffff
iwl3945 0000:06:00.0: Unable to init EEPROM
iwl3945 0000:06:00.0: PCI INT A disabled
iwl3945: probe of 0000:06:00.0 failed with error -2

I have  Ubuntu 12.04 with 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:52 UTC 2012 i686 i686 i386 GNU/Linux

Should I start another topic?

---

### Post by chili555 on 2012-05-18
> Should I start another topic?You certainly could; however, looking at this forum and Google, I'm not confident there is an answer as I said above.

---

### Post by lejono on 2012-08-01
After massive frustration trying to fix the problem, it turns out to be a hardware issue.  It got to the point where it was happening every half hour, so I decided to boot up windows (which I never do), and wouldn't you know it, but it was happening there as well. There are lots of similar reports, so it may be a common hardware issue with this wireless card.  Got a replacement from Lenovo, and bang, problems solved.

---

