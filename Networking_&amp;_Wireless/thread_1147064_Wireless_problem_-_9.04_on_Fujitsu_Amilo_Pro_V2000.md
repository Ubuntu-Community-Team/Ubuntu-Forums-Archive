---
title: "Wireless problem - 9.04 on Fujitsu Amilo Pro V2000"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by cartes on 2009-05-03
Hi, I have recently installed Ubuntu 9.04 on my laptop. I am really happy I made the switch but I have a problem:

The wireless button wouldn't work but with a bit of googling I tried [http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/](http://odzangba.wordpress.com/2007/05/15/intel-corporation-prowireless-2200bg-amilo-pro-v2000-ubuntu/) (in my case the the directory was modprobe not modprob), i.e.

edit /etc/modules and add: fsam7400 on a new line;
created /etc/modprobe.d/options with: options fsam7400 radio=1

This works from shutdown but not when resuming from suspend.

I have tried: [http://aimzster.page.ph/?p=590](http://aimzster.page.ph/?p=590) but editing /etc/default/acpi-support so that STOP_SERVICES=&#8221;networking&#8221; hasn't worked for me.

Is there an equivalent to /etc/modprobe.d/options that I could edit/create that works for resume?

Any help appreciated.

---

### Post by Til_Valhall_vi_drar! on 2009-10-05
allright i know that this is an old thread, but i got this laptop and i can give some very primitive steps in how to get wireless working, but not how to make it work after reboot and all that, because im really a gentooist.

The modules you need is: ipw2200; wistron_btns

The firmware files you need is: ipw2200-bss.fw; ipw2200-ibss.fw; ipw2200-sniffer.fw

The userland tools (user programs): wireless-tools (iwconfig iwlist...)

so you need to insert the modules:

```
sudo modprobe ipw2200 && sudo modprobe wistron_btns
```

Note: the wistron_btns is for the wireless button, i really don't know why it is needed, but it is.

check if you got the firmware: ```
sudo ls /lib/firmware/ipw2200-*
```

Acutally, you should have noticed if you don't have them when you injected the module "ipw2200".

Note: You normally only needs the ipw2200-bss.fw, thats for connecting to regular access-points. The other two is for Ad-hoc and sniffing.

Now, go to /sys/class/net/eth1/device. Really, if you don't know how to do this, then figure it out. Now check if the RF kill switch is on:

```
sudo cat rf_kill
```

if its 0, then its off (thats good). If its 1, then ```
sudo printf "1">rf_kill
```. if its 2, then press the wireless button. well you figure it out.

Optional: if you want the led to be on, do ```
printf "1">led
```

Now, to scan for networks, do ```
sudo iwlist eth1 scan
```

And to associate to a ap, do: RTFM ```
man iwconfig
``` or STFW [http://www.google.com/](http://www.google.com/).

---

