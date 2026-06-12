---
title: "Very slow wifi in Ubuntu 11.04 RT73usb."
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by lookihavethis on 2011-04-28
Hi, im new here, i installed Ubuntu 11.04 Amd64 today (and  have tried ubuntu 10.10 in the past and had the exact same issue.).
I had this problem with the wifi, as it recognizes the adaptor (tplink321g) but it cant connect to the right speed. This is my only problem with ubuntu now.
If anybody else is having the same issue, and most of all if anybody has the solution to it. 

Thanks in advance!

---

### Post by JoZ3 on 2011-04-30
Same problem here but I'm update from 10.10... wifi very slow... wired connection work fine

---

### Post by JoZ3 on 2011-04-30
Same problem here with wifi...

and pollmar69 eh???

---

### Post by cisoprogressivo on 2011-05-03
Same problem here with D-Link DWL-G122.
Revert back to 10.10 works.
Install ndiswrapper works, but freeze the sistem after a while.

---

### Post by chili555 on 2011-05-03
Some devices have a conflict; they are grabbed by both rt73usb *AND* rt2500usb. We need to do:```
lsmod | grep -e rt2 -e rt7
```Let's see if rt2500usb is in there. If so, we need to blacklist it.

Who's first? Let's see your details.

---

### Post by Elfy on 2011-05-03
> **JoZ3 said:**
> Same problem here with wifi...

and pollmar69 eh???

Please report posts like this - it's spam.

---

### Post by cisoprogressivo on 2011-05-03
> **chili555 said:**
> Some devices have a conflict; they are grabbed by both rt73usb *AND* rt2500usb. We need to do:```
lsmod | grep -e rt2 -e rt7
```Let's see if rt2500usb is in there. If so, we need to blacklist it.

Who's first? Let's see your details.

```
ciso@Fuji:~$ lsmod | grep -e rt2 -e rt7
rt73usb                26854  0 
rt2x00usb              19693  1 rt73usb
rt2x00lib              39075  2 rt73usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
crc_itu_t              12627  2 rt73usb,firewire_core

```

rt2x00usb seems to be loaded by rt73usb, right?

---

### Post by chili555 on 2011-05-03
> rt2x00usb seems to be loaded by rt73usb, right?Yes; that's OK, it's a dependency of rt73usb. We do not see rt2**5**00usb. You might try:```
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
```If it helps, we can write a simple conf file to make it permanent. Please post back so your colleagues will learn.

---

### Post by cisoprogressivo on 2011-05-03
> **chili555 said:**
> Yes; that's OK, it's a dependency of rt73usb. We do not see rt2**5**00usb. You might try:```
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
```If it helps, we can write a simple conf file to make it permanent. Please post back so your colleagues will learn.
I unplugged the wifi key.
I removed the module and loaded with nohwcrypt=1, than plugged the key.
Same problem.

---

### Post by DaimonPl on 2011-05-03
For me it doesn't work at all with ubuntu 11.04. DHCP timout...

---

### Post by chili555 on 2011-05-03
Sorry; I'm out of ideas.

---

### Post by edgar2705 on 2011-05-03
same problem (dhcp timeout), i think we must report a bug

one of this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773599](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/773599)

---

### Post by jarkko jaatinen on 2011-05-04
I have RT2500 Ath9285 both works perfectly well ubuntu 10.10 rt2500 in this time in linux mint. But 11.04 its even slower than my huawei 1mb  3g connection .Problem might be in natty. Wired connections works perfectly. .And TL-WN cant remember numbers TP-LINK usb wireless card works fine . well better than nothing one out of three.:)

---

### Post by ghormax on 2011-06-18
I have a similar problem (slow WLAN) and this read out:

> rt73usb                26854  0 
crc_itu_t              12627  1 rt73usb
rt2500usb              22621  0 
rt2x00usb              19693  2 rt73usb,rt2500usb
rt2x00lib              39075  3 rt73usb,rt2500usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211


so what does it mean when I also have rt2500usb ?

thanks for your help

---

### Post by chili555 on 2011-06-18
> so what does it mean when I also have rt2500usb ?It means you probably have a driver conflict. You might have better luck if you blacklist it. Alternatively, if that doesn't work correctly, blacklist rt73usb and un-blacklist rt2500usb. The only way is to try:```
sudo su
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and give us a report so the searchers will learn.

---

### Post by ghormax on 2011-06-20
Unfortunately, no change. Last week, my WLAN speed was much better! Could it have been an update?

I have recently fixed the channel of the router because the web had disconnected from time to time. Should I undo that change? 

Also I tried to install the backports which was recommended on another site but they seem to be no longer part of synaptic (ie I cannot install them via sudo apt-get)

```
E: Unable to locate package linux-backports-modules-wireless-natty-generic

```

---

### Post by zoubidoo on 2011-07-19
I'm getting both rt73usb and rt2500usb loaded.  I get downloads of around 10-15kb/s while a different wireless adaptor gets 400+kb/s

```
lsmod | grep -e rt2 -e rt7
rt73usb                22434  0 
crc_itu_t               1371  1 rt73usb
rt2500usb              18141  0 
rt2x00usb               9703  2 rt73usb,rt2500usb
rt2x00lib              27509  3 rt73usb,rt2500usb,rt2x00usb
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126144  2 rt2x00lib,mac80211
led_class               2864  2 rt2x00lib,acer_wmi

```

Platform: Ubuntu 10.04.3 LTS, kernel 2.6.32-32-generic 32 bit.

Wireless adaptor: Bus 001 Device 002: ID 050d:705a Belkin Components F5D7050A Wireless Adapter

I unloaded rt2500usb (rmmod) and am getting high download speeds once again. This module clearly needs blacklisting on my system.

Many thanks to chili555 for revealing the problem!

Is there an existing bug report to add some heat to?

---

### Post by chili555 on 2011-07-19
> Is there an existing bug report to add some heat to?I haven't seen a recent, on-going bug report. You could certainly register and start one: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

I'm glad it's working!

---

### Post by zoubidoo on 2011-07-19
Bug report created, see [https://bugs.launchpad.net/ubuntu/+bug/812981](https://bugs.launchpad.net/ubuntu/+bug/812981)

Not sure which package to assign it to, so I didn't specify one.

A minor correction to my last post: removing the module may not be sufficient, a reboot may be necessary.

---

### Post by zoubidoo on 2011-07-20
I wonder if there is something else wrong.

I'm still getting bandwith fluctuation that doesn't look like normal variation: Less than 20kb/s most of the time and occasional peaks of 600kb/s.  Other wifi adaptors have a far more constant bandwidth.

Any ideas?

---

### Post by t1010011 on 2011-07-24
Just posting to say I have the same issue...

natty amd64
2.6.38-11-generic
D-Link DWA-110
only rt73usb is loaded
and with ndiswrapper, blacklisting rt73usb and using dr71wu the system freezes after a while...

please if anyone has a clue in how to fix the rt73usb driver or the ndiswrapper freezing...

---

### Post by ctsdownloads on 2011-12-27
Amazes me no one has mentioned this. Not that most people realize the real problem -- heat.is.a.problem.

I am not kidding. Try this: next time it's bugging out, feel the dongle. Feel a bit hot to the touch? Here's the million dollar tip. Cooling pad. While newer 802.11n Ralink dongles come with cradles due to Linux driver heat issues, the old 802.11g ones don't. If an extension cable isn't enough, a cooling pad for the notebook does indeed make a HUGE difference with both speed and overall stability. In other words, no more failed page loads and other related hassles.

Another huge tip (using OpenDNS): 

$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ gksudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
Restarted networking or the PC

What that does, is make it so you're not using your router's DNS settings. While rarely an issue, using my dns settings locally instead of my DNS showing up as my router IP under network manager. Heat and local DNS settings. RT73usb works just fine and has for years. ;) Good luck

*Side note: Anyone who tweaked stuff -- I make zero promises. RT73usb works out of the box and has for years. Junk like ndiswrapper is a fast track to a migraine. I'd start completely fresh -- test the laptop cooling pad with RT73usb using a LiveCD -- this way, you know I am right before bothering to reinstall to undo all of the stuff that may have been tweaked already. ;)*

---

### Post by edras on 2012-02-14
> **chili555 said:**
> Yes; that's OK, it's a dependency of rt73usb. We do not see rt2**5**00usb. You might try:```
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
```If it helps, we can write a simple conf file to make it permanent. Please post back so your colleagues will learn.

It worked fine! Thank you!

---

