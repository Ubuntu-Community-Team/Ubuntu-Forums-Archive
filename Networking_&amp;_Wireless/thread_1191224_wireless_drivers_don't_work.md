---
title: "wireless drivers don't work"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by afterdeth on 2009-06-18
I'm brand new to linux, so bear with me

i have a D-link DWA-130 wireless USB stick, and the Linux drivers i installed from the D-link website don't allow me to access the internet. if anyone can suggest what the problem, or solution/alternative might be, i'd really appreciate it. here's the information i can provide:

installation instructions i followed (provided in the readme file of Dlink's linux driver download):

[INDENT][LEFT]Runing the scripts accomplish all operations including building up modules  
from the source code, installing driver to the kernel and starting up the nic. 
    1. Build up the drivers from the source code 
      make 
 
    2. Install the driver to the kernel 
          make install 
          reboot 
 
    3. bring up wlan if nic is not brought up by GUI, such as NetworkManager 
      ifconfig wlan0 up  
      Note: use ifconfig to check whether wlan0 is brought up and use iwconfig to check your wlan interface name,  
                since it may change wlan0 to wlan1,etc.
[/LEFT]
[/INDENT]i was only able to complete step 2, i tried typing **ifconfig wlan0 up** but nothing happens.

---

### Post by Cacadril on 2009-06-18
Disclaimer: I know nothing about your usb wifi.

Nothing outwardly visible is supposed to happen when you type the command ifconfig wlan0 up. Now, if you type only "ifconfig wlan0", you should get some data about the device, including its UP state. After you type this command, the device should look like this, approximately:

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Now this device is also accessible to the iwconfig command. If the device is not UP, iwconfig does not work.
But I believe network manager should pick up the device and run ifconfig up for you (or do the corresponding system calls) when the module has been loaded. You should check if the kernel picks up the device upon reboot. (no, don't reboot now, you have already done that.) Check in /var/log/kern.log to see if you can find a message that the kernel recognizes your new device. (This file is hard to read. Get used to scan through tons of "chineese" for some crumbs of known driver names or the like.) Also use lsusb with some verbosity options, to see that Linux indeed sees the device, and use lsmod to see what modules are currently loaded. you should see the name of the new module there. If not, 
you probably must research that first. If you know the module name, Try "modprobe modulename" to see if it gets loaded.

C.

---

### Post by Hobgoblin on 2009-06-18
Did you try without installing drivers?

I say this because the Windows mindset is to install drivers first otherwise how can it possibly work.  With Linux often the drivers are already there.

---

