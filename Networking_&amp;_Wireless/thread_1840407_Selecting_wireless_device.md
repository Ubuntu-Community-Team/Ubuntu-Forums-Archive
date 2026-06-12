---
title: "Selecting wireless device"
date: 2011-09-07
forum: Networking &amp; Wireless
---

### Post by BobvanderPoel on 2011-09-07
I have a acer laptop with builtin broadcom wireless. With the a bit of downloading I got the internal device working just fine with Natty.

But, in the time that it didn't work I got a USB stick interface. Again, this works fine. Just a matter of plugging it in. 

Now I have a problem :) The plug in has a bit better speed and range. So, there are times I'd like to use it (esp. since I can extend the antenna on a usb cable and hang it out a window). But, now, when I plug in the stick I end up with 2 active networks (wlan0 and wlan1).

So, the question is: How can I selectively disable one network. I tried doing "ifconfig wlan0 down" and that worked for a few seconds, but then the internal net came back up. 

Even better would be a config which says "if the usb is plugged in turn off the internal device".
 
Or if I do need to have both active ... can I select a preferred path to use? I have no idea if the system is actually reading data from both devices (timing tests suggest that only the internal is being used, but I'm not sure).


Thanks.

---

### Post by nm_geo on 2011-09-07
> **BobvanderPoel said:**
> I have a acer laptop with builtin broadcom wireless. With the a bit of downloading I got the internal device working just fine with Natty.
 
But, in the time that it didn't work I got a USB stick interface. Again, this works fine. Just a matter of plugging it in. 
 
Now I have a problem :) The plug in has a bit better speed and range. So, there are times I'd like to use it (esp. since I can extend the antenna on a usb cable and hang it out a window). But, now, when I plug in the stick I end up with 2 active networks (wlan0 and wlan1).
 
So, the question is: How can I selectively disable one network. I tried doing "ifconfig wlan0 down" and that worked for a few seconds, but then the internal net came back up. 
 
Even better would be a config which says "if the usb is plugged in turn off the internal device".
 
Or if I do need to have both active ... can I select a preferred path to use? I have no idea if the system is actually reading data from both devices (timing tests suggest that only the internal is being used, but I'm not sure).
 
 
Thanks.
 
Interesting question..
 
I have an internal wireless card that uses the b43 driver and I experiment with USB adapters just to see if they will work. All that I have tried have not been stronger than my internal to date.
 
Anyway, when I want to turn off my internal wlan0 I simply do the following command.
 
```
 
sudo modprobe -r b43

```
 
That will temporarily disable my internal wireless until next reboot or until I re-tickle the driver with 
 
```
 
sudo modprobe b43 

```
 
When I want to turn off one of my USB adapters that uses the ath9k_htc I do the same processes just changing the driver name. I had never consider a auto bash script as I only do it when testing a new adapter.
 
Hope this helps... You will need to determine your wireless and USB adapter drivers.
Usually you can see them doing either.
 
```
 
sudo lshw -C network

```
 
or
 
```
 
nm-tool

```
 
Good Luck

---

### Post by BobvanderPoel on 2011-09-07
Thanks so much! Never occurred to me that virtually removing the device by removing the driver would work. Nice quick and dirty solution.

I did test a ftp transfer and, using the builtin 'G' it took 40 seconds to transfer 2100 files a total of 50meg. With the usb stick 'N' it took 30 seconds. I suspect that some of the time is in file create/lookup overhead. I should test with a larger file. Another day.

Still, would be nice to have this automated. I have found the usb stick to have much greater range.

Best and thanks.

---

### Post by praseodym on 2011-09-07
Hi,

you can use a little script:

```
gksu gedit /etc/udev/rules.d/10-wlan-stick.rules 
```
Insert:

```
# UDEV-rule for external wireless stick
# unloads/loads driver for internal broadcom card

ACTION=="add", GOTO="device_check"
ACTION=="remove", GOTO="onboard_load"

LABEL="device_check
### stick plugged in, internal wireless driver unload
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe -rf b43"

GOTO="rules_end"

LABEL="onboard_load"
### stick unplugged, loads internal card driver
BUS=="usb", KERNEL=="wlan*" RUN+="/sbin/modprobe b43"

LABEL="rules_end"
```
save, close, and
```
sudo service udev reload
```

---

### Post by BobvanderPoel on 2011-09-07
Wonderful! I'll try it later today. Looks like it should be just perfect for the job!

Thanks.

---

### Post by BobvanderPoel on 2011-09-08
Again, a thank you!

I installed the script and it appears to be running 100%

Thumbs up to you.

Best,

---

