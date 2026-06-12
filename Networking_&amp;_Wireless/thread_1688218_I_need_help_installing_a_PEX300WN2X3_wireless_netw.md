---
title: "I need help installing a PEX300WN2X3 wireless network adapter on ubuntu10.10"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by pjorge1036 on 2011-02-15
I'm new to Ubuntu and Linux for that matter. I am trying to install a Star Tech PEX300WN2X3 wireless card but I'm completely lost. The installation Cd has 2 tar. files with the linux drivers but I'm just clueless as to what to do with them. Any help will be appreciated.

---

### Post by amsterdamharu on 2011-02-15
If your wireless is usb can you see it when it's plugged in giving the following command?
```
lsusb -v
```

If it's a pci card can you see it with the following command?
```
lspci -v
```

Could you post the output of the commands here (only the relevant part with the information about the wireless card)?

To execute the command(s) you can press alt + F2, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in code tags: &#91;code][COLOR=Red]Your pasted stuff[/COLOR]&#91;/code]

---

### Post by Hippytaff on 2011-02-15
Also, if you double click of the Tar files, extract the contents to a folder somewhere. Open the folder and there should be a readme - text file in there. I would imagine there would be instructions there.
 
It depends whether the drivers need to be complied or not, but read up on modprobe, which is the command for installing drivers.

---

### Post by pjorge1036 on 2011-02-15
OK, this is the output:
```
02:00.0 Network controller: RaLink RT2860 Wireless 802.11n PCIe
    Subsystem: RaLink Device 2860
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: rt2800pci
    Kernel modules: rt2860sta, rt2800pci


```
And BTW thanks for replying.

---

### Post by amsterdamharu on 2011-02-15
Before downloading and compiling the newest driver you might check to see if it is just a setting:
Could you post the output of the following commands?

```
sudo apt-get install rfkill
rfkill list
sudo ifconfig -a
cat /etc/networks
```



I did find one interesting bug report here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594866](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/594866)

A suggestion is made to blacklist all the rt drivers but the rt2860sta:
To list currently loaded drivers with rt:
```
lsmod | grep rt
```

adding:
```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
 
```to /etc/modprobe.d/blacklist.conf
Press alt + F2, type "gksu gedit /etc/modprobe.d/blacklist.conf" (no quotes) and click run. You can now add the blacklist lines and save. Maybe need a reboot before it works.

---

### Post by amsterdamharu on 2011-02-15
Here is how to get the latest drivers but before going down that road you should post the output of the commands I posted before.

[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

---

### Post by pjorge1036 on 2011-02-15
output # 1
```
pjorge1036@pjorge-Home:~$ sudo apt-get install rfkill
[sudo] password for pjorge1036: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  rfkill
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 8,158B of archives.
After this operation, 65.5kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/universe rfkill amd64 0.4-1 [8,158B]
Fetched 8,158B in 0s (18.8kB/s) 
Selecting previously deselected package rfkill.
(Reading database ... 159315 files and directories currently installed.)
Unpacking rfkill (from .../rfkill_0.4-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up rfkill (0.4-1) ...
pjorge1036@pjorge-Home:~$ 
```

---

### Post by pjorge1036 on 2011-02-15
output #2

```

pjorge1036@pjorge-Home:~$ lsmod | grep rt
rt2860sta             559618  0 
rt2800pci              10233  0 
rt2800lib              31970  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  2 rt2860sta,rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
mac80211              267163  3 rt2x00usb,rt2x00pci,rt2x00lib
parport_pc             30086  1 
cfg80211              170485  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci
parport                37032  3 ppdev,parport_pc,lp
pjorge1036@pjorge-Home:~$ 
```

---

### Post by pjorge1036 on 2011-02-15
> **amsterdamharu said:**
> 

A suggestion is made to blacklist all the rt drivers but the rt2860sta:
To list currently loaded drivers with rt:
```
lsmod | grep rt
```adding:
```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
 
```to /etc/modprobe.d/blacklist.conf
Press alt + F2, type "gksu gedit /etc/modprobe.d/blacklist.conf" (no quotes) and click run. You can now add the blacklist lines and save. Maybe need a reboot before it works.
I had to try this a couple times because as I stated before I am not familiar with Linux and my computer knowledge is very limited but, I found what I was doing wrong  and now it's working like a charm.
 Thank you for your help, I never would have done it without you!

---

### Post by amsterdamharu on 2011-02-16
Great to hear it's solved, there is a link thread tools on the top of the page that's where you can mark this thread as solved.

People with the same problem might stumble upon this thread and use it for their solution as well, they should check out the status of the bug here:
[http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007)

---

