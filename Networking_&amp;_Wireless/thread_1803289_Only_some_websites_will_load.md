---
title: "Only some websites will load"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by Lumsdoni on 2011-07-13
Like many people it would seem, I was having issues with only some websites loading.  

Specifically it was only on battery power, and then I realised it was more prevalent when PowerNow had been disabled.

I tried all the solutions on these forums including updating drivers, disabling ipv6 etc but to no avail, but then stumbled upon this solution. From [here]("http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/")

```
Just open a Terminal window in Ubuntu and type

sudo iwconfig

This will list the available wireless interfaces in your system. Now check out your wireless device name here, usually it will be wlan0

Now type the command

sudo iwconfig wlan0 power off

What this essentially does is switch off the power management by Ubuntu for your wireless device. That’s it, and now trying to download a file or watching a youtube video, and you will see that your wireless Internet connection is now back to top speed 

But this is only a temporary solution, because the next time your operating system starts, you will have to run this command again. So we actually need a permanent solution to forever prevent Ubuntu from handling the power management of our wireless device. How to get that done?

All we need to do is edit the file at the path /etc/pm/power.d/wireless – if this file or path does not exist, then you need to create it.

So cd to the directory /etc/pm/power.d and if this directory structure is not there then you need to create it using mkdir.

The create or edit the file called wireless in this folder using the following command in a terminal window

sudo pico /etc/pm/power.d/wireless

NOTE: I prefer pico to gedit, if you are more comfortable with gedit, then simply repace pico with gedit.

The above command opens the wireless file for editing as a root user.

In this file add the following lines and save the file and exit. That’s it.

#!/bin/sh

/sbin/iwconfig wlan0 power off

The above lines tell Ubuntu not to manage the power supply to the wlan0 wireless device. So even after you restart your system, Ubuntu will not control the power supply of your USB wireless device, and there you are your wireless internet speed back to normal forever or at least till you face another issue. - Read more @ http://www.hitxp.com/articles/software/ubuntu-fix-slow-wireless-internet-connection-speed-upgrading-11-04-natty-narwhal/ © hitxp.com
```

---

