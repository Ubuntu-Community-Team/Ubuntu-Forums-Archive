---
title: "toshiba nb505 wifi not working"
date: 2011-12-08
forum: Networking &amp; Wireless
---

### Post by mrvn on 2011-12-08
Hi I'm new to Linux running  Ubuntu 10.04  on my netbook. I followed this thread [http://ubuntuforums.org/showthread.php?t=1687719](http://ubuntuforums.org/showthread.php?t=1687719) to initially get the wifi up and running however the wifi stopped working after an update. What should I do to solve this problem ?

---

### Post by Bucky Ball on 2011-12-08
Go through the steps in post #4 on your link again.

---

### Post by mrvn on 2011-12-08
> **Bucky Ball said:**
> Go through the steps in post #4 on your link again.

I followed the steps in post # 4 but the wifi still seems to not work. I get the output : 
rtl8192ce-dkms is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded

---

### Post by Bucky Ball on 2011-12-09
Oh, okay. Open a terminal and try this:

```
sudo apt-get update
```Then;

```
sudo apt-get upgrade
```This *will not* upgrade your Ubuntu release but all packages it is using. You need to get online with a cable to get this working. You might also then look in System>Admin>Additional Drivers

---

### Post by mrvn on 2011-12-09
> **Bucky Ball said:**
> Oh, okay. Open a terminal and try this:

```
sudo apt-get update
```Then;

```
sudo apt-get upgrade
```This *will not* upgrade your Ubuntu release but all packages it is using. You need to get online with a cable to get this working. You might also then look in System>Admin>Additional Drivers

I did a upgrade but still nothing. When I go to the drivers option I get a reading of: 
            
            Linux driver for Realtek RTL819x WiFi cards 

            the driver is activated but not currently in use

Is this the problem ? All I have to do is activate the driver ?

---

### Post by Bucky Ball on 2011-12-09
Yep. Try de-activating it then switching it on again. Watch for any error messages that may appear and let us know (unless it works, that is). ;)

---

### Post by mrvn on 2011-12-09
> **Bucky Ball said:**
> Yep. Try de-activating it then switching it on again. Watch for any error messages that may appear and let us know (unless it works, that is). ;)

I tried the deactivating it & turning it back on again. That didn't work, is there a way activate it through the command line?

---

### Post by Bucky Ball on 2011-12-09
Could you open Synaptic package and search for b43. What have you got installed that has b43 in its name? Anything? Try installing b43-fwcutter and firmware-b43-installer. Reboot. You may only need the latter but give both a go. 

I just checked your link again and those steps really shouldn't be necessary anymore. Something that happened with whatever was installed there may be your issue but let's keep digging. ;)

---

### Post by mrvn on 2011-12-09
> **Bucky Ball said:**
> Could you open Synaptic package and search for b43. What have you got installed that has b43 in its name? Anything? Try installing b43-fwcutter and firmware-b43-installer. Reboot. You may only need the latter but give both a go. 

I just checked your link again and those steps really shouldn't be necessary anymore. Something that happened with whatever was installed there may be your issue but let's keep digging. ;)

I found b43-fwcutter and and installed it + rebooted my machine. Couldn't find firmware-b43-installer in the package manager.

---

### Post by mrvn on 2011-12-09
I'm reading this page : [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20Internet%20access") and it says *"On Ubuntu 11.04 installing the 'firmware-b43-installer' package takes care of the downloading and installation of the b43 driver" *I got b43-fwcutter but how do I download and install firmware-b43-installer ? Seems like this is what I really need... maybe I need to read this over.

---

### Post by Bucky Ball on 2011-12-09
Simple. Synaptics Package Manager. Search for and install firmware-b43-installer. Reboot. As I mentioned ...

---

