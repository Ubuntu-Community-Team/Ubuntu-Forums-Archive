---
title: "really slow download speed"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by PhunnyJesta on 2009-12-09
just installed ubuntu 9.10 for dual OS combo with windows XP. Having trouble with my internet connection now. In windows xp i get my full 1.5mbps connection but in Ubuntu, im only getting 0.2 to 0.4mbps


running tests on [URL="http://www.speedtest.net/"]http://www.speedtest.net/
[/URL]
*edit* my ping is a bit better, it dropped about 60ish

---

### Post by PhunnyJesta on 2009-12-09
*bump* plz i really need help

---

### Post by DavidFourer on 2009-12-10
> **PhunnyJesta said:**
> just installed ubuntu 9.10 for dual OS combo with windows XP. Having trouble with my internet connection now. In windows xp i get my full 1.5mbps connection but in Ubuntu, im only getting 0.2 ... [www.speedtest.net/](www.speedtest.net/)

I disabled ipv6 protocol.  There are many threads on this.

>>  Edit /etc/default/grub file
gksudo gedit  /etc/default/grub
>>  Change
GRUB_CMDLINE_LINUX_DEFAULT=”quiet splash”
>>  to
GRUB_CMDLINE_LINUX_DEFAULT=”ipv6.disable=1 quiet splash”
>>  Save and exit the file
>>  Update the grub from the command line
sudo update-grub

Or do it from menus.
I have not done this but it looks right in my Karmic install.
System>preferences>network connections.  Highlight the connection used and select edit.  Click ipv6 settings and select "ignore"

I tried [http://www.speedtest.net/](http://www.speedtest.net/)
It says I am getting 5 mb/s download.  I never got over 1.5 in real life.  I got only 0.1 mb/s (100 kb/s) on a recent download from Ubuntu repos, before looking into the ipv6 thing.  I am anxious to see what I get now from real downloads.

I wonder if there is a site I can go to and just download a file and see what happens.

---

