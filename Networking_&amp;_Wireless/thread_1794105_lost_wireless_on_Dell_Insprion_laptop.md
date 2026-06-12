---
title: "lost wireless on Dell Insprion laptop"
date: 2011-06-30
forum: Networking &amp; Wireless
---

### Post by glendavee on 2011-06-30
My wife's laptop is Dell Inspiron 6400 running 11.04. Wireless has recently stopped working. Running 
rfkill list all 
shows dell-wifi hard blocked no soft blocked no.
The fn plus F2 keys toggle status between blocked no and blocked yes, but network manager still can't see network
I've tried removing the Broadcom STA driver - no joy. 

Grateful for any suggestions

---

### Post by mikewhatever on 2011-06-30
Please, help us help you, and post some relevant technical info. Check out the link below for the info on what to post.
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by glendavee on 2011-06-30
Network controller is BCM4311
output of iwconfig   l0  no wireless extensions
                     eth0 no wireless extensions
ifconfig gives 
eth0 Link encap:Ethernet   HWaddr 00:1d:09:bf:84:08
     UP BROADCAST MULTICAST  MTU:1500  Metric:1


output of iwlist scan 
eth0   Interface doesn't support scanning
l0     ditto

using kernel 2.6.38-8

Hope this helps

---

### Post by mikewhatever on 2011-06-30
Thanks, that was a step in the right direction. Why don't you just post the outputs as is, preferably using 
[noparse]```

```[/noparse] tags to make them more readable.
...and what about the output of **sudo lshw -C network**?

---

### Post by glendavee on 2011-06-30
Difficult to post outputs as is when not using the computer in question. However have now managed to get a wired connection to laptop in question and here is info requested



angela@angela-laptop:~$ sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:bf:84:08
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.4 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 memory:ef9fe000-ef9fffff


regards

---

### Post by chili555 on 2011-06-30
> However have now managed to get a wired connection to laptop in question and here is info requestedAwesome! Now let's get our geek on and crack this case before supper. Please also post:```
dmesg | grep b43
rfkill list all
lsmod | grep dell
```The pipe symbol | is on the right side of my US keyboard on the same key with \> Thanks.

---

### Post by glendavee on 2011-06-30
Here goes

angela@angela-laptop:~$ dmesg | grep b43
[   29.908675] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
angela@angela-laptop:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
angela@angela-laptop:~$ lsmod | grep dell
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop

---

### Post by chili555 on 2011-06-30
We're getting close! Now, how about:```
ls /etc/modprobe.d | grep b43
sudo modprobe b43
iwconfig
```Thanks.

---

### Post by glendavee on 2011-06-30
angela@angela-laptop:~$ ls /etc/modprobe.d | grep b43
angela@angela-laptop:~$ sudo modprobe b43
[sudo] password for angela: 
angela@angela-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by chili555 on 2011-06-30
Everything looks beautiful. Does it scan?```
sudo iwlist wlan0 scan
```Do you see networks when you click the Network Manager icon? Can you click yours and yell, "Angela! It works!"

---

### Post by glendavee on 2011-06-30
Sorry, no champagne just yet...


angela@angela-laptop:~$ sudo iwlist wlan0 scan
[sudo] password for angela: 
wlan0     Interface doesn't support scanning : Network is down

---

### Post by chili555 on 2011-06-30
Something's wacky. I see nothing wrong to fix. It ought to spring to life. Let's do a full diagnostic. We are going to create a text file and zip it so I can examine the log files. Please detach the ethernet cable and cold-boot. Open a terminal and do:```
lspci-nn > glen.txt
dmesg >> glen.txt
lsmod >> glen.txt
zip glen.zip glen.txt
```Now hook up the ethernet cable and attach the file glen.zip that you will find in your user directory to your reply using the paperclip tool at the top of the reply box.> I've tried removing the Broadcom STA driver - no joy. Did it seem to work with the STA driver before Angela complained? I am working on a suspicion.

---

### Post by glendavee on 2011-06-30
Here's the .zip file
hope it helps

---

### Post by chili555 on 2011-06-30
Please do:```
sudo su
echo "blacklist wl" >> /etc/modprobe.d/blacklist.conf
echo b43 >> /etc/modules
exit
```Reboot and let me see:```
dmesg | grep b43
iwconfig
```The Broadcom 4311 is one of those quirky devices that's claimed by two drivers, so we load one automatically and blacklist the other. If this works as expected, we'll take one more housekeeping step.

---

### Post by nm_geo on 2011-06-30
He has that perfect storm..  B44 and b43 need the ssb module STA (wl) wants to blacklist ssb.  Interesting verrry Interesting. Watch and learin' here.

---

### Post by chili555 on 2011-06-30
> **nm_geo said:**
> He has that perfect storm..  B44 and b43 need the ssb module STA (wl) wants to blacklist ssb.  Interesting verrry Interesting. Watch and learin' here.Here's a clue for all you driver students:```
$ modinfo wl | grep 4311
alias:          pci:v000014E4d0000[COLOR="Red"]4311[/COLOR]sv*sd*bc*sc*i*
$ modinfo ssb | grep 4311
alias:          pci:v000014E4d0000[COLOR="Red"]4311[/COLOR]sv*sd*bc*sc*i*
```Obviously, one or the other will work, but not both. Rollin' the dice and a little Googling told me to try b43 first. If it springs to life, we'll remove and purge bcmwl-kernel-source.

Sometimes, I'm even surprised myself about how they come out.

---

### Post by glendavee on 2011-07-01
This gets curiouser and curiouser. Now can't establish either wired or wireless contact, so I'm back on my own machine. Here are the outputs requested :
[COLOR="Red"]angela@angela-laptop:~$ dmesg | grep b43 
[   27.601923] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
[   27.601937] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64 
[   27.733345] b43-phy0: Broadcom 4311 WLAN found (core revision 10) 
[   27.992671] Registered led device: b43-phy0::tx 
[   27.992704] Registered led device: b43-phy0::rx 
[   27.992732] Registered led device: b43-phy0::radio 
[   43.045631] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   43.045637] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[   43.045641] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[   44.296079] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   44.296084] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[   44.296087] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[   50.099995] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   50.100057] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[   50.100061] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[   55.077537] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   55.077543] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[   55.077547] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[   60.059529] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   60.059536] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[   60.059540] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[   65.062424] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   65.062430] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[   65.062434] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[   76.166881] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[   76.166887] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[   76.166891] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[  143.428608] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[  143.428614] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[  143.428617] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[  143.513599] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[  143.513604] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[  143.513608] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[  154.469227] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[  154.469232] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[  154.469236] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
[  154.525863] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found 
[  154.525869] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found 
[  154.525872] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website. 
angela@angela-laptop:~$ iwconfig 
lo        no wireless extensions. 

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off [/COLOR]

---

### Post by chili555 on 2011-07-01
We can get the wireless going very easily if we have the wired going. Please do:```
sudo modprobe b44 ssb
ifconfig
```Is your wired working? If so, don't blink or do anything but:```
sudo apt-get install b43-fwcutter firmware-b43-installer
```If it goes well, with no error, reboot and detach the ethernet cable. Your wireless should be working. We'll need to do a couple of more housekeeping steps.

---

### Post by glendavee on 2011-07-01
Nothing is easy here. Still no wired connection. Here's what happened :


angela@angela-laptop:~$ sudo modprobe b44 ssb 
[sudo] password for angela: 
FATAL: Error inserting b44 (/lib/modules/2.6.38-8-generic/kernel/drivers/net/b44.ko): Unknown symbol in module, or unknown parameter (see dmesg) 
angela@angela-laptop:~$ ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

### Post by chili555 on 2011-07-01
> Error inserting b44 (/lib/modules/2.6.38-8-generic/kernel/drivers/net/b44.ko): Unknown symbol in module, or unknown parameter (see dmesg) Yikes! Dr. Chili doesn't like that one bit! Let's follow the suggestion:```
dmesg | grep -e b44 -e ssb
```I have to take a tranquilizer now...

---

### Post by glendavee on 2011-07-01
angela@angela-laptop:~$ dmesg | grep -e b44 -e ssb 
[   27.836118] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243) 
[   27.836131] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243) 
[   27.836142] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243) 
[   27.836152] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243) 
[   27.876158] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0 
[  101.433999] b44: Unknown parameter `ssb'

---

### Post by chili555 on 2011-07-01
Dr. Chili very seldom curses, but I deserve a curse. I goofed. How about a redo:

We can get the wireless going very easily if we have the wired going. Please do:
```
sudo modprobe b44 
sudo modprobe ssb
ifconfig
```
Is your wired working? If so, don't blink or do anything but:
```
sudo apt-get install b43-fwcutter firmware-b43-installer

```Sorry about that!

---

### Post by glendavee on 2011-07-01
hallelujah!!  You got there.  Now have wireless up and running.
I'm very impressed!

---

### Post by chili555 on 2011-07-01
I'm glad it's working. Let's clean up a few things.```
sudo apt-get remove --purge bcmwl-kernel-source
```Now look for any left over items in /etc:```
ls /etc/modprobe.d | grep b43
```Is there anything in there named b43-something? If so, post it so we can examine it:```
cat /etc/modprobe.d/b43-whatyoufound
```We will probably remove it but, to be certain, let's look at it first.

I think you're all set, but if Angela has any more difficulty, please post back.

---

### Post by glendavee on 2011-07-01
All seems well. modprobe shows nothing. Seems like we're done. Again, many thanks Dr Chili

---

### Post by nm_geo on 2011-07-01
Excellent chili you calmed the perfect storm .. I sure would like to search those bloacklist files but we will see..

---

### Post by mikewhatever on 2011-07-02
> **glendavee said:**
> All seems well. modprobe shows nothing. Seems like we're done. Again, many thanks Dr Chili

Glad you solved it, but I am curious, how did you end up with the two drivers installed?

---

### Post by glendavee on 2011-07-03
I'm ashamed to tell you that I haven't a clue. The wireless had been working ok, though it was a bit tempermental from time to time. Problem surfaced when laptop was booted after a couple of weeks vacation. To best of my knowledge there were no changes made, other than via update manager - maybe a new kernel didn't like the configuration?

---

### Post by mikewhatever on 2011-07-03
That's ok, sometimes, things just happen. Thanks for your wonderful cooperation, and thanks to Chili555 for great know-how.

---

