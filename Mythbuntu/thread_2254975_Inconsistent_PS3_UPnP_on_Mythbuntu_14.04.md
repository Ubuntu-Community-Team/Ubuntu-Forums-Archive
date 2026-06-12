---
title: "Inconsistent PS3 UPnP on Mythbuntu 14.04"
date: 2014-12-01
forum: Mythbuntu
---

### Post by martin41 on 2014-12-01
I just did a clean install of Mythbuntu 14.04 and I am running MythTV 0.27 and have run all the updates.  The issue I am running into, which I never had a problem with on 12.04, is that when I go to stream through the PS3 I have to refresh media servers to see the MythTV box and this doesn't always work.  Sometimes I have to reboot the MythTV box and then scan to get it to work.  On 12.04 with 0.27 it just would always appear on the PS3 without having to do anything.  Has anyone else experienced this or have suggestions on how to get it to work consistently?  I've tried the troubleshooting on the wiki [http://www.mythtv.org/wiki/UPnP](http://www.mythtv.org/wiki/UPnP) with no luck either.

---

### Post by Lester_Burnham on 2014-12-02
Hi,

I have seen my mythbackend UPnP server disappear on many occasions. It used to be pretty solid, back when I was using an upgraded 12.04 to 13.10 machine.

I've been using 0.27 fixes, keeping up to date weekly. Might to see if I can enable a log for mythavserver, as backend log reports everything is ok.

Lester

---

### Post by dannyboy79 on 2014-12-03
if you just can't get it working and you aren't seeing anything in the logs, you could use an alternative solution just to share the media with your PS3, any DLNA or UPnP server should work.

---

### Post by martin41 on 2014-12-03
One thing I forgot to mention is that the old setup used to show on my Samsung Smart TV as well and now I never see it there as an option.  It is like the MythTV is not letting itself be known properly on the network.

---

### Post by martin41 on 2014-12-08
So I think I've solved this issue finally. It doesn't work as well as it did with past versions of Ubuntu but it's about 90%-95% better.

The fix was disabling IPv6

> To check if IPv6 is enabled or disabled, from a terminal window:
  $ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
  0 means it’s enabled and 1 is disabled.
  To disable IPv6
  $ sudo su -
# nano /etc/sysctl.conf
  and add these lines to sysctl.conf file
  #disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
  Save sysctl.conf file with new config, then reboot your system
  # reboot
  Check your system again
  $ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
  Now you should see “1&#8243; means IPv6 has been disabled on your system.



[http://askubuntu.com/questions/346126/how-to-disable-ipv6-on-ubuntu](http://askubuntu.com/questions/346126/how-to-disable-ipv6-on-ubuntu)

---

