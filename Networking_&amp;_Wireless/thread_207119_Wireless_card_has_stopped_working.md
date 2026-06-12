---
title: "Wireless card has stopped working"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by katana6434 on 2006-07-01
Hi

I hope you can help me.  I am a complete newbie when it come to Linux.

I have decided to try and get to grips with Linux and have chosen Ubuntu to play around with.  I installed it yesterday and everything went fine and everything worked, including my wireless card (Cisco Aironet 340 I believe).

I turned the system on this morning and the card is not working.  In fact I don't seem to be able to see represented on the system anywhere.  It origanally installed as eth2, and now in Network Settings I only have eth0 and eth1 (these are normal nerwork ports that I don't use).

Does anyone have any idea how to get my wireless card back.  As I said earlier I am completely new to Linux and I have no idea where to begin.  

Any help would be great.

Cheers

---

### Post by katana6434 on 2006-07-02
Doesn't any body have any help they can offer....

---

### Post by MacLeod_1980 on 2006-07-03
Hi there, I don't know if this will help but...

I have a Averatec 3250 with a Ralink RT500 chip for wireless, my wireless network is restricted with WEP encryption. I had some issues with my actual chipset, initially I couldn't even load the Network GUI without it crashing when I tried to edit wireless config. The problem was resolved by removing an IRQ conflict between the wireless and monitor - weird huh - but thats another story.

Once I was able to edit the config I could setup my wireless configuration, with WEP key and all (I am using ascii not hex). I was still unable to connect... through my searching I found this [post]("http://ubuntuforums.org/showpost.php?p=1153031&postcount=14") from this [thread]("http://ubuntuforums.org/showthread.php?t=187571&highlight=network+manager+wep") which references this [guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")...

Unfortunately the post I initially refered to with regards to specifying restricted within /etc/network/interfaces was not infact the solution... but a step towards it.

I specified MY wireless (ra0) to be restricted through the terminal 

**sudo iwconfig ra0 key restricted**

retried my connection and it worked. After some messing around I found that I needed to specify 'restricted' differently within interfaces. So I opened up interfaces...

**sudo gedit /etc/network/interfaces**

searched for MY wireless interface (ra0) and eddited my encryption key line to look like

**wireless-key restricted s:XXXXXXXXXX**

Alternate to what is descibed in the aforementioned guide, [Config File section]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#head-f55187f916615b9ab7ecdda4431b3642e533e74e"). So if someone wants to look into this that would be good - as I am not sure how to officially log my findings??

I hope this is of some use to someone, as it took me a while to find my solution but I got there, and I am a noob at linux.

**NEVER GIVE UP TRYING**

---

