---
title: "Broadcom 43xx driver install and speed is slower than on WIn 7"
date: 2010-12-29
forum: Networking &amp; Wireless
---

### Post by hpng on 2010-12-29
Hello:

I have a HP dv7 with Ubuntu 64 bits 10.04
I read this:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

I did all this ( found at bottom of above readme file ):

"Ubuntu:
------
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate

Sometimes the driver does not show up in the Hardware Drivers choices.  In
this case, try reintalling the driver from the GUI or shell like this:

From the GUI:
Package Manager (System>Administration>Synaptic Package Manager). Click the 
Reload button in the upper left corner of Synaptic to refresh your index then 
search for and reinstall the package named bcmwl-kernel-source.

From the shell:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

In either GUI or text case, after reinstalling, reboot your machine.

Now go back to System->Administration->Hardware Drivers
and you should see the driver enabled and working.
"
Last paragraph should read like this:
"Now go back to System->Administration->Hardware Drivers
and active the Broadcom STA driver, then you should see 
the driver enabled and working".

Here is my problem:
I have dual boot install:  Win7 and Ubuntu 10.04.
After installing driver, Firefox 3.6 runs fine, but slower on Ubuntu than 
on Win 7.  At times, I timed the download of a new webpage by looking at 
the progress bar at bottom right of Firefox.  It took about 30 seconds 
( and at times longer ) to complete download ( that means when the 
progress bar completes.  This is latency time is consistent for all web 
destination. It only takes a few seconds on Win 7 with Firefox 3.6

Now, here is the puzzle.  When I run Adobe Flash, there is NO gaps in video or 
sound. I also check with Sudo iwConfig, and wireless speed is 48 to 54 Mb/s.
So I think my BCM 4313 wireless is working fine.  

My other thought is there may be some setting on Firefox that I need to 
change to enable faster page update. Any ideas?

How do you check speed of Ethernet connection?

Please advice.


Thanks.

---

### Post by PatchesTheCaveman on 2010-12-29
It sounds like you might be using the b43 driver instead of the Broadcom STA driver.  That usually exhibits slower performance.

To check, go to Applications > Accessories > Terminal on your top panel.  Then, in the black box that appears, type the following and press Enter:
```
lspci -v
```

Information about many of your devices will appear.  One of them will say *Network Controller:  Broadcom Corporation BCM4312* (or whichever model # you have).  Underneath that it will say *Kernel driver in use:*.  If it says *wl* you have the right driver.  

If it says *b43* you don't.  Go to System > Administration > Additional Drivers and make sure the Broadcom STA wireless driver is installed.  If so, go back to your terminal and run:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

To the end of that file, add the following lines:
```
blacklist b43
blacklist b43legacy
```

That will blacklist the b43 driver so the STA driver is forced to load.  Reboot and see if that improves your performance.

If for some reason your wireless stops working, go back and remove those lines and run
```
sudo modprobe b43
```
to bring the b43 driver  back online.  Then let us know so we can figure out what's going on.

---

### Post by hpng on 2010-12-29
here is  portion of what I got from this command:
lspci -v 

```


02:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
    Subsystem: Hewlett-Packard Company Device 1483
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at f0100000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use:** [COLOR=Blue]wl[/COLOR]**
    Kernel modules:** [COLOR=Blue]wl[/COLOR]**

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
    Flags: bus master, fast devsel, latency 0, IRQ 26
    I/O ports at 2000 [size=256]
    Memory at f0004000 (64-bit, prefetchable) [size=4K]
    Memory at f0000000 (64-bit, prefetchable) [size=16K]
    Expansion ROM at f0010000 [disabled] [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169


```

As you can see, I got the correct driver:   wl

Likewise, my Gigabit ethernet is slow too.

Please advice.

Thanks.

---

