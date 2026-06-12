---
title: "i cant create P2P network  (ubuntu 11.04)"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by mohdforever on 2011-05-01
hi guys 
i've a strange problem with my new OS (ubuntu 11.04)

my wireless card is working well .... but (11.04) is not able to create an ad-hoc (peer-to-peer) network successfully.

i have made a P2P network by (ubuntu 10.10) ... it had worked well ... and i could sharing my internet and files to other computer .

now, the problem is i'm able to create a new ad-hoc network but it doesn't listed in other computer. 

anyone help me ????

pleasssssssssssssse

:(

---

### Post by lores on 2011-05-17
Same problem here.

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

lsmod|grep ath
ath9k                 118238  0 
mac80211              294370  1 ath9k
ath9k_common           13851  1 ath9k
ath9k_hw              323077  2 ath9k,ath9k_common
ath                    23773  2 ath9k,ath9k_hw
cfg80211              178528  3 ath9k,mac80211,ath

---

### Post by mohdforever on 2011-05-17
please we need some help

...............

i'm going to install ubuntu 10.04 (LTS) instead of 11.04 
it's  a bad distribution

---

### Post by lores on 2011-05-17
I agree that 11.04 was/is not ready for release. Perhaps the Ubuntu developers should reconsider the tightness of the six months' release cycle and possibly loosen it a bit...

---

### Post by mohdforever on 2011-05-19
that's right 

i agree with you

---

### Post by Elline on 2011-05-19
So is it a common problem?
I have never made ad-hoc networks before and now think I'm doing something wrong.

Just like in many wiki entries and articles I:
1) Open the network manager.
2) Create new wireless, name it UbuntuAdhoc and set SSID the same.
3) Change mode to Ad-Hoc.
4) Save it without encryption (just to see it works).

Is it right? I thought I shall now see an UbuntuAdhoc from another computers, but it's not the case. Or did I does something wrong? 

Please reply, it seems that I am even less experienced in this than you. :)

---

### Post by lores on 2011-05-19
Yes, you should see it on other computers as soon as you choose to "connect" to it on your Ubuntu PC.

A shortcut to creating an AdHoc would have been clicking the NM and choosing "Create new network".

Are you using Ubuntu 11.04? If so, then you probably are affected by this bug, too (this function used to work on earlier Ubuntus).

---

### Post by Elline on 2011-05-20
I didn't know about connecting to itself. Yes, I am using 11.04 and only way I found to connect to...itself was to choose "Connect to hidden wireless network" in NM and then choose UbuntuAdhoc. Well, then the network applet appears to be connecting (showing a spinning circle) and after a while it throws me a notification "**Wireless network** disconnected". That's all.

I saw some instructions [here]("http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html"), I know they can be outdated, but what about IPv4 settings? Doesn't it need to be set? As it says:

> Click the Add button and enter a local IP address, Netmask and Gateway, i.e. 192.255.0.1, 255.255.255.0, and 1.1.1.1 respectively.

By the way have you considered creating an Access Point? I was struggling with it yesterday but some things working. May be of any help.

---

### Post by Elline on 2011-05-20
There is some some progress I have.

I followed [this]("http://ubuntuforums.org/showpost.php?p=10193794&postcount=6"), turned on sharing and NM at once connected to itself.
Yes, it shows me that network is active but... I can't see it from another device. Oh, snap.

It's a little bit offtop but I'm curious to ask somebody with such an experience. Will it be possible to share an internet connection through ad-hoc and at a time have a file sharing possibility between these computers?

---

### Post by Elline on 2011-05-20
Well, now I followed [these]("http://www.ubuntugeek.com/creating-an-adhoc-host-with-ubuntu.html") instructions (in brief: to add manually IPv4 settings as such: 192.255.0.1, 255.255.255.0, 1.1.1.1). 
And the network seems to be wisible! But...it's not sharing any internet.

When on a netbook (which is only wireless), when executing "dhclient wlan0" it sends some requests but fails to achieve an IP and connection.

In fact I have no NM on this netbook, only use minimal environment is it the problem? I thought when you connecting to a wireless network you need to achieve an IP through DHCP.

---

### Post by mohdforever on 2011-05-22
yes, ad-hoc access point offer you to sharing files and internet.
but in ubuntu 11.04 we have big problem to create ad-hoc access point

so, you can't sharing file and internet through you network
moreover, you can't see your network from another device.

that's the problem

---

### Post by Elline on 2011-05-22
Ok, it's sad but thanks for your reply!

---

### Post by omelette on 2011-08-05
I wish I had started with a "ad-hoc" search for the problem that I and the others commenting here are experiencing, rather than going off on a "DHCP" tangent like I did - it would have saved me a great deal of time!  Anyway, it's some comfort to know that it's not just me...

For the record, with 10.04 and Natty 11.04 installed side-by-side, I am able to switch to and fro between them.  Ubuntu 10.04's wireless works flawlessly. I see from several forums that the problem also seems to be confined to Ath9k wireless chipset.  Attempting to eliminate NetworkManager as the culprit, I have just removed it completely from 11.04, installing Wicd in it place.  No difference unfortunately, so the problem seems to be manifesting 'deeper down'...

Does anyone know if Ubuntu 11.10 and the Ath9k chipset suffer from the same dilemma regarding ad-hoc connections?

---

### Post by gyussz on 2011-08-05
As I experienced the problem is actually in the 2.6.38 kernel series. Installing the 2.6.39 kernel, from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) fixes the problem, but you may experience some other problems with it as it has built for oneiric, not natty.

---

### Post by omelette on 2011-08-08
Damn, nearly missed your post!

**I have just installed kernel 2.6.39rc4 and can confirm that it fixes the ad-hoc problem!!! :D**

Thanks for that!  I had tried the latest 2.6.38.11 in the repository but it didn't have an effect.  btw that link you posted has Natty images now so someone must have updated it since you were there.  They're still release-candidates though so you are probably right about the possibility of something else getting fcuked up. :)

---

### Post by omelette on 2011-08-12
I have just made a disturbing discovery.  Installing 2.6.39_rc4 fixes the ad-hoc wireless problem alright but unbelievably, **_it also deactivates the UFW firewall each time you reboot!!!_**  And when you re-enable UFW, your internet is stopped dead! I have also removed & installed it several times just to be sure - with 2.6.38 (current kernel) on rebooting, UFW is activated & internet working.  Install 2.6.39_rc4 and UFW is disabled on restarting and enabling UFW results in no internet access.

Needless to say, this is completely unacceptable. I'm going to have to switch back to F15 for my ad-hoc internet sharing until someone fixes this thing.  Not happy about that either. The thing I've noticed when Fedora 15 is ad-hoc sharing is that despite them forcing Selinux down your throat, the default firewall configuration leaves 4-5 ports open for the world to probe, whereas UFW by default returns an almost perfect score with the Shields Up firewall test.  It actually fails but only because it responds to ping.  Very easy to fix, then it returns a perfect score.  Check it out below.

[http://www.grc.com/]("http://www.grc.com/")

---

### Post by omelette on 2011-08-12
After I calmed down I went and installed **v3.0.1-oneiric** which is the latest kernel build found at the above site.  ad-hoc sharing works and so does UFW - so all is right again with the world. :)

Edit  That was a bit premature, this seems to have the same problem!  Jesus wept.....

---

