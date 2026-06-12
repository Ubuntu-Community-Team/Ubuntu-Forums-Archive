---
title: "Strange wireless bug.."
date: 2009-08-21
forum: Networking &amp; Wireless
---

### Post by aatyler on 2009-08-21
I have 9.04 installed on my ASUS-M50VM-B1, output of lspci -v for wireless is:

```
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
        Subsystem: Device 1a3b:1067
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fdff0000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath9k
        Kernel modules: ath9k

```


I have a dual boot setup using GRUB and ubuntu as the primary and vista as the secondary. 

I had trouble with my WIFI lastnight and this morning, on a hunch i loaded vista to see if the problem was localized to ubuntu. To my surprise I found that wireless was soft disabled in windows, i re-enabled it, and found that it worked fine. When I booted back into linux, wireless worked like a charm. I experimented by disabling it in windows again, and the problem re-occured. Any one ever heard of this before? I guess it's technically not a ubuntu issue, but does any one know a way of making ubuntu override whatever the windows driver is doing?


Adam

---

### Post by The Toxic Mite on 2009-08-21
Try pressing the wi-fi on/off button ;)

Tell me how it goes :)

-TTM-

---

### Post by aatyler on 2009-08-22
> **The Toxic Mite said:**
> Try pressing the wi-fi on/off button ;)

Tell me how it goes :)

-TTM-


lol, :P I don't think i was clear enough:

I log into ubuntu, and when I attempt to log onto my wireless network, ubuntu continually fails to connect even though it detects my wireless card just fine, i have the physical switch on, and it sees the wireless networks.

to fix the problem I reboot into windows and I see that the windows driver for the wireless is turned off, I turn it on, then reboot back into linux and everything works fine. 
The reason I wonder is that if I use my windows drivers to turn off the wlan, then linux won't be able to connect to the wireless networks. Is there some command / driver in linux that controls the wlan ? I already checked my logs and it recognizes the wireless card just fine on bootup without any error messages.... I guess if this is the only issue I have with ubuntu i'll be happy anyways, but I was just wondering. 


EDIT: oh, i forgot to mention, when the wireless doesn't connect I get alot of timed out messages from it in my logs.

Thanks for the reply,

Adam

---

### Post by excogitation on 2009-08-27
try installing
```
sudo aptitude install linux-backports-modules-jaunty-generic
```
[taken from here]("http://ubuntuforums.org/showthread.php?t=1205318")

---

### Post by aatyler on 2009-09-05
Ok, thanks, I'll try that when I get a chance. I read that thread but it seemed like a different problem. Thanks for the reply, sorry I didn't respond sooner. i'll repost after I try it out.
 
 
Tyler

---

### Post by aatyler on 2009-09-05
Seems to be working now. certainly connects faster. I still have to manually activate the wlan. we'll see what happens. Thanks for the help


-Adam

---

