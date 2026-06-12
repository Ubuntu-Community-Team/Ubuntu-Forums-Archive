---
title: "Ralink rt 3062sta broke with linux update"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by bobman321123 on 2011-11-21
Hey all,
I used to have an issue with the wireless card I have, but that was solved here: [http://ubuntuforums.org/showthread.php?t=1820351](http://ubuntuforums.org/showthread.php?t=1820351)

However, when I downloaded some ubuntu updates, it now gives me a message of "FATAL: rt3062sta does not exist"

so I tried the whole 

"make 
make install
sudo modprobe rt3062sta "
 again.
But this time, it gives me a new error which says "FATAL: Error inserting rt3062sta (/lib/modules3.0.0-13-generic/kernel/drivers/net/wireless/rt3062sta.ko): Invalid argument".

what the heck is the issue here?

P.s. I'd appreciate some rather quick help, as fixing the internet on this computer is somewhat urgent.

Thanks in advance,
Josh

---

### Post by chili555 on 2011-11-21
> what the heck is the issue here?Issue**S**, actually. First of all, when you compile a driver from source, it is specific to the kernel under which it was compiled. You therefor need to compile again for the new kernel. In a terminal, navigate to the directory where the files are located; for example:```
cd Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
```Now recompile:```
sudo su
make clean
make
make install
```The second issue is that the module is called rt3**5**62sta, not rt3062sta:```
modprobe rt3562sta
exit
```

---

### Post by bobman321123 on 2011-11-21
Sorry about the wait, I'm currently dual booting windows XP and linux (something that will be fixed as soon as the wireless on linux is back up XD) and I had to shut down and retry what you said.

So, first off, the module that I successfully used for 2.5 months before the update was indeed 3062, and not 3562. But no matter, I suppose 3062 is outdated.... *shrug*.
Anywho, I tried what you said with the 3562 module, 
"
sudo su
make clean
make
make install
sudo modprobe rt3562sta
"
But when I did, it loaded the module fine (it was listed in the "additional drivers" section of the systems settings), and absolutely nothing happened. 
When I had loaded the 3062 module before the update, it would wait for a second and then connect me to the wifi. 
But with this new one, it loads what seems to be a blank module.
What's wrong?

---

### Post by chili555 on 2011-11-21
Let's take a look at a few settings. Please run and post:```
lspci -nn | grep 0280
iwconfig
dmesg | grep -e rt2 -e rt3
```Thanks.

---

### Post by bobman321123 on 2011-11-21
when I typed "lspci -nn | grep 0280" it returned.
01:07.0 Network controller [0280]: Ralink corp. Device [1814:3062]

When I entered iwconfig it returned:
lo            no wireless extensions
eth0          no wireless extensions
ra0           Ralink STA
              Link Quality:0 Signal level:0 Noise level:0
              Rx invalid nwid:0 invalid crypt:0 invalid misc:0

When I entered dmesg | grep -e rt2 -e rt3 it returned: 
[ 294.215414] ==> rt2860_probe
[ 294.215903] rt2860 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[ 294.218601] @rt2860_probe MAC address: 08:01:08:01:08:01
[ 294.218606]<== rt2860_probe
[ 306.496570] rt28xx_get_wireless_stats --->

p.s. sorry about the wait, I had to type all that out by hand, please forgive any small typos.

---

### Post by chili555 on 2011-11-22
We need to make sure a competing driver is not loaded. Please run:```
lsmod | grep -e rt2 -e rt3
```We hope that rt2800pci is not loaded. If it is, let's blacklist it:```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and check again:```
iwconfig
dmesg | grep -e rt2 -e rt3
```If it's more convenient, you can copy and paste from the terminal into a text document using Gedit, for example, and move the text document on a USB key to post here.

---

### Post by bobman321123 on 2011-11-22
When I ran "lsmod | grep -e rt2 -e rt3"
It returned: 
rt3562sta                982298  0
So, I rebooted and ran lsmod from a blank start.
When I did so, it listed nothing at all as having been loaded.

So anyways, I rebooted and ran iwconfig, 
which returned: 
lo        no wireless networks
eth0      no wireless networks

dmesg | grep -e rt2 -e rt3: 
displays absolutely nothing

p.s. is it possible that I've downloaded the incorrect module?

---

### Post by chili555 on 2011-11-22
> So, I rebooted and ran lsmod from a blank start.
When I did so, it listed nothing at all as having been loaded.That just indicates that the module didn't automagically load on boot. If you load it manually, you should get a wireless interface ra0:```
sudo modprobe ra0
iwconfig
```As well, you should then get some activity in the kernel messages:```
dmesg | grep -e rt2 -e rt3
```> p.s. is it possible that I've downloaded the incorrect module? I don't know which one you downloaded. The one I referred to in my example, DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217, is the latest available on Ralink's website. It is pretty old in Linux terms, almost a year! It produced many warnings, but no errors, when I compiled it on my own system. It is clearly intended to be correct for your device:```
chili@LAPTOP60:~$ modinfo Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko | grep 3062
filename:       Desktop/Forum/L_/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217/os/linux/rt3562sta.ko
alias:          pci:v0000[COLOR="Red"]1814[/COLOR]d0000[COLOR="Red"]3062[/COLOR]sv*sd*bc*sc*i*
```

This is a tough issue. The intent is to fold all the 'staging' modules into the mainline module in kernel >= 3.0. Your device is intended to be driven by rt2800pci. Before you modprobe rt3562sta, you might try rt2800pci:```
sudo modprobe rt2800pci
iwconfig
```Do you have a wireless interface wlan0? Does it try to connect? Any clues here?```
dmesg | grep rt2
```

---

### Post by bobman321123 on 2011-11-22
When I ran sudo modprobe ra0 after manually loading the module, it returned:
FATAL: Module ra0 not found.

when I ran iwconfig:
lo no wireless extensions
eth0 no wireless extensions
ra0 Ralink STA
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0

when I ran dmesg | grep -e rt2 -e rt3:

[  528.870181] ===> rt2860_probe
[  528.870664] rt2860 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[  528.873392] @rt2860_probe MAC address: 08:01:08:01:08:01
[  528.873397] <=== rt2860_probe
[  532.011008] rt28xx_get_wireless_stats --->
[  707.151578] rt28xx_get_wireless_stats --->

when I rebooted and tried " sudo modprobe rt2800pci" instead of the rt3562sta module, it didn't error, but nothing at all happened.
when I then ran iwconfig, it returned:
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

When I ran "dmesg | grep rt2":

[  104.463838] rt2800pci 0000:01:07.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
[  104.502298] Registered led device: rt2800pci-phy0::radio
[  104.502338] Registered led device: rt2800pci-phy0::assoc
[  104.502383] Registered led device: rt2800pci-phy0::quality
[  104.696602] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware


p.s. I'm pretty sure that module is the exact version I have downloaded.

---

### Post by chili555 on 2011-11-22
Arrrgh! Sorry about the mis-step; I meant:```
sudo modprobe rt3562sta
```> I'm pretty sure that module is the exact version I have downloaded. It's easy to find out.```
modinfo rt3562sta
```Does it report version 2.4.1.1?

Did you make the required changes before you compiled?> Right click the package and select 'Extract here.' Open the folder that is extracted and open os/linux/config.mk with the text editor and set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'. They are currently =n. Proofread, save and close the text editor.If not, you'll need to do so and recompile:```
cd Desktop/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217
sudo su
make clean
make
make install
modprobe -r rt3562sta
modprobe rt3562sta
exit
```

---

### Post by bobman321123 on 2011-11-23
*gasp* Oh my goodness! When i changed the WPA support to Y, and recompiled, it worked! 
Thank you so much, you're a lifesaver. :D

p.s.sorry about the long wait, I had something that _needed_ done, so I booted to windows for a day.

Thanks again! 
Josh

---

### Post by chili555 on 2011-11-23
No probs. I'm very glad it's working! Have fun!

---

