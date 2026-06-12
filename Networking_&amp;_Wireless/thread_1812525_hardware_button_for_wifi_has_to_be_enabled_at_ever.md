---
title: "hardware button for wifi has to be enabled at every power on"
date: 2011-07-26
forum: Networking &amp; Wireless
---

### Post by b3rylord on 2011-07-26
After upgrading from 10.10 to 11.04 via the online upgrading method I had much trouble getting wireless to work but after following the instructions at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) it burst into life, that is until I powered off and now I have to sudo modprobe b43 before the hardware button for the wifi will work and and then I am able to get online. This is for every power on session!! Once enabled it will switch on and off via the hardware button and the light is operational. 
Before the sudo modprobe b43 the button does something as evidenced by sudo rfkill list after each press of the button. Is there any way to have the command sudo modprobe b43 inserted somewhere in the power on sequence? This was a working function on 10.10!

---

### Post by mikewhatever on 2011-07-26
To make sure b43 gets autoloaded at startup, try adding it to /etc/modules.

```
gksudo gedit /etc/modules
``` 

or use the following command once:

```
echo b43 | sudo tee -a /etc/modules
```

---

### Post by b3rylord on 2011-07-28
> **mikewhatever said:**
> To make sure b43 gets autoloaded at startup, try adding it to /etc/modules.

```
gksudo gedit /etc/modules
```or use the following command once:

```
echo b43 | sudo tee -a /etc/modules
```

Thank you so much for that, the second option worked fine!! Could you break down the command to tell me what it is doing? I am trying to get savvy with some of the commands!!

---

### Post by mikewhatever on 2011-07-28
Sure, echo just prints out whatever comes after it, in this case, b43, | is a pipe that redirects or pipes the first command through the second, and 'tee -a' just appends data to the specified file.

---

