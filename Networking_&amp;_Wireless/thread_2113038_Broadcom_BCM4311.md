---
title: "Broadcom BCM4311"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by McTrick on 2013-02-06
Okay, so I wanted to be able to figure this one out on my own but I don't think that's going to happen. I have an old HP Compaq 6515b, I am running gnome remix 12.10 full install. It runs great! 

I have one minor problem tho that I cannot seem to fix :( My wireless driver wasn't there at first so I ran apt-get update && apt-get upgrade. Boom there it was, so I selected it in additional drivers, did a reboot and then BOOM it was gone fml. I removed it, purged it, used autoremove, and then installed linux-firmware-nonfree... Yay its working, but damn it all it wont stay connected for more than a minute or so. It is constantly asking for re-authentication.

I have been through the forums, the only thing that almost worked was nothing. Any help would be great. I am trying to set this up for my wife. She loves the look, feel, and speed of gnome-remix. But if I cant get this thing some reliable wireless I am afraid I will have to send her back to Windows... Nobody wants that.

---

### Post by kurt18947 on 2013-02-06
To start with, if it's an internal card, could you open a terminal and post the output of this command:

```
lspci
```If it's a USB dongle, use this command:

```
lsusb
```We're looking for the chipset used in your machine.  It'll look something like this:

> 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
A wireless device is typically a network controller, not an ethernet controller which is a wired network device.  There are exceptions to that though.

You might also have better success having this moved to the networking and wireless forum if you don't get replies here.  Wireless networking & linux are popular topics.

---

### Post by McTrick on 2013-02-06
I believe this is what your looking for.

10:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
30:00.0 Network controller: Broadcom Corporation BCM4311 802.11a/b/g (rev 02)

As I said, I have tried to activate this and as soon as I did a reboot the driver completely disappeared. This is why I put it in the Hardware section, but I will move it as suggested as soon as I figure out how.

---

### Post by tgalati4 on 2013-02-06
You need to load or reload the Broadcom proprietary driver.

Open a terminal and post the output of:

```
dmesg | grep b43
```

It should look something like:

tgalati4@Dell600m-mint14 ~ $ dmesg | grep b43
[   32.330472] Registered led device: b43-phy0::tx
[   32.330511] Registered led device: b43-phy0::rx
[   32.330545] Registered led device: b43-phy0::radio
[   32.588055] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[ 2726.412085] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)

---

### Post by howefield on 2013-02-06
> **McTrick said:**
> ..This is why I put it in the Hardware section, but I will move it as suggested as soon as I figure out how.

Thread moved to "Networking and Wireless" and thread title edited to reflect the subject.

---

### Post by McTrick on 2013-02-06
[    9.972663] b43-phy0: Broadcom 4311 WLAN found (core revision 13)
[   10.851153] Registered led device: b43-phy0::tx
[   10.851175] Registered led device: b43-phy0::rx
[   10.851198] Registered led device: b43-phy0::radio
[   19.532063] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  214.884105] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  215.744100] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  216.484100] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  216.884103] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  275.896118] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  523.324924] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  523.916098] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  542.664079] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  543.304218] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  544.184129] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  544.560072] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[  561.588079] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)

Not sure about what I am about to say, but it looks like its having an issue loading the firmware...

Also I had an idea, seeing how broadcom always likes to manage its own stuff in windows I decided to try and install wcid Network Manager hoping maybe that would work... No luck, still the same thing. It cannot get past "validating authentication" and then give me an error "bad password". I went in to my router and set up a guest accoung and niether network manager nor wcid will connect to it. Freezes up at "obtaining ip address"

---

### Post by McTrick on 2013-02-06
> **howefield said:**
> Thread moved to "Networking and Wireless" and thread title edited to reflect the subject.


Thanks :)

---

### Post by ankur1993 on 2013-02-06
first to detect modem.
using terminal type lsusb.
and install wireless.

---

### Post by wildmanne39 on 2013-02-06
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.

Also please make sure have network manager installed and then remove wicd you can not have both installed at the same time.
Thanks

---

### Post by McTrick on 2013-02-06
> **ankur1993 said:**
> first to detect modem.
using terminal type lsusb.
and install wireless.

Output of lsusb:
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Also you said "install wireless", I'm not sure what your asking. My wireless is on, it picks up a signal, and sometimes connects for a few seconds before asking for my network password again...

---

### Post by McTrick on 2013-02-06
Okay I think I attached the file and I have removed wcid as suggested. Sorry for being such a noob,

---

### Post by McTrick on 2013-02-06
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back  and attach the netinfo.txt file.

Also please make sure have network manager installed and then remove wicd you can not have both installed at the same time.
Thanks

Done! :)

---

### Post by wildmanne39 on 2013-02-06
Hi, please do:
```
sudo apt-get purge b43-fwcutter firmware-b43-installer
```
Then:
Download the b43 zip file then drag and drop the file to your desktop. Right-click it and select Extract Here. Open a terminal and do:
```
cd Desktop
sudo mv b43/* /lib/firmware
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43
```
if it does not connect remove the textinfo file in your home folder and run the wireless script again and attach the results.
Thanks

---

### Post by McTrick on 2013-02-06
[QUOTE= sudo rmmod -f ssb
sudo modprobe b43[/CODE]if it does not connect remove the textinfo file in your home folder and run the wireless script again and attach the results.
Thanks[/QUOTE]

I cannot get past sudo rmmod -f ssb it keeps giving me "ERROR: Removing 'ssb': Resource temporarily unavailable.. 

Sorry for being such a pain...

---

### Post by wildmanne39 on 2013-02-06
Hi, I suspect it is because your ehternet is also using that module, why don't you disable it and try the commands again.
Thanks

---

### Post by lbourik on 2013-03-09
Hello! I am completely noob to Ubuntu as I have been using them only for a couple of days now...
First of all thank you all in advance for your time and help! the forum is great! 
I have a Latitude D430 and after installing 12.10 I cannot use the wifi. I followed several threads witout success unfortunately.
I tried to remove all drivers, disabled the STA drivers from software sources and load b43 but it does not seem to work.
At one point I had kernel module ssb with kernel driver b43 but that did not work.
Also rfkill command returns nothing in terminal and I have played around with blacklist config but no success either.
I have synaptic manager installed, tried to remove wl and b43 and reinstall bcmwl kernel source wtih STA common, STA source but no success.
Then uninstalled STA common STA source and loaded dkms but did not work either....
Ethernet working good and I have internet access. However, in Desktop and at the network bar/sign wirelless is not a listed (i.e. not selection, hotspots nothing :))
I can see that there is a battle of drivers happening :) and the issues with conflict but I am probably missing too many info and data... :confused: 
Hence, please help!! I have restored bcmwl, activated the STA driver in software sources and there seem to be no driver at the moment.

here are the current lspci -vnn results

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at efdfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: wl, ssb

I have also updated to 3.0.5.-18 ..or something near :P

Thank you very much!! 
I greatly appreciate your help to save the laptop :P

---

### Post by Hadaka on 2013-03-09
Hi, please do..
```
 sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
thanks

---

### Post by lbourik on 2013-03-10
> **Hadaka said:**
> Hi, please do..
```
 sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
thanks

Hi! That is amazing! Thank you a lot! Followed your instructions and wireless is up and running.
However after reboot I had to repeat sudo modprobe b43 to make it work again. Otherwise it was in the same state with before...
Do you know how could I solve that problem? It is not much to write the command every time but it would be nicer
not follow the same drill every time :)! Should I blacklist or remove something?
It seemed that I was missing the linux firmware non free bit...If it is not a big trouble could you drop me a line what your commands did and what was the issue?
I am really keen to learn something new and understand bit better how things are working :P
lspci -vnn now reads:
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at efdfc000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb


I had the same before without result...so I guess the firmware made the difference..:confused:

Thank you very much for your help! please let me know if there is a way not to have to modprobe b43 every time I reboot :)
Really happy that there is a solution after all...and such a fast and short one..so great!:)

---

