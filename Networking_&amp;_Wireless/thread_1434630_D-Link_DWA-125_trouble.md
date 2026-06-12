---
title: "D-Link DWA-125 trouble"
date: 2010-03-20
forum: Networking &amp; Wireless
---

### Post by ChairsForSquares on 2010-03-20
Hi all I'm new here and I recently purchased a D-Link DWA-125 Wireless N adapter. Its USB device id is 07d1:3c16.

At chilli555's request, here's the information that terminal gives me:
[B]
iwconfig[/B]

lo        no wireless extensions.

eth0      no wireless extensions.

**lsmod **|** grep -e rt2 -e -rt3**

rt3070sta             503348  0 

**dmesg **|** grep -e rt2 -e -rt3**

[   21.130207] rt3070sta: module is from the staging directory, the quality is unknown, you have been warned.
[   21.135613] usbcore: registered new interface driver rt2870



Thanks in advance for your help!

---

### Post by chili555 on 2010-03-20
I am not at all sure *any* native Linux driver claims this particular usb.id! Let's cheat.

Were these the steps you followed?  [http://www.uluga.ubuntuforums.org/showpost.php?p=8966294&postcount=37](http://www.uluga.ubuntuforums.org/showpost.php?p=8966294&postcount=37)

If so, please remove the device and amend these files to reflect your usb.id:> sudo gedit /etc/udev/rules.d/network_drivers.rules

Add one long line:
Code:

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="[COLOR="Red"]3c16[/COLOR]", RUN+="/sbin/modprobe -qba rt3070sta"

Proofread twice, save and close gedit.
Code:

sudo gedit /etc/modprobe.d/network_drivers.conf

Add one long single line:
Code:

install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "07d1 [COLOR="Red"]3c16[/COLOR]" > /sys/bus/usb/drivers/rt2870/new_id

As always, proofread very carefully, save and close gedit.

Re-insert the device and run:```
iwconfig
```Do you now have a wireless interface?

---

### Post by ChairsForSquares on 2010-03-20
lo        no wireless extensions.

eth0      no wireless extensions.

Also when I added those lines of code, those were the only thing in an otherwise empty box. Should that be the case?

---

### Post by chili555 on 2010-03-20
> those were the only thing in an otherwise empty box. Should that be the case?Yes, exactly.

Please reboot with the device inserted and let me know the result of *iwconfig*.

---

### Post by ChairsForSquares on 2010-03-20
It works! Thanks for your help, chilli!

---

### Post by chili555 on 2010-03-20
Great news! I haven't seen this exact usb.id before and now we know how to make it work. Enjoy.

---

### Post by Zanzacar on 2010-04-10
I did exactly as was described in Chili's response. It has not worked for me. Did I need to download some drivers and put them in the locations that the drivers were referring to? Is my device ID going to be the same as his? I would really like to get this DWA-125 working. I have used Linux for only a few hours so if you could please make it as simple as possible that would be great. Thanks for your help ahead of time.

--Zac

---

### Post by chili555 on 2010-04-10
> Is my device ID going to be the same as his? Maybe. Let's check by opening a terminal and do:```
lsusb
```Is your usb.id the same: 07d1:3c16 ? If not, please post yours.

Please do:```
sudo modprobe rt3070sta
dmesg | grep rt3
```Please post the result. Thanks.

---

### Post by motin on 2010-06-15
Seems to be relevant, I posted how to install a working driver for the device with id 07d1:3c0d on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546653)

There are many threads about this issue, but I couldnt find a complete solution anywhere. Hope this helps!

---

### Post by barlaventoexpert on 2010-09-16
Chili555's solution worked for me on Ubuntu 10.04

D-Link DWA-125

Many Thanks

---

### Post by ubutu_newbie on 2010-10-15
hi everyone.

hope you guys wont mind for me asking the same questions as all the others. Started using ubuntu in august 2010.

im also having same trouble getting my d-link dwa 125 adapter to work on my desktop

read and did everything as mentioned above.

please help

thank you in advance

---

### Post by chili555 on 2010-10-15
First, please run:```
lsusb
```Confirm that your usb.id is indeed 07d1:3c16. If so, please redo the steps in post #2, but substitute rt2870sta for every instance of rt3070sta. Reboot and let us have your report.

If your usb.id is not 07d1:3c16, post it and we'll decide how to proceed.

The module rt3070sta has been absorbed into rt2870sta, I believe.> $ modinfo rt2870sta 
filename:       /lib/modules/2.6.35-22-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/[COLOR="Red"]RT3070[/COLOR] Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       [COLOR="Red"]rt3070[/COLOR].bin
firmware:       rt2870.bin
--- snip ---

---

### Post by schryer on 2010-10-24
My D-Link wireless usb connector (07d1:3c16) is not being recognized.

lsusb gives:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 058f:9520 Alcor Micro Corp. EMV Certified Smart Card Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 046d:0991 Logitech, Inc. QuickCam Pro for Notebooks
Bus 001 Device 004: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 001 Device 002: ID 07d1:3c16 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

A kernel module page for CONFIG_RT2800USB give the following vendor info:
vendor: 07d1 ("D-Link System"), product: 3c16 ("DWA-125 Wireless N 150 Adapter(rev.A2) [Ralink RT2870]")

I have read multiple posts about this issue and tried a number of things:
[http://www.uluga.ubuntuforums.org/showthread.php?t=1425564](http://www.uluga.ubuntuforums.org/showthread.php?t=1425564)
[http://georgia.ubuntuforums.org/showthread.php?p=9197565](http://georgia.ubuntuforums.org/showthread.php?p=9197565)
[http://ubuntuforums.org/showthread.php?t=1518043](http://ubuntuforums.org/showthread.php?t=1518043)

Currently I have a clean 10.10 install with a modified blacklist file:
tail -n4 /etc/modprobe.d/blacklist.conf 
blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib

The command: 
sudo modprobe rt2870sta

does not change the output of iwconfig, which returns:
lo        no wireless extensions.

eth0      no wireless extensions.

What more can I do?  I have not yet tried recompiling anything yet since 
there is conflicting information out there.

I run a generic 64 bit kernel:
uname -a
Linux david-home 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux

---

### Post by flash63 on 2010-10-24
Hello,
a simple way to aktivate rt2870sta für this device. 
[http://ubuntuforums.org/showpost.php?p=9971253&postcount=10](http://ubuntuforums.org/showpost.php?p=9971253&postcount=10)

Beware of the device ID 07d1:3c16 which is used here.

---

### Post by schryer on 2010-10-24
I followed the steps in the following post and no joy.
[http://ubuntuforums.org/showpost.php...3&postcount=10](http://ubuntuforums.org/showpost.php...3&postcount=10)

I tried with and without blacklisting as in my previous post.
I tried after a reboot.
I tried with and without the dongle plugged in while executing the commands.

No joy.  Others seem to have this device being recoginzed and are onto the connection problems.  I cannot reach this stage.

Should I move onto another driver?  Perhaps a test on another system? (I have not done this yet).

Thanks for your advice in advance,
David

---

### Post by chili555 on 2010-10-24
> **schryer said:**
> I followed the steps in the following post and no joy.
[http://ubuntuforums.org/showpost.php...3&postcount=10](http://ubuntuforums.org/showpost.php...3&postcount=10)

I tried with and without blacklisting as in my previous post.
I tried after a reboot.
I tried with and without the dongle plugged in while executing the commands.

No joy.  Others seem to have this device being recoginzed and are onto the connection problems.  I cannot reach this stage.

Should I move onto another driver?  Perhaps a test on another system? (I have not done this yet).

Thanks for your advice in advance,
DavidYour link is broken; please repost.

---

### Post by schryer on 2010-10-24
I used the link suggested by flash63
[http://ubuntuforums.org/showpost.php?p=9971253&postcount=10](http://ubuntuforums.org/showpost.php?p=9971253&postcount=10)

---

### Post by chili555 on 2010-10-24
Let's see what's going on under the hood. Please post:```
dmesg | grep rt2
lsmod | grep rt2
```Thanks.

---

### Post by schryer on 2010-10-24
dmesg | grep rt2
[91030.149052] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[91030.156559] usbcore: registered new interface driver rt2870
[91143.457261] usbcore: deregistering interface driver rt2870
[91259.368869] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[91259.376685] usbcore: registered new interface driver rt2870
[94028.458015] Error: Driver 'rt2870' is already registered, aborting...
[94049.846777] Error: Driver 'rt2870' is already registered, aborting...
[94068.338433] Error: Driver 'rt2870' is already registered, aborting...
[94089.721115] Error: Driver 'rt2870' is already registered, aborting...
[95201.344993] usbcore: deregistering interface driver rt2870

lsmod | grep rt2
Does not return anything.

---

### Post by chili555 on 2010-10-24
So that means the driver module rt2870sta is not even loaded!

I am sure I am going to hate the answer to this; please post:```
lsmod | grep ndis
```Thanks.

---

### Post by schryer on 2010-10-24
lsmod | grep ndis
returns nothing.

I have never tried ndiswrapper for this problem.

---

### Post by flash63 on 2010-10-24
Hello,
the code for your device D-LINK DWA-125N A2 ID 07d1:3c16

Add the ID (command in one line):
```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
```
Remove the Stick and unload the modul
```
sudo modprobe -rf rt2870sta
```
Reconnect the Stick and driver
```
sudo modprobe rt2870sta
iwconfig
```
Interface available? Try to connect!

The solution works? Ok, automatic driver load if the stick was plugged in:
```
sudo gedit /etc/udev/rules.d/10-d_link.rules
```
contents:
```
# UDEV-Rule for D-LINK DWA-125N A2 ID 07d1:3c16
SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c16", RUN+="/sbin/modprobe rt2870sta"
```
make it ready to work
```
sudo service udev reload
```
.. or restart

---

### Post by schryer on 2010-10-24
It works, and connects.

Thank you for sticking this one out flash63 and chili555.

I needed the explicit remove stick instruction that was different from the 
first set of instructions. 

Now for a reboot test....
Cheers,
David

---

### Post by chili555 on 2010-10-24
Deleted.

---

### Post by mnorth on 2010-10-25
I'd been having trouble with the d-link dwa-125 as well, had been following the advice here with little luck...however I also had been having trouble with distro's on the laptop with the card, old dell inspiron 1100....this past weekend I installed peppermint ice distro on the machine and everything worked fine out of the gate including the d-link dwa-125...very happy now that I've got a distro working and wireless as well...btw thanks for all the advice, I probably will be using it when I install on an older desktop, with a bit better cpu & vid card than the old laptop....

---

### Post by vonbureck on 2010-11-16
Just chiming in to say a big thank you to chilli555 -- the initial fix in this thread worked perfectly for me. First time ever that I got a wireless card working under Ubuntu :)

For anyone else trying this, I first made sure that none of the rt2*/rt3* modules were loaded (lsmod did not show any), purged all ndiswrapper stuff, and then added the two lines to two config files as per chilli555's instructions and rebooted with the device still connected. The key thing (which is perhaps not stressed enough in related threads for this) was the 07d1:3c16 usb device ID.

---

### Post by chili555 on 2010-11-16
> a big thank you to chilli555And a big you're welcome. I'm glad it's working. Have fun!

---

### Post by vasu84 on 2010-12-01
hi

 im new to ubuntu and have been trying to install the Dlink DWA 125 but no luck.
All i know is that when i do lsusb on the terminal window this is the msg i get

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 07d1:3c16 D-Link System 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

and from wat i understand the dlink 07d1:3c16 is diff adapter.

i dnt know where to download the software or drivers from. I would be  needing help from the start from where to download the driver how to  extract it and on and on.

Can anyone help me please.
oh and i forgot to mention im using ubuntu 10.10


Thanks
Vasu

---

### Post by chili555 on 2010-12-02
Some people have great luck with this particular usb.id and some have trouble. Here is post describing the easiest method and reporting success.

[http://ubuntuforums.org/showpost.php?p=9971253&postcount=10](http://ubuntuforums.org/showpost.php?p=9971253&postcount=10)

Please post back if you need guidance.

---

### Post by Mike922 on 2010-12-30
. . . and all my troubles went away.

Well, not ALL. Like the birds out my window, I'm on line. 

Thanks,
Mike

---

### Post by Ozitraveller on 2011-01-01
> **chili555 said:**
> First, please run:```
lsusb
```Confirm that your usb.id is indeed 07d1:3c16. If so, please redo the steps in post #2, but substitute rt2870sta for every instance of rt3070sta. Reboot and let us have your report.

If your usb.id is not 07d1:3c16, post it and we'll decide how to proceed.

The module rt3070sta has been absorbed into rt2870sta, I believe.

Hi chili555

I'm running Lucid Ubuntu.

My usb:id is 07d1:3c16 and doing as you suggested and substituting rt2870sta for rt3070sta in step #2 works.

Thanks

---

### Post by chili555 on 2011-01-01
Awesome! Glad it's working. Have fun.

---

### Post by Ozitraveller on 2011-01-08
> **Ozitraveller said:**
> Hi chili555

I'm running Lucid Ubuntu.

My usb:id is 07d1:3c16 and doing as you suggested and substituting rt2870sta for rt3070sta in step #2 works.

Thanks


Now it's not working

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1_rename  IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 009: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 002 Device 008: ID 045e:0750 Microsoft Corp. 
Bus 002 Device 007: ID 07d1:3c16 D-Link System 
Bus 002 Device 004: ID 03f0:1712 Hewlett-Packard Printing Support
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ca:180a Ricoh Co., Ltd 
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1_rename  IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     RTxx70 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2011-01-09
Please post:```
cat /etc/udev/rules.d/network_drivers.rules
cat /etc/modprobe.d/network_drivers.conf
dmesg | grep -i rt2
```Thanks.

---

### Post by Ozitraveller on 2011-01-09
> **chili555 said:**
> Please post:```
cat /etc/udev/rules.d/network_drivers.rules
cat /etc/modprobe.d/network_drivers.conf
dmesg | grep -i rt2
```Thanks.

Hi Chili555

I'm at work at the moment I'll do it when I'm home tonite.

Cheers
Ozi

---

### Post by Ozitraveller on 2011-01-10
Hi chili555

Sorry for the delay, I'm a little busy this week.

cat /etc/udev/rules.d/network_drivers.rules
```

# UDEV-Rule for D-LINK DWA-125N A2 ID 07d1:3c16
SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c16", RUN+="/sbin/modprobe rt2870sta"
# ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba rt2870sta"

```

cat /etc/modprobe.d/network_drivers.conf
```

install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id
# install rt2870sta /sbin/modprobe --ignore-install rt2870sta; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id
# install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id

```

dmesg | grep -i rt2
```

[  204.197054] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  204.204611] usbcore: registered new interface driver rt2870

```


iwconfig
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan1_rename  IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     RTxx70 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by chili555 on 2011-01-11
> cat /etc/udev/rules.d/network_drivers.rules

```
# UDEV-Rule for D-LINK DWA-125N A2 ID 07d1:3c16
SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c16", RUN+="/sbin/modprobe rt2870sta"
# ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba
```I disagree with this section. I suggest you remove the device and change it to:```
# UDEV-Rule for D-LINK DWA-125N A2 ID 07d1:3c16
#SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c16", RUN+="/sbin/modprobe rt2870sta"
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba
```Let's see if we can figure out the rename issue. Please post:```
cat /etc/udev/rules.d/70-persistent-net.rules
```We may need to adjust it.

Thanks.

---

### Post by Ozitraveller on 2011-01-11
> **chili555 said:**
> I disagree with this section. I suggest you remove the device and change it to:```
# UDEV-Rule for D-LINK DWA-125N A2 ID 07d1:3c16
#SUBSYSTEM=="usb", SYSFS{idVendor}=="07d1", SYSFS{idProduct}=="3c16", RUN+="/sbin/modprobe rt2870sta"
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba
```Let's see if we can figure out the rename issue. Please post:```
cat /etc/udev/rules.d/70-persistent-net.rules
```We may need to adjust it.

Thanks.

Ok I'll do when I get home.

Also, this a dual boot laptop with Win 7 64, so wondering whether any firmware updates to the built-in wifi may have disabled it?

---

### Post by chili555 on 2011-01-11
> wondering whether any firmware updates to the built-in wifi may have disabled it?I doubt it for many reasons.

---

### Post by Ozitraveller on 2011-01-11
Ok thanks chili555

---

### Post by Ozitraveller on 2011-01-11
Hi chili555

Here's the output.

cat /etc/udev/rules.d/70-persistent-net.rules
```

# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x11ab:0x4354 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:25:64:40:c9:a1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:26:5e:09:2f:7c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

---

### Post by chili555 on 2011-01-12
It looks perfect. Since you changed the rules file as I suggested, is there any improvement? Does wlan_rename still appear in iwconfig?

---

### Post by Ozitraveller on 2011-01-12
Hi chili555

Sorry for the delays, bit of a timezone difference. I think it is but I'll have to check.

cheers
Ozi

---

### Post by Ozitraveller on 2011-01-13
Wired Network
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

No Wired Network
D-Link BA-125
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     RTxx70 Wireless  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  
          Link Quality=10/100  Signal level:0 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2011-01-13
We are going to do a complete diagnostic workup. We are going to create a large text document, zip it and post it here. I and a few colleagues will examine it and hopefully gain some insight as to what's happening. Insert the device; detach the ethernet cable and reboot. Open a terminal and do:```
dmesg > ozi.txt
sudo lshw -C network >> ozi.txt
lsmod >> ozi.txt
sudo cat /var/log/syslog | grep wlan >> ozi.txt
zip ozi.zip ozi.txt
```You will find a zip file in your user directory called ozi.zip. Please attach it to your reply.

---

### Post by Ozitraveller on 2011-01-13
Thanks I'll pots it tonite local time :)

Hope you find something useful in there!

Thanks chili555

Ozi

---

### Post by Ozitraveller on 2011-01-18
Hi Chili555

You are probably busy, but curious to know whether anything has come to light in your analysis so far?
Cheers
Ozi

---

### Post by chili555 on 2011-01-19
> **Ozitraveller said:**
> Hi Chili555

You are probably busy, but curious to know whether anything has come to light in your analysis so far?
Cheers
OziSorry about that. I am usually good about juggling several clients at once, but not always. I need a secretary! My apologies.

I notice you have both a Broadcom wireless card as well as the D-link. This is an interesting line:> b43-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.Are you not using the Broadcom because the switch doesn't seem to work? The module dell-laptop which is loaded in your case frequently misbehaves in just this manner. Does the switch now work if you remove the module?```
sudo rmmod -f dell-laptop
```Often, the hardware switch will also be needed to get the *USB* wireless working.

If it were me, I'd try to get the internal wireless working if for no other reason, that the dongle isn't sticking out to get caught and snapped off!


-------------

Hint to chili: RT3070STA.dat

---

### Post by Ozitraveller on 2011-01-19
Hi chili555

Yes I understand your multi client issues, I have a similar problem. :)

Yes that was my plan to get the built-in wireless working again, I was hoping to get range with the D-Link. The built-in wireless doesn't alway work in windows either.

I'll let you know the results when I get home.

Thanks

Ozi

---

### Post by Ozitraveller on 2011-01-20
Hi chili555

```
sudo rmmod -f dell-laptop
```

Tried this but wireless is still disabled.

---

### Post by chili555 on 2011-01-20
Let's stop the drivers for the Broadcom from loading. This will probably solve the wlan1_rename issue as well. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add two new lines:```
blacklist ssb
blacklist b43
```Proofread, save and close gedit. Now do:```
sudo mkdir /etc/Wireless/RT3070STA
```If it complains that the file exists, that's fine, just proceed to:```
sudo gedit /etc/Wireless/RT3070STA/RT3070STA.dat
```A new empty file should appear. Add a single word:```
Default
```Proofread, save and close gedit. Reboot.

How is your wireless working? If it isn't, post:```
iwconfig
dmesg | grep -i rt3
```Thanks.

---

### Post by chili555 on 2011-01-20
Let's stop the drivers for the Broadcom from loading. This will probably solve the wlan1_rename issue as well. Please do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add two new lines:```
blacklist ssb
blacklist b43
```Proofread, save and close gedit. Now do:```
sudo mkdir /etc/Wireless/RT3070STA
```If it complains that the file exists, that's fine, just proceed to:```
sudo gedit /etc/Wireless/RT3070STA/RT3070STA.dat
```A new empty file should appear. Add a single word:```
Default
```Proofread, save and close gedit. Reboot.

How is your wireless working? If it isn't, post:```
iwconfig
dmesg | grep -i rt3
```Thanks.

---

### Post by Ozitraveller on 2011-01-21
Hi chili555

I'm using wireless to post reply, so it's working with the D-Link!

I had built-in wireless working but it keeps disconnecting

Thanks for the help. Much appreciated.

I'll post back in a couple of days when I see how stable it is.

Ozi

---

### Post by chili555 on 2011-01-21
Excellent! I'll look forward to your report.

---

### Post by Ozitraveller on 2011-01-24
Hi chili555

It's working well and stable! :)

Thanks for the help.

Ozi

---

### Post by rog3rj on 2011-02-17
> **chili555 said:**
> First, please run:```
lsusb
```Confirm that your usb.id is indeed 07d1:3c16. If so, please redo the steps in post #2, but substitute rt2870sta for every instance of rt3070sta. Reboot and let us have your report.

If your usb.id is not 07d1:3c16, post it and we'll decide how to proceed.

The module rt3070sta has been absorbed into rt2870sta, I believe.
This action solved the problem for me.  This was on a clean install of Ubuntu 10.10 before carrying out updates.  My first use of Ubuntu after a working life on MS.  Thanks for the help.

---

### Post by muntu_X on 2011-02-20
Hi

I have just installws Ubuntu Maverick 10.10 (kernel 2.6.35) and am using a D-Link wireless dongle with usb.id  07d1:3c0d.  

The wireless is working but download speed is approx 6.5 mbps down and up 1.9 mbps. I am wondering if I have not got the driver loading correctly.  Having searched the forum posts I have completed the below steps:

ran sudo apt-get remove --purge ndiswrapper*

Downloaded and untarred 2009_1204_RT3070_Linux_STA_v2.1.2.0
ran sudo make - 2 errors implicit declarations of usb_buffer_alloc and usb_buffer_free
Modified rtmp_usb.h to declare usb_free_coherent and usb_alloc_coherent
ran sudo make
ran sudo make install

Note at this point in the /lib/modules/2.6.35.25-generic/kernel/drviers/staging the only modules that exist are rt2860, rt2870
modified /etc/udev/rules.d/network_drivers.rules
and /etc/modprobe.d/network_drivers.conf as per chili55 post 37

jonie@holly:~/Downloads$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0402:5642 ALi Corp. 
Bus 001 Device 003: ID 07d1:3c0d D-Link System DWA-125 Wireless 150 USB Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"jane_belkin"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:17:3F:0B:F2:78   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-59 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jonie@holly:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:6c:6c:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:820 errors:0 dropped:0 overruns:0 frame:0
          TX packets:820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68608 (68.6 KB)  TX bytes:68608 (68.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:5a:0f:8b:b7  
          inet addr:192.168.5.6  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::226:5aff:fe0f:8bb7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:21410 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3173 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3851596 (3.8 MB)  TX bytes:562707 (562.7 KB)


/etc/modprobe.d/blacklist.conf
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib

lsmod | grep -e rt2 -e rt3
rt3070sta             572713  0 
rt2870sta             446110  1 
crc_ccitt               1699  1 rt2870sta

dmesg | grep -e rt2 -e rt3 
[  449.332856] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  449.340139] usbcore: registered new interface driver rt2870
[  450.429100] <==== rt28xx_init, Status=0
[  452.687106] <==== rt28xx_init, Status=0
[  807.490347] <==== rt28xx_init, Status=0
[  809.129736] <==== rt28xx_init, Status=0
[ 1204.939893] <==== rt28xx_init, Status=0
[ 1206.640521] <==== rt28xx_init, Status=0
[ 2288.957753] usbcore: registered new interface driver rt3070
[ 2339.670344] <==== rt28xx_init, Status=0
[ 2341.517314] <==== rt28xx_init, Status=0


sudo cat modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
rt3070sta

Please advise if I have the driver correctly installed and any suggestions as to how I might improve performance.  Are there recommended wireless network cards that I could install that might be better?

Thanks in advance

---

### Post by chili555 on 2011-02-21
> Please advise if I have the driver correctly installed and any suggestions as to how I might improve performance.I have a few suggestions. Please undo this step altogether:> modified /etc/udev/rules.d/network_drivers.rules
and /etc/modprobe.d/network_drivers.conf as per chili55 post 37
Do so like this:```
sudo rm /etc/udev/rules.d/network_drivers.rules
sudo rm /etc/modprobe.d/network_drivers.conf
```Next, amend the blacklist.conf file so that the lines you added read like this:```
blacklist rt2800usb
[COLOR="Red"]blacklist rt2800lib[/COLOR]
blacklist rt2x00usb
blacklist rt2x00lib
[COLOR="Red"]blacklist rt2870sta[/COLOR]
```Reboot and give us your report. We'll see how this performs before we go on to Plan B.

---

### Post by muntu_X on 2011-02-21
Hi Chili555
Thanks for your response.  I did as suggested, rebooted and have the following

jonie@holly:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"jane_belkin"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 00:17:3F:0B:F2:78   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=55/100  Signal level:-61 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jonie@holly:~$ lsmod | grep -e rt2 -e rt3
rt3070sta             572713  0 
rt2870sta             446110  1 
crc_ccitt               1699  1 rt2870sta

jonie@holly:~$ dmesg | grep -e rt2 -e rt3 
[   13.881461] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   13.951218] usbcore: registered new interface driver rt2870
[   13.960773] usbcore: registered new interface driver rt3070
[   26.756508] <==== rt28xx_init, Status=0
[   28.458781] <==== rt28xx_init, Status=0
jonie@holly:~$ 

Speed is still approx the same.  Plan B is?
Cheers

---

### Post by chili555 on 2011-02-21
> jonie@holly:~$ lsmod | grep -e rt2 -e rt3
rt3070sta 572713 0
rt2870sta 446110 1
crc_ccitt 1699 1 rt2870sta
See here that rt2870sta is loading? That means you could not have blacklisted it correctly. Please post:```
cat /etc/modprobe.d/blacklist.conf
cat /etc/modules
```We'll fix it up.

---

### Post by muntu_X on 2011-02-21
hey again

I can't see where I've got it wrong :(

cat /etc/modprobe.d/blacklist.conf
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
blacklist amd77x_edac


blacklist rt2800usb
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta

--------------------

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
rt3070sta

I'll check again with a shutdown and start.
Appreciate your assistance.

---

### Post by muntu_X on 2011-02-25
Can anyone recommend a good wireless card that they are using with ubuntu 10.10?
Cheers

---

### Post by DMurray on 2011-03-23
Hi all.
I was reading chili555's and flash63's suggestions to make a DWA 125 work on Ubuntu 10.04. And they were great!
Just like one poster, I also have trouble with Windows not connecting after, errr, fixing stuff in Linux. It is just a metter of removing and reinserting the adapter into the USB. Why does it happen? I don't know.
But one problem remains: when I tell the system to connect to my wireless network, it keeps asking for the WPA/WPA2 password even though what I type is right.
Did anyone experience this before?

Thanks in advance

---

### Post by alistair1946 on 2011-06-21
Hi folks.
I have updated my Ubuntu to Natty Narwhall 11.04 and my D-link DWA125 07d1:3c16 dongle has lost its way again. Seems unable to shake hands with my WAP. Keeps on trying to connect without success.
Could someone take me through the process of elimination to sort this out please.
I had the dongle working under 10.10 although spasmodically.
Thanks in advance,
Al

---

### Post by chili555 on 2011-06-22
> **alistair1946 said:**
> Hi folks.
I have updated my Ubuntu to Natty Narwhall 11.04 and my D-link DWA125 07d1:3c16 dongle has lost its way again. Seems unable to shake hands with my WAP. Keeps on trying to connect without success.
Could someone take me through the process of elimination to sort this out please.
I had the dongle working under 10.10 although spasmodically.
Thanks in advance,
AlIs rt2800usb blacklisted?```
lsmod | grep rt2
cat /etc/modprobe.d/blacklist.conf
```Thanks.

---

### Post by blackløtus on 2011-06-22
hi,

I followed all the steps but i have a problem at the end when I type "sudo modprobe rt2870sta" the answer is:

> FATAL: Module rt2870sta not found.
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt2870staI'm running ubuntu 10.04 version for powerpc in a ibook g4 and the USB device id is 07d1:3c16.

can somebody help me with this 

thanks

---

### Post by chili555 on 2011-06-22
> **blackløtus said:**
> hi,

I followed all the steps but i have a problem at the end when I type "sudo modprobe rt2870sta" the answer is:

I'm running ubuntu 10.04 version for powerpc in a ibook g4 and the USB device id is 07d1:3c16.

can somebody help me with this 

thanksPlease post:
```
cat /etc/udev/rules.d/network_drivers.rules
cat /etc/modprobe.d/network_drivers.conf
dmesg | grep -i rt2
```It is likely that you missed one of these files or made a typographical error. Linux is precise; it's like my old English teacher, it goes crazy when it sees something not spelled correctly or capitalized.

Thanks.

---

### Post by blackløtus on 2011-06-22
sorry for my english I am just learning, it's not my native languaje.

Here are the codes that you requested:

cat /etc/udev/rules.d/network_drivers.rules
> 
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba rt2870sta"cat /etc/modprobe.d/network_drivers.conf
> 
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS;/bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_iddmesg | grep -i rt2 (not response)

PD: I'm thinking that the kernel of powerpc version had not included that module (I'm running 2.6.32-32-powerpc)

regards!

---

### Post by chili555 on 2011-06-22
> sorry for my english I am just learning, it's not my native languaje.No problem. I was just kidding around about that English teacher stuff. > I'm thinking that the kernel of powerpc version had not included that moduleLet's check:```
modinfo rt2870sta
```I'm guessing the powerpc kernel has this stuff all organized a bit differently: /sys/bus/usb/drivers/rt2870/new_id

You might try to look around in /sys/bus and see what you see. Maybe we can work out how to do it.

---

### Post by blackløtus on 2011-06-23
hi chili555,

modinfo rt2870sta

> ERROR: modinfo: could not find module rt2870sta
inside /sys/bus/ are the next folders:
aoa-soundbus
i2c
ieee1394
mdio_bus
pci
platform
serio
usb
hid
ide
macio
of_platform
pci_express
scsi
spi

related with the usb I only have seen this folder /sys/bus/hid/drivers/generic-usb , but inside it it isn't the rt2870sta

regards

---

### Post by chili555 on 2011-06-23
You were quite correct. Your powerpc kernel does not include the module rt2870sta. Do you have rt2800usb?```
modinfo rt2800usb
```We could try to trick rt2800usb to drive your device.

Did your original PowerPC not come with a built-in wireless card?> inside /sys/bus/ are the next folders:
aoa-soundbus
i2c
ieee1394
mdio_bus
pci
platform
serio
usbWhat's inside /sys/bus/usb/drivers?

---

### Post by blackløtus on 2011-06-23
modinfo rt2800usb:
> 
filename:       /lib/modules/2.6.32-32-powerpc/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     7283B4CC49D9F4EB1D146BA
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
depends:        rt2x00lib,rt2x00usb,crc-ccitt
vermagic:       2.6.32-32-powerpc mod_unload modversions 
parm:           nohwcrypt: Disable hardware encryption. (bool)

My ibook g4 had a built-in wireless card but it don't works fine and I think that it will not work with aircrack.

inside /sys/bus/usb/drivers are these folders:

> appletouch  btusb  hiddev  hub  usb  usbfs  usbhid


PD: do you think that may be better change the d-link dwa 125 for another usb adapter which uses another chipset?

thanks for your help

---

### Post by chili555 on 2011-06-23
> alias: usb:v07D1p[COLOR="Red"]3C0D[/COLOR]d*dc*dsc*dp*ic*isc*ip*There you go! Please do:```
sudo rm /etc/udev/rules.d/network_drivers.rules
sudo rm /etc/modprobe.d/network_drivers.conf
sudo gedit /etc/modprobe.d/blacklist.conf
```Remove all the lines that blacklist rt2800usb and rt2x00usb and lib. Proofread carefully, save and close gedit. Now do:```
sudo modprobe rt2800usb
iwconfig
```Is your wireless now working?

---

### Post by blackløtus on 2011-06-23
it don't works :(

usb:v07D1p[COLOR=Red]3C0D[/COLOR]d*dc*dsc*dp*ic*isc*ip*                      

with this are you refering to my usb device? it then you are wrong, mine it's:
07d1:[COLOR=Red]3c16f 
[/COLOR]

---

### Post by chili555 on 2011-06-23
Sorry about that. There are three or four cases here with different versions of the DWA-125. > do you think that may be better change the d-link dwa 125 for another usb adapter which uses another chipset?
You could do that, or you could upgrade to a later version of Ubuntu where the device is recognized. In later versions, rt2800usb recognizes it.

We could also try to trick rt2800usb to drive your device. Amend the files you wrote:> /etc/udev/rules.d/network_drivers.rules
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba [COLOR="Red"]rt2800usb[/COLOR]"
```
/etc/modprobe.d/network_drivers.conf
```
install rt2800usb /sbin/modprobe --ignore-install [COLOR="Red"]rt2800usb[/COLOR] $CMDLINE_OPTS;/bin/echo "07d1 3c16" > /sys/bus/usb/drivers/[COLOR="Red"]rt2800[/COLOR]/new_id 
```It might work, but I don't know. I don't have the device.

---

### Post by blackløtus on 2011-06-23
> **chili555 said:**
>  You could do that, or you could upgrade to a later version of Ubuntu where the device is recognized. In later versions, rt2800usb recognizes it.

We could also try to trick rt2800usb to drive your device. Amend the files you wrote:It might work, but I don't know. I don't have the device.

I have tried this, but don't works, iwconfig returns "no wireless extensions"

On wich version of ubuntu must I upgrade? I can do this from the update manager? You think that the driver rt2800usb will work in the newest versions?orry about that. There are three or four cases here with different versions of the DWA-125.
Wich chipset has good support in ubuntu powerpc's version?
forgiveness for the many questions.

regards

---

### Post by chili555 on 2011-06-23
No problem at all; ask all the questions you want about Ubuntu. That's what I enjoy doing.

I think the rt2870sta chipset does a fine job, except many users have trouble getting it to do N speeds. If you are not streaming video or something equally speed-intensive, that may not be an issue. 

I'm not sure what version in PowerPC you'd need to upgrade to; my wife's computer, running 2.6.32-32-*generic* has the module rt2870sta in it. Have you installed all possible updates on your current system?

We could download and compile the driver from Ralink: [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)  How well it would work on PowerPC I have no opinion.

You could download the live CD for Ubuntu 10.10 and try it with your USB device.

As always, I'll be very glad to help you any way I can.

---

### Post by alistair1946 on 2011-06-23
Originally Posted by **alistair1946**                                      
                 Hi chilli555, here is the requested info. Al



alistair@ubuntu:~$ lsmod | grep rt2  
 rt2870sta             410104  1  
 rt2860sta             494649  0  
 crc_ccitt              12595  3 rt2870sta,irda,rt2860sta  
 alistair@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf  
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
 #Blacklist borked RT28xx drivers so RT2870STA will work.  
 rt2800usb  
 rt2x00usb  
 rt2x00lib

Please pardon the hiccup but I'm still getting used to this forum. I will use the "quick reply" in future.
Cheers

---

### Post by chili555 on 2011-06-23
> alistair@ubuntu:~$ lsmod | grep rt2
rt2870sta 410104 1
rt2860sta 494649 0
crc_ccitt 12595 3 rt2870sta,irda,rt2860sta Do you also have an internal Ralink wireless device? If not, please do:```
sudo gedit /etc/modules
```If there is a line in there that refers to rt28[COLOR="Red"]6[/COLOR]0sta, then remove it. Proofread carefully, save and close gedit. Now do:```
sudo rmmod -f rt2860sta
```Now does your wireless work better?

---

### Post by alistair1946 on 2011-06-24
> **chili555 said:**
> Do you also have an internal Ralink wireless device? If not, please do:```
sudo gedit /etc/modules
```If there is a line in there that refers to rt28[COLOR="Red"]6[/COLOR]0sta, then remove it. Proofread carefully, save and close gedit. Now do:```
sudo rmmod -f rt2860sta
```Now does your wireless work better?
Hi chili555
No internal Ralink wireless device on machine.
Removed rt2860sta from /etc/modules only "lp" remaining
Did code 
sudo rmmod -f rt2860sta

without any change in dongle response, however my WAP SSID now shows up on wireless manager.
appreciate your help from *SHAKY CITY down under*

---

### Post by chili555 on 2011-06-24
> without any change in dongle response, however my WAP SSID now shows up on wireless manager.
appreciate your help from SHAKY CITY down underDoes that mean you are able to connect and life is good? Or...what?

---

### Post by blackløtus on 2011-06-24
hi chili555,
I have upgrade my system to version 10.10. It's running the kernel 2.6.35-28-powerpc and not includes the rt2870sta, altough in my desktop pc with the 2.6.32-32-generic includes it, as you say.

In other way I have downloaded the rt3070 driver from the ralink's page and when I type "sudo make" I get the next error:

> make -C tools
make[1]: Entering directory `/home/davidone/Descargas/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/davidone/Descargas/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools'
/home/davidone/Descargas/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/davidone/Descargas/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux/Makefile
make -C /lib/modules/2.6.35-28-powerpc/build SUBDIRS=/home/davidone/Descargas/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO/os/linux modules
make: *** /lib/modules/2.6.35-28-powerpc/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2
also i downloaded the rt2870 from this page [http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-%28ubuntu%29/](http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-%28ubuntu%29/) 
that is patched for the kernel 2.6.35 and get this error with "sudo make"
> 
make -C tools
make[1]: Entering directory `/home/davidone/Descargas/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/davidone/Descargas/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools'
/home/davidone/Descargas/2010_0709_RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/davidone/Descargas/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.35-28-powerpc/build SUBDIRS=/home/davidone/Descargas/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux modules
make: *** /lib/modules/2.6.35-28-powerpc/build: No such file or directory.  Stop.
make: *** [LINUX] Error 2

Maybe I can modify the make file, but I don't know wich is the build equivalent directory in the powerpc's kernel

regards!

---

### Post by chili555 on 2011-06-24
Let's try the simple way before we try to compile from source. I am fairly confident your wireless will work if you simply follow the procedure in post #2 here: [http://ubuntuforums.org/showthread.php?t=1434630](http://ubuntuforums.org/showthread.php?t=1434630)

---

### Post by blackløtus on 2011-06-24
> **chili555 said:**
> Let's try the simple way before we try to compile from source. I am fairly confident your wireless will work if you simply follow the procedure in post #2 here: [http://ubuntuforums.org/showthread.php?t=1434630](http://ubuntuforums.org/showthread.php?t=1434630)

I tried another time this and the answer was the same that was with the kernel 2.6.32

> FATAL: Module rt3070sta not found.
sh: cannot create /sys/bus/usb/drivers/rt2870/new_id: Directory nonexistent
FATAL: Error running install command for rt3070sta
I think that the kernel of powerpc's version had different drivers that the generic versions.

---

### Post by chili555 on 2011-06-24
Sorry about that! Please amend the files you created to read like this. > sudo gedit /etc/udev/rules.d/network_drivers.rules

Add one long line:
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="07d1", ATTR{idProduct}=="3c16", RUN+="/sbin/modprobe -qba rt2870sta"
```

Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.
Code:

sudo gedit /etc/modprobe.d/network_drivers.conf

Add one long single line:
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "07d1 3c16" > /sys/bus/usb/drivers/rt2870/new_id
```

Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:
Code:

sudo modprobe rt2870sta
Sorry about the confusion; I meant rt2870sta, the module that your newly installed 10.10 now contains.

---

### Post by blackløtus on 2011-06-24
I have tiped modinfo rt2870sta and the response was: "ERROR: modinfo: could not find module rt2870sta"
I'm thinking that the powerpc version had some diferent modules. Maybe it's inpossible to run the dwa 125 in a powerpc arquitecture with ubuntu...

---

### Post by alistair1946 on 2011-06-24
Sorry chili555, dongle still trying to connect but not succeeding.
Cheers, awaiting further help info.

---

### Post by chili555 on 2011-06-24
> In other way I have downloaded the rt3070 driver from the ralink's page This is the file you want; you can safely delete the RT2870 file you downloaded.

Did you make these changes as mentioned in the README?> In os/linux/config.mk 
	--- snip ---
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.You will need the build tools. Get a wired ethernet connection and do:```
sudo apt-get install build-essential linux-headers-generic
```I am not familiar with PowerPC headers; I am not sure this is correct. You may, instead, need *linux-headers-powerpc*.

Then do:```
cd Descargas/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.2_DPO
sudo su
make
make install
modprobe rt5370sta
exit
```It compiles with warnings but no errors and installs on my x86 system running Natty. I do not know how it will do on your PowerPC system.

Post any errors and we'll work them out together.

---

### Post by chili555 on 2011-06-24
> **alistair1946 said:**
> Sorry chili555, dongle still trying to connect but not succeeding.
Cheers, awaiting further help info.When you see your network SSID and click it, are you asked for your password? Please see attached. When you fill it in, does it try to connect? Have you double-checked the password?

---

### Post by alistair1946 on 2011-06-24
> **chili555 said:**
> When you see your network SSID and click it, are you asked for your password? Please see attached. When you fill it in, does it try to connect? Have you double-checked the password?

Hi Chili555
1. Password required and checked to be correct
2. Network details already entered and checked again. Correct

I have completed network manager details including SSID, ESSID MTU: automatic, wireless security type(WPA & WPA personal) plus password, IPv4: Automatic (DHCP), IPv6 Settings (Ignore)

I'm copying /etc/wireless/RT2870STA/RT2870STA.dat for your perusal

#The word of "Default" must not be removed  
 Default  
 CountryRegion=5  
 CountryRegionABand=7  
 CountryCode=  
 ChannelGeography=1  
 SSID=ALs  
 NetworkType=Infra  
 WirelessMode=5  
 Channel=0  
 BeaconPeriod=100  
 TxPower=100  
 BGProtection=0  
 TxPreamble=0  
 RTSThreshold=2347  
 FragThreshold=2346  
 TxBurst=1  
 PktAggregate=0  
 WmmCapable=1  
 AckPolicy=0;0;0;0  
 AuthMode=WPA2PSK  
 EncrypType=TKIP  
 WPAPSK=  
 DefaultKeyID=1  
 Key1Type=0  
 Key1Str=  
 Key2Type=0  
 Key2Str=  
 Key3Type=0  
 Key3Str=  
 Key4Type=0  
 Key4Str=  
 PSMode=CAM  
 AutoRoaming=0  
 RoamThreshold=70  
 APSDCapable=0  
 APSDAC=0;0;0;0  
 HT_RDG=1  
 HT_EXTCHA=0  
 HT_OpMode=0  
 HT_MpduDensity=4  
 HT_BW=1  
 HT_BADecline=0  
 HT_AutoBA=1  
 HT_AMSDU=0  
 HT_BAWinSize=64  
 HT_GI=1  
 HT_MCS=33  
 HT_MIMOPSMode=3  
 HT_DisallowTKIP=1  
 HT_STBC=0  
 EthConvertMode=  
 EthCloneMac=  
 IEEE80211H=0  
 TGnWifiTest=0  
 WirelessEvent=0  
 MeshId=MESH  
 MeshAutoLink=1  
 MeshAuthMode=OPEN  
 MeshEncrypType=NONE  
 MeshWPAKEY=  
 MeshDefaultkey=1  
 MeshWEPKEY=  
 CarrierDetect=0  
 AntDiversity=0  
 BeaconLostTime=4  
 FtSupport=0  
 Wapiifname=ra0  
 WapiPsk=  
 WapiPskType=  
 WapiUserCertPath=  
 WapiAsCertPath=  
 PSP_XLINK_MODE=0  
 WscManufacturer=  
 WscModelName=  
 WscDeviceName=  
 WscModelNumber=  
 WscSerialNumber=  
 RadioOn=1
 
It includes SSID and security type
Hope this may help. AL

---

### Post by blackløtus on 2011-06-25
hi chili555,

yet I have compiled the driver without errors (the problem was that I haven't download the linux-headers-powerpc)

> 
Did you make these changes as mentioned in the README?I only make this changes 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.                      

The error comes when I typed sudo modprobe rt5370sta

> FATAL: Error inserting rt5370sta (/lib/modules/2.6.35-28-powerpc/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)PD: I have taken a loock at the dmesg but i don't know what it is and I not posted it because it's very large

regards

---

### Post by chili555 on 2011-06-25
Let's see what's going on under the hood. Please run and post:```
sudo cat /var/log/syslog | grep -e rt2 -e etwork | tail -n 25
```Thanks.

---

### Post by chili555 on 2011-06-25
> **blackløtus said:**
> hi chili555,

yet I have compiled the driver without errors (the problem was that I haven't download the linux-headers-powerpc)

I only make this changes 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.                      

The error comes when I typed sudo modprobe rt5370sta

PD: I have taken a loock at the dmesg but i don't know what it is and I not posted it because it's very large

regardsLet's load it into a text file and you can post it as an attachment to your reply using the paperclip tool at the top of the reply box. Please do:```
dmesg > blacklotus.txt
```You will find the text file blacklotus.txt in your user directory. Please attach it to your reply.

---

### Post by blackløtus on 2011-06-25
Hi chili555,

here is the code that you have requested, I have put the "dmesg" and the [FONT=monospace]"[/FONT]sudo cat /var/log/syslog | grep -e rt2 -e etwork | tail -n 25" in the same zip file.

regards

---

### Post by chili555 on 2011-06-25
You did a good job of collecting the data and zipping it; however, there is no reference to rt5370sta at all! Please do:```
sudo modprobe rt5370sta
dmesg | grep rt5
```Post the results or zip and attach if it's easier.

---

### Post by blackløtus on 2011-06-25
Here is the missed info

sudo modprobe rt5370sta:
> 
FATAL: Error inserting rt5370sta (/lib/modules/2.6.35-28-powerpc/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
dmesg | grep rt5
> 
[  186.047004] rt5370sta: module license 'unspecified' taints kernel.
[  186.047777] rt5370sta: Unknown symbol usb_alloc_urb (err 0)
[  186.048117] rt5370sta: Unknown symbol usb_free_urb (err 0)
[  186.048637] rt5370sta: Unknown symbol usb_alloc_coherent (err 0)
[  186.049354] rt5370sta: Unknown symbol usb_register_driver (err 0)
[  186.050220] rt5370sta: Unknown symbol usb_put_dev (err 0)
[  186.051707] rt5370sta: Unknown symbol usb_get_dev (err 0)
[  186.052279] rt5370sta: Unknown symbol usb_submit_urb (err 0)
[  186.052999] rt5370sta: Unknown symbol usb_free_coherent (err 0)
[  186.053725] rt5370sta: Unknown symbol usb_control_msg (err 0)
[  186.055225] rt5370sta: Unknown symbol usb_deregister (err 0)
[  186.056412] rt5370sta: Unknown symbol usb_kill_urb (err 0)


---

### Post by chili555 on 2011-06-25
I wonder if there were any interesting warnings in the build process. Let's make another information file. Please do:```
cd Descargas/2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.2_DPO
sudo su
make clean
make > blacklotus2.txt
make install >> blacklotus2.txt
modprobe rt5370sta >> blacklotus2.txt
exit
```Please attach blacklotus2.txt to your reply.

I'm beginning to think the driver is not compatible with PowerPC's kernel. I will, however, keep looking for a way to get it going with you.

Maybe that's why rt2870sta is not included in the PowerPC version of Ubuntu; because it can't and won't work.

---

### Post by PCNetSpec on 2011-06-25
@**blacklotus** and **chili555**

I don't know if I'm missing something here, but the drivers that contain the **07d1:3c16** device ID are the **2011_0107_RT3070_RT3370_Linux_STA_v2.5.0.1_DPO** drivers.

under the **#ifdef RT3070** section of **/common/rtusb_dev_id.c**

Not sure if you still need to blacklist the rt2800usb drivers with these though, but it can't hurt... personally I'd also blacklist rt2870sta if present.

I've upped a pre-modified version here:
[http://dl.dropbox.com/u/11876059/2011_0107_RT3070_RT3370_Linux_STA_v2.5.0.1_DPO.tar.bz2](http://dl.dropbox.com/u/11876059/2011_0107_RT3070_RT3370_Linux_STA_v2.5.0.1_DPO.tar.bz2)
(if it helps)

pre-modified == WPA enabled.

Now that you have the linux-headers-powerpc and build-essential installed, hopefully they'll compile... but remember to run **make && make install** as root.

Running **[B]make**[/B] as a regular user won't work.

Once installed:
```
modprobe rt3070sta
```

Then **if they work**, but don't survive a reboot... add them to /etc/modules with:
```
sudo sh -c 'echo rt3070sta >> /etc/modules'
```

Sorry if I'm treading on any toes, but worth a try ??

Disclosure - I wrote the tutorial that was mentioned earlier at:
[http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-(ubuntu)/](http://linuxforums.org.uk/hardware-compatibility/ralink-rt2870-based-usb-wireless-n-adapters-(ubuntu)/)

---

### Post by blackløtus on 2011-06-25
I have make other zip file.

@PCNetSpec
The problem cames after installing the driver when I type "sudo modprobe rt5370sta"

> FATAL: Error inserting rt5370sta (/lib/modules/2.6.35-28-powerpc/kernel/drivers/net/wireless/rt5370sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
regards

---

### Post by PCNetSpec on 2011-06-25
Do you get the same error if you **sudo modprobe rt3070sta** ?

---

### Post by blackløtus on 2011-06-25
> **PCNetSpec said:**
> Do you get the same error if you **sudo modprobe rt3070sta** ?

Hi PCNetSpec,

I have download the driver of your link and after compiling and install it I have got the same response:
> 
                             FATAL: Error inserting rt3070sta  (/lib/modules/2.6.35-28-powerpc/kernel/drivers/net/wireless/rt3070sta.ko):  Unknown symbol in module, or unknown parameter (see dmesg)                      

regards

---

### Post by PCNetSpec on 2011-06-25
OK, I've just found this:
[http://www.linuxforums.org/forum/wireless-internet/161550-rt3070sta-module-license-unspecified-taints-kernel-solved.html](http://www.linuxforums.org/forum/wireless-internet/161550-rt3070sta-module-license-unspecified-taints-kernel-solved.html)

I've modified the **usb_main_dev.c** as suggested and uploaded them here:
[http://dl.dropbox.com/u/11876059/blacklotus-2011_0107_RT3070_RT3370_Linux_STA_v2.5.0.1_DPO.tar.bz2](http://dl.dropbox.com/u/11876059/blacklotus-2011_0107_RT3070_RT3370_Linux_STA_v2.5.0.1_DPO.tar.bz2)

Compile and install those and see if you still get the error when you:
```
sudo modprobe rt3070sta
```

I have no idea if this will work, but may be worth a try.

This may also help:
[http://mintppc.org/forums/viewtopic.php?f=10&t=247](http://mintppc.org/forums/viewtopic.php?f=10&t=247)

---

### Post by blackløtus on 2011-06-26
I have tried to install the driver of your link and I can load him, the problem is that it not works fine, I can't connect to my wireless network. Really don't appears any wireless connection.

The output of iwconfig:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  

regards

---

### Post by PCNetSpec on 2011-06-26
If the rt2870sta drivers aren't included by default in the PPC distro, is the firmware present ?

```
ls -l /lib/firmware | grep rt
```

---

### Post by alistair1946 on 2011-06-27
Hi chili555, are you able to check and confirm that this .dat info in posting #90 is correct for use with rt2870sta drivers please. Cheers Al

---

### Post by chili555 on 2011-06-27
> **alistair1946 said:**
> Hi chili555, are you able to check and confirm that this .dat info in posting #90 is correct for use with rt2870sta drivers please. Cheers AlIt looks pretty good to me. Usually, when the driver is compiled to use Network Manager, NM takes over and supplies the details, ESSID, WPA password, etc. so that the .dat file is not really needed, except the all important word Default.

Are you able to scan?```
sudo iwlist ra0 scan
```Any errors here?```
dmesg | grep -e ra0 -e rt2 -e rt3
```

---

### Post by alistair1946 on 2011-06-27
> **chili555 said:**
> It looks pretty good to me. Usually, when the driver is compiled to use Network Manager, NM takes over and supplies the details, ESSID, WPA password, etc. so that the .dat file is not really needed, except the all important word Default.

Are you able to scan?```
sudo iwlist ra0 scan
```Any errors here?```
dmesg | grep -e ra0 -e rt2 -e rt3
```

Here are the results for above.

alistair@ubuntu:~$ sudo iwlist ra0 scan 
 [sudo] password for alistair:  
 ra0       Interface doesn't support scanning.  
 

 alistair@ubuntu:~$ dmesg | grep -e ra0 -e rt2 -e rt3  
 [   30.637192] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.  
 [   31.493728] usbcore: registered new interface driver rt2870  
 [   39.574895] <==== rt28xx_init, Status=0  
 [   46.520728] RTMPFilterCalibration - can't find a valid value, loopcnt=102 stop calibrating<==== rt28xx_init, Status=0  
 alistair@ubuntu:~$  
 
Cheers, Al.

---

### Post by blackløtus on 2011-06-30
hi,
I'm very greatfull for all your help @chili555 and @PCNetSpec, but I finally returned the dwa 125 because seems that it don't works fine in powerpc's architectures. I have asked the TP-Link TL-WN821N with atheros chipset that uses the ar9170usb driver. This driver is included in my kernel and I hope that it will work fine. If I have a problem I will ask in the forum.

Thanks for all.

Regards

---

### Post by chili555 on 2011-06-30
> **blackløtus said:**
> hi,
I'm very greatfull for all your help @chili555 and @PCNetSpec, but I finally returned the dwa 125 because seems that it don't works fine in powerpc's architectures. I have asked the TP-Link TL-WN821N with atheros chipset that uses the ar9170usb driver. This driver is included in my kernel and I hope that it will work fine. If I have a problem I will ask in the forum.

Thanks for all.

RegardsThe firmware is usually not included. You can install it with:```
sudo apt-get install linux-firmware
```I am very sorry we were not able to be more successful.

---

### Post by alistair1946 on 2011-08-09
Hi chilli555, after much frustration and time consumed I have gone and hard wired my linux machine to my WAP and got connected straight away. Great!!!!
I would like to ditch the Windows on this machine (running dual boot at present) and run linux as my sole OS. Is there some way of doing this using partitioning software to delete the Windows OS and leave linux remaining.
Sorry about this delay as I have been unconnected since last communications with you. Woild be greatful for your advice.
Regards Al

---

### Post by chili555 on 2011-08-10
There is a procedure that involves a package called *gparted*. From a live CD, you simply resize the Linux partition over the Windows partition. Then you should redo GRUB so it has no reference to Windows. It is a procedure I have not done in many years. I have been Windows-free for many years, except for one old harddrive I still have with XP so I can tweak my Logitech Harmony remotes.

I strongly suggest you seek guidance on General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331) 

Somebody over there will be more qualified to help.

---

### Post by alistair1946 on 2011-08-11
Hi Chilli555, Thanks a lot for your input in helping me through these issues. I am an older user but enjoy fiddling with linux and the word FREE is right to the fore in my vocabulary. I don't have your skill level but try to help myself where possible.
Kindest regards,
Al

---

### Post by chili555 on 2011-08-11
Older? I may have you beat. I won't say exactly but here are two hints. I retired in the 90s and we are going out today to buy a gift for my great-grandson's birthday.

Have fun!

---

