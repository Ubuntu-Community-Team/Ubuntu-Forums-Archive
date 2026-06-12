---
title: "Broadcom 4311 - Ubuntu 12.04 - No dice."
date: 2012-05-02
forum: Networking &amp; Wireless
---

### Post by Roasted on 2012-05-02
Once again here we are with another Broadcom issue...

While my Intel wireless card is on its way, I'd at least like to utilize some wireless connectivity for the brief time I'll be utilizing this Broadcom card. When I fired up 12.04, the STA driver was installed by default. A quick Google revealed dozens of people saying remove that driver and run the following:

$ sudo apt-get update
$ sudo apt-get install firmware-b43-installer
$ sudo apt-get remove bcmwl-kernel-source
$ sudo reboot

Buuuuuut... there's a catch. It didn't work for me. No wlan entry shows up in ifconfig, but I can see the wireless card under lspci. Any thoughts on this?

---

### Post by oddhack on 2012-06-10
> **Roasted said:**
> Buuuuuut... there's a catch. It didn't work for me. No wlan entry shows up in ifconfig, but I can see the wireless card under lspci. Any thoughts on this?

Did you get this sorted out? I just dealt with the problem under Ubuntu 12.04 on a Dell Latitude D620 with the Broadcom 4311 and found that I actually needed to reboot *twice* before the wireless device showed up (I did not try and analyze the logs to figure out why, but... shades of Windows!).

After the second reboot, the device showed up as wlan0 - it had been eth0 in Ubuntu 10.04. Seems to be working now and it does show up in both ifconfig and iwconfig.

I am confused as to where the actual network devices have gone to in 12.04 - there is neither a /dev/wlan0 nor a /dev/eth0 for the wired port - but as they're both working I won't get obsessed about it.

---

### Post by Roasted on 2012-06-10
> **oddhack said:**
> Did you get this sorted out? I just dealt with the problem under Ubuntu 12.04 on a Dell Latitude D620 with the Broadcom 4311 and found that I actually needed to reboot *twice* before the wireless device showed up (I did not try and analyze the logs to figure out why, but... shades of Windows!).

After the second reboot, the device showed up as wlan0 - it had been eth0 in Ubuntu 10.04. Seems to be working now and it does show up in both ifconfig and iwconfig.

I am confused as to where the actual network devices have gone to in 12.04 - there is neither a /dev/wlan0 nor a /dev/eth0 for the wired port - but as they're both working I won't get obsessed about it.

Nah, I never got it working. I ended up buying an Intel Wifi N card online for a matter of 11 bucks. Considering the previous one was wifi G, didn't work, and was driving me crazy, 11 bucks to bump it to wifi N (N wireless at home) and know it would work (since Intel has traditionally had great Linux support) I figured it was a win win.

Haven't looked back since.

(hope you're taking notes, Broadcom)

---

