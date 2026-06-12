---
title: "Hardware network switch on a Dell Vostro 1320"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by p3car on 2009-06-23
I have been struggling to understand a peculiar problem with my new Dell Laptop. Network manager on Ubuntu 9.04 tells me that wireless is disabled.
The Vostro has a Broadcom BCM 312 (rev 01) wireless card. When I started the 9.04 live CD I was very happy to see that I had wireless working out of the box.

I installed and the wireless was working for a short time. I plugged in to my wired network and installed the suggested updates. There was a recommendation to install kernel 2.6.28-13 and at first I thought this to be the reason for not having any wireless. Network manager  just keeps telling me that "wireless is disabled".

I tried different drivers, used ndiswrapper, built the STA driver from broadcom, but with no luck.

I reinstalled 9.04, the live cd still had wireless working. I installed the suggested updates but stayed on 2.6.28-11 kernel, but  I only had wireless working for a short while.

Yesterday I realised that the driver was working propery. Entering
```
sudo iwlist eth1 scan 
``` gave me a list of available networks.

I tried wicd and I was able to connect to my network.

Today I have googled and my understanding of the problem is that network manager really believes that the wireless is disabled. The Vostro has a hardware switch and by looking into what HAL gave as feedback on 
```
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/dell_wlan_switch org.freedesktop.Hal.Device.KillSwitch.GetPower
```The above command returned:
method return sender=:1.0 -> dest=:1.75 reply_serial=2
   int32 0

Where the int32 0 suggests that HAL sees the hardware switch as set to off.

Is there any way of forcing HAL to set the KillSwitch parameter to on?
I have looked in the BIOS if I can disable the switch, but haven't found that option?
I could run wicd, but I also needs 3G connection from time to time and I really like network manager to control my usb-modem.

/P

---

### Post by cmreigrut on 2009-06-23
I'm having the same problem with wireless on a Dell Vostro 1720.  Syslog shows
```

NetworkManager: <info> Found radio killswitch /org/freedesktop/Hal/devices/pci_8086_4232_rfkill_5100AGN_wlan
NetworkManager: <info> Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch
...
NetworkManager: Wireless now disabled by radio killswitch

```

It worked a few days ago, and works fine even booting Jaunty from the LiveCD.  Anyone have any ideas?

---

### Post by lmintfans on 2009-06-23
[SIZE=3]Yes, I also recognized this problem- NetworkManager failed after updating kernel.
This problem might be caused by the wireless switch.

I testes two laptops, Dell Vostor 1320 and Asus F6V, with the same wireless adapter, Intel 5100.
The Asus F6V was Ok; however, Dell Vostor 1320 was failed.

I also found an interesting condition.
The wireless sign of ASUS F6V would be started during the procedure of booting GRUB.
For Dell Vostor 1320, the wireless sign would be started during the procedure of booting X-Window.

Coul other Dell users help me to confirm when the wireless sign is started?

I guessed that if the wireless sign of Dell Vostor 1320 could be started during the procedure of booting GRUB, NetworkManager would successfully control the wirless adapter.

Now, i am performing some tests.
If any special findings, i will report the results.

[/SIZE]

---

### Post by p3car on 2009-06-24
My network seems to start during the boot, when I have the Ubuntu splash screen showing. This is the same behaviour as I have on an old Thinkpad that the Vostro is replacing.

---

### Post by p3car on 2009-06-24
I also have a comment about killwitch in my log.

 
```
NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch
NetworkManager: <info>  Wireless now disabled by radio killswitch 
```

I tried to start the machine with the hardware switch off, but then the keyboard is not responding when I'm trying to log in.

I'd be happy with disabling the switch, but the BIOS seems to have no option for this.

---

### Post by p3car on 2009-06-24
I found a solution in this thread:
[http://ubuntuforums.org/showthread.php?t=490250](http://ubuntuforums.org/showthread.php?t=490250)

I downgraded HAL as suggested, using force in Synaptic manager on the following three packages:

hal
libhal-storage1
libhal1

The wireless is no longer disabled, and I can connect to my wireless network.
Only little annoyance is that update manager prompts me to upgrade the three packages.

---

### Post by lmintfans on 2009-06-24
Thanks P3Car! :D
I will try your suggestion later.
 
For Dell Vostor 1320, my keyboard and touchpad will also be freezed.
 
Today, I tried the kernel updat with Lenovo Y530.
The wireless adapter is Intel 5100.
 
After kernel update, the wireless sign was still started during booting the GRUB.
Consequently, the NetworkManager was OK for Lenovo Y530.

---

### Post by lmintfans on 2009-06-24
Great, p3car.:KS
 
Based on your suggestion, I downgraded hal, libhal-storage1, and libhal1 from 0.5.12~rc1-ubuntu3 to 0.5.12~rc1-ubuntu1.
 
This problem will be solved and NetworkManager will be fine.
It may be a bug?!
 
Thanks for help.

---

### Post by p3car on 2009-06-25
It seems to be a bug. The latest version was supposed to enable the killswitch on Dell computers. That may be true, but they fixed a bit too much :o

I will see if there is a bug report on Launchpad

---

### Post by simosx on 2009-07-02
Here is the bug report that has the "fix" that caused the issues,
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/368553](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/368553)

---

### Post by p3car on 2009-07-03
And here is a bug report

[https://bugs.launchpad.net/ubuntu/+bug/390743](https://bugs.launchpad.net/ubuntu/+bug/390743)

BTW I noticed the same behaviour on my brother's HP, don't know the model.

I also locked the versions of hal and lib-hal to avoid having update manager reminding me of these upgrades.

It seems to be OK to go to the latest version of lib-halstorage

---

### Post by simosx on 2009-07-03
> **p3car said:**
> And here is a bug report

[https://bugs.launchpad.net/ubuntu/+bug/390743](https://bugs.launchpad.net/ubuntu/+bug/390743)

BTW I noticed the same behaviour on my brother's HP, don't know the model.

I also locked the versions of hal and lib-hal to avoid having update manager reminding me of these upgrades.

It seems to be OK to go to the latest version of lib-halstorage

Have a look at [https://bugs.edge.launchpad.net/ubuntu/+source/hal/+bug/394663](https://bugs.edge.launchpad.net/ubuntu/+source/hal/+bug/394663)

I think the problem was that for some time, hal has been mis-reporting the rfkill value for these laptops. However, at that time, the hal script had a bug and it would always fail with an error, and this error was received as if 'Wireless is always On'. So, NetworkManager would think the wireless is always activated, but you would see wireless networks only when the rfkill switch is really off.

The solution would be for these laptops HAL should be able to report correctly when the rfkill switch is on or off.

---

### Post by cmreigrut on 2009-08-12
I finally got this one solved, but only after a lot of help from IRC.  See [http://www.reigrut.net/wiki/index.php/Dell_Vostro_1720#Wireless_Switch_Problem](http://www.reigrut.net/wiki/index.php/Dell_Vostro_1720#Wireless_Switch_Problem)

---

### Post by p3car on 2009-09-10
I have just upgraded the BIOS to rev A03. One of the thing mentioned in the changes was that rfkillswitch was fixed. The upgrade of the BIOS solved my problem with network manager stating that the wireless was disabled. I have tested this on 9.10 alpha 5.

---

### Post by bors71 on 2010-07-04
> **p3car said:**
> I have just upgraded the BIOS to rev A03. One of the thing mentioned in the changes was that rfkillswitch was fixed. The upgrade of the BIOS solved my problem with network manager stating that the wireless was disabled. I have tested this on 9.10 alpha 5.
Same here, i just updated my bios from a02 to a04.... the wireless problem solved!!!

thanks.

---

