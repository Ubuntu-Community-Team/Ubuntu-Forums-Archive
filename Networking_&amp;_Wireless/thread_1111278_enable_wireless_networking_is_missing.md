---
title: "enable wireless networking is missing"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by novecento on 2009-03-30
Hello,

I installed Xubuntu 8.04 a while ago on an old small laptop, wireless is done via a PCMCIA wireless card.   Everything worked fine until last week.  I shutdown the laptop normally and next day he lost the "enable wireless" tick box.  WiFi Radar is installed as well and with WiFi Radar I see the wireless networks around, but can not connect.

I re-installed network-manager without success, cleaned up /etc/networking/interfaces as described here  [http://ubuntuforums.org/showthread.php?t=279212]("http://ubuntuforums.org/showthread.php?t=279212"), but nothing made my button "enable wireless networking" visible again.

Has anybody an idea how to recover and make wlan usable again?

Many thanks and regards,

                    Novecento

---

### Post by TxRxBuffer on 2009-03-30
i have the same exact problem. And where can i find "/etc/networking/interfaces" i am so lost. Thanks in Advance.

---

### Post by novecento on 2009-03-30
I found the issue,  bug in network-manager;

work-around:
- open the network settings window (application/System/network)
- unlock & select Wirless connection & properties
- disable the roaming mode  and save
- enable the roaming mode and save

===>  enable wireless is back again


permanent fix:
Add 
deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) hardy main 
to your packet sources and update to a corrected version of network manager

regards,
        Novecento

---

### Post by novecento on 2009-03-30
Hello TxRxbuffer,

sorry for not answering, but unfortunately I noticed your post after submission of my 2. post.

to edit your interfaces file, you first

1.  open a terminal (in my Xbuntu you go Applications and look for terminal)

2. save the old interface file in case you need it for recovery:
sudo cp /etc/network/interfaces  /etc/network/interfaces.save

sudo will require the first time your password


3. open an editor in superuser mode, I prefer to use pico:
sudo pico /etc/network/interfaces

4. After pico opens and you can edit the file. Please note pico isn't a graphical editor, you cannot use the mouse only the arrow keys are allowed to move arround.

Make your changes or deletions 

with strg + o  you save the file to disk, with strg + x you quit the editor  (on some keyboards strg is labelled as ctrl)

I hope this helps

regards, 
          Novecento

---

### Post by bobrun2000 on 2011-03-09
Hi,

I'm having the same kind of problem. I installed Xubuntu a week ago, the wifi was working fine but it let me down 2 days ago.

I tried different things, for example : 
-  this command```
[INDENT]service network-manager stop
 rm /var/lib/NetworkManager/NetworkManager.state
 service network-manager start
[/INDENT]
```then reboot

- I tried modifying /var/lib/NetworkManager/NetworkManager.state 
from : > 
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true
to : > 
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
then reboot


But nothing worked, any ideas for me? 

Thanks

---

