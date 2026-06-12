---
title: "random crash: Centrino PRO/Wireless 2200BG"
date: 2006-02-25
forum: Networking &amp; Wireless
---

### Post by toonmuylkens on 2006-02-25
Hello,

I have a problem with wireless internet in ubuntu.
It all works fine for 10->20 minutes. But then the system just freezes/crashes.
I can't give any more input. Only ctr alt system request (for unmounting the disks and rebooting) works.

This is the way I start going wireless:
{
echo 1000 > /sys/class/firmware/timeout
rmmod ipw2200
modprobe ipw2200
#comment: I added the 3 lines above, because it might have fixed it... but it didn't
ifconfig eth0 down # the wired network is going down
ifconfig eth1 up
iwconfig eth1 key 1234567891 #it's a WEP key
dhclient eth1 # the router privides a dhcp server
}
the network works, without packet loss and at great speed

One time I was working in console mode when it happend and I was able to see some output from the kernel... but nothing seems very usefull... it said: crashed while using this modules: .... (all my modules, so not a specific one)

I am using this modules for going wireless:
{
root@asus:/home/toon # lsmod |grep ipw
ipw2200                92680  0
firmware_class          9472  1 ipw2200
ieee80211              27012  1 ipw2200
ieee80211_crypt         5636  2 ipw2200,ieee80211
}       

also: i found this on another forum: can it be the problem? also what is the stack size for ubuntu kernels?
{
Some drivers (especially for Intel Centrino PRO/Wireless 2200BG and 2100) need significant stack space. Kernel stack size on Windows is generally 12k (3 pages) but only 8k - sizeof(task_struct) = about 6.5k on Linux. Stack overflows, although rare but still theoretically possible can lead to semi-random crashes. This is even more likely to happen when using kernels compiled with CONFIG_4KSTACKS (which is the default in Fedora Core 2). An experimental workaround for this can be enabled by running "dldrconfig --enable-workaround=stack" but the safest solution is to increase the kernel stack size to 16k. (see the download section at [http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/) for available pre-built 16K kernel packages and patch options).
}

cheers
toon

---

### Post by toonmuylkens on 2006-02-26
I have come to some new insight:
I don't think the system crashes because of the stack size being to small.
I have searched for some answers on a few forums and I think stack size can only be a problem when using a windows driver with 'ndiswrapper'.
But I use native linux drivers.

But I seem to be the only one with this problem, because I find very little about this subject on the net.

If you have a centrino processor with wireless build in, please tell me how you get it to work

thanks
toon

---

### Post by toonmuylkens on 2006-02-26
Problem solved!!

I'll explain how I fixed it:
I have recompiled the ipw2200 and ieee modules
and that's all :-)

[http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)
---> this tutorial will explain you how to recompile the modules. I used a more recent version though.

---

