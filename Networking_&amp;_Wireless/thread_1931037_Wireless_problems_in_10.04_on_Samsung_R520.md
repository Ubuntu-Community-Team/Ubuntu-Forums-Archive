---
title: "Wireless problems in 10.04 on Samsung R520"
date: 2012-02-24
forum: Networking &amp; Wireless
---

### Post by daisybell on 2012-02-24
I am trying to get the wireless working on my Samsung R520 on Ubuntu 10.04. I've tried the simple suggestions that a Google search threw up, but the outputs from various commands seem to suggest that my wireless card isn't recognised.

The parts of lspci that seem relevant are below. 

```

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)
    Subsystem: Askey Computer Corp. Device 7160
    Flags: bus master, fast devsel, latency 0, IRQ 11
    I/O ports at 2000 [size=256]
    Memory at f6000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: r8192_pci

06:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
    Subsystem: Samsung Electronics Co Ltd Device c050
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at fa000000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 4000 [size=256]
    [virtual] Expansion ROM at f4000000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

```I wasn't sure if the 'network controller' was my wireless card. 

iwconfig gives

```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```Am I right in thinking my wireless card is not being recognised? How can I fix it?

---

### Post by kurt18947 on 2012-02-24
Hi

Some popular RealTek adapters were not plug & play until after 10.04.  Posting the output of 'lspci' (I assume this is the built-in adapter)  might be helpful to get a better chipset ID.  Something like this
```
Bus 002 Device 002: **ID 0846:9030** NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]
```
This is USB but you get the idea :).

---

### Post by daisybell on 2012-02-24
Well, that was the output of lspci at the top there, but I think the chipset ID is **10ec:8192** which suggests it's the Realtek 8192e.

I think I must have known this already because I notice now I have some drivers for the 8192e downloaded, probably from a previous attempt to fix this.

I have also run through the ndiswrapper troubleshooting steps at [http://ubuntuforums.org/showthread.php?t=885847 ]("http://ubuntuforums.org/showthread.php?t=885847")but got the UNCLAIMED error. sudo modprobe ndiswrapper gave me

```
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.

```

In #5 I got the unknown symbol error.

So after that I tried to compile ndiswrapper from source, following the instructions in #7 but when I got to the make command, I got this 

```
make: *** No targets specified and no makefile found. Stop.

```

So I don't think I have a working version of ndiswrapper any more either :(
[]("http://ubuntuforums.org/showthread.php?t=885847")

---

### Post by westie457 on 2012-02-24
Take a look at this thread [http://ubuntuforums.org/showthread.php?t=1689148](http://ubuntuforums.org/showthread.php?t=1689148)

Not exactly what you are looking for and for a later version (10.10) however it might provide a solution for you.

---

### Post by daisybell on 2012-02-24
Sadly, that fix doesn't work for me. 

I ran lsmod | grep 819 but there was no output at all. I went ahead and did the blacklist and rebooted, but as I expected it didn't work and iwconfig says 

```

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

I don't seem to have an entry for "kernel driver in use" in the lspci output for the Realtek device, so could that be part of the problem? I thought I should have the driver that came with Lucid, but I also downloaded ones from the Linux on Samsung forums (as per another suggestion from Google).

I will try with a newer release of Ubuntu on a live usb tomorrow, though I would prefer to stick with Lucid at the moment.

---

### Post by daisybell on 2012-02-25
With a bit more patience and following the suggested steps on that topic (and not doing it at 1am helped, I'm sure!) I do now have wireless working. Thank you for the link :)

However... all is not quite right. I had to use
```

sudo modprobe r8192e_pci
```to get it to work, and as I expected, I have to do this after every reboot. 

Is there a solution so I don't have to do this every time?

---

### Post by westie457 on 2012-02-25
Open a terminal and type this in ```
sudo gedit /etc/modules
``` and add r8192e_pci to the end of the file, proof-read save and exit.
Then ```
sudo reboot
```

All should now be working.

Hope this is helpful.

---

### Post by daisybell on 2012-02-26
Thanks, that has worked and the wireless is now functioning properly right after booting. 

Unfortunately, the wireless slows down especially after using it for a little while and when streaming video. I've found some other topics covering that, so I will try the suggestions in those for now.

---

