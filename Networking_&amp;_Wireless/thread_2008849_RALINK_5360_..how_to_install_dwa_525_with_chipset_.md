---
title: "RALINK 5360 ..how to install dwa 525 with chipset ralink 5360 on ubuntu 10.04.."
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by anshul121 on 2012-06-23
how to install dlink dwa 525 wireless adapter card with ralink 5360 on ubuntu 10.04...

i have tried everything but not got the solutions...did anyone know solution..?

Ubuntu engineers please help........

---

### Post by varunnalwa on 2012-06-24
I am facing the same problem , have searched everywhere on google but didn't find a solution. If any one have the solution please share it.Thanks in advance.

---

### Post by chili555 on 2012-06-24
> **varunnalwa said:**
> I am facing the same problem , have searched everywhere on google but didn't find a solution. If any one have the solution please share it.Thanks in advance.Would you both please open a terminal and run and post:```
lsb_release -d
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by dqvn on 2012-10-18
```
pos@pos-ThinkCentre-M58e:~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS
pos@pos-ThinkCentre-M58e:~$ lspci -nn | grep 0280
03:04.0 Network controller [0280]: Ralink corp. Device [1814:5360]
```


Here is my information. Hope you could help me. 

Thanks alot

---

### Post by chili555 on 2012-10-18
I love a challenge and so will you, I hope. This is a relatively new device and we are going to have to experiment a bit. Please download RT539x PCIe here: [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

Download it to your desktop. Right-click it and select 'extract here.' It is handily a bz2.bz2 file, so you may have to 'extract here' a couple of times. Good work, Ralink! Now open a terminal and, with an internet connection, do:```
sudo apt-get install linux-headers-generic build-essential
```Open the folder you extracted and drill down to os/linux/config.mk and with a text editor change:
```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y[/COLOR]
```Proofread, save and close the text editor. Now open the file os/linux/pci_main_dev.c with a text editor. Make the addition I've highlighted here:```
#ifdef RT5390
	{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5390_PCIe_DEVICE_ID)},
	{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC539F_PCIe_DEVICE_ID)},
	{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5392_PCIe_DEVICE_ID)},
	{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5362_PCI_DEVICE_ID)},
        [COLOR="Red"]{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5360_PCI_DEVICE_ID)},[/COLOR]
#endif /* RT5390 */
```Everything before and after is unchanged. Spacing, punctuation, brackets, etc. are crucial. Proofread carefully twice before you save and close the text editor. Now back to the terminal:
```
cd Desktop/2011
```
Press Tab and the rest will fill in automagically. Press Enter.
```
sudo su
make
make install
modprobe rt5390sta
echo rt5390sta >> /etc/modules
exit

```
Your wireless should now be working.

---

### Post by davidkl on 2013-03-27
Thanks a million, chili555, worked wonderfully!

---

### Post by vezolmi on 2013-04-11
Thanks a lot!! I've installed the D-Link N 150 PCI DWA-525 Ralink 5360 Wifi adapter in Lubuntu 12.04 as stated above, in the #5 post of this thread!!

---

### Post by vezolmi on 2013-04-13
Now the RT539x PCIe driver can be downloaded from [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)

---

### Post by chili555 on 2013-04-13
> **vezolmi said:**
> Now the RT539x PCIe driver can be downloaded from [http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001](http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5001)Yes, indeed! Please be aware, all you searchers, that the package referred to is a 2011 version. It will probably compile just fine in Ubuntu 10.04 but not in 12.04 and later.

---

### Post by shubh3108 on 2013-05-15
> **chili555 said:**
> I love a challenge and so will you, I hope. This is a relatively new device and we are going to have to experiment a bit. Please download RT539x PCIe here: [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

Download it to your desktop. Right-click it and select 'extract here.' It is handily a bz2.bz2 file, so you may have to 'extract here' a couple of times. Good work, Ralink! Now open a terminal and, with an internet connection, do:```
sudo apt-get install linux-headers-generic build-essential
```Open the folder you extracted and drill down to os/linux/config.mk and with a text editor change:
```
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR=Red]y[/COLOR]
```Proofread, save and close the text editor. Now open the file os/linux/pci_main_dev.c with a text editor. Make the addition I've highlighted here:```
#ifdef RT5390
    {PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5390_PCIe_DEVICE_ID)},
    {PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC539F_PCIe_DEVICE_ID)},
    {PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5392_PCIe_DEVICE_ID)},
    {PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5362_PCI_DEVICE_ID)},
        [COLOR=Red]{PCI_DEVICE(NIC_PCI_VENDOR_ID, NIC5360_PCI_DEVICE_ID)},[/COLOR]
#endif /* RT5390 */
```Everything before and after is unchanged. Spacing, punctuation, brackets, etc. are crucial. Proofread carefully twice before you save and close the text editor. Now back to the terminal:
```
cd Desktop/2011
```
Press Tab and the rest will fill in automagically. Press Enter.
```
sudo su
make
make install
modprobe rt5390sta
echo rt5390sta >> /etc/modules
exit

```
Your wireless should now be working.

Ok, so I have the same problem of installing the required driver BUT for Ubuntu 12.04.

Can anyone explain what the following piece of code does?```
sudo apt-get install linux-headers-generic build-essential
```I cannot connect to the internet via ethernet and hence need to know whether I can skip this step (or how to do it without internet).

Thanks

---

### Post by shubh3108 on 2013-05-16
So I skipped the first step from chili555's guide and was able to get the device working. :o
Just to be on the safe side, I re-did the entire guide (this time with the first step).

This might be a very stupid question but can I now delete the folder with the driver files that I have on Desktop?

---

### Post by chili555 on 2013-05-16
> Can anyone explain what the following piece of code does?

```
sudo apt-get install linux-headers-generic build-essential
```

I cannot connect to the internet via ethernet and hence need to know whether I can skip this step (or how to do it without internet).
It installs, from the internet , extra packages that are, ahem, *essential*, in order to compile from source code. No, the steps may not be skipped; otherwise I would have skipped typing the instruction!

You can download on some other computer all the prerequisite parts and pieces on a USB stick and transfer them and install them on Ubuntu. It is, however, an involved process and hardly ever goes perfectly in the first or second try.

Are you sure you haven't a friend or neighbor that would help you out with a quick trip to the ethernet? Also, if you could borrow another USB wireless, you could take care of linux-headers-generic and build-essential in a few moments.

If you just have to do it the long, hard way, post back and I'll link some other cases.

---

### Post by shubh3108 on 2013-05-16
> **chili555 said:**
> It installs, from the internet , extra packages that are, ahem, *essential*, in order to compile from source code. No, the steps may not be skipped; otherwise I would have skipped typing the instruction!

You can download on some other computer all the prerequisite parts and pieces on a USB stick and transfer them and install them on Ubuntu. It is, however, an involved process and hardly ever goes perfectly in the first or second try.

Are you sure you haven't a friend or neighbor that would help you out with a quick trip to the ethernet? Also, if you could borrow another USB wireless, you could take care of linux-headers-generic and build-essential in a few moments.

If you just have to do it the long, hard way, post back and I'll link some other cases.

Oh I see. The thing is that it is a desktop computer and my router is installed quite far away from it. 

However, as I said in my previous post I was able to connect to the internet without running that command and then went through the entire process again (including the first command). So do you think I am good now?

And can I remove the folder with the driver files from my desktop?

Thanks for all the help.

---

### Post by chili555 on 2013-05-16
> And can I remove the folder with the driver files from my desktop?No. You compiled the driver for your currently running kernel only. Someday soon, a later kernel will be installed by Update Manager. You will then need to recompile:```

sudo su
[COLOR="#FF0000"]make clean[/COLOR]
make
make install
modprobe rt5390sta
exit


```Glad it's working!

---

### Post by Muzafsh on 2013-05-27
The following commands yielded the pasted outputs

[B]# cat /etc/lsb-release; uname -a
# lspci -nnk | grep -iA2 net
# lsusb
# iwconfig
# rfkill list all
# lsmod[/CODE]
[/B]

1:~$ cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"
Linux ALHAMDULILLAH11 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 17:35:01 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



```


1:~$ lspci -nnk | grep -iA2 net
```
0a:0b.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705_2 Gigabit Ethernet [14e4:1654] (rev 03)
    Subsystem: IBM Device [1014:02f8]
    Kernel driver in use: tg3
--
0a:0c.0 Network controller [0280]: Ralink corp. Device [1814:5360]
    Subsystem: D-Link System Inc Device [1186:3c05]



```


lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04ca:0061 Lite-On Technology Corp. 

```
:~$ iwconfig
```
lo        no wireless extensions.


eth0      no wireless extensions.

```



:~$ rfkill list all
```
- No output -

```


:~$ lsmod
```
Module                  Size  Used by
snd_intel8x0           38570  2 
snd_ac97_codec        134869  1 snd_intel8x0
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                97275  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180153  10 rfcomm,bnep
ppdev                  17113  0 
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32866  1 
serio_raw              13211  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_intel8x0,snd_pcm
rt2800pci              18715  0 
rt2800lib              58967  1 rt2800pci
crc_ccitt              12707  1 rt2800lib
rt2x00pci              14620  1 rt2800pci
rt2x00lib              55326  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506862  3 rt2800lib,rt2x00pci,rt2x00lib
i915                  478189  3 
drm_kms_helper         46978  1 i915
drm                   241971  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915
mac_hid                13253  0 
cfg80211              205774  2 rt2x00lib,mac80211
eeprom_93cx6           12767  1 rt2800pci
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47238  0 
hid                    99636  1 usbhid
floppy                 70207  0 
tg3                   152085  0 



```

Help most appreciated !!!

thanks,

---

