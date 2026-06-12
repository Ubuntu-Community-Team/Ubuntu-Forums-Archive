---
title: "Ubuntu 9.04 - Can't connect to wireless, no idea why"
date: 2009-05-28
forum: Networking &amp; Wireless
---

### Post by whirli on 2009-05-28
About an hour ago everything was fine and I could connect to the internet. Then, after a bit of googling to learn how to do it, I changed my screen resolution by editing /etc/X11/xorg.conf (I think that was its name?). After editing that file, I restarted the laptop, but after that it hasn't been able to connect to wireless. 

When I click on the wireless icon the dropdown menu has three choices, "Wired network," "disconnected," and "VPN Networks >". The first two are in unclickable grey text. Was it the screen resolution changing that broke something? What did I do?

A friend told me to type iwconfig in the terminal, which I did, getting the messages "lo   no wireless extensions," "eth0   no wireless extensions," and "pan0   no wireless extensions". Is that normal?

Sorry for incoherency and/or stupidity, I'm completely new to this.

---

### Post by ixpl on 2009-05-29
/etc/init.d/networking restart  may work for you, won't hurt anyway.  you could also try    sudo wlanconfig ath0 create wlandev wifi0 wlanmode managed  This is what i have to do to get my card in and out of monitor mode. You may need to replace ath0 with wlan0

---

### Post by whirli on 2009-05-29
When I type /etc/init.d/networking restart it says
"ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
ifup: failed to open statefile /var/run/network/ifstate: Permission denied
[fail]"

I can't do the second of the things you suggested because "the problem 'wlanconfig' is currently not installed"... I guess I need an internet connection to install it...

---

### Post by saisai on 2009-05-29
use sudo
sudo /etc/init.d/networking restart

---

### Post by whirli on 2009-05-29
It says "* Reconfiguring network interfaces...                                   [ OK ] " but then nothing happens even after I reboot...

I think the problem is that it doesn't see the wlan0? Right now I'm using Ubuntu straight from the disk--live session user--and when I type iwconfig now I get
```

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"74D17"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:01:FA:7B:A8   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=48/100  Signal level:-72 dBm  Noise level=-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```

Before it was only lo, eth0, and pan0... How do I make it see the wlan0? Why does it work here on the live session user account from the disk, but not on the actual installed OS?

---

### Post by whirli on 2009-05-29
More information: After googling some more, I found that someone with a wireless problem similar/maybe identical to mine posted a thread on this forum about a year ago, [http://ubuntuforums.org/showthread.php?t=878508](http://ubuntuforums.org/showthread.php?t=878508) (they were a lot more coherent than me in explaining the problem lol).

However, they ended up buying a new adapter entirely. Is there any actual fix for this problem? IMO, it's especially weird how wireless works fine when i use ubuntu straight from the disk, but not on my account. Maybe I should just reinstall ubuntu?

---

