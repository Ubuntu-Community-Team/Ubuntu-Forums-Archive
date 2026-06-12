---
title: "ASUS USB-N13 B1 adapter configuration problems"
date: 2012-09-13
forum: Networking &amp; Wireless
---

### Post by mrule on 2012-09-13
I have checked elsewhere and have not found a solution. 

I have a Dell Studio Slim 540s running Ubuntu 12.04.
I moved into a new place and need to pick up internet via wireless. 
I purchased an ASUS USB-N13 revision B1 USB wireless adapter, as it allegedly works with linux
I have installed the drivers and am getting very intermittent connectivity
It is not a problem with signal strength, and the network SSID and password have been entered correctly.
The network I am trying to connect to is a WPA personal network with an ASUS repeater providing coverage for my part of the building. 
Windows and Mac laptops connect to this network without a hitch. 
I have been trying to get the ubuntu to machine to connect for about a week now and haven't found any solutions yet.

Here is some basic system information

```
~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

~$ uname -a                                                                               
Linux petra 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

~$ lsusb                                                
Bus 001 Device 006: ID 0b05:17ab ASUSTek Computer, Inc.
```

I'd post more but I really don't know what information would be helpful in debugging this problem. 

For the most part, the adapter sees local wireless networks and attempts to connect to them. It asks me for the password three times before giving up and turning off wireless. Sometimes, if I boot the machine while it is also plugged in to the wired ethernet, I can get wireless up and running, and this connection persists with good signal strength and connectivity after the ethernet connection is removed. However, rebooting either the machine or the repeater severs this connection, and it cannot be re-established without again booting the machine while plugged in to ethernet. 

So, to me this is all very mysterious and I have been spending many hours for some time trying to understand what is happening. 

Any help would be greatly appreciated. I posted also at [askubuntu]("http://askubuntu.com/questions/186829/wireless-not-working-on-desktop-with-asus-usb-n13-b1-wireless-adapter") but have not received useful information there yet. 

Thanks, 
Michael.

---

### Post by mrule on 2012-09-14
Update : I don't know why, but if I boot without the wired connection and then run

```
sudo service network-manager restart
```

once the computer starts up, I seem to get a wireless connection. So, it looks like its just a matter of making sure the wireless starts correctly. I'm not sure how to explain other behaviors, but I feel like I'm closer to a solution.

Maybe solved? I still don't understand what the problem was though.

---

### Post by mrule on 2012-09-14
Update : I don't know why, but if I boot without the wired connection and then run

```
sudo service network-manager restart
```

once the computer starts up, I seem to get a wireless connection. So, it looks like its just a matter of making sure the wireless starts correctly. I'm not sure how to explain other behaviors, but I feel like I'm closer to a solution.

Maybe solved? I still don't understand what the problem was though.

---

### Post by mrule on 2013-01-10
Update: after a few months of enjoying partially working wireless ( requiring a manual restart of network manager after booting ), I am back to having no wireless, following an upgrade to quantal. 

Any help would be appreciated. I have posted a new thread here 
[http://ubuntuforums.org/showthread.php?p=12443560](http://ubuntuforums.org/showthread.php?p=12443560)

---

