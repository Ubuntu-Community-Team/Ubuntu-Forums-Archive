---
title: "Can't connect with wireless but ethernet ok"
date: 2012-10-28
forum: Networking &amp; Wireless
---

### Post by leisure01 on 2012-10-28
I have recently installed Ubuntu which came with CAELinux 2011. I can connect to the internet via ethernet but wireless does not work. I have no experience with Linux. 
Unfortunately I cannot update to later version of Ubuntu as I have been told the other software that was bundled with CAELinux 2011 would cease to work.
Any advice welcome.
 
Some details are as follows:
 
Ubuntu version:
Ubuntu 10.04.3 LTS 64 bit with Kernel 2.6.32-34
 
Computer:
Samsung NP300E5A laptop
 
Wireless Card:
Intel Centrino Wireless N130
 
Output from command "sudo lshw -C network":
 
*-network UNCLAIMED 
description: Network controller 
product: Intel Corporation 
vendor: Intel Corporation 
physical id: 0 
bus info: pci@0000:01:00.0 
version: 34 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list 
configuration: latency=0 
resources: memory:c0500000-c0501fff 
*-network 
description: Ethernet interface 
product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 0 
bus info: pci@0000:02:00.0 
logical name: eth0 
version: 06 
serial: e8:03:9a:2c:3a:7b 
size: 10MB/s 
capacity: 1GB/s 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
resources: irq:26 ioport:2000(size=256) memory:c0404000-c0404fff(prefetchable) memory:c0400000-c0403fff(prefetchable)

---

### Post by Abhinav Kumar on 2012-10-28
May be there is no wireless driver in your system.
just grab a LAN wire and use a wired connection to connect to the internet.
I assume if their is no proxy.

However, if there is a proxy, enter desired proxy settings by selecting   Network Proxy from System->Preferences. Now the username and password need to be  given
For this, type in the terminal 
sudo gedit /etc/apt/apt.conf
and after giving the password follow the following format in apt.conf file
Acquire  http:: proxy "http://username: password@ur_PROXY"
Acquire  http:: proxy "ftp://username: password@ur_PROXY"
Acquire  https:: proxy "https://username: password@ur_PROXY"
save it and now you should see your computer can connect to the wired connection
through the proxy.:smile:

Now, select additional drivers from System->Administration .
Ubuntu should automatically select the driver for you. just install and restart may be required after the install.

---

### Post by leisure01 on 2012-10-28
[LEFT]Thank you for the quick response.  Not sure if I followed your instructions correctly or not.  I tried the following:

Used ethernet to log on to internet.
Went to: System - Administration - Hardware Drivers

A pop up box appeared with the message:
"Searching for additional drivers"

A further pop up box appeared with the message:
"No proprietary drivers are in use on this system"

Unfortunately nothing seems to have changed.
[/LEFT]

---

### Post by westie457 on 2012-10-28
Copy and paste this into a terminal. Despite the look of it, it is one command.

```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

Open the File Browser and locate the wireless_script file and double-click on it, select either 'Run in Terminal' or 'Run' and enter your password. When you have a 'Netinfo.txt' file created attach it to a new reply here by clicking on the paperclip at the top of the message pane.

Thank you

---

### Post by leisure01 on 2012-10-28
Thanks for your response westie457, netinfo file attached.

---

### Post by westie457 on 2012-10-28
Have not found many threads on here about your issue.

Try the steps in he second half of post #2 in this thread.
[http://ubuntuforums.org/showthread.php?t=1929943](http://ubuntuforums.org/showthread.php?t=1929943)

If this does not help then I suggest that you do what is in post #4 of the same thread.

Hope this helps

---

### Post by leisure01 on 2012-10-28
Thanks again for the suggestion westie457.  I checked out the threads you recommended, unfortunately the one from post #2 didn't seem to come to a conclusion.  Post #4 was a recommendation to upgrade to a later version of ubuntu, this is a nonstarter for me because much of the software with CAELinux won't run in later versions.  Thanks for your time anyway.

---

### Post by westie457 on 2012-10-28
Have not given up completely on this. Had a look at the CAELinux site and their Forums, you might have better luck installing Mint and adding the CAELinux apps to that.

Mint is based on Ubuntu and uses most of the same repositories. Some things that do not work in Ubuntu sometimes work in Mint.

You will probably have to download the CAELinux apps individually from sourceforge.net or you could wait for the new version when it is released.

Other than these suggestions I have no further ideas.

---

### Post by leisure01 on 2012-10-28
Thanks again for your perseverance westie457, I will check out mint.

---

### Post by leisure01 on 2012-10-28
Solved the problem by installing a driver from a later version of ubuntu using the method shown in the thread linked below.

[http://ubuntuforums.org/showthread.php?t=1940468](http://ubuntuforums.org/showthread.php?t=1940468)

 It all went smoothly up to the point where the wget and tar commands  were required.  For some reason a not found error occurred.  However  this was overcome by going direct to the http address, downloading and  extracting the required files to my machine and then carrying on with  the rest of the steps.
The wireless is now working perfectly and I didn't need to upgrade to  the latest version of ubuntu which would have caused problems for some  of the applications on the CAELinux distribution.
Thanks to all who have helped.

---

