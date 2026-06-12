---
title: "EEE PC 1000HE RT2860 / WAP2 problem"
date: 2011-07-16
forum: Networking &amp; Wireless
---

### Post by Bedlore on 2011-07-16
I'm running a fresh install of Natty 11.04, 2.6.38-10-generic #46-Ubuntu SMP i686 i686 i386.

I compiled as per [http://ubuntuforums.org/showthread.php?t=1476007](http://ubuntuforums.org/showthread.php?t=1476007) the process seemed to go smoothly but I still am unable to connect to my network which is secured by WAP2.  I do get occasionally connections but often they are very slow, but 99% of the time it just won't connect.

Please help me debug it as I don't really where to start.

---

### Post by chili555 on 2011-07-16
Let's start with:```
lspci -nn | grep 0280
lsmod | grep rt2
```Thanks!

---

### Post by Bedlore on 2011-07-16
Thanks :)

bedlore@oat:~$ lspci -nn | grep 0280
01:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]

bedlore@oat:~$ lsmod | grep rt2
rt2860sta             765048  0 
rt2800pci              18119  0 
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              13986  1 rt2800pci
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
eeprom_93cx6           12653  1 rt2800pci

---

### Post by chili555 on 2011-07-16
You probably didn't need to build rt2860sta from source. You have a conflict that, once resolved, will probably fix your wireless. Please do:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

---

### Post by Bedlore on 2011-07-16
Upon reboot I no wireless interface is shown in the network manager anymore, I wonder if this could relate to me earlier installing wicd and then later purging it?

The previous outputs now look like this:

lsmod | grep rt2
rt2860sta             765048  0 

lspci -nn | grep 0280
01:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]

---

### Post by chili555 on 2011-07-16
Let's see:```
modinfo rt2860sta
iwconfig
dmesg | grep rt2
```> 
lsmod | grep rt2
rt2860sta 765048 0

lspci -nn | grep 0280
01:00.0 Network controller [0280]: Ralink corp. RT2860 [1814:0781]
Perfect!

I have an early start tomorrow. See you later.

---

### Post by Bedlore on 2011-07-17
Thanks heaps.  Here is the output you asked for;

# modinfo rt2860sta
filename:       /lib/modules/2.6.38-10-generic/kernel/drivers/net/wireless/rt2860sta.ko
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
vermagic:       2.6.38-10-generic SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)


# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  
          Mode:Auto  Frequency=2.412 GHz  Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


# dmesg | grep rt2
[   14.273235] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.273314] rt2860 0000:01:00.0: setting latency timer to 64
[ 2571.613036] !!! rt28xx Initialized fail !!!
[ 2572.048293] !!! rt28xx Initialized fail !!!
* last line repeats *

---

### Post by chili555 on 2011-07-17
I think it is looking for and missing the .dat file. Let's look:```
dmesg | grep -i rt2
ls /etc/Wireless/
ls /etc/Wireless/RT2860STA
```We're close!

---

### Post by Bedlore on 2011-07-17
Thanks for your persistence

```

root@oat:~# dmesg | grep -i rt2
[   14.628953] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.629032] rt2860 0000:01:00.0: setting latency timer to 64

root@oat:~# ls /etc/Wireless/
RT2860STA

root@oat:~# ls /etc/Wireless/RT2860STA/
RT2860STA.dat

```

---

### Post by chili555 on 2011-07-17
Here is yesterday:> # dmesg | grep rt2
[ 14.273235] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[ 14.273314] rt2860 0000:01:00.0: setting latency timer to 64
[COLOR="Red"][ 2571.613036] !!! rt28xx Initialized fail !!!
[ 2572.048293] !!! rt28xx Initialized fail !!!
* last line repeats *[/COLOR] And today:> # dmesg | grep -i rt2
[   14.628953] rt2860 0000:01:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   14.629032] rt2860 0000:01:00.0: setting latency timer to 64So is it working today? Does it scan?```
sudo iwlist ra0 scan
```Can you see networks in Network Manager?

---

### Post by Bedlore on 2011-07-18
$ sudo iwlist ra0 scan
ra0       No scan results

Previously my wireless was referred to as wlan0 for what its worth.

Nothing visible in network manager and now I no longer have "Enable/Disable Wireless" although I note I still can from the hardware level.

---

### Post by chili555 on 2011-07-18
Unless someone has removed it, rt2860sta is included in recent kernels by default. Most devices cause a conflict by also loading rt2800pci. When the wireless doesn't work very well because of the underlying conflict, many compile a new driver from source. Since it doesn't fix the underlying driver conflict, it still doesn't work very well! Let's see if we can unravel your situation. 

First, let's make sure the original is still there:```
sudo updatedb
locate rt2860sta
```If the original is still in place in kernel/drivers/staging/rt2860, then we can safely remove the not-working driver that you compiled:```
cd Desktop/2010_07_16_RT2860_Linux_STA_v2.4.0.0/
```Substitute the correct location, if not as above. Now do:```
sudo su
make clean
make uninstall
rmmod -f rt2860sta
modprobe rt2860sta
exit
```Any improvement?

---

### Post by Bedlore on 2011-07-18
I've getting the distinct impression I've made a real pickle of this. No joy at this point I'm afraid.

I followed your directions..

# locate rt2860sta
/lib/modules/2.6.38-10-generic/kernel/drivers/staging/rt2860/rt2860sta.ko.dist
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko

...
$ modprobe rt2860sta
FATAL: Module rt2860sta not found.

---

### Post by chili555 on 2011-07-18
> /lib/modules/2.6.38-10-generic/kernel/drivers/staging/rt2860/rt2860sta.ko[COLOR="Red"].dist[/COLOR]Very interesting! Well, almost no pickle is too big for me! Please do:```
sudo mv /lib/modules/2.6.38-10-generic/kernel/drivers/staging/rt2860/rt2860sta.ko.dist /lib/modules/2.6.38-10-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
sudo modprobe rt2860sta
```Be sure to check blacklist and make sure rt2800pci is listed:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Make sure this line exists or add it:```
blacklist rt2800pci
```Proofread, save and close gedit.

Now is it working?

---

### Post by Bedlore on 2011-07-18
After moving.
sudo updatedb
# locate rt2860sta
/lib/modules/2.6.38-10-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2860/rt2860sta.ko

# sudo modprobe rt2860sta
FATAL: Module rt2860sta not found.

Last line of /etc/modprobe.d/blacklist.conf does contain: blacklist rt2800pci

Alas, no joy.

---

### Post by Bedlore on 2011-07-18
On the upside, I just noticed my bean count is clicking over nicely :)

---

### Post by chili555 on 2011-07-18
Well, hopefully you won't get to 100 in this thread! Please try a reboot and then see if it loaded:```
lsmod | grep rt2
sudo modprobe rt2860sta
```

---

### Post by Bedlore on 2011-07-18
# lsmod | grep rt2
# sudo modprobe rt2860sta
FATAL: Module rt2860sta not found.

---

### Post by Bedlore on 2011-07-18
You think I need to start from scratch and recompile? 

2am here so I'd better hit the sack, thanks again.

---

### Post by chili555 on 2011-07-18
First try this:```
sudo apt-get install --reinstall linux-image-`uname -r`
```Shut down the computer, get some rest and we'll try tomorrow.

Those backticks are on the left side of my US keyboard on the same key with ~.

---

### Post by thunderloki on 2011-07-18
On that note, I am having the same problem with Desktop -- modprobe rt2860sta results in "not found".  I am thinking if I do a locate rt2860sta it will give me what I need, but ... not too sure if that will help me.  Maybe I can install it from the server CD?  I am able to modprobe it in Server mode.

---

### Post by chili555 on 2011-07-18
> I am thinking if I do a locate rt2860sta it will give me what I need,Please do, back on your thread, please.

---

### Post by Bedlore on 2011-07-18
> **chili555 said:**
> First try this:```
sudo apt-get install --reinstall linux-image-`uname -r`
```

Woohoo!  That did the trick, brilliant, I'm a happy chappy, now I can go to bed and knowing tomorrow will be a happier day :D

Thanks heaps, do you have a paypal account or similar where I can show some appreciation.  It's people like yourself that keep the net and linux a wonder-filled place.

Oh, will I need to recompile with each new kernel or should this driver build survive updates?

---

### Post by chili555 on 2011-07-18
You showed me all the appreciation I ever need:> I'm a happy chappy, now I can go to bed and knowing tomorrow will be a happier dayIf you feel you just must show some appreciation, then I suggest: [http://www.ubuntu.com/community/get-involved/donate](http://www.ubuntu.com/community/get-involved/donate)

I'm glad it's working. Enjoy it, my friend!

---

