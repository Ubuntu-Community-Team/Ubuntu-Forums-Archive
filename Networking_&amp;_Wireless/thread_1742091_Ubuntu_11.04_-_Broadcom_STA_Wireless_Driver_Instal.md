---
title: "Ubuntu 11.04 - Broadcom STA Wireless Driver Install fail - Broadcom BCM4313"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by angbermu on 2011-04-28
After installing natty 11.04 (fresh install) I got an error trying to activate the Broadcom STA Wireless Driver in my **Dell Latitude e6510**. Going into the Synaptic Package Manager and selecting "Mark for Reinstallation" resolved the issue for me...

My Wireless Card: **Broadcom BCM4313**

Error: *"Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log"*

In logfile /var/log/jockey.log I got:
*2011-04-28 11:39:40,365 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver*

---

### Post by xz2yqb on 2011-04-29
I have a similar problem. my wireless connection is disabled after upgrade from ubuntu 10.10 to 11.04.

---

### Post by Sef on 2011-04-29
Moved to N & W.

Check out this [thread]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers").

---

### Post by gco79 on 2011-04-29
Hi
the important part of the link above for me was this bit:

> **Note:** On Ubuntu 11.04 installing the  'firmware-b43-installer' package takes care of the downloading and  installation of the b43 driver. 

Wireless fired up immediately after installing that

---

### Post by 4000xt on 2011-04-29
Hi,

I had the exact same issue as you 10.10 wireless was working fine but when I upgraded to 11.04 it stopped working and would not find the wireless card.

1) Goto this webpage - [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Scroll down to the section Installing b43 drivers and follow the steps there to install the drivers.

When I completed that I was able to see my wireless card but it was complaining that there was no firmware install.

2) Goto the webpage - [http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation](http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation)

Scroll down to the heading Other distributions not mentioned above.

Here are the steps i followed.

   1 wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2)    
2 tar xjf b43-fwcutter-013.tar.bz2    
3 cd b43-fwcutter-013    
4 make    
5 cd ..

and then the following

   1 export FIRMWARE_INSTALL_DIR="/lib/firmware"    
2 wget [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)    
3 tar xjf broadcom-wl-4.178.10.4.tar.bz2    
4 cd broadcom-wl-4.178.10.4/linux    
5 sudo ../../b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

This should get your card working.  Mine fired up right away. Goodluck

---

### Post by angbermu on 2011-04-29
I think that as the card is a BCM4313 the driver needed is the broadcom-sta, b43 seems not to be supported.


**[Unsupported chips]("http://wireless.kernel.org/en/users/Drivers/b43#Unsupported_chips")** for b43/b43legacy.

lspci -vnn | grep BCM
```
02:00.0 Network Controlled [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727]
```

On the other hand I had today fixed a HP Laptop with a BCM4318 with the 'firmware-b43-installer' package.

---

### Post by 4000xt on 2011-04-29
Sorry I should have paid more attention to that.

---

### Post by tynen on 2011-04-29
'Mark for re-installation' bcmwl-kernel-source fixed the problem for me. Wireless is working great now on my Dell Latitude E6510.

---

### Post by Gnorrogh on 2011-04-30
[https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397/comments/6](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397/comments/6)

Did the trick for me, just installed Maverick's version of the driver, and it fired up like a charm just like it used to do. Got a BCM4311. =)

---

### Post by xz2yqb on 2011-04-30
in the step 5 of the second part, does the command is completed??
thanks

> **4000xt said:**
> Hi,

I had the exact same issue as you 10.10 wireless was working fine but when I upgraded to 11.04 it stopped working and would not find the wireless card.

1) Goto this webpage - [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Scroll down to the section Installing b43 drivers and follow the steps there to install the drivers.

When I completed that I was able to see my wireless card but it was complaining that there was no firmware install.

2) Goto the webpage - [http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation](http://wireless.kernel.org/en/users/Drivers/b43#firmwareinstallation)

Scroll down to the heading Other distributions not mentioned above.

Here are the steps i followed.

   1 wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-013.tar.bz2)    
2 tar xjf b43-fwcutter-013.tar.bz2    
3 cd b43-fwcutter-013    
4 make    
5 cd ..

and then the following

   1 export FIRMWARE_INSTALL_DIR="/lib/firmware"    
2 wget [http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.178.10.4.tar.bz2)    
3 tar xjf broadcom-wl-4.178.10.4.tar.bz2    
4 cd broadcom-wl-4.178.10.4/linux    
5 sudo ../../b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta.o

This should get your card working.  Mine fired up right away. Goodluck

---

### Post by 4000xt on 2011-05-01
> **xz2yqb said:**
> in the step 5 of the second part, does the command is completed??
thanks

Just make sure the last command is pointing to where the b43-fwcutter program is located.
Let me know how you make out.

---

### Post by gaston1982 on 2011-05-02
> **Gnorrogh said:**
> [https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397/comments/6](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/711397/comments/6)

Did the trick for me, just installed Maverick's version of the driver, and it fired up like a charm just like it used to do. Got a BCM4311. =)

This also worked for me on my Dell Vostro 3500

---

### Post by rafaelgranado on 2011-05-03
I also have a DELL Vostro 3500. I can't remove the new driver to install the old one.

It says that the catalog needs to be repaired

---

### Post by L1mit30 on 2011-05-04
I have a similar problem. Seems that wifi and lan drivers are all there. Now when I boot my laptop (Inspiron N7010) the network manager applet says under wifi disconnected. I cant make it to scan or detect any networks. When I shut down the laptop and I boot it with the LAN cable in, the wifi starts scanning and it works like a charm. So i am not sure if it is a module issue or what. If is it how can I make it to "start" when the laptop is booting? 
The driver that my laptop is using for the wifi when it is working is the brcm80211.

Any tip will help. Thank you.

---

### Post by Dudi00 on 2011-06-04
Hello I have similar problem with Toshiba a660-1ex BCM4313.

When I want make step 5 it said that comand not found, what's wrong?

---

### Post by dicle on 2011-06-28
[SIZE=2]Hi,
You may use the driver provided by the producer here, [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

readme.txt explains everything. [/SIZE][SIZE=2]Immediately [/SIZE][SIZE=2]after completing the installation, available wireless networks should be visible.

[/SIZE]

---

### Post by sepul6 on 2011-09-01
I had the same problem, and my wireless didn't appear after :
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```

but I have found that b43 is conflicting with another module (lib80211/wl)
so in this case, run  :
```

lsmod | grep wl

```

if it shows something, uninstall wl and lib80211 modules
```

sudo rmmod wl
sudo rmmod lib80211

```


It is now fixed, and ubuntu (11.04) recognizes my Dell D620 wireless

---

### Post by ataraxic on 2011-10-01
I've had the same problem. I've got lenovo s10-3s. Installed 11.04 from scratch. wireless was not working. After couple of hours of struggling I've found what was the problem. For some reason *acer-wmi* module was installed:
```

# lsmod | grep acer
acer_wmi               23153  0 
sparse_keymap          13666  2 acer_wmi,ideapad_laptop

```

And the *rfkill* gives me the following results:
```

# rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

After removing *acer-wmi*
```

# modprobe -r acer-wmi

```

it immediately starts up and works like charm!
*rfkill* gives
```

# rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

And don't forget to *blacklist* it:
```

# echo "blacklist acer-wmi" >> /etc/modprobe.d/blacklist.conf

```

so it won't be loaded by default.
Cheers.

---

### Post by zooey on 2011-10-08
i had the same problem with lenovo idepad and adding acer_wmi to blacklist worked for me :)

---

### Post by collisionystm on 2011-10-08
lol I just did this the other day. It was extremely simple.

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

And here are the directions for Debian you can reference.

[http://wiki.debian.org/wl#Squeeze](http://wiki.debian.org/wl#Squeeze)

Good Luck! I can say my BCM4313 on a Vostro is working like a champ. Now If I could get the stupid amd audio to work....

---

