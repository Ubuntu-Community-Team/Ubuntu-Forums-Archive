---
title: "Asus USB-N12 on Ubuntu 12.10"
date: 2013-01-07
forum: Networking &amp; Wireless
---

### Post by mrule on 2013-01-07
After an automatic update my USB network adapter stopped working. I have spent one day trying to fix it from available information online and have not been successful. I need help.

Here is some basic system information, but please do ask for more if it will help. 

~$ uname -a
Linux ******** 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

~$ lsb_release -a                                                                                                                                                                                           
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal

~$ lsusb
Bus 002 Device 002: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]



Currently, all drivers from the realtek website that I download are broken archives. The driver from Asus does not compile with the headers for the 3.5 kernel. I applied a patch that fixed this, but the install failed -- for the rather mundane reason that the file RT3070STA.dat was missing, but RT2870STA.dat was present instead. I didn't want to proceed by renaming this file because it was unclear whether that would break everything. Older realtek drivers have even more problems with the headers for kernel version 3.5.* that I haven't attempted to resolve by hand. 

In summary : 

realtek drivers from website are all broken on download
asus website driver is clearly not what it should be
older realtek drivers seem very incompatible with 3.5.x
default drivers, if any, aren't working.

I don't know where to go from here?

---

### Post by mrule on 2013-01-10
any leads? anyone?

---

### Post by mrule on 2013-01-10
Update:

It seems that there are no realtek drivers for kernel version 3.5.* yet. They only support up to 3.0.8

Driver download site for RTL8192CU found at 

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8192CU)

via [http://forums.linuxmint.com/viewtopic.php?t=94495&f=53](http://forums.linuxmint.com/viewtopic.php?t=94495&f=53)

---

### Post by mrule on 2013-01-10
Update:

Attempting to install the 3.0.* driver on 3.5.* compiles without error but causes a kernel panic when loaded. Subsequently, the machine is so overwhelmed by USB errors that the keyboard doesn't even work properly. So, don't do that. Looks like support for 3.5.* is impossible and I should not have let the computer update itself.

---

### Post by mrule on 2013-01-10
It looks like the most recent LTS release compatible with this wireless hardware is 11.04 ( natty ).

---

### Post by mrule on 2013-01-10
Since the device isn't supported on newer kernel versions, I am booting in to 2.6.38-13. 

I restored the natty sources in apt at outlined in [http://ubuntuguide.org/wiki/Ubuntu:Natty#Manually_add_repositories](http://ubuntuguide.org/wiki/Ubuntu:Natty#Manually_add_repositories)

I then grabbed the old headers
sudo apt-get install build-essential linux-headers-2.6.38-13-generic

after this I was able to compile and load the realtek drivers without very bad things ( kernel panic ) happening. Still waiting to see if this restores wireless functionality. Will update with more information.

---

### Post by mrule on 2013-01-10
Update: 

Using an older kernel has at least gotten me back to the previous level of functionality. 

If I boot the machine with a wired connection, network manager starts and I can view wireless networks, but I cannot connect to them if I subsequently disconnect the wired connection. 

If I boot without the wired connection network manager does not start, but I can access wireless internet after starting it manually. 

The only question that remains is how to ensure that network manager starts automatically even without a wired connection on startup. I'll report back if I figure this out.

Things like this make me wish there were a black-box warning on any upgrade that changes the kernel version. CAUTION: THIS UPDATE MAY BREAK SUPPORT FOR SOME OF YOUR HARDWARE, INCLUDING AUDIO, VIDEO, AND NETWORKING, ARE YOU SURE YOU WANT TO PROCEED?. In my opinion, given the headaches I've experienced over the years, update manager should *never* try to apply an automatic update that changes the kernel version without displaying such a message.

---

### Post by mrule on 2013-01-10
It seems that the failure of network manager to start automatically is related to 

[http://askubuntu.com/questions/220377/why-doesnt-network-manager-start-at-boot](http://askubuntu.com/questions/220377/why-doesnt-network-manager-start-at-boot)

The trick is to comment out auto configuration of eth0 ( wired internet ) in the /etc/network/interfaces config file. This will allow network manager to start without a wired connection.

---

### Post by SUPERFITTER on 2013-04-08
Has anyone found a solution to Asus USB-N13 Wireless-N300 Adapter on Ubuntu 12.10?

---

### Post by mrule on 2013-04-08
My research suggests no... even my temporary solution failed for no apparent reason recently ( no updates or config change, just rebooted the machine, and I can't get the driver to load ) so...

---

### Post by SUPERFITTER on 2013-04-13
chili555, has found the answer: [http://ubuntuforums.org/showthread.php?t=2133710&page=3](http://ubuntuforums.org/showthread.php?t=2133710&page=3)

Thank you chili555

---

