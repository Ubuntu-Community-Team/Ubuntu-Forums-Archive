---
title: "Ubuntu video on HP Pavilion g7 1153er with hybrid radeon 6470M and Intel 3000"
date: 2013-09-05
forum: Multimedia Software
---

### Post by i-koliadynskyy on 2013-09-05
Hello everybody. I will start this thread like most of people. :)
I  am new guy in Ubuntu. I have tried to make right installation but always  getting some problems. I have laptop HP Pavilion g7 1153er. 
This  laptop equipped with ATI Radeon HD 6470M and i5 2410M CPU so I have  hybrid graphic with Intel hd video 3000. I have took this laptop with  Windows.

But I am working with web-services and developement a  lot so would like change my OS to Ubuntu. I have started with Ubuntu  12.04 and got that my system doesnt want to start up without additional  parameter nomodeset. I have used it, install OS and thought that problem  is with radeon. So I have installed (from 7 time reinstalled OS) driver  from amd site. But this isn't help. When I checked my logs I see that  main problem is with intel video.
```
Fatal server error:
[    18.145] atiddxProbe: fail to probe intel VGA device
[    18.145] (EE) 
Please consult the The X.Org Foundation support 
    at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    18.145] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    18.146] (EE)
```

I checked  intel drivers and saw that they are adapted to Ubuntu 13.04 now. So I  have tried few times install them to Ubuntu 12.04 and failed. To move  further I have installed Ubuntu 13.04. This system required two  additional boot parameters to work: acpi=off and nomodeset. I have  installed and seen that it works with slow screen processing. Than I  installed Intel driver and this helped to me remove acpi=off from boot  string.

I have digged a lot of info to check all this things like  a new user. I know that experience it is great but I am trying to solve  this problem third day and my work is stopped. Do not want to switch  back :)

So could any body help me to find solution for video processing speed. I still thinking that problem is with drivers.
What is the best in my situation? And do I need to use nomodest for each start up?

Please help me with this problem or post some links for similar problem. I have checked many posts but problems was little bit different.

Sorry for my english and thanks :)

Maybe this will help.
```
uname -a
Linux w-HP-Pavilion-g7 3.8.0-19-generic #30-Ubuntu SMP Wed May 1 16:35:23 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

```
lspci -k | grep VGA -A2
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Hewlett-Packard Company Device 1672
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
--
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M/7400M Series]
    Subsystem: Hewlett-Packard Company Device 1672
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)

```

---

### Post by i-koliadynskyy on 2013-09-05
I have move further and tried to install amd driver .... thought it will help. After generation of xorg.config and reboot I have got again error in xorg
atiddxProbe: fail to probe intel VGA device

after revert xorg.config to backup I was able to start ubuntu but the desktop was empty. I have tried to start unity but got another 

error compiz (core) - Error: Plugin 'opengl' not loaded.

Completely confused :(

---

### Post by i-koliadynskyy on 2013-09-10
anyone? :(

---

### Post by SeijiSensei on 2013-09-10
If you don't care about switching between the Intel and ATI graphics chips, go into the BIOS and turn on "fixed mode."  That will force the machine to use the ATI chip all the time.  Now run the "Additional Drivers" application to make sure it has installed the ATI driver.  I'm using an HP dv6t here with the ATI device forced on and an HDMI connection to a television.

---

### Post by i-koliadynskyy on 2013-09-11
Thanks for reply.

 I have posted one forum ([https://www.linux.org.ru/forum/linux-hardware/9564762?lastmod=1378898678815](https://www.linux.org.ru/forum/linux-hardware/9564762?lastmod=1378898678815)) and I  have got reply with suggestion to try "acpi_backlight=vendor" option for  grub. This helped a lot. With using acpi_backlight=vendor option  without nomodest I have seen right graphics for ubuntu 12.04 but havent  set hybrid graphics there right.

 
Than I have tried to do the same with Ubuntu 13.04. And made:
    1) “acpi_backlight=vendor” option in start line for installation Ubuntu 13.04
    2) after installing OS all grub options left configurated in grub. So I have installed intel driver than([https://01.org/linuxgraphics/downloads](https://01.org/linuxgraphics/downloads))
    3) checked grub configuration,
   ```
 $ sudo gedit /etc/default/grub
```
    keeped “acpi_backlight=vendor”, and  removed “nomodeset” from there and got GRUB_CMDLINE_LINUX="acpi_backlight=vendor"
    saved config
    ```
$ sudo update-grub
```
    4) installed ati catalyst according to [http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Raring_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx)
    

And after this steps I have got all my problems solved

 The main reason of atiddxProbe: fail to probe intel VGA device was using of “nomodeset” at grub for boot without black screen but “acpi_backlight=vendor” helped a lot.

---

