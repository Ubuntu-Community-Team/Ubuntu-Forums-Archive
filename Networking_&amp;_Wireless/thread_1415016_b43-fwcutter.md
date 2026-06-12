---
title: "b43-fwcutter"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by shoepolice on 2010-02-24
Hi,

A new install of Ubuntu 9.10 on an Acer Aspire 3000 is not recognising my wireless device. Details here (see 2nd post for full details as per details required sticky thread above);

[http://ubuntuforums.org/showthread.php?t=1414453](http://ubuntuforums.org/showthread.php?t=1414453)

I went through loads of steps to no avail, but now have the bcmwl5a driver installed with ndiswrapper. However, the final thread I used to try and fix it suggested installing the b43-fwcutter. With this now installed, do I need to revert to a different driver? I think I've just worked out that I don't.

Going round in circles and now don't know where to go. Any help available please? Paypal pint in it for whoever fixes it :)

Extra tags: unable to see if hardware is present; could not find network configuration tool.

---

### Post by chili555 on 2010-02-24
> Paypal pint in it for whoever fixes itThis flies in the face of the spirit and intent of free and open source software, in my opinion. I suggest you not make money offers here. 

Is your system working well with the Windows driver and ndiswrapper? If so, why change anything? If not, post back and tell us your problems and we'll do our very best to help you fix them...for free.

---

### Post by shoepolice on 2010-02-24
> **chili555 said:**
> This flies in the face of the spirit and intent of free and open source software, in my opinion. I suggest you not make money offers here. 

Is your system working well with the Windows driver and ndiswrapper? If so, why change anything? If not, post back and tell us your problems and we'll do our very best to help you fix them...for free.

The system is not working with windows driver and ndiswrapper. When I boot up the external wifi light does not flash, so I'm guessing it is not being recognised by Ubuntu. When I try to configure network in Windows Wireless Drivers GUI I get the error message "Could not find network configuration tool" and when I just open the GUI it says "Unable to see if hardware is present".

And re the paypal pint, it was meant as a friendly gesture, not bribery. If a mate gave me something for free I'd buy him a pint down the pub next time, I meant this along the same lines. I thought the spirit and intent of free and open source software was to contribute voluntarily to those who provide it? Apologies if I have this wrong.

---

### Post by chili555 on 2010-02-24
> The system is not working with windows driver and ndiswrapper.Please open a terminal and do:```
sudo modprobe ndiswrapper
ndiswrapper -l
iwconfig
rfkill list
```With this information, we will have a better idea how to proceed.

If we solve this, I will expect a pint when I am next in your town; but then I expect to buy us a second one!

---

### Post by shoepolice on 2010-02-24
Deal.

sudo modprobe ndiswrapper
```

jim@ubuntu:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

```

ndiswrapper -l
```

jim@ubuntu:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5a : driver installed
    device (14E4:4318) present (alternate driver: ssb)

```

iwconfig
```

jim@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

rfkill list

*returns nothing*

---

### Post by chili555 on 2010-02-24
> wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0It looks perfectly healthy to me. What happens when you click the Network Manager icon and try to connect? Do you see networks?

---

### Post by boomerian on 2010-02-24
Thanks to you both (and I no longer drink)!
I, too, have been struggling with a Broadcom wireless.
Do I need to remove ndiswrapper if I load B43-fwcutter?
Cheers,

---

### Post by shoepolice on 2010-02-24
Well well, it works now. Must have been something I did last night but didn't notice it working or the reboot has fixed it.

So, err, does that mean you owe me a pint? :)

Hopefully my thanks for your time will suffice.

---

### Post by shoepolice on 2010-02-24
Boomerian - no, I haven't uninstalled anything. You might want to take this thread on with chili555 if he doesn't mind.

---

### Post by chili555 on 2010-02-24
> **boomerian said:**
> Thanks to you both (and I no longer drink)!
I, too, have been struggling with a Broadcom wireless.
Do I need to remove ndiswrapper if I load B43-fwcutter?
Cheers,Please start a new thread. I'll be right there.

---

### Post by chili555 on 2010-02-24
> Hopefully my thanks for your time will suffice.I am glad it's working and I feel generously rewarded! Enjoy.

---

