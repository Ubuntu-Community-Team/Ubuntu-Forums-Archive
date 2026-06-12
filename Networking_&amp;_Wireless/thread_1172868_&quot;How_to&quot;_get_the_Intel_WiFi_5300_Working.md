---
title: "&quot;How to&quot; get the Intel WiFi 5300 Working in Ubuntu 9.04"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by HunterThomson on 2009-05-29
[COLOR="Blue"][SIZE="3"]How to get the Intel WiFi 5100 5300 Working in Ubuntu 9.04[/SIZE][/COLOR]
by, HunterThomson - HowTo's that WORK ! [COLOR="Red"][SIZE="4"]But not this one ;)[/SIZE][/COLOR]
[COLOR="Red"][SIZE="4"]Out of Date
It seems Ubuntu messed up this Kernel before it was officially released
Try the newest Kernel in this repo I talk about in this HowTo
Or look at page 2. I have info on how to install the 2.6.30 Kernel[/SIZE][/COLOR]

[COLOR="Blue"]OK, you will need to install the new Pre-released Kernel and backports
I think that it is really just the new Ubuntu Kernel that is fixed. So, when we officially are on Ubuntu Kernel 2.6.28-12 then you probably will not need to do this.[/COLOR]


_>You will need to enable Ubuntu Pre-released updates by first opening the "Software Sources" GUI here..._

You can find it here...
```
System/Administration/Software Sources
```

_>Now click on the "Updates" Tab and check the box to the left of "Pre-released updates (jaunty-proposed)"_

_>Then click close and it will up date the package list._

_>Now open a terminal and install the linux-backports-modules-jaunty_

```
sudo apt-get update && sudo apt-get install linux-backports-modules-jaunty
```

_>Now [COLOR="Red"]DON'T Reboot[/COLOR]_

_>Install the Kernel headers for this new Kernel because you will need them latter._

```
sudo apt-get install linux-headers-2.6.28-12-generic
```

>Ok all done really just go back into the "Software Sources" and Un-check that box next to the "Pre-released updates (jaunty-proposed)"

>Then click "close" and it will update the package list agin. And Reboot :)

--------------------------------------------------------------------
"5100" "5300" "intel" "intel wireless 5300" "intel wireless 5100" "How To" "Fixed" "Solved" "working" "Not Working" "Corruption" "Download"  site:ubuntuforums.org

---

### Post by greenie9 on 2009-06-12
Hi,

I have a Dell studio 15 laptop, which has the 5300 wireless card in it
I followed your guide, and mine still doesnt work :(
Am attempting to connect to an 802.11n router using WPA encryption
it shows the icon in the top right as connecting, and it has 2 green lights, but it still keeps going round and round in circles
my WPA key doesnt get stored as plain text and more, it comes out as a heap of gibberish, so im not sure if that is part of the problem

and/all help would be appreciated, thanks!

> 04:00.0 Network controller: Intel Corporation PRO/Wireless 5300 AGN [Shiloh] Network Connection
        Subsystem: Intel Corporation Device 1121
        Flags: bus master, fast devsel, latency 0, IRQ 2297
        Memory at f8000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

never mind, found this:
[http://ubuntuforums.org/showpost.php?p=7415234&postcount=3](http://ubuntuforums.org/showpost.php?p=7415234&postcount=3)

---

### Post by HunterThomson on 2009-06-13
Well thanks for that link :) I bet other people looking at this tread will be helped by that. 

Also, I am glad you got it fixed.

---

### Post by dzuchowski on 2009-08-26
> **greenie9 said:**
> Hi,

I have a Dell studio 15 laptop, which has the 5300 wireless card in it
I followed your guide, and mine still doesnt work :(
Am attempting to connect to an 802.11n router using WPA encryption
it shows the icon in the top right as connecting, and it has 2 green lights, but it still keeps going round and round in circles
my WPA key doesnt get stored as plain text and more, it comes out as a heap of gibberish, so im not sure if that is part of the problem

and/all help would be appreciated, thanks!



never mind, found this:
[http://ubuntuforums.org/showpost.php?p=7415234&postcount=3](http://ubuntuforums.org/showpost.php?p=7415234&postcount=3)


> **Evil Dax said:**
> Jaunty64, Intel WiFiLink 5100 and WPA2

lspci:
07:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

OS:
Jaunty64: 2.6.28-11-generic

Issue:
non-secured and WEP working, while WPA and WPA2 fail to connect

Solution:
download latest microcode from Intel:
[http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz](http://intellinuxwireless.org/iwlwifi/downloads/iwlwifi-5000-ucode-8.24.2.12.tgz)
put the file into /lib/firmware

change modprobe:
```

sudo modprobe -r iwlagn
sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

```And you can connect to WPA2

how do you copy the intel microcode from intel link to the /lib /firmware

---

### Post by HunterThomson on 2009-08-27
> **dzuchowski said:**
> how do you copy the intel microcode from intel link to the /lib /firmware

I have never done it but I would guess you simply copy the file there and make sure the permissions are correct.

---

### Post by imitsi on 2009-08-27
Hi there

I'm running Ubuntu 9.04 (fully updated) on VMware and I can't get it to see my Intel 5100. I have tried the instructions above but they weren't successful. Anything else I can try?

Many thanks

imitsi

---

### Post by imitsi on 2009-08-27
Kernel is 2.6.28-15-generic

---

### Post by dzuchowski on 2009-08-27
> **HunterThomson said:**
> I have never done it but I would guess you simply copy the file there and make sure the permissions are correct.

a simple drag and drop with the mouse wont work as it is a protected area of the file system.  I know we need to use the sudo cp command but do not know how to do that. I wish linux was more like Windows Vista and I could just drag and drop the directory or files to were I want them. Does anyone know how to copy the files over? I think i have them on my flash drive and also on my desktop as well for kubuntu. Also which is better ubuntu with genome or kbuntu with kde 4.3.. Yes i upgraded it to 4.3 kde... from the command line no less... thanks google.

---

### Post by HunterThomson on 2009-08-27
> **dzuchowski said:**
> a simple drag and drop with the mouse wont work as it is a protected area of the file system.  I know we need to use the sudo cp command but do not know how to do that. I wish linux was more like Windows Vista and I could just drag and drop the directory or files to were I want them. Does anyone know how to copy the files over? I think i have them on my flash drive and also on my desktop as well for kubuntu. Also which is better ubuntu with genome or kbuntu with kde 4.3.. Yes i upgraded it to 4.3 kde... from the command line no less... thanks google.

You need to open the file manager as the root user. You can do this a couple ways. You could run the application form the terminal as the sudo user.

```
sudo konqueror
```

Or there should be and option in konqueror to open the current directory as root.

---

### Post by HunterThomson on 2009-08-27
> **imitsi said:**
> Kernel is 2.6.28-15-generic

It would seem that this HowTo is out of date. I'll update it and post when I have.

You know I would maybe try installing the new Kernel 2.6.30. I'll post how to do that and try it, tell us if it works.

---

### Post by HunterThomson on 2009-08-27
This is this guy Wyth that posted this in another thread for something ells but it will tell you how to install the 2.6.30 kernel.

The reason I went with the 2.6.30 kernel was to disable IPv6 system-wide. In the current kernel, IPv6 is enabled automatically, and it can't be turned off without recompiling the kernel. I didn't feel like recompiling, and I wanted the speed boost afforded by turning off IPv6, so 2.6.30 kernel, here we come.

If you're interested in trying it out (and it may solve a few other hardware issues for some), here's what to do (borrowed from the HOWTO: Jaunty Intel Graphics Performance Guide).

In your terminal, run the following commands, depending on the system you're using (32 bit or 64 bit):

i386 users:

```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_i386.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_i386.deb
$ sudo dpkg -i linux-headers-2.6.30-02063003-generic_2.6.30-02063003_i386.deb linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb linux-image-2.6.30-02063003-generic_2.6.30-02063003_i386.deb
```

amd64 users:

```
$ wget -c http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.3/linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb
$ sudo dpkg -i linux-headers-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb linux-headers-2.6.30-02063003_2.6.30-02063003_all.deb linux-image-2.6.30-02063003-generic_2.6.30-02063003_amd64.deb
```

---

