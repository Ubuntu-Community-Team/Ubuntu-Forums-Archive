---
title: "Azio AWD102N - I give up!"
date: 2011-05-01
forum: Networking &amp; Wireless
---

### Post by eitsuop on 2011-05-01
I tried downloading the driver provided on their website, couldn't compile it.

I tried [this tutorial]("http://ubuntuforums.org/showthread.php?t=1476007"), and I was doing well until I got to the part where I was supposed to run this:
```
sudo ifconfig wlan0 down
```
which resulted in:
```
wlan0: ERROR while getting interface flags: No such device

```
which I searched for and got no solution for.
So I tried to use ndiswrapper as a last resort, and found a guide to [here]("http://ubuntuforums.org/showthread.php?t=1481710"), but look at that! I need to run the ifconfig for that one, too.

Does ANYONE have a way to get this wireless card working on 10.10? I've been at it for hours, and it's not even my computer...

Thank you for ANY help you can provide.

EDIT: Is this card supported natively in 11.04? Should I upgrade?

---

### Post by eitsuop on 2011-05-03
I hate to be a bumper, but my brother is currently without a usable computer. Does anyone have any idea what's going wrong with my install attempts?

Are there any commands I can run to get more info, if needed?

---

### Post by chili555 on 2011-05-03
You can safely skip that step. As well, if the module is not loaded when you try the next step, ignore it, too.

Just continue on with the process.

---

### Post by eitsuop on 2011-05-04
Okay, this time I got to step 6 in [this guide]("http://ubuntuforums.org/showthread.php?t=1476007") before hitting a snag. I checked the directory it pointed me to, and the .ko file doesn't exist. The rt2860 folder is there but empty even when I hit CTRL+H

---

### Post by chili555 on 2011-05-04
> Step 6
Rename the old rt2860sta.ko driver file to rt2860sta.ko.dist using:

Code:

sudo mv /lib/modules/2.6.*/kernel/drivers/staging/rt2860/rt2860sta.ko rt2860sta.ko.dist

Attention: you need to replace the * with the actual directory name of your kernel, please check the folder name with Nautilus.
If the .ko file doesn't exist, then there is no need to rename it to keep it from conflicting with the driver you built.

Please proceed.

No one can write a tutorial that fits all cases for all people all the time. I know because I've tried and failed.

---

### Post by eitsuop on 2011-05-04
Sorry, I just didn't know what steps are crucial. I've never had to set up anything manually in Ubuntu before. It always just worked!

---

### Post by eitsuop on 2011-05-04
Nope, even after getting through the entire tutorial, it isn't working.

Does anyone have the INF file or whatever for ndswrapper for this wireless card? I'm getting to last-resort tactics, now.

---

### Post by chili555 on 2011-05-04
Please run and post:```
lspci -nn
modinfo rt2860sta
dmesg | grep -i rt2
```Just post the line in lspci that relates to the Azio; it's probably a Ralink chipset.

I've downloaded the file from their website; let me have a look.

Actually, I believe the card is natively supported in 10.10.

---

### Post by eitsuop on 2011-05-04
```
derek@Derek-Linux:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:0369] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP55 LPC Bridge [10de:0360] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP55 SMBus [10de:0368] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP55 Memory Controller [10de:036a] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036c] (rev a1)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP55 USB Controller [10de:036d] (rev a2)
00:04.0 IDE interface [0101]: nVidia Corporation MCP55 IDE [10de:036e] (rev a1)
00:05.0 RAID bus controller [0104]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:05.1 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:05.2 IDE interface [0101]: nVidia Corporation MCP55 SATA Controller [10de:037f] (rev a2)
00:06.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI bridge [10de:0370] (rev a2)
00:06.1 Audio device [0403]: nVidia Corporation MCP55 High Definition Audio [10de:0371] (rev a2)
00:08.0 Bridge [0680]: nVidia Corporation MCP55 Ethernet [10de:0373] (rev a2)
00:0f.0 PCI bridge [0604]: nVidia Corporation MCP55 PCI Express bridge [10de:0377] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:06.0 Multimedia audio controller [0401]: Creative Labs SB0400 Audigy2 Value [1102:0008]
01:07.0 Network controller [0280]: RaLink Device [1814:3062]
02:00.0 VGA compatible controller [0300]: nVidia Corporation G84 [GeForce 8600 GTS] [10de:0400] (rev a1)
derek@Derek-Linux:~$ modinfo rt2860sta
filename:       /lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/rt2860sta.ko
license:        GPL
version:        2.4.0.0
srcversion:     65223B8B7D9C2800C048813
alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.35-28-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)
derek@Derek-Linux:~$ dmesg | grep -i rt2
derek@Derek-Linux:~$ 

```

And, yes, I also found from a bit of research that it's supposed to be natively supported, but for some reason it isn't working, still. I tried Ubuntu's driver tool thing, too. Nothing. :/

---

### Post by jawilljr on 2011-05-04
Chili,

These steps should get eitsuop chipset working

```
blacklist rt2860sta
install wicd
uninstall network-manager
turn off wifi power management
```

then reboot and it should work

Jerry

---

### Post by chili555 on 2011-05-04
That's very interesting to an old wireless hacker like me. It looks like the module compiled OK. After the fact compilations from Ralink go to kernel/drivers/net/wireless which you have. The built-in rt2860sta is installed in kernel/drivers/staging/rt2860 which I have.

However, if we look at the pci.id for your device:> Network controller [0280]: RaLink Device [[COLOR="Red"]1814:3062[/COLOR]]We notice it is ***not*** mentioned in modinfo for rt2860sta:> alias:          pci:v00001432d00007768sv*sd*bc*sc*i*
alias:          pci:v00001432d00007748sv*sd*bc*sc*i*
alias:          pci:v00001432d00007738sv*sd*bc*sc*i*
alias:          pci:v00001432d00007727sv*sd*bc*sc*i*
alias:          pci:v00001432d00007758sv*sd*bc*sc*i*
alias:          pci:v00001432d00007728sv*sd*bc*sc*i*
alias:          pci:v00001432d00007708sv*sd*bc*sc*i*
alias:          pci:v00001A3Bd00001059sv*sd*bc*sc*i*
alias:          pci:v00001814d00000781sv*sd*bc*sc*i*
alias:          pci:v00001814d00000701sv*sd*bc*sc*i*
alias:          pci:v00001814d00000681sv*sd*bc*sc*i*
alias:          pci:v00001814d00000601sv*sd*bc*sc*i*There is no device number 3062 anywhere in this list. My conclusion is that it's the _wrong_ driver for your device.

The module rt2800pci contains that pci.id, it's a terrible driver.

You could email Azio for guidance.

You could download and compile the right driver rt3562sta from Ralink.

[http://ubuntuforums.org/showthread.php?t=1609086](http://ubuntuforums.org/showthread.php?t=1609086)

I'll be happy to help you in any case.

---

### Post by jawilljr on 2011-05-04
> The module rt2800pci contains that pci.id, it's a terrible driver.

That is the official kernel driver for his PCI chipset.


Just like rt2800usb is the official driver for ralink USB devices.

Jerry

---

### Post by chili555 on 2011-05-04
> These steps should get eitsuop chipset workingUsing what driver, do you imagine? He has NO working driver now, none.> That is the official kernel driver for his PCI chipset.Have you ever seen one actually work satisfactorily? It may be "official" but it's sad.

---

### Post by jawilljr on 2011-05-04
> **chili555 said:**
> Using what driver, do you imagine? He has NO working driver now, none.Have you ever seen one actually work satisfactorily? It may be "official" but it's sad.

He should have the rt2800pci drivers installed still.

Yes... every Ralink device I ever used... those staging driver are sad.  Where do you think Ralink gives there source code to? Take a guess... they give them to [serialmonkey](http://rt2x00.serialmonkey.com/)... and where do they post the drivers at? [compat-wireless](http://wireless.kernel.org)

And whatever is at compat-wireless will eventually get put into the latest kernel.

Jerry

---

### Post by chili555 on 2011-05-04
> He should have the rt2860pci drivers installed still.As I pointed out above, rt2860sta doesn't claim his device. He also reported,> Nope, even after getting through the entire tutorial, it isn't working.

---

### Post by eitsuop on 2011-05-04
When executing:
```
sudo modprobe rt3562sta
```
I get:
```
FATAL: Error inserting rt3562sta (/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/rt3562sta.ko): Device or resource busy
```
And this is even with the network disabled.


Sorry about the chipset confusion, I was led to believe that it was the correct one for the card.

Also, I'm a "she" :)

---

### Post by jawilljr on 2011-05-04
eitsuop

What is the output of 

```
lsmod |grep rt
```

and 

```
cat /etc/modprobe.d/blacklist.conf
```

Jerry

---

### Post by chili555 on 2011-05-04
Device or resource busy usually means it's already driving an interface! Let's see:```
iwconfig
lsmod | grep -e rt2 -e rt3
```Did you download and compile that quickly? I'm impressed!

---

### Post by eitsuop on 2011-05-04
lsmod command gave:
```
rt2860sta             797285  0 
parport_pc             26058  1 
agpgart                32011  1 nvidia
parport                31492  3 ppdev,parport_pc,lp

```

blacklist command gave:
```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

blacklist rt2800pci
blacklist rt2800usb
blacklist rt2800lib

```

Chili's suggestion returned:
```
derek@Derek-Linux:~$ lsmod | grep -e rt2 -e rt3
rt2860sta             797285  0 
derek@Derek-Linux:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by jawilljr on 2011-05-04
I'll let Chili continue...

but if it was my box I would delete these:

```
blacklist rt2800pci
blacklist rt2800usb
blacklist rt2800lib
```

And put this in it's place:

```
blacklist rt2860sta
```

Then reboot.... but you will probable have to install wicd and remove network-manager.

Jerry

on edit here is my 'lsmod |grep -e rt2 -e rt3

```
rt2800usb              18235  0 
rt2800lib              45181  1 rt2800usb
crc_ccitt              12667  1 rt2800lib
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              294370  3 rt2800lib,rt2x00usb,rt2x00lib
cfg80211              178528  2 rt2x00lib,mac80211
```

The only difference you should be seing is the rt2800usb should be replace with rt2800pci.

Jerry

---

### Post by chili555 on 2011-05-04
Please try:```
sudo rmmod -f rt2860sta
sudo modprobe rt3562sta
iwconfig
```

---

### Post by eitsuop on 2011-05-04
> **chili555 said:**
> Please try:```
sudo rmmod -f rt2860sta
sudo modprobe rt3562sta
iwconfig
```

You, sir, are a MIRACLE WORKER. Thank you SO MUCH.

---

### Post by eitsuop on 2011-05-05
Well, it worked great until now. He says he's rebooted about 3 times since we did the fix, and now on reboot number 4 it's stopped working. :mad:

Edit: I got it half working again by blacklisting the rt2860sta one. The network indicator now actually shows the wireless section, but no networks show up.

---

### Post by chili555 on 2011-05-06
Let's do some diagnostics. Reboot so we have a fresh start and do:```
sudo su
modprobe rt3562sta
echo rt3562sta >> /etc/modules
iwlist ra0 scan
exit
```Can you connect now? Does it survive a reboot?

---

### Post by eitsuop on 2011-05-07
```
derek@Derek-Linux:~$ sudo su
[sudo] password for derek: 
root@Derek-Linux:/home/derek# modprobe rt3562sta
FATAL: Error inserting rt3562sta (/lib/modules/2.6.35-28-generic/kernel/drivers/net/wireless/rt3562sta.ko): Device or resource busy
root@Derek-Linux:/home/derek# echo rt3562sta >> /etc/modules
root@Derek-Linux:/home/derek# iwlist ra0 scan
ra0       Interface doesn't support scanning.

root@Derek-Linux:/home/derek# exit
exit
```

---

### Post by chili555 on 2011-05-07
Let's see:```
lsmod | grep -e rt3 -e rt2
demsg | grep -e rt3 -e rt2
modinfo rt3562sta
```Thanks.

---

### Post by funguygordy on 2011-06-28
I am having issues with this wireless card as well.  I am not really sure where to start, but I am running 10.04 (should I upgrade?) and am looking for a push in the right direction.

thanks!

---

### Post by chili555 on 2011-06-28
> **funguygordy said:**
> I am having issues with this wireless card as well.  I am not really sure where to start, but I am running 10.04 (should I upgrade?) and am looking for a push in the right direction.

thanks!Do you have the same device?```
lspci -nn
```

---

### Post by funguygordy on 2011-06-28
```

Network controller [0280]: RaLink Device [1814:3062]

```

Yes, it is the same as the OP.

---

### Post by chili555 on 2011-06-28
> **funguygordy said:**
> ```

Network controller [0280]: RaLink Device [1814:3062]

```

Yes, it is the same as the OP.I wrote a pretty decent howto a few days ago: [http://ubuntuforums.org/showthread.php?t=1790271&page=2](http://ubuntuforums.org/showthread.php?t=1790271&page=2)

Please see posts #13 et seq. Please note that you need build tools and headers:```
sudo apt-get install build-essential linux-headers-generic
```

---

### Post by funguygordy on 2011-06-28
Thanks, will I need to be connected via lan in order to obtain those?

---

### Post by chili555 on 2011-06-28
> **funguygordy said:**
> Thanks, will I need to be connected via lan in order to obtain those?Yes. They may already be installed. Check:```
sudo dpkg -s build-essential
sudo dpkg -s linux-headers-generic
```If the package is installed, you will see 'OK installed.'

---

### Post by funguygordy on 2011-06-28
They were, and I am making this post from my Ubuntu partition.  Thanks for the help!

---

### Post by chili555 on 2011-06-28
> **funguygordy said:**
> They were, and I am making this post from my Ubuntu partition.  Thanks for the help!Awesome, Gordy! Glad it's working.

---

