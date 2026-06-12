---
title: "Wireless does not work anymore after resume"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by joaqal on 2010-02-07
Hello:
My wireless was working fine until about a week or two ago. Now for no apparent reason (maybe an upgrade conflict? Otherwise I set fuse permissions and started using "sshfs" at about the same time...) whenever I resume from standby or hibernate, it no longer works and I have to reboot to get it to work again.

I've tried several older solutions to similar problems including adding 
```
STOP_SERVICES="networking"
```
 to "/etc/default/acpi-support" as well as running
```
sudo dhclient
```
None of these succeeds in enabling the wireless again.

I am using a "Broadcom B43" wireless driver from the "Hardware Drivers" "System" menu.

Here is the output of  "lspci -v" (please let me know if any other info is usefull):

```

02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Hewlett-Packard Company Device 12f4
        Flags: bus master, fast devsel, latency 64, IRQ 17
        Memory at e8100000 (32-bit, non-prefetchable) [size=8K]
        Kernel driver in use: b43-pci-bridge
        Kernel modules: ssb

```

Thanks in advance for your help.

---

### Post by mushwars on 2010-02-07
have you tired something as simple as restarting networking or even simpler (even though it says its connected its not) disconnecting then reconnecting, I have the same problem on my laptop when ever I stand it by, and that seems to fix it.

---

### Post by joaqal on 2010-02-07
How would I disable/enable it? In my case, clicking on the wireless icon (top right corner) shows "enable wireless" grayed out (I cant click it). Also, the wireless LED on the laptop is turned off after resuming (this was not the case before...), and pressing the hardware button does not turn the LED back on. I've gone through the "Network Tools" utility in the systems menu and I didn't find an enable/disable option there.
I tried using "iwconfig" (don't know if that makes sense) with the option "txpower on" but that didn't do anything.

---

### Post by mushwars on 2010-02-07
Ah :) a laptop that helps..

do you have a hard key on your laptop that enables and disables wireless?

It could be that somehow your computer disables wireless and ubuntu doesnt know how to turn it back on automatically. Try hitting fn + f2 <-- thats what it is for me. And see if then you can connect to wireless. If that doesnt do it then hit fn + f2 again because then you will possibly have your wireless disabled then.

to restart networking you would do this
```
sudo service networking restart
```

---

### Post by joaqal on 2010-02-07
There is no function icon on the f2 key (tried it anyways...). However, there is a wireless hardware button (mentioned in my previous post) that does not succeed in re-enabling the wireless (or even in turning back on the wireless LED indicator on the laptop).

---

### Post by joaqal on 2010-02-09
Does anyone have any suggestions on how to get wireless working once again after resuming from standy / hibernate?

---

### Post by joaqal on 2010-02-09
<CODE>
jazs@jazs-pc:~$ sudo service networking restart
restart: Unknown instance: 
jazs@jazs-pc:~$ sudo service networking
Usage: /etc/init.d/networking {start|stop|restart|force-reload}
jazs@jazs-pc:~$ sudo service networking start
networking stop/waiting
jazs@jazs-pc:~$ sudo service networking stop
stop: Unknown instance: 
jazs@jazs-pc:~$ sudo service networking force-reload
reload: Unknown instance: 
jazs@jazs-pc:~$ 
</CODE>

---

### Post by Goombie on 2010-03-18
You might want to take a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1416172](http://ubuntuforums.org/showthread.php?t=1416172)

---

### Post by RonB123123 on 2010-03-23
This command doesn't work:
sudo service networking restart

This command works for me:
sudo /etc/init.d/networking force-reload

but it doesn't refresh the network icon in the top right hand corner. Any way to do that?

---

### Post by RonB123123 on 2010-03-29
Is there any way to reset the wireless service to reload the wireless networks? because when mine fails, I feel that if I could restart it, it would find and be able to connect to my wireless network again.

---

