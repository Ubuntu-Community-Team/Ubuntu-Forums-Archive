---
title: "HP dm 1-3025dx help!!"
date: 2011-07-24
forum: Networking &amp; Wireless
---

### Post by blazing64 on 2011-07-24
This is solved go to page #2 for instructions


Hi, I'm pretty new to Ubuntu/Linux, and could use some direction here...
This link will help show my netbook wireless situation:

[http://wontek.com/laptops/laptops/hp-pavilion-dm1-3025dx-review](http://wontek.com/laptops/laptops/hp-pavilion-dm1-3025dx-review)

A quick read of the article says I need to compile a module to get the wireless to work... ??? Now I'm lost... can anyone point me in the right direction to compile a module?? and what exactly would that be doing???:(

I believe I need this wireless driver: Ralink 2011 802.11 b/g/n WiFi Adapter
computer: HP dm 1-3025dx
OS: Ubuntu 10.04 Netbook

---

### Post by wildmanne39 on 2011-07-24
Hi, run these commands in terminal please
```
lsusb
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list All
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by blazing64 on 2011-07-24
```
x@xrt:~$ lsusb
Bus 006 Device 002: ID 148f:2000 Ralink Technology, Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 0bb2:6098 Ambit Microsystems Corp. USB Cable Modem
Bus 004 Device 002: ID 045e:0745 Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 04f2:b236 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
x@xrt:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: RaLink Device [1814:539f]
x@xrt:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

pan0      no wireless extensions.

x@xrt:~$ rfkill list All
Bogus list argument 'All'.
x@xrt:~$ 

```

---

### Post by blazing64 on 2011-07-24
srry for taking so long, had to let the updates finish

---

### Post by wildmanne39 on 2011-07-24
Hi, do you have an internal card and a usb card plugged in at the same time?

---

### Post by blazing64 on 2011-07-24
I sure do... usb plugged directly to modem, wireless card is inside, and inactive... well no usb card, just usb directly to modem

---

### Post by wildmanne39 on 2011-07-24
Hi, I found a thread with your card that is solved with good instructions but you will need to read carefully, if you need more help post back with what you have done and the results, and we will help you.

[http://ubuntuforums.org/showthread.php?t=1740963](http://ubuntuforums.org/showthread.php?t=1740963)

---

### Post by blazing64 on 2011-07-24
Thank-You, wish me luck

---

### Post by blazing64 on 2011-07-24
I believe everything got posted

---

### Post by wildmanne39 on 2011-07-24
Hi, yes you did that is why I took it out of my post, I noticed it as soon as I clicked submit. Good Luck and be careful compiling drivers is a task.

---

### Post by blazing64 on 2011-07-24
TY!! the post worked!! I'm going to list and simplify the steps here, so anyone else with a new Hp 3025dx netbook can get their wifi working.... :



[LIST=1]
[*]Download the  [RT5390PCIe]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekV5THpFM0wyUnZkMjVzYjJGa09URTNNVFl4TkRrMk1TNTZhWEE5UFQweU1ERXdYekV5TVRkZlVsUTFNemt3WDB4cGJuVjRVMVJCWDFZeUxqUXVNQzQwWDFkcFJtbENWRU52YldKdlgwUlFUdz09Qw%3D%3D") driver from ralinktech.com --> Software --> Linux
[*]Unzip the download zip file anywhere. I did it in the default Downloads directory
[*]go to the 2010_xxx extracted directory
[*]go to os/linux/
[*]Edit the config.mk file as below:
HAS_ATE=y (no change, it was originally as is)
HAS_WPA_SUPPLICANT=y (no change, it was originally as is)
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y (no change, it was originally as is)
HAS_ANTENNA_DIVERSITY_SUPPORT=y originally was n -- this was the only thing I modified)
[*]in terminal, cd to the 2010_xx directory
[*]run command 'make'
[*]Make sure 'make compile' exists without errors. I got an error "too  many arguments to format" towards the end of the compile but it did  compile successfully eventually. And so I ignored the errors. You would  see ***errors*** if the compile is not successful. In which, something  went wrong and you may need to tweak the makefile or config.mk files  before compile is successful.
[*]run command 'sudo make install'
[*]reboot your machine... wifi should now work
[/LIST]
again, this wasn't my post, but hopefully this helps the next poor guy 

Thnx wildmanne39!!

---

### Post by wildmanne39 on 2011-07-24
Hi, that is great I am glad it worked and I must say that you must be a very sharp person to have got it to work that quickly.

Thank you for posting this procedure it will help many people in the future,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by blazing64 on 2011-07-24
yeah, was wondering how to mark as solved, TY!!

---

### Post by wildmanne39 on 2011-07-24
Hi, your are very welcome!

---

