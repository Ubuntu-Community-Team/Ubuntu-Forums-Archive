---
title: "This wireless card SHOULD work but..."
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by Tangbuntu on 2010-10-27
I'm running Ubuntu 9.10.  I am pretty useless with Linux having been a Windows user most of my life.  So small words and things for me to copy and paste if I have to use terminal would be muchly appreciated =).

I'm really sorry if this has been answered - I have trawled the forums and tried a few fixes but I can't seem to get any of them to work - lately this one:
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)
which seemed to be downloading madwifi - but when I do this:
```
lspci -v | less
```I still can't see anything that resembles a wireless card.

My card should work with Ubuntu as far as I can see.  It is a TP-Link PCMCIA card - TL-WN610F and according to the Hardware Support Wiki should work out of the box:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link)

I have put the SSID and password into the network connection - but as far as I can see the problem is hardware and not my settings.  I think it may have been working previously but I was having DNS issues (now fixed) - but was able to ping google.  Now I'm not =(.

I'm not sure if that's enough / too much info.  Thanks in advance!

---

### Post by Tangbuntu on 2010-10-27
PS - My Kernel Version etc is:
Linux Peasant 2.6.31-15-generic-pae #50-Ubuntu SMP Tue Nov 10 16:12:10 UTC 2009 i686 GNU/Linux

---

### Post by Tangbuntu on 2011-02-27
[http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/comment-page-1/#comment-918](http://dimitar.me/madwifi-drivers-for-ubuntu-9-10-karmic-koala-or-linux-kernels-2-6-29-and-above/comment-page-1/#comment-918) 

I got the drivers working by downloading the suggested madwifi version (ie not the newest one, that doesn't work) and following these steps.

---

