---
title: "How i got D-Link dwa-140 B2 (3071 chip) to work in lucid 10.04"
date: 2010-07-30
forum: Networking &amp; Wireless
---

### Post by pure_x01 on 2010-07-30
Note!: you might need to run sudo on most places in this tutorial

```

$ lsusb | grep D-L
Bus 002 Device 005: ID 07d1:3c0a D-Link System

```Apparently it is based on 3071 chipset when searching on google

1. Visit [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and download
[RT8070/RT3070USB(RT307x)]("http://www.ralinktech.com/license_us.php?n=2&p=0&t=U0wyRnpjMlYwY3k4eU1ERXdMekEzTHpJNEwyUnZkMjVzYjJGa01EUXdOVEE1TnpBd01TNWllakk5UFQxRVVFOWZVbFF6TURjd1gweHBiblY0VTFSQlgxWXlMak11TUM0MFh6SXdNVEF3TmpBMExuUmhjZz09Qw%3D%3D")

2. Unpack and enter the directory

3. Type [FONT=Courier New]make[/FONT]

4. Copy the file [FONT=Courier New]os/linux/rt3070sta.ko[/FONT] in to the dir [FONT=Courier New]/lib/modules/2.6.32-23-generic/kernel/drivers/net/wireless[/FONT] folder

4.5  also
```
$ cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
```5. type ```
$ depmod -a
```6. type ```
$ modprobe rt3070sta
```7. Blacklist the existing 28xx drivers in /etc/modprobe.d/blacklist.conf by adding the following rows:
```

blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2870sta

```(make sure that they are not loaded by typing lsmod) (possible restart at this point?)

8. insert the usb card (it should be working and you should see it in the network manager in gnome)

9. To get it to load when booting you need to ad an entry in to [FONT=Courier New]/etc/modules[/FONT]
```
rt3070sta
```I also created a file called[FONT=Courier New] /etc/modprobe.d/rt3070sta.conf[/FONT]  and inserted the row:
```
alias ra0 rt3070sta
```Note! : I followed the readme README_STA_usb in the driver directory. It is written for 28xx and redhat but most of it is useful

---

### Post by Guyka13 on 2010-08-27
Hi

It seems I installed driver after repeat your tutorial, but i cant connect to my network.

```
lsusb | grep D-L
Bus 001 Device 004: ID 07d1:3c0a D-Link System
``````
iwconfig ra0
ra0       Ralink STA  ESSID:"11n-AP"  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated
          Bit Rate:1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-41 dBm  Noise level:-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
``````
lsmod | grep ^rt
rt3070sta             640902  1
```

Any solutions?

Thanks

---

### Post by rathodsa on 2010-10-03
There's another way.  Go to D-Link.com and download the linux driver. 

These are the instructions
Driver Install:
    Please use following command 
    > sudo tar xvf 2010_0413_RT3070_Linux_STA_v2.1.3.0.tar.gz
    > cd 2010_0413_RT3070_Linux_STA_v2.1.3.0
    > sudo make
    > sudo make install
    #plugin the DWA-140(USB device) then the driver should be loadup by system.
    # now user may use "networkmanager" to site survey and connect to AP.
    
    Worked flawlessly.  It was remarkably easy.  My 11 year old felt he could do it.

Still works on 10.10 rc.

---

### Post by DJArty on 2011-02-04
On 2.6.35 kernels  need to patch Ralink [linux drivers]("http://www.ralinktech.com/support.php?s=2") RT2870USB(RT2870/RT2770)	07/09/2010 2.4.0.1 for compile without errors.

So, download official driver RT2870USB(RT2870/RT2770)... 
then
```
tar xvf 2010_0709_RT2870_Linux_STA_v2.4.0.1.tar.bz2
cd 2010_0709_RT2870_Linux_STA_v2.4.0.1/
wget -qO- http://www.linuxcrew.de/wp-content/uploads/2010/10/rt2870sta_usb_kernel2635.patch | patch -ul -p0
make
sudo make install

```
  
More info [here]("http://www.linuxcrew.de/2010/10/11/").

---

### Post by DJArty on 2011-02-08
Update...  :)   (previous don't work normally with  H/W Ver.: B2 ID 07d1:3c0a )
Need to download RT8070/RT3070/RT3370 USB   08/31/2010   2.5.0.1
for D-Link DWA-140 H/W Ver.: B2   ID 07d1:3c0a   (looks like D-Link 3072 chip).
Add MODULE_LICENSE("GPL");  into the os/linux/usb_main_dev.c for normal compile. (and maybe sudo mkdir /tftpboot  can help too).
Set up in os/linux/config.mk :
HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```
cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
make
sudo insmod os/linux/rt3070sta.ko
```

Working good with 130M connection speed (real 85/65 speedtest speed).

---

### Post by Burky on 2011-08-24
> **rathodsa said:**
> There's another way.  Go to D-Link.com and download the linux driver. 

These are the instructions
Driver Install:
    Please use following command 
    > sudo tar xvf 2010_0413_RT3070_Linux_STA_v2.1.3.0.tar.gz
    > cd 2010_0413_RT3070_Linux_STA_v2.1.3.0
    > sudo make
    > sudo make install
    #plugin the DWA-140(USB device) then the driver should be loadup by system.
    # now user may use "networkmanager" to site survey and connect to AP.
    
    Worked flawlessly.  It was remarkably easy.  My 11 year old felt he could do it.

Still works on 10.10 rc.

Not sure if I see the place to download any drivers on D-Link :((

---

