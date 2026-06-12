---
title: "UBUNTU 10.04 Wireless Network Issues"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by TRaptor on 2011-04-24
Hey guys,
I am on a Dell Vostro 1520, running Ubuntu 10.04 and I am having problems connecting to the internet via wireless. Wired connection works but wireless doesn't. My laptop is running a Broadcom BCM4312 wireless card. And it says "wireless is disabled", how do I enable it?

What do I have to do to get this working? I really like Ubuntu but am disliking the pain I am going through trying to get this working. Any help is greatly appreciated!

---

### Post by josephmills on 2011-04-24
hi there and welcome please press ctrl+alt+t after the box shows up please type in```
 rfkill list all
``` then  paste it here thanks

---

### Post by leviathan8 on 2011-04-24
Tick "Enable Wireless" by right clicking on the network manager applet. It is in your notification area (the small icons that show different programs running in tray), usually located on the top panel near the clock, if it hasn't been changed by you.

---

### Post by TRaptor on 2011-04-24
Here is the outcome of "rfkill list all":
```

0: dell-wifi: Wireless LAN
           Soft blocked: no
           Hard blocked: yes
1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no

```And there is nothing there that says "Enable Wireless"!

---

### Post by josephmills on 2011-04-24
> **TRaptor said:**
> Here is the outcome of "rfkill list all":
```

0: dell-wifi: Wireless LAN
           Soft blocked: no
           Hard blocked: yes
1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no

```And there is nothing there that says "Enable Wireless"!

try ```
rfkill unblock all
``` or ```
rfkill unblock wifi 
``` tell us what happens

---

### Post by TRaptor on 2011-04-24
> **josephmills said:**
> try ```
rfkill unblock all
``` or ```
rfkill unblock wifi 
``` tell us what happens

Thanks but it didn't make any difference. Any other suggestions?

---

### Post by josephmills on 2011-04-24
turn on  your wireless button thats what the hard block is telling us that your wireless button switch is off untill it is turned on it will not work lets see what you are working with ```
sudo lshw -C network
``` IT TAKES A WHILE TO LOAD please post out put here thanks

---

### Post by TRaptor on 2011-04-25
> **josephmills said:**
> turn on  your wireless button thats what the hard block is telling us that your wireless button switch is off untill it is turned on it will not work

Do you mean the switch of the side of my laptop that disables wireless? If so that is already in the on position!

> **josephmills said:**
> lets see what you are working with ```
sudo lshw -C network
``` IT TAKES A WHILE TO LOAD please post out put here thanks

Here is the print out for that:

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:a8:37:c0
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:4000(size=256) memory:fe004000-fe004fff(prefetchable) memory:fe000000-fe003fff(prefetchable) memory:fe020000-fe03ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f6000000-f6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:a3:23:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by TRaptor on 2011-04-25
> **TRaptor said:**
> Do you mean the switch of the side of my laptop that disables wireless? If so that is already in the on position!



Here is the print out for that:

```

  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:a8:37:c0
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:4000(size=256) memory:fe004000-fe004fff(prefetchable) memory:fe000000-fe003fff(prefetchable) memory:fe020000-fe03ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f6000000-f6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:a3:23:e0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

Bump....

---

### Post by josephmills on 2011-04-25
> **TRaptor said:**
> Bump....
move the switch for the wifi to off then on again then post the out come of ```
rfkill list 
``` thanks

---

### Post by josephmills on 2011-04-25
see you need the b43 driver but we need to get the switches figured out first
after you figure that out please post ```
lsmod | grep b43 
``` and ```
dmesg | grep b43 
``` thanks and just to make sure that you have the 4312 please do a 
```
lspci -vnn | grep 14e4
```

---

### Post by TRaptor on 2011-04-25
> **josephmills said:**
> move the switch for the wifi to off then on again then post the out come of ```
rfkill list 
``` thanks

Did that and it gave me the the same:
```
0: dell-wifi: Wireless LAN
           Soft blocked: no
           Hard blocked: yes
1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no
```

> **josephmills said:**
> see you need the b43 driver but we need to get the switches figured out first
after you figure that out please post ```
lsmod | grep b43 
``` 

That gives:
```

b43                                 163523   0
mac80211                     205146   1   b43
cfg80211                       126517   2  b43,mac80211
led_class                             2864   2  b43,sdhci
ssb                                     38671  1  b43

```

> **josephmills said:**
> and ```
dmesg | grep b43 
```

Here is that:
```

[ 8885.132530] b43-pci-bridge 0000:0e:00.0: PCI INT A disabled
[ 8887.047433] b43-pci-bridge 0000:0e:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 8887.047495] b43-pci-bridge 0000:0e:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf6000004)
[ 8887.047507] b43-pci-bridge 0000:0e:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 8887.047524] b43-pci-bridge 0000:0e:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
[ 8887.592071] b43-pci-bridge 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 8916.800457] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[ 8916.803071] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[ 8916.806037] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 8916.806044] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 8916.806048] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 8933.708272] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[ 8933.710815] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[ 8933.713777] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 8933.713784] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 8933.713789] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.

```


> **josephmills said:**
> just to make sure that you have the 4312 please do a 
```
lspci -vnn | grep 14e4
```

And here is that:
```

0e:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)

```

---

### Post by josephmills on 2011-04-25
[b]8933.713777] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 8933.713784] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 8933.713789] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)[/b]


Bingo ok please click on this link it will download your firmware and driver [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 then after you downloaded it move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/ 
``` then tell us when you get that far

---

### Post by TRaptor on 2011-04-25
> **josephmills said:**
> [b]8933.713777] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 8933.713784] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 8933.713789] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)[/b]


Bingo ok please click on this link it will download your firmware and driver [http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz](http://www.omattos.com/sites/default/files/b43-all-fw.tar_.gz)
 then after you downloaded it move it to you **home folder** then right click on your on your home folder ** not** your download. now you want to **create a folder** called **wireless** then put the download in the folder. After that go back to your terminal and type in ```
sudo cp -r ~/wireless/* /lib/firmware/ 
``` then tell us when you get that far

If I leave the download as is and put into the wireless folder I created, then I just did that and ran the code in the terminal! What next?

BTW: I appreciate your help!

---

### Post by josephmills on 2011-04-25
```

cd /lib/firmware

```
then 
```

sudo -s 

```
then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```
tell us what happens

---

### Post by TRaptor on 2011-04-25
> **josephmills said:**
> ```

cd /lib/firmware

```
then 
```

sudo -s 

```
then 
```

tar -xzf b43-all-fw.tar_.gz

``` then 
```

exit

```
tell us what happens

Did all that and then a sudo reboot and nothing changed!

---

### Post by josephmills on 2011-04-25
could I see a ```
dmesg | grep b43 
``` thanks

---

### Post by TRaptor on 2011-04-25
> **josephmills said:**
> could I see a ```
dmesg | grep b43 
``` thanks

Here it is:
```
[    1.112609] b43-pci-bridge 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.112627] b43-pci-bridge 0000:0e:00.0: setting latency timer to 64
[   10.651387] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   10.822626] Registered led device: b43-phy0::tx
[   10.822644] Registered led device: b43-phy0::rx
[   10.822660] Registered led device: b43-phy0::radio


```

---

### Post by Dittie on 2011-04-25
Having the same exact problem. You'd think that something would get worked out between these Broadcom wireless cards and ubuntu by now ;) Every time I upgrade to a new ubuntu, I have to go through and re-fix differently.

---

### Post by josephmills on 2011-04-25
could we please see another ```
rfkill list 
```

---

### Post by TRaptor on 2011-04-25
> **josephmills said:**
> could we please see another ```
rfkill list 
```

Its the same still:
```
0: dell-wifi: Wireless LAN
           Soft blocked: no
           Hard blocked: yes
1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no
```

---

### Post by josephmills on 2011-04-25
> **TRaptor said:**
> Its the same still:
```
0: dell-wifi: Wireless LAN
           Soft blocked: no
           Hard blocked: [COLOR="DarkRed"]yes[/COLOR]
1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no
```
  
Hard blocked: [COLOR="DarkRed"]yes[/COLOR]

this is still the problem  turn the switch off for the wifi and do a ```
rfkill unblock all
```
```
rfkill unblock wlan
```
```
rfkill unblock wifi 
```
anything? 
if not try it with the switch on again. some times you have to hold down the button  what kind of computer is this ?

---

### Post by TRaptor on 2011-04-25
> **josephmills said:**
> Hard blocked: [COLOR="DarkRed"]yes[/COLOR]]

this is still the problem  turn the switch off for the wifi and do a ```
rfkill unblock all
```
```
rfkill unblock wlan
```
```
rfkill unblock wifi 
```
anything? 
if not try it with the switch on again. some times you have to hold down the button  what kind of computer is this ?

Its a Dell Vostro 1520. And its a switch not a button. Ran those code with the switch off and then with it on and then rebooted and its still the same.

---

### Post by bkratz on 2011-04-25
> **TRaptor said:**
> Its the same still:
```
0: dell-wifi: Wireless LAN
           Soft blocked: no
           Hard blocked: yes
1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no
```



You might want to look at this bug report and consider the  removal of the module named "dell-laptop" and see if this fixes your problem.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701259)

---

### Post by TRaptor on 2011-04-25
> **bkratz said:**
> You might want to look at this bug report and consider the  removal of the module named "dell-laptop" and see if this fixes your problem.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/701259)

I deleted the dell-laptop.ko file. But it didn't change anything, except for now when I click the network icon in the menu bar it has a "Connect to Hidden Wireless Network" item.

---

### Post by bkratz on 2011-04-25
> **TRaptor said:**
> I deleted the dell-laptop.ko file. But it didn't change anything, except for now when I click the network icon in the menu bar it has a "Connect to Hidden Wireless Network" item.



When you look at rfkill list does it still show as hard blocked?

---

### Post by matt_symes on 2011-04-25
Hi

Try this. 

```
sudo rm /dev/rfkill
sudo shutdown -r now
```

It may work. I seem to remember reading it might not be hardware and i'm sure it was on a dell PC. No guarantees though.

Kind regards

---

### Post by TRaptor on 2011-04-25
> **bkratz said:**
> When you look at rfkill list does it still show as hard blocked?
It doesn't have anymore:
```

0: dell-wifi: Wireless LAN
           Soft blocked: no
           Hard blocked: yes

```

But this is what is showing:
```

1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no

```


> **matt_symes said:**
> Hi

Try this. 

```
sudo rm /dev/rfkill
sudo shutdown -r now
```

It may work. I seem to remember reading it might not be hardware and i'm sure it was on a dell PC. No guarantees though.

Kind regards

Thanks but it doesn't make a difference!

---

### Post by bkratz on 2011-04-25
Well that is good. Do you now see other networks when you left click on the network icon? You might also post the outputs of

sudo iwlist scan

and

iwconfig

---

### Post by josephmills on 2011-04-25
could we also see a ```
lsmod
``` thanks
**edit also have you tried fn+f2?**

---

### Post by TRaptor on 2011-04-25
> **bkratz said:**
> Well that is good. Do you now see other networks when you left click on the network icon? You might also post the outputs of sudo iwlist scan and iwconfig

Here is the output of "sudo iwlist scan":
```

Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 

```

And here is the iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off

```

> **josephmills said:**
> could we also see a ```
lsmod
``` thanks

Here is the lsmod:
```

Removing code as per josephmills suggestion!

```

Thanks!

---

### Post by bkratz on 2011-04-25
Not what I expected to see. Are you sure you typed it correctly?

---

### Post by TRaptor on 2011-04-25
> **bkratz said:**
> Not what I expected to see. Are you sure you typed it correctly?

Yea I typed the "sudo iwlist scan" command wrong. Here is what it is:
```

lo                        Interface doesn't support scanning.

eth0                        Interface doesn't support scanning.

wlan0                        Interface doesn't support scanning  :  Network is down

```

EDIT: There it is!

---

### Post by bkratz on 2011-04-25
> **TRaptor said:**
> Yea I typed the "sudo iwlist scan" command wrong. Here is what it is:
```

lo                        Interface doesn't support scanning.

eth0                        Interface doesn't support scanning.

wlan0                        Interface doesn't support scanning  :  Network is down

```

EDIT: There it is!

It may not fix anything but you might try

```
sudo iwconfig wlan0 txpower 15
```

If you get an error, try a smaller number like 12 or 10.

And you did have your wired connection disconnected--right?

---

### Post by TRaptor on 2011-04-25
> **bkratz said:**
> It may not fix anything but you might try

```
sudo iwconfig wlan0 txpower 15
```

If you get an error, try a smaller number like 12 or 10.

And you did have your wired connection disconnected--right?

No error. But it didn't change!


Never connected it to via wired connection. I am using my mac to type this out.

---

### Post by josephmills on 2011-04-25
> **TRaptor said:**
> No error. But it didn't change!


Never connected it to via wired connection. I am using my mac to type this out.

how did you download the driver or did you bring it over via mac?

---

### Post by josephmills on 2011-04-25
please take out your ipaddress but could we see a ```
sudo lshw -C networks 
``` it takes a while to load
**have you tried fn+f2?**

---

### Post by TRaptor on 2011-04-26
> **josephmills said:**
> please take out your ipaddress but could we see a ```
sudo lshw -C networks 
``` it takes a while to load
**have you tried fn+f2?**

Where is my ip address in the code I posted? 

And that ```
sudo lshw -C networks 
``` didn't give me anything it just returned me to the command line. No errors but nothing happened.


> **josephmills said:**
> how did you download the driver or did you bring it over via mac?

Downloaded it on the mac and transfered it over via jump drive!

---

### Post by bkratz on 2011-04-26
> **TRaptor said:**
> Where is my ip address in the code I posted? 

And that ```
sudo lshw -C networks 
``` didn't give me anything it just returned me to the command line. No errors but nothing happened.




Downloaded it on the mac and transfered it over via jump drive!



I believe what he/she really wanted was

sudo lshw -C network 

with no s on network

---

### Post by TRaptor on 2011-04-26
> **josephmills said:**
> how did you download the driver or did you bring it over via mac?

> **bkratz said:**
> I believe what he/she really wanted was

sudo lshw -C network 

with no s on network

Here it is:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:32 ioport:4000(size=256) memory:fe004000-fe004fff(prefetchable) memory:fe000000-fe003fff(prefetchable) memory:fe020000-fe03ffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f6000000-f6003fff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


```

---

### Post by chili555 on 2011-04-26
@josephmills - Please see private message. You can probably get his Broadcom going, too.

---

### Post by josephmills on 2011-04-26
> **chili555 said:**
> @josephmills - Please see private message. You can probably get his Broadcom going, too.

thank you chill555 you are a rock star!  this is the message that some of the pm that I got 

@ traptor  lets see a ```
lsmod | grep dell
```

---

### Post by TRaptor on 2011-04-26
> **josephmills said:**
> thank you chill555 you are a rock star!  this is the message that some of the pm that I got 

@ traptor  lets see a ```
lsmod | grep dell
```

Here you go:
```

dell_wmi                             1793   0

```

---

### Post by josephmills on 2011-04-26
> **TRaptor said:**
> Here you go:
```

dell_wmi                             1793   0

```

hmm.. try this ```
sudo rmmod -f dell-laptop
```
then a ```
rfkill list 
``` let us know what happens

---

### Post by chili555 on 2011-04-26
He doesn't have dell-laptop; let's try instead:```
sudo rmmod -f dell-wmi
sudo rfkill unblock all
rfkill list
```

---

### Post by josephmills on 2011-04-26
I would do exactly what chili555 say's that is one smart person right there. thanks again chili555 aka Jedi

---

### Post by TRaptor on 2011-04-28
> **chili555 said:**
> He doesn't have dell-laptop; let's try instead:```
sudo rmmod -f dell-wmi
sudo rfkill unblock all
rfkill list
```

Here is what I get:
```

1: phy0: Wireless LAN
            Soft blocked: no
            Hard blocked: no

```

---

### Post by chili555 on 2011-04-28
We got rid of 'hard blocked=yes' as in post #21. Now does your wireless work?```
sudo iwlist wlan0 scan
```Can you see networks when you click the Network Manager icon? Can you connect?

---

### Post by TRaptor on 2011-04-28
> **chili555 said:**
> We got rid of 'hard blocked=yes' as in post #21. Now does your wireless work?```
sudo iwlist wlan0 scan
```Can you see networks when you click the Network Manager icon? Can you connect?

No, I can't connect! I can't even see any networks, all it says under the "Wireless Networks" section is disconnected. 

The result of that code is:
```

wlan0      Interface doesn't support scanning  :  Network is down

```

---

### Post by chili555 on 2011-04-28
I wonder if there are any interesting messages:```
dmesg | grep wlan
```

---

### Post by TRaptor on 2011-04-28
> **chili555 said:**
> I wonder if there are any interesting messages:```
dmesg | grep wlan
```

That gives nothing!

---

### Post by TRaptor on 2011-04-29
> **traptor said:**
> that gives nothing!

bump!

---

### Post by chili555 on 2011-04-30
It seems that you have two wireless devices; a Broadcom built-in and another, USB perhaps. For now, I am going to concentrate on the Broadcom. If the second one is a USB, please unplug it and set it aside.

I think the firmware has gone to the wrong place. It's supposed to be in /lib/firmware/**b43**. Let's check:```
ls /lib/firmware | grep ucode
ls /lib/firmware/b43
```Thanks.

---

### Post by TRaptor on 2011-05-02
> **chili555 said:**
> It seems that you have two wireless devices; a Broadcom built-in and another, USB perhaps. For now, I am going to concentrate on the Broadcom. If the second one is a USB, please unplug it and set it aside.

I think the firmware has gone to the wrong place. It's supposed to be in /lib/firmware/**b43**. Let's check:```
ls /lib/firmware | grep ucode
ls /lib/firmware/b43
```Thanks.

Here you go:
```

$ ls /lib/firmware | grep ucode
iwlwifi-1000-3.ucode
iwlwifi-3945-2.ucode
iwlwifi-4965-2.ucode
iwlwifi-5000-1.ucode
iwlwifi-5000-2.ucode
iwlwifi-5150-2.ucode
iwlwifi-6000-4.ucode
$ ls /lib/firmware/b43
a0g0bsinitvals4.fw   a0g1initvals13.fw    b0g0initvals4.fw    ucode11.fw
a0g0bsinitvals5.fw   a0g1initvals5.fw     b0g0initvals5.fw    ucode13.fw
a0g0initvals4.fw     b0g0bsinitvals13.fw  lp0bsinitvals13.fw  ucode4.fw
a0g0initvals5.fw     b0g0bsinitvals4.fw   lp0initvals13.fw    ucode5.fw
a0g1bsinitvals13.fw  b0g0bsinitvals5.fw   pcm4.fw
a0g1bsinitvals5.fw   b0g0initvals13.fw    pcm5.fw

```

Thanks!

---

### Post by chili555 on 2011-05-02
So far, so good. Let's see why the Broadcom won't start up:```
dmesg | grep b43
ls -al /lib/firmware/b43
```Thanks.

---

### Post by TRaptor on 2011-05-02
> **chili555 said:**
> So far, so good. Let's see why the Broadcom won't start up:```
dmesg | grep b43
ls -al /lib/firmware/b43
```Thanks.

Here you go:
```

$ dmesg | grep b43
[    1.113423] b43-pci-bridge 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.113441] b43-pci-bridge 0000:0e:00.0: setting latency timer to 64
[   10.585244] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   10.771292] Registered led device: b43-phy0::tx
[   10.771308] Registered led device: b43-phy0::rx
[   10.771326] Registered led device: b43-phy0::radio
[   10.833316] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   11.023240] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   11.026091] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   11.026230] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   11.026365] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   12.252525] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[   12.269254] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[   12.272887] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[   12.273076] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[   12.273252] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2986.553096] b43-pci-bridge 0000:0e:00.0: PCI INT A disabled
[ 2996.376185] b43-pci-bridge 0000:0e:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[ 2997.024219] b43-pci-bridge 0000:0e:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[ 2997.604469] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[ 2997.607066] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[ 2997.610609] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 2997.610616] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 2997.610621] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[ 2997.633283] b43 ssb0:0: firmware: requesting b43/ucode15.fw
[ 2997.641168] b43 ssb0:0: firmware: requesting b43-open/ucode15.fw
[ 2997.654943] b43-phy0 ERROR: Firmware file "b43/ucode15.fw" not found
[ 2997.654947] b43-phy0 ERROR: Firmware file "b43-open/ucode15.fw" not found
[ 2997.654950] b43-phy0 ERROR: You must go to http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware and download the correct firmware for this driver version. Please carefully read all instructions on this website.
$ ls -al /lib/firmware/b43
total 176
drwxr-xr-x  2 joe  joe   4096 2008-04-19 07:36 .
drwxr-xr-x 50 root root  4096 2011-04-25 15:22 ..
-rw-r--r--  1 joe  joe     18 2008-04-18 14:27 a0g0bsinitvals4.fw
-rw-r--r--  1 joe  joe    158 2008-04-18 14:27 a0g0bsinitvals5.fw
-rw-r--r--  1 joe  joe   2680 2008-04-18 14:27 a0g0initvals4.fw
-rw-r--r--  1 joe  joe   1858 2008-04-18 14:27 a0g0initvals5.fw
-rw-r--r--  1 joe  joe    158 2008-04-18 14:27 a0g1bsinitvals13.fw
-rw-r--r--  1 joe  joe    158 2008-04-18 14:27 a0g1bsinitvals5.fw
-rw-r--r--  1 joe  joe   2056 2008-04-18 14:27 a0g1initvals13.fw
-rw-r--r--  1 joe  joe   1858 2008-04-18 14:27 a0g1initvals5.fw
-rw-r--r--  1 joe  joe    158 2008-04-18 14:27 b0g0bsinitvals13.fw
-rw-r--r--  1 joe  joe     18 2008-04-18 14:27 b0g0bsinitvals4.fw
-rw-r--r--  1 joe  joe    158 2008-04-18 14:27 b0g0bsinitvals5.fw
-rw-r--r--  1 joe  joe   2056 2008-04-18 14:27 b0g0initvals13.fw
-rw-r--r--  1 joe  joe   2680 2008-04-18 14:27 b0g0initvals4.fw
-rw-r--r--  1 joe  joe   1858 2008-04-18 14:27 b0g0initvals5.fw
-rw-r--r--  1 joe  joe    158 2008-04-18 14:27 lp0bsinitvals13.fw
-rw-r--r--  1 joe  joe   2052 2008-04-18 14:27 lp0initvals13.fw
-rw-r--r--  1 joe  joe   1320 2008-04-18 14:27 pcm4.fw
-rw-r--r--  1 joe  joe   1320 2008-04-18 14:27 pcm5.fw
-rw-r--r--  1 joe  joe  26600 2008-04-18 14:27 ucode11.fw
-rw-r--r--  1 joe  joe  24424 2008-04-18 14:27 ucode13.fw
-rw-r--r--  1 joe  joe  20080 2008-04-18 14:27 ucode4.fw
-rw-r--r--  1 joe  joe  22088 2008-04-18 14:27 ucode5.fw


```

Thanks!

---

### Post by chili555 on 2011-05-02
It looks like you have a wired ethernet connection; if so, please do:```
sudo apt-get install firmware-b43-installer
```I believe that will download and install the firmware you're missing.

---

### Post by TRaptor on 2011-05-03
> **chili555 said:**
> It looks like you have a wired ethernet connection; if so, please do:```
sudo apt-get install firmware-b43-installer
```I believe that will download and install the firmware you're missing.

No, I don't have a wired connection, can I download it on a separate computer and then transfer and install?

---

### Post by chili555 on 2011-05-03
It doesn't actually contain the firmware; it goes on the internet to get it and installs it in the right place.

Do you have b43-fwcutter on your system? We might be able to grab this:  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Then do:```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

---

### Post by TRaptor on 2011-05-04
> **chili555 said:**
> It doesn't actually contain the firmware; it goes on the internet to get it and installs it in the right place.

Do you have b43-fwcutter on your system? We might be able to grab this:  [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Then do:```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
tar xjf broadcom-wl-4.150.10.5.tar.bz2
cd broadcom-wl-4.150.10.5/driver
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

I get to:
```
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```

and it says "Cannot open input file wl_apsta_mino.o".

---

### Post by chili555 on 2011-05-04
Are you in the correct directory? When you do:```
ls
```You should see:> config         wl_ap_mimo.o  wl_apsta_micro.o  wl_apsta.o      wl_sta_mimo.o
wl_ap_micro.o  wl_ap.o       wl_apsta_mimo.o   wl_sta_micro.o  wl_sta.o
Maybe it's a matter of permissions. In the Broadcom directory, please do:```
sudo chmod 777 *
```Then try again.

---

### Post by TRaptor on 2011-05-04
> **chili555 said:**
> Are you in the correct directory? When you do:```
ls
```You should see:Maybe it's a matter of permissions. In the Broadcom directory, please do:```
sudo chmod 777 *
```Then try again.

I am in the right directory and I ran that sudo chmod 777 * and it didn't make a difference.

---

### Post by chili555 on 2011-05-04
Please open a terminal and do:```
cd broadcom-wl-4.150.10.5/driver
ls -al
```Do you see this?```

total 7808
drwxr-xr-x 3 chili chili    4096 2008-01-06 12:57 .
drwxr-xr-x 5 chili chili    4096 2008-01-06 12:57 ..
drwxrwxrwx 2 chili chili    4096 2008-01-06 12:57 config
-rwxrwxrwx 1 chili chili  712544 2008-01-06 12:57 wl_ap_micro.o
-rwxrwxrwx 1 chili chili 1056404 2008-01-06 12:57 wl_ap_mimo.o
-rwxrwxrwx 1 chili chili  748865 2008-01-06 12:57 wl_ap.o
-rwxrwxrwx 1 chili chili  841958 2008-01-06 12:57 wl_apsta_micro.o
-rwxrwxrwx 1 chili chili 1194265 2008-01-06 12:57 [COLOR="Red"]**wl_apsta_mimo.o**[/COLOR]
-rwxrwxrwx 1 chili chili  879467 2008-01-06 12:57 wl_apsta.o
-rwxrwxrwx 1 chili chili  725112 2008-01-06 12:57 wl_sta_micro.o
-rwxrwxrwx 1 chili chili 1048199 2008-01-06 12:57 wl_sta_mimo.o
-rwxrwxrwx 1 chili chili  764987 2008-01-06 12:57 wl_sta.o

```If so, please do:```
export FIRMWARE_INSTALL_DIR="/lib/firmware"
sudo b43-fwcutter -w "$FIRMWARE_INSTALL_DIR" wl_apsta_mimo.o
```Please tell me what happens.

---

