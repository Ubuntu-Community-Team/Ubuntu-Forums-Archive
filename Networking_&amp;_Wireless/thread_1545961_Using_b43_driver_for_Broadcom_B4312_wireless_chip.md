---
title: "Using b43 driver for Broadcom B4312 wireless chip"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by nathanf534 on 2010-08-04
I just installed Ubuntu 8.04, and wireless was working without having to do anything. When I go to Hardware Drivers, I see only "Broadcom STA wireless driver" and it is disabled, and not in use, so Im not even sure what driver is being used.

I want to be able to use the B43 driver using fwcutter, but I can't get it to work.

Ive used [http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/](http://penkin.wordpress.com/2008/03/28/ubuntu-804-broadcom-wireless/) to use fwcutter, but after I restart the computer, it seems like that didn't accomplish anything. There aren't any other drivers listed under Hardware Drivers.

Here is some information about my current setup.

```

nathan@lappy:~$ lspci | grep Network
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

``````

nathan@lappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:2  Signal level:182  Noise level:168
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


```

---

### Post by snowpine on 2010-08-04
Welcome to the forums Nathan!

The best source of "Broadcom on Ubuntu" information that I am aware of is here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

You mention that "wireless was working without having to do anything" so I am not exactly sure what your question is? :)

---

### Post by nathanf534 on 2010-08-04
> You mention that "wireless was working without having to do anything" so I am not exactly sure what your question is? :smile:Sorry, I forgot to mention that. I need the b43 drivers so I can use Monitor mode on my wireless card. The STA driver doesn't support monitor mode.


Also, Ive tried the site you just provided earlier already, but I get the same problem as before, I don't see any new drivers available, and nothing is different.

And Ive already checked the my chipset and PCI-ID are supported by the b43 driver.

---

### Post by snowpine on 2010-08-04
> **nathanf534 said:**
> Sorry, I forgot to mention that. I need the b43 drivers so I can use Monitor mode on my wireless card. The STA driver doesn't support monitor mode.


Also, Ive tried the site you just provided earlier already, but I get the same problem as before, I don't see any new drivers available, and nothing is different.

I am not familiar with the "monitor mode" feature, sorry. :(

---

### Post by nathanf534 on 2010-08-04
> I am not familiar with the "monitor mode" feature, sorry. 

Well then forget that I need monitor mode :P, I just need help getting the b43 driver working, I can get monitor mode to work easily after that.

---

### Post by bkratz on 2010-08-04
> **nathanf534 said:**
> Well then forget that I need monitor mode :P, I just need help getting the b43 driver working, I can get monitor mode to work easily after that.

If using 8.04, you may have trouble with the b43 driver (obviously), it was not well supported until much later, about 9.10 I think ( could be wrong). Anyway, you may want to input the following in the terminal

```
lspci -vnn | grep 14e4
```

Then go to this link and see if your particular 4312 is even supported by b43

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

---

### Post by nathanf534 on 2010-08-04
> If using 8.04, you may have trouble with the b43 driver (obviously), it was not well supported until much later, about 9.10 I thinkFunny you say that, I was trying it on 9.10 and couldn't get it to work for similar reasons, so I tried 8.04 to see if it would be any different. 

I don't mind switching Ubuntu versions if you know one that is sure to work.

Also, I have already checked 
lspci -vnn | grep 14e4
 and mine is supported.

```
nathan@lappy:~$ lspci -vnn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

---

### Post by snowpine on 2010-08-04
> **nathanf534 said:**
> Well then forget that I need monitor mode :P, I just need help getting the b43 driver working, I can get monitor mode to work easily after that.

I've never tried b43, as STA works perfectly for my needs... perhaps another member can be of further assistance. :)

---

### Post by bkratz on 2010-08-04
> **nathanf534 said:**
> Funny you say that, I was trying it on 9.10 and couldn't get it to work for similar reasons, so I tried 8.04 to see if it would be any different. 

I don't mind switching Ubuntu versions if you know one that is sure to work.

Also, I have already checked 
lspci -vnn | grep 14e4
 and mine is supported.

```
nathan@lappy:~$ lspci -vnn | grep 14e4
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```


At that site---
If you look carefully it was not supported until the 

```
14e4:4315
supported 2.6.33 and later (PIO mode)
```

This kernel was not used until 10.04 , so 9.10 would have been a problem.

use

uname -rm

to see what kernel you have.

---

### Post by snowpine on 2010-08-04
> **bkratz said:**
> If you look carefully it was not supported until the 

```
14e4:4315
supported 2.6.33 and later (PIO mode)
```

This kernel was not used until 10.04 , so 9.10 would have been a problem.

Actually 10.04 uses 2.6.32 so I think you are out of luck until 10.10 is released.

---

### Post by bkratz on 2010-08-04
> **snowpine said:**
> Actually 10.04 uses 2.6.32 so I think you are out of luck until 10.10 is released.


I went ahead and hooked up my 10.04 system just to see the kernel and it is indeed  2.6.32-24, I usually use 9.04 (personal preference, because my intel graphics are better). Sorry about the error--you could update the kernel all the way up to the daily build of

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

all the way to 2.6.35, but I would just wait you could introduce other problems.

---

### Post by bkratz on 2010-08-04
If interested in the above

[http://www.ubuntugeek.com/kernel-2-6-35-officially-available-for-ubuntu-10-04.html](http://www.ubuntugeek.com/kernel-2-6-35-officially-available-for-ubuntu-10-04.html)

---

### Post by nathanf534 on 2010-08-04
thanks bkratz, I will try this and post what I get.

---

### Post by nathanf534 on 2010-08-04
ok, so I installed the newest version of Ubuntu available, (10.4) and followed the instructions you gave me to upgrade the kernel.

After the upgrade, uname -rm returns 2.6.32-24-generic i686, and I need 2.6.33 for the b43 driver to work, however I was able to install the b43 driver, and successfully put my wireless card in monitor mode anyway.

Thanks for all the help, this is a great forum :D

---

### Post by snowpine on 2010-08-04
> **nathanf534 said:**
> ok, so I installed the newest version of Ubuntu available, (10.4) and followed the instructions you gave me to upgrade the kernel.

After the upgrade, uname -rm returns 2.6.32-24-generic i686, and I need 2.6.33 for the b43 driver to work, however I was able to install the b43 driver, and successfully put my wireless card in monitor mode anyway.

Thanks for all the help, this is a great forum :D

Awesome news! Now you have me curious about "monitor mode"... I'm assuming it's an Aircrack kind of thing?

---

### Post by coldraven on 2010-08-04
I'm using 10.04 (32bit) and I think that I have the same Broadcom controller. It works for me using the STA driver although I always have a Red exclamation mark on the Network Wi-Fi icon.
I've no idea what that means! It connects within a few seconds and has not given me any trouble.

```
10:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express [14e4:1693] (rev 02)
30:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)

```

---

### Post by bkratz on 2010-08-04
Sure glad you figured out how to get it working, ( I'm sure for aircrack!) post one Coldraven he already had the STA driver working but realized that the STA driver does not allow the monitor mode.

If you can go to the thread tools and mark it solved perhaps it will help someone else.

---

### Post by nathanf534 on 2010-08-06
> Awesome news! Now you have me curious about "monitor mode"... I'm assuming it's an Aircrack kind of thing?

Monitor mode lets your wireless card read any packet that is in the air, not just packets from the AP you are connected to. It is necessary for things such as aircrack.

Also, I just noticed the b43 driver also allows packet injection. :)

---

### Post by rlelliott on 2010-09-23
b43 monitor mode works out of the box with SECmic3.1 @ secmic.org

---

### Post by bobharvey on 2010-09-28
> **coldraven said:**
> I'm using 10.04 (32bit) and I think that I have the same Broadcom controller. It works for me using the STA driver although I always have a Red exclamation mark on the Network Wi-Fi icon.
I've no idea what that means! It connects within a few seconds and has not given me any trouble.

I have the same situation, and as a start have reported at least the lack of documentation of the red pling as a bug:
[https://bugs.launchpad.net/bugs/649632](https://bugs.launchpad.net/bugs/649632)

---

