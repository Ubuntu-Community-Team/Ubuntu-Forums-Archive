---
title: "Can't activate Broadcom STA in &quot;Additional Drivers&quot;"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by charles14618 on 2011-06-27
I have installed Ubuntu 11.04 on my Lenovo B570 in a dual boot config alongside Windows 7. I've downloaded the correct Broadcom STA drivers (the model is Broadcom BCM4313) with another PC, transferred them with a USB stick, installed them with Synaptic and locked the version as was recommended. I've also used the rfkill command to turn off the software block, so both hardware and software switches are OK. 
 
The problem is when I go to the "Additional Drivers" application, it yells at me for not having internet access, and then shows up completely empty. This confuses me because I've manually installed it, so I would think it would show up regardless, but it doesn't. 
 
In a final effort to make it happy, I've brought it to work and connected it through the Ethernet, setting up the proxy LAN settings to let it through the firewall. I can get on the web with Firefox with that method, however when I launch "Additional Drivers", it sits there searching for drivers endlessly, so I'm guessing it's not really connected. 
I feel like I'm really close here - I just need to enable the Broadcom driver, but I can't because "Additional Drivers" won't show it.

---

### Post by amahi on 2011-06-27
oK.[COLOR=Red]You do not need to download the file[/COLOR].remove it!!!

We have 2 ways to install the drivers in Ubuntu 

 I :installation of the synaptic (access internet)

II: [COLOR=Blue]Installation Manual (I'd recommend the second method.)[/COLOR]

You do not need to download the file. You should install the following packages.
[COLOR=Red]dkms[/COLOR] package prerequisites that must be installed. ,install dkms form  Ubuntu 4.11  DVD(cd):
path:
> /pool/main/d/dkms


then:

[COLOR=Red]for Wireless Driver:Go to this track [/COLOR]

> [LEFT]/pool/restricted/b/bcmwl [/LEFT]


install it.
You do not need to download and install another package.!!!

after this,go to terminal and type:(If your network manager is not working, and says unmanaged, or Networking disabled)

> [LEFT]sudo rm /var/lib/NetworkManager/NetworkManager.state[/LEFT]


finally :init 6

---

### Post by josephmills on 2011-06-27
WELCOME to Ubuntu Forums could you please open you termninal and type in ```
lspci -nn 
```then enter then  ```
lsmod
``` then  ```
rfkill list all
``` then paste it all here we will get you going in no time ;)

---

### Post by Josh_1970 on 2011-06-27
I have the same setup (Lenovo B570 installed with Win 7 and dual booting Ubuntu 11.04 installed through the Windows Installation.  

Once (when I connected to router via cable and then disconnected) the wireless worked. Since then, if I disable and re-enable the Additional Drivers, it will detect my network but keeps giving me bad password error even thought I put it in right. (It works just fine in Windows and for all my other wireless devices).  Every boot I have to redo this, but I cannot connect. I have the specs from above if needed, but since I can see the network, I don't think that's the issue.

Thanks,

Josh_1970

---

### Post by charles14618 on 2011-06-27
Thanks everyone, I fixed it in the Ubuntu answers at this link: [https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/162928](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/162928)

Turns out on the Lenovo's you need to blacklist another driver that's on there for an Acer (for some reason): 

During installation it advises internet  connection (via LAN) in order to download the correct wl drivers.  Otherwise it disconnects wl during network-manager installation.
Anyway make sure this package is installed.
[http://packages.ubuntu.com/natty/bcmwl-kernel-source](http://packages.ubuntu.com/natty/bcmwl-kernel-source)
 Have a look there, verify /etc/modprobe.d/blacklist.conf and note bug reports.
[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/161920](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/161920)

---

### Post by charles14618 on 2011-06-27
PS - I love that I fought this for a week and then finally decided to use the Ubuntu community, then solved it in about an hour.  You guys rule.  I'm new to Linux for home use and I'm loving it already.

---

