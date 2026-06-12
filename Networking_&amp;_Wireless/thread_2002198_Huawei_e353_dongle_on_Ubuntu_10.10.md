---
title: "Huawei e353 dongle on Ubuntu 10.10"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by Rosengeek on 2012-06-12
Howdo:
I'm trying to get the "Three" Huawei E353 Dongle working on 10.10.
I've picked up the option module rebuild as supplied by "tvboxspy" on 21.7.2011. However when I compile/"make" it I get:

~/E353/10.10$ make
make -C /lib/modules/2.6.32-41-generic/build M=/home/menahem/E353/10.10 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-41-generic'
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "usb_wwan_tiocmset" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_open" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_dtr_rts" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_resume" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_set_termios" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_startup" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_disconnect" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_write_room" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_chars_in_buffer" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_tiocmget" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_release" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_close" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_suspend" [/home/menahem/E353/10.10/option.ko] undefined!
WARNING: "usb_wwan_write" [/home/menahem/E353/10.10/option.ko] undefined!
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-41-generic'
menahem@menahem-laptop:~/E353/10.10$ 

sudo make install gives: -

"Backup file present already"
cp option.ko /lib/modules/2.6.32-41-generic/kernel/drivers/usb/serial/option.ko
/sbin/depmod -a

When I subsequently try to run sakis3g I get:
Error occured [sic!]
Failed to load module "option"

I have installed build_essential

Running modprobe gives me :-

¬/E353/10.10$ modprobe option vendor=0x12d1 product=0x1506
FATAL: Error inserting option (/lib/modules/2.6.32-41-generic/kernal/drivers/usb/serial/option.ko):Operation not permitted

Any help would be appreciated 

Thanks
Rgeek

---

### Post by coffeecat on 2012-06-12
Two comments.

Ubuntu 10.10 is now past end-of-life - it is no longer supported, so you would do better using a more up-to-date version of Ubuntu, such as the latest Long-Term support 12.04.

Your Huawei E353 works out of the box in Ubuntu 11.10 and 12.04.

---

### Post by Rosengeek on 2012-06-12
Thanks! How annoying!
I'm running on a Asus EeePC &I understood that 10.10 is the latest support offered.
I'll investigate - thanks

Rgeek

---

### Post by coffeecat on 2012-06-12
> **Rosengeek said:**
> I'm running on a Asus EeePC &I understood that 10.10 is the latest support offered.

The LTS releases (Long Term Support) are released every two years in April of even numbered years. Currently supported LTS releases are 10.04 with about 10 months support to go on the desktop but a couple more years for the server version, and the recent 12.04 which will be supported for five years. The intermediate versions released every 6 months are supported for only 18 months, hence 10.10 (= 2010 - Oct) having passed end of life.

If you do install 12.04, you'll be confronted with the new Unity desktop which is quite different from the classic desktop that the standard version of 10.10 came with. Or, if you are using the netbook version of 10.10, the Unity interface that 12.04 comes with is massively improved over the version that came with 10.10.

---

### Post by Rosengeek on 2012-06-15
Wow! I've spent the last few days upgrading.
Contrary to what I specified, I wasn't even at release 10.04.
The upgrade fetched 1400+ packages to make it to 10.04. That was OK (but took a day..).
Then I was pretty soon prompted to go to 11.04. Some 1600+ packages were fetched.

Let me just say that there are definite improvements with the Huaewei dongle support. We're getting there. 

Unfortunately, the system start is not working. That is to say, I get to the log-on screen which presents my ID and the space to input the password - but it's frozen - I can't get past there.
What I have to do is boot in (latest) recovery mode, opt for "Run in Failsafe Graphics" & from then onwards it's fine.
Is this normal or is there something to prod other than my work-around!?

Thanks 
R-Geek

---

### Post by coffeecat on 2012-06-15
> **Rosengeek said:**
> 
The upgrade fetched 1400+ packages to make it to 10.04. That was OK (but took a day..).
Then I was pretty soon prompted to go to 11.04. Some 1600+ packages were fetched.

You could have gone directly from 10.04 to 12.04, but you would have had to change a setting in the package manager for this to prompt you for this. Having said that, it sounds as though you are now getting a graphics problem and this might be worse in 12.04, if you have an old graphics chipset. What is your graphics card? If you are not sure, the output of this command will tell you:

```
lspci | grep VGA
```

---

