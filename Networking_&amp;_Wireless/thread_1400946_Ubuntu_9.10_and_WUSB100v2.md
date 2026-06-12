---
title: "Ubuntu 9.10 and WUSB100v2"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by f2dfashion on 2010-02-07
I am by far an expert but I wanted to post this to hopefully save some people hours of wanting to pull their hair out, so here it goes.

**Blacklisting modules**

Open terminal
```
sudo gedit /etc/modprobe.d/blacklist.conf 
```

And add...
```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
blacklist ndiswrapper
```

Save and exit.

**Compiling a New Kernel Module (Driver)**

You'll need a compiler and Linux headers installed
```
sudo apt-get install build-essential linux-headers-generic
```

**Config and Install Driver**

Next you have to download the rt3070USB driver from ralinktech (Will add link if mod allows)

Extract these files then move to the dir. in terminal:
```
cd Downloads/2009_1110_RT3070_Linux_STA_v2.1.2.0
```

Next, we have to make a few adjustments to the config...

Start with config.mk in /os/linux/:
```
gedit /os/linux/config.mk
```

Then find:
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=n
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n
```

and change to:
```
# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=y
# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y
```

Save and close

Then open usb_main_dev.c in /os/linux/:
```
gedit /os/linux/usb_main_dev.c
```

Then add the following before the #endif
```
{USB_DEVICE(0x1737,0x0078)}, /* Linksys WUSB100v2 */
```

**Compile**

Now run:
```
make
make install
```

Now you have to delete the rt2870sta that came with the install and load the new module
```
sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/staging/rt2870
modprobe rt3070sta
insmod /lib/modules/`uname -r`/kernel/drivers/net/wireless/rt3070sta.ko

```

Now if you run iwconfig you should see an ra0 interface but if you run ifconfig its not there. So here is the fix:
```
mv /etc/Wireless/rt3070sta /etc/Wireless/rt2870sta
```

Now restart network-manager:
```
/etc/init.d/networking restart
restart network-manager
```

Now you should see wireless connections available in network manager (This may require a restart)

I hoped this helped and like I said I am no expert and this was from doing research and forgive me if some is out of order I did my best to replicate what I did.

Plus I would like to thank peepingtom from ubuntuforums (Will add link if mod allows)
because he was vital in figuring this out and I hope this helps.

~Bruce

---

