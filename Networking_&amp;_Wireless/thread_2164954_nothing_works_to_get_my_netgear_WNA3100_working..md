---
title: "nothing works to get my netgear WNA3100 working."
date: 2013-08-02
forum: Networking &amp; Wireless
---

### Post by micheal2 on 2013-08-02
hello guys/gals my system is ubuntu 12.04 X64 and my wireless device is the netgear WNA3100 bcm43231 i have tried everything i can find on getting this to work and i just can not get anything to work coorectly, so what should i do first ?

---

### Post by Bucky Ball on 2013-08-02
Welcome to the forums. What have you done already? Is this a USB device? What happens when you plug it in? With the dongle plugged in (or even if it's an internal wireless card) please do the following:

1/ Look in 'Additional Drivers'. Is there anything in there related to b43 or STA?
2/ Right click on the network icon. Is 'Enable Networking' and 'Enable Wireless' ticked?
3/ Run the following two commands, one at a time, in a terminal and post the output back here, please (Accessories>Terminal):

```
sudo lshw -C network
iwconfig
```

I know this sounds odd, but are you sure it wasn't working when you plugged it in? Did anything happen? Not the same as Win or Mac; many drivers for wireless cards and other things are already included in the Ubuntu kernel and therefore don't need to be installed (and installing unecessary ones can be problematic so hold your fire until we find out what's already in there from the commands above).

With the dongle in, what happens when you left click on the network icon? Does it show any nearby networks for you to connect to? If so, what happens when you try to connect to yours? ;)

Failing all this, you might like to peruse:

[https://duckduckgo.com/?q=bcm43231+ubuntu+12.04&kl=au-en](https://duckduckgo.com/?q=bcm43231+ubuntu+12.04&kl=au-en)

A quick scan shows that chipset has been problematic in the past. I have no idea whether it is in the present. :-k

---

### Post by micheal2 on 2013-08-02
i have treid every type of install with ndiswrapper i have found and they just do not work, the WNA3100 is a usb card, i do not have additional drivers at all in my system settings surprisingly :( dont know what thats about. i know a bit about linux in general im definatly not new to it :) but this is just driving me nuts! lol


```
micheal@micheal-desktop:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c22d Logitech, Inc. G510 Gaming Keyboard
Bus 003 Device 003: ID 046d:c06b Logitech, Inc. G700 Wireless Gaming Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 004: ID 03f0:7211 Hewlett-Packard 

```

```
micheal@micheal-desktop:~$ sudo lshw -C network
[sudo] password for micheal: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 00:25:22:e7:db:7b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.1.155 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:45 ioport:d000(size=256) memory:dc104000-dc104fff memory:dc100000-dc103fff


```

```
micheal@micheal-desktop:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.


```

---

### Post by silconsystem on 2013-08-02
Hi Micheal,

I'm currently experiencing the same issues with a laptop I just got. This is a caused by a bug thats making problems with the broadcom drivers.
here's a similar thread; [http://ubuntuforums.org/showthread.php?t=1967515](http://ubuntuforums.org/showthread.php?t=1967515)
and I've found more about this particular problem on google. seems that the drivers are 'blacklisted' by ubuntu somehow.
Now I have to go offline but tommorrow I want to look into getting the wlan fixed for my laptop, if you still have no solution I'll keep u posted and if u found a fix I'd love to know :)

Good luck, hope this little info will help you a bit.


Rob

---

### Post by chili555 on 2013-08-02
> **micheal2 said:**
> i have treid every type of install with ndiswrapper i have found and they just do not work, 

Bus 002 Device 003: ID **0846:9020** NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]

 What interesting messages do you find here?```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Thanks.

---

### Post by micheal2 on 2013-08-02
when i run 
```
sudo modprobe ndiswrapper
```

 the terminal just sits there forever and does nothing 

```
micheal@micheal-desktop:~$ dmesg | grep ndis
[ 8569.535599] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[ 8761.177605]  [<ffffffffa04c8d79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 8761.177628]  [<ffffffffa04d84eb>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 8761.177656]  [<ffffffffa04d9013>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 8761.177725]  [<ffffffffa04ca282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 8761.177737]  [<ffffffffa04820a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 8881.178437]  [<ffffffffa04c8d79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 8881.178461]  [<ffffffffa04d84eb>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 8881.178489]  [<ffffffffa04d9013>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 8881.178558]  [<ffffffffa04ca282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 8881.178569]  [<ffffffffa04820a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 9001.179251]  [<ffffffffa04c8d79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 9001.179275]  [<ffffffffa04d84eb>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 9001.179303]  [<ffffffffa04d9013>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 9001.179372]  [<ffffffffa04ca282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 9001.179383]  [<ffffffffa04820a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 9121.180076]  [<ffffffffa04c8d79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 9121.180099]  [<ffffffffa04d84eb>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 9121.180127]  [<ffffffffa04d9013>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 9121.180196]  [<ffffffffa04ca282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 9121.180208]  [<ffffffffa04820a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 9241.180904]  [<ffffffffa04c8d79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 9241.180927]  [<ffffffffa04d84eb>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 9241.180955]  [<ffffffffa04d9013>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 9241.181024]  [<ffffffffa04ca282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 9241.181035]  [<ffffffffa04820a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 9361.181732]  [<ffffffffa04c8d79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 9361.181755]  [<ffffffffa04d84eb>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 9361.181783]  [<ffffffffa04d9013>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 9361.181852]  [<ffffffffa04ca282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 9361.181863]  [<ffffffffa04820a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 9481.182558]  [<ffffffffa04c8d79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 9481.182582]  [<ffffffffa04d84eb>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 9481.182610]  [<ffffffffa04d9013>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 9481.182679]  [<ffffffffa04ca282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 9481.182690]  [<ffffffffa04820a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 9601.183380]  [<ffffffffa04c8d79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 9601.183403]  [<ffffffffa04d84eb>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 9601.183431]  [<ffffffffa04d9013>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 9601.183500]  [<ffffffffa04ca282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 9601.183512]  [<ffffffffa04820a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 9721.184205]  [<ffffffffa04c8d79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 9721.184228]  [<ffffffffa04d84eb>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 9721.184256]  [<ffffffffa04d9013>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 9721.184326]  [<ffffffffa04ca282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 9721.184337]  [<ffffffffa04820a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
[ 9841.185034]  [<ffffffffa04c8d79>] load_wrap_driver+0x119/0x1d0 [ndiswrapper]
[ 9841.185057]  [<ffffffffa04d84eb>] wrap_pnp_start_device+0x3b/0x2c0 [ndiswrapper]
[ 9841.185084]  [<ffffffffa04d9013>] wrap_pnp_start_usb_device+0xf3/0x130 [ndiswrapper]
[ 9841.185153]  [<ffffffffa04ca282>] loader_init+0xc2/0x150 [ndiswrapper]
[ 9841.185164]  [<ffffffffa04820a0>] wrapper_init+0xa0/0x1000 [ndiswrapper]
```

---

### Post by chili555 on 2013-08-02
That's an unhappy system right there. Let's dig a bit deeper:```
ndiswrapper -l
lsb_release -a
```Where did you get your .inf and .sys files? From one of my postings here on the forum?

---

### Post by micheal2 on 2013-08-02
yea and its a fresh install of 12.10 aside from following your guide and about 4 or so others which all pretty much say to do the same things.

```
micheal@micheal-desktop:~$ ndiswrapper -l
bcmwlhigh5 : invalid driver!

```


```
micheal@micheal-desktop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal

```

---

### Post by chili555 on 2013-08-02
> bcmwlhigh5 : invalid driver!There you have it. Is your system 32- or 64-bit?```
arch
```I have a few files around here. Once I know your particulars, I'll attach them and we'll try to get it working.

---

### Post by micheal2 on 2013-08-02
its a 64bit  x86_64 i actually have the files from one of your other posts but they didnt work lol

---

### Post by chili555 on 2013-08-02
Please try these. First remove the files you have:```
sudo ndiswrapper -e bcmwlhigh5
```And to be doubly sure:```
sudo rm -rf /etc/ndiswrapper/*
sudo modprobe -r ndiswrapper
```Now install the new files:```
sudo ndiswrapper -i Desktop/Broadcom_bcm43xx_USB_32_64bit_v2/bcmn43xx64.inf
sudo modprobe ndiswrapper
```Any improvement?```
ndiswrapper -l
dmesg | grep ndis
```

---

### Post by micheal2 on 2013-08-02
it just hangs at 
```
sudo modprobe -r ndiswrapper
```

neem sitting here for about 5 min now :(

---

### Post by chili555 on 2013-08-02
> **micheal2 said:**
> it just hangs at 
```
sudo modprobe -r ndiswrapper
```

neem sitting here for about 5 min now :(Please kill the terminal and reboot. Then try again.

---

### Post by micheal2 on 2013-08-03
i said F it and reinstalled 12.04 :P but still wireless is not working out of the box, actually neither did my video but i got that situated already, simple xorg.conf file change up, as of right now everything is a fresh install aside from the nvidia stuff so i should only have to install ndiswrapper and use those files you linked ... right lol 

i am still on a 64b arch aswell

```
micheal@micheal-Ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 045e:00dd Microsoft Corp. Comfort Curve Keyboard 2000 V1.0
Bus 003 Device 003: ID 046d:c06b Logitech, Inc. G700 Wireless Gaming Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 002 Device 004: ID 03f0:7211 Hewlett-Packard 


```

a side note im curiouse if my usb 3 hub is even fuctioning correctly becuase my wifi adapter is plugged in to that hub.


ok so i went through and did all that in the post above and when i run

```
sudo modprobe ndiswrapper
```

i get this
```
FATAL: Module ndiswrapper not found.
```

---

### Post by silconsystem on 2013-08-03
GoodMorning,

I found this post, along with many other issues with the broadcom cbm43xxx drivers
[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers)

If you read the post you'll see that the broadcom drivers have to be disabled in the blacklist. Hope this works for you, cuz I've got the same issue here but I dont have a wired connection here and have to take the laptop to a friend later to try it myself.

Shame that this doesnt work out of the box, in my case its a built-in card of a Dell laptop and Dell & Linux mostly play nice together.


Greetz,


Rob

---

### Post by chili555 on 2013-08-03
> **silconsystem said:**
> GoodMorning,

I found this post, along with many other issues with the broadcom cbm43xxx drivers
[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers)

If you read the post you'll see that the broadcom drivers have to be disabled in the blacklist. Hope this works for you, cuz I've got the same issue here but I dont have a wired connection here and have to take the laptop to a friend later to try it myself.

Shame that this doesnt work out of the box, in my case its a built-in card of a Dell laptop and Dell & Linux mostly play nice together.


Greetz,


RobI am unaware of any Broadcom built-in card that needs ndiswrapper. This poster's card is a pretty rare USB Broadcom device. There is no native driver to blacklist!

---

### Post by chili555 on 2013-08-03
> **micheal2 said:**
> 
ok so i went through and did all that in the post above and when i run

```
sudo modprobe ndiswrapper
```

i get this
```
FATAL: Module ndiswrapper not found.
```Did you install ndiswrapper?```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9 ndiswrapper-dkms
```

---

### Post by Bucky Ball on 2013-08-03
@ siliconsystem: If you have *_exactly_* the same issue as the original poster (which you don't as you have an *internal* card and have stated only that it's Broadcom), and a fresh install of 12.04 with identical output, etc., please follow chilli's instructions.

You will have more luck if you post a new thread regarding your issue using a descriptive title and outlining what you've done so far and what the machine is doing. If you're not using the WNA3100 this thread title doesn't relate to your issue. ;)

By all means, follow this thread and add anything helpful or get tips, but, for many reasons, it gets confusing trying to fix different issues on one thread. There's room for another, more specific to your issue (with your details).

---

### Post by silconsystem on 2013-08-03
Hi There,

I just stumbled onto this post and noticed maybe the device is different but it still needs the broadcom bcm43xxx driver wich many people seem to have issues with.
NetGear, Inc. WNA3100(v1) Wireless-N 300 [**_Broadcom BCM43231_**]
I still havent had the time to figure out exactly whats wong with my install, but a little experimentation got ubuntu at least to recognize the driver so I could activate it but since it still wanted to download something and I had just crappy connection I decided to take my laptop towards a proper eth0 connection first.

Anywayz, thanks for your advice guys !!


I hope a solution is not too far away !

---

### Post by micheal2 on 2013-08-03
ok enough thread jacking :) 


@chilli
i have installed all of those, but i think there is something wrong with the DKMS from ubuntu everytime i install it i start getting msg's from ubuntu saying something is wrong and to send an error report.

---

### Post by chili555 on 2013-08-03
> **micheal2 said:**
> ok enough thread jacking :) 


@chilli
i have installed all of those, but i think there is something wrong with the DKMS from ubuntu everytime i install it i start getting msg's from ubuntu saying something is wrong and to send an error report.Please try:```
sudo apt-get remove ndiswrapper-dkms
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```I hope we don't have to get out the big tools!

---

### Post by micheal2 on 2013-08-03
```
micheal@micheal-Ubuntu:~$ sudo apt-get remove ndiswrapper-dkms 
[sudo] password for micheal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ndiswrapper-dkms
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 778 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 195559 files and directories currently installed.)
Removing ndiswrapper-dkms ...

------------------------------
Deleting module version: 1.57
completely from the DKMS tree.
------------------------------
Done.
micheal@micheal-Ubuntu:~$ sudo modprobe -r ndiswrapper
FATAL: Module ndiswrapper not found.
micheal@micheal-Ubuntu:~$ sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.


```

im starting to thinik we are going to lol, i dont understand why if so many ppl have this card someone has to be able to create a native linux driver for the damn thing lol or atleast a one stop shop application that determines - installes- removes- just generally fixes the system for use with ndis wrapper automattically

---

### Post by micheal2 on 2013-08-03
so i was playing around and check this out

```
micheal@micheal-Ubuntu:~$ ndiswrapper -v
ERROR: modinfo: could not find module ndiswrapper
module version is too old!
utils version: '1.9', utils version needed by module: '0'
module details:
ERROR: modinfo: could not find module ndiswrapper

You may need to upgrade driver and/or utils to latest versions available at
http://ndiswrapper.sourceforge.net


```

---

### Post by micheal2 on 2013-08-03
ok so i think i got it fixed, here is waht i did

First uninstall the ndiswrapper you have using synaptic and mark for complete removal
then 
```
download this http://sourceforge.net/projects/ndiswrapper/files/latest/download
```

cd into that dir and run
```
make
sudo make install
```

then load up your .inf file and you should have a working list of wireless ap's to join  :P

now lets see if it conect and stays connected, not connecting i have a WPA_Personal security so perhaps i need to do more i remmber using wpa_supplicant before on ubuntu but not sure if its needed still


ok i got it to connect, it takes quite a while to connect but its staying connected so far, also on reboot i have to run
```
sudo modprobe ndiswrapper
```

thanks so much chilli :)

---

### Post by chili555 on 2013-08-03
> **micheal2 said:**
> 
ok i got it to connect, it takes quite a while to connect but its staying connected so far, also on reboot i have to run
```
sudo modprobe ndiswrapper
```

thanks so much chilli :)Awesome! Let's fix the loading problem:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```You should be all set.

---

### Post by micheal2 on 2013-08-03
i knew it had been to good to be true lol, so i rebooted again and now it wont connect :(

---

### Post by chili555 on 2013-08-03
Please round up the usual suspects:```
lsmod | grep ndis
ndiswrapper -l
dmesg | grep ndis
```Thanks.

---

### Post by micheal2 on 2013-08-03
```
 micheal@micheal-Ubuntu:~$ lsmod | grep ndisndiswrapper           283370  0 
```

i actually had to unplug and re plugin the stick for it to show up as present.
```
micheal@micheal-Ubuntu:~$ ndiswrapper -l
bcmn43xx64 : driver installed
	device (0846:9020) present

```

```
micheal@micheal-Ubuntu:~$ dmesg | grep ndis
[    8.375126] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[    9.811899] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[   10.068016] usbcore: registered new interface driver ndiswrapper
[  457.943372] usbcore: deregistering interface driver ndiswrapper
[  457.959067] ndiswrapper: device wlan0 removed
[  469.343031] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  469.515152] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  469.776445] usbcore: registered new interface driver ndiswrapper
[  642.552158] ndiswrapper: device wlan0 removed
[  643.020254] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  648.696238] ndiswrapper: device wlan0 removed
[  649.260339] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[  652.796214] ndiswrapper: device wlan0 removed
[  827.071938] usbcore: deregistering interface driver ndiswrapper
[  834.509404] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  834.514406] usbcore: registered new interface driver ndiswrapper
[  860.854589] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded



```

---

### Post by chili555 on 2013-08-04
I'd like to better understand what is going wrong here. Please shut down your computer completely, not reboot. Make sure the Netgear is inserted. Start the computer and log in. Is the wireless working? Please run:```
dmesg > micheal2.txt
lsmod >> micheal2.txt
```If not, remove and re-insert the Netgear. Now is it working? Run:```
dmesg >> micheal2.txt
lsmod >> micheal2.txt
zip micheal2.zip micheal2.txt  
```Find the file micheal2.zip in your user directory and attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by micheal2 on 2013-08-05
srry been busy, ill once i finish installing this game ill do all that and upload it.

shutdown, rebooted, and the wireless works it just does not connect and not for a lack of trying, but it keeps trying and every now and then it connects for a sec and then disconnects then keeps trying 

[ATTACH]245109[/ATTACH]

---

### Post by micheal2 on 2013-08-05
so oddly enough my ubuntu locked up (i think it was flash) so i rebooted and my wireless connected right off the bat, so i ran lsmod and dmesg to micheal2-connected.txt for you then after i did that the wireless disconnected
[ATTACH]245110[/ATTACH]

---

### Post by bazsound on 2013-11-08
Thanks to this thread i got my Netgear wna-3100 to work with just a few commands. I havnt rebooted yet so it may go pear shaped. This thread hasnt been updated in a while so i may come back with some comments.

I just installed 12.04 Lubuntu alternate for an old machine to be used as a media centre.

Instlaling ndiswrapper from sourceforge, then using the driver provided in this thread, and running the recent commands it worked straight away.

It did take a while to connect, but currently isntalling updates on this other machine at pretty much same speeds as my machine directly connected to my tethered connection.

Thanks :-)

---

### Post by bazsound on 2013-11-08
well after a reboot, wireless no longer connects to my hotspot just like what happens with others, why does this work when first installing and works great untilll,,, reboot.

is there no solution to this yet.


Ok i might have gotten somewhere but i havnt rebooted yet, i tried rmmod ndiswrapper and modprobe ndiswrapper, even unpluiging and pluging back in but it would still just sit tryhing to connect.

So went for the uninstall of the driver, but, ndiswrapper complained that the file didnt exist in /etc/ndiswrapper/ so i copied the file to that location and now it connects in a second.

I just have to reboot to see if it works again

nope didnt solve it, after reboot fails to connect.

---

### Post by vanquishedangel on 2013-11-11
I have this card to, and mine is working sort of, here is my system:

Ubuntu 13.10 64bit
AMD Athalon x2 3.0 ghz
8 gig ram

I have 2 wireless cards (for comparison)

1) Belkin n150 model f9l1001v1 (uses kernel drivers, linux drivers)

2) Netgear n300 model wna3100 (uses ndiswrapper)

Now the belkin n150 always stays connected and can download very fast (2mb+ per second) However when I game with it my ping sucks and and Heroes of Newerth shows the disconnect symbol evey second, and it lags.

With the netgear however, if i try to download or play flash it starts out really fast but then all the sudden stops after about one or two seconds. I get no disconnect notice and the icon displays that the internet is still connected, however firefox, the software updater, or anyother program cannot access the internet. I cannot access the internet at all after that and either have to reboot or unplug the card and plug it back in. However when I game with this card ping is good and it remains steady, never diconnects on heros of newerth. I have also employed wondershaper to limit internet speed on this card and it has helped some with the disconnects, but not enough at all. I have also changed the txpower to 15, but again it has helped some, but it is such a minor amount that the card is still very dysfunctional for watching videos, downloading, or even just websurfing.

**_To install the drivers:_**

I used ndiswrapper from the repos, I have ndiswrapper-common, ndiswrapper-dkms, ndiswrapper-utils-1.9, ndisgtk (front end for ndiswrapper). I installed the driver in wine from the disk, then I opened ndisgtk and then installed the driver from the wine directory. the wine directory is:

Drive c--->Program Files (x86)--->NETGEAR--->WNA3100--->Driver--->WINXP64--->bcmwlhigh5.inf

Now this installs the windows xp 64bit driver (if wine is 64 bit, and set to windows xp), but baffels me as to why it installs in the "Program Files (x86)" folder in windows. I tried the files linked in may forums but none of them worked, only the one off the disk did, but it is in an .exe and so wine is required to get the driver. The windows 7, windows vista drivers will not work for me.

**_The usual suspects:_**

shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ lsmod | grep ndis
ndiswrapper           279457  0 
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ ndiswrapper -l
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/kvm.conf line 1: ignoring bad line starting with 'kvm_amd'
bcmwlhigh5 : driver installed
	device (0846:9020) present
netrtwlanu : driver installed
shawn@shawn-HP-Compaq-dc5750-Small-Form-Factor:~$ dmesg | grep ndis
[   32.300126] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   32.871318] ndiswrapper: driver bcmwlhigh5 (Netgear,03/28/2011, 5.100.68.46) loaded
[   33.290320] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005325000, 16000, 4
[   33.290326] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005328e80, 16000, 5
[   33.290328] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000532cd00, 16000, 5
[   33.290330] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005330b80, 16000, 5
[   33.290332] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005334a00, 16000, 5
[   33.290334] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005338880, 16000, 5
[   33.290336] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000533c700, 16000, 5
[   33.290338] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005340580, 16000, 5
[   33.290341] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005344400, 16000, 5
[   33.290343] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005348280, 16000, 5
[   33.290345] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000534c100, 16000, 4
[   33.290347] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000534ff80, 16000, 5
[   33.290351] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005353e00, 16000, 5
[   33.290354] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005357c80, 16000, 5
[   33.290356] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000535bb00, 16000, 5
[   33.290358] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000535f980, 16000, 5
[   33.290360] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005363800, 16000, 5
[   33.290362] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005367680, 16000, 5
[   33.290364] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000536b500, 16000, 5
[   33.290366] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000536f380, 16000, 5
[   33.290368] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005373200, 16000, 5
[   33.290370] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005377080, 16000, 4
[   33.290372] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000537af00, 16000, 5
[   33.290374] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000537ed80, 16000, 5
[   33.290376] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005382c00, 16000, 5
[   33.290378] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005386a80, 16000, 5
[   33.290380] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000538a900, 16000, 5
[   33.290382] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000538e780, 16000, 5
[   33.290384] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005392600, 16000, 5
[   33.290387] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc90005396480, 16000, 5
[   33.290389] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000539a300, 16000, 5
[   33.290391] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc9000539e180, 16000, 4
[   33.290393] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053a2000, 16000, 4
[   33.290395] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053a5e80, 16000, 5
[   33.290397] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053a9d00, 16000, 5
[   33.290399] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053adb80, 16000, 5
[   33.290401] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053b1a00, 16000, 5
[   33.290403] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053b5880, 16000, 5
[   33.290405] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053b9700, 16000, 5
[   33.290407] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053bd580, 16000, 5
[   33.290409] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053c1400, 16000, 5
[   33.290411] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053c5280, 16000, 5
[   33.290414] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053c9100, 16000, 4
[   33.290416] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053ccf80, 16000, 5
[   33.290418] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053d0e00, 16000, 5
[   33.290420] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053d4c80, 16000, 5
[   33.290423] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053d8b00, 16000, 5
[   33.290425] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053dc980, 16000, 5
[   33.290427] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053e0800, 16000, 5
[   33.290429] ndiswrapper (MmBuildMdlForNonPagedPool:1864): ffffc900053e4680, 16000, 5
[   33.305335] ndiswrapper (ndis_encode_setting:383): unknown type: 3
[   33.603365] usbcore: registered new interface driver ndiswrapper

---

