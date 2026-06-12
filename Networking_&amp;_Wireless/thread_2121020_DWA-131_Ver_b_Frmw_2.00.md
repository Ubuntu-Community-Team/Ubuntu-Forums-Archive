---
title: "DWA-131 Ver b Frm/w 2.00"
date: 2013-02-28
forum: Networking &amp; Wireless
---

### Post by revelias on 2013-02-28
I've been a general Ubuntu user for about two years now and consider myself to have just enough knowledge to be dangerous. Now long story short, I recently purchased a D-link DWA-131 usb wifi adapter on the promise that it would work right out the box. Turns out that this is both true and false. It seems that D-link revised this model at some point and while the old version does work out the box the new one does not. 
Not to be dissuaded I searched the forums and found numerous post on how to get this device running. Unfortunately none of them was directly on point nor did following their directions help. The best that I have been able to accomplish is getting the network manager to show that wireless signals were available but that the device was not ready or that that the firmware was missing. This of course lasted only until I rebooted my machine.
Can anyone help me with this issue.
I am currently running Ubuntu 12.04.

---

### Post by chili555 on 2013-02-28
Please open a terminal and run and post:```
lsusb
```Thanks.

---

### Post by revelias on 2013-02-28
The result of lsusb is
Bus 001 Device 003: ID 2001:330d D-Link Corp.

fyi. I checked the  USB_IDS file and my version of DWA-131 is not listed but the previous version is.

---

### Post by chili555 on 2013-02-28
```
ID 2001:330d D-Link Corp.
```I can't find *any* way to get this going. We might try ndiswrapper. Did you get a disk of Windows drivers with the device? 

This appears to be a very new device. Let's blaze new trails!

---

### Post by revelias on 2013-02-28
Yes, it came with a disc that has Win XP, Vista, and 7 drivers.

---

### Post by kurt18947 on 2013-03-01
Thanks for posting this.  I've recommended this adapter in the past as 'just works'.  Mine does.   It looks like I should temper this in the future.  I _hate_ it when manufacturers substantially change a device (I'd certain consider changing chipsets/firmware a substantial change) and keeps the model designation.

---

### Post by chili555 on 2013-03-01
A very interesting case. I downloaded the XP drivers, which are what ndiswrapper requires. A glance at the .inf files confirms it is for your device:> ;;****************************************************************************
;; IDs for X86
;;****************************************************************************

[DLink.NTx86]

%DLink.DeviceDesc% = RTL8192cu.ndi, USB\VID_2001&PID_330D
;;****************************************************************************
;; IDs for X64
;;****************************************************************************

[DLink.NTamd64]

%DLink.DeviceDesc% = RTL8192cu.ndi, USB\VID_[COLOR="#FF0000"]2001[/COLOR]&PID_[COLOR="#FF0000"]330D[/COLOR]Also, as you can see, it is an 8192cu device. Unfortunately, the usb.id 2001:330d isn't covered in the latest rtl8192cu driver, nor in compat-wireless. So, it seems, ndiswrapper is the best alternative for now. I am sure it will be covered soon. I have zipped the 32- and 64-bit drivers in a zip file and put it on my personal Dropbox: [https://dl.dropbox.com/u/58267392/xp.zip](https://dl.dropbox.com/u/58267392/xp.zip)

Download the file xp.zip to your desktop. Find out if you need 32- or 64-bit driver files with:```
arch
```Get a temporary wired ethernet connection and do:```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```Right-click the file xp.zip on your desktop and select Extract Here. Now, back to the terminal:```
sudo ndiswrapper -i Desktop/xp/[COLOR="#FF0000"]WinXP[/COLOR]/netrtwlanu.inf   [COLOR="#FF0000"]<--or WinX64 if yours is a 64-bit system[/COLOR]
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```Is it working? Are we there yet??

---

### Post by wadelius on 2013-03-01
I've got this adapter as well, and have been trying to get it to work with my 12.10 installation. I've found that a dlink adapter with the same VID and PID is included in the compat-wireless source (rtl8192cu) for kernel 3.8.

So I upgraded to kernel 3.8 from as instructed on [http://handytutorial.com/install-linux-kernel-3-8-in-ubuntu-12-10-12-04/](http://handytutorial.com/install-linux-kernel-3-8-in-ubuntu-12-10-12-04/) 

After upgrading I ran ```
sudo modprobe rtl8192cu
```. lsmod the gives:
```
jwad@jwad-LENOVO3000-V100:~$ lsmod | grep 8192
rtl8192cu              67488  0 
rtl8192c_common        47737  1 rtl8192cu
rtlwifi                70250  1 rtl8192cu
mac80211              541819  5 rtl8192cu,rtl8192c_common,iwl3945,rtlwifi,iwlegacy
```

So the module shows up together with my old wireless iwl3945.

But when plugging it in and trying iwconfig the only wireless than shows up is the old one.

Any suggestions? Is my assumption that compat-wireless 3.8 is included in standard kernel 3.8 correct?

---

### Post by chili555 on 2013-03-01
The trick, of course, is whether the new kernel's version of rtl8192cu actually covers your device.```
modinfo rtl8192cu | grep 330D
```And you can get the old driver iwl3945 to not load by blacklisting it.```
sudo su
echo "blacklist iwl3945" >> /etc/modprobe.d/blacklist.conf
modprobe -r iwl3945
exit
```What was not working about your Intel? Mine works beautifully in every respect.

---

### Post by revelias on 2013-03-02
> **chili555 said:**
> A very interesting case. I downloaded the XP drivers, which are what ndiswrapper requires. A glance at the .inf files confirms it is for your device:Also, as you can see, it is an 8192cu device. Unfortunately, the usb.id 2001:330d isn't covered in the latest rtl8192cu driver, nor in compat-wireless. So, it seems, ndiswrapper is the best alternative for now. I am sure it will be covered soon. I have zipped the 32- and 64-bit drivers in a zip file and put it on my personal Dropbox: [https://dl.dropbox.com/u/58267392/xp.zip](https://dl.dropbox.com/u/58267392/xp.zip)

Download the file xp.zip to your desktop. Find out if you need 32- or 64-bit driver files with:```
arch
```Get a temporary wired ethernet connection and do:```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```Right-click the file xp.zip on your desktop and select Extract Here. Now, back to the terminal:```
sudo ndiswrapper -i Desktop/xp/[COLOR=#FF0000]WinXP[/COLOR]/netrtwlanu.inf   [COLOR=#FF0000]<--or WinX64 if yours is a 64-bit system[/COLOR]
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```Is it working? Are we there yet??

Everything seemed to go well until I entered the last code ```
 sudo modprobe ndiswrapper
``` then it returned "FATAL: Module ndiswrapper not found."

---

### Post by chili555 on 2013-03-02
> **revelias said:**
> Everything seemed to go well until I entered the last code ```
 sudo modprobe ndiswrapper
``` then it returned "FATAL: Module ndiswrapper not found."Please try:```
sudo apt-get install ndiswrapper-dkms
sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9
sudo modprobe ndiswrapper
```Don't make me get out the big hammer!!

---

### Post by revelias on 2013-03-02
> **chili555 said:**
> Please try:```
sudo apt-get install ndiswrapper-dkms
sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9
sudo modprobe ndiswrapper
```Don't make me get out the big hammer!!

I ran the codes without errors but it did not get the device running.

---

### Post by chili555 on 2013-03-02
Let's see if there are any informative messages:```
ndiswrapper -l
```That's a lower-case L for 'list.'```
dmesg | grep ndis
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

---

### Post by revelias on 2013-03-03
> **chili555 said:**
> Let's see if there are any informative messages:```
ndiswrapper -l
```That's a lower-case L for 'list.'```
dmesg | grep ndis
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

I ran the codes ```
ndiswrapper -l
``` returned "netrtwlanu : driver installed" while ```
dmesg | grep ndis
``` didn't return anything.

---

### Post by chili555 on 2013-03-03
What..?? Was the device inserted at the time? If so, and the .inf file was correct for the device, it ought to have also returned 'device present.' Check:```
lsusb
```Does the device show up as before?> Device 003: ID [COLOR="#FF0000"]2001:330d[/COLOR] D-Link Corp.Now check the .inf file:```
less Desktop/xp/[COLOR="#FF0000"]WinXP[/COLOR]/netrtwlanu.inf   [COLOR="#FF0000"]<--or WinX64 if yours is a 64-bit system[/COLOR]
```Do you see the parts I quoted?> %DLink.DeviceDesc% = RTL8192cu.ndi, USB\VID_2001&PID_330D
;;************************************************ ****************************
;; IDs for X64
;;************************************************ ****************************

[DLink.NTamd64]

%DLink.DeviceDesc% = RTL8192cu.ndi, USB\VID_[COLOR="#FF0000"]2001[/COLOR]&PID_[COLOR="#FF0000"]330D[/COLOR]Get out of 'less' with q.

Perhaps the module needs to be loaded first:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```This case gets more interesting by the moment!

---

### Post by revelias on 2013-03-03
> **chili555 said:**
> What..?? Was the device inserted at the time? If so, and the .inf file was correct for the device, it ought to have also returned 'device present.' Check:```
lsusb
```Does the device show up as before?Now check the .inf file:```
less Desktop/xp/[COLOR=#FF0000]WinXP[/COLOR]/netrtwlanu.inf   [COLOR=#FF0000]<--or WinX64 if yours is a 64-bit system[/COLOR]
```Do you see the parts I quoted?Get out of 'less' with q.

Perhaps the module needs to be loaded first:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```This case gets more interesting by the moment!

OK I re-ran the codes with the device in and got: driver installed device (2001:330D) present for "ndiswrapper -l" and nothing returned for the second code.

---

### Post by chili555 on 2013-03-03
> OK I re-ran the codes *with the device in* Excellent.

Please do:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```Reboot so we have a clean slate. Then run:```
iwconfig > revelias.txt
dmesg  >> revelias.txt
```Find the text file revelias.txt in your user directory and paste it here:  [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Give us the link so we can study the messages and try to see what's going wrong.

---

### Post by revelias on 2013-03-03
> **chili555 said:**
> Excellent.

Please do:```
sudo su
echo ndiswrapper >> /etc/modules
exit
```Reboot so we have a clean slate. Then run:```
iwconfig > revelias.txt
dmesg  >> revelias.txt
```Find the text file revelias.txt in your user directory and paste it here:  [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Give us the link so we can study the messages and try to see what's going wrong.

I ran ```
sudo su
echo ndiswrapper >> /etc/modules
exit
```
and rebooted with the device in which resulted in kernal panic with the gui crashing. I then rebooted without the device and was able to log in but once i plugged the device in it crashed the system.

Here is the link to the output:
[http://paste.ubuntu.com/5582795/](http://paste.ubuntu.com/5582795/)

---

### Post by chili555 on 2013-03-03
Yikes! Any clues here?```
cat /var/log/syslog | grep ndis | tail -n20
```If there are few or no lines of output, look here:```
cat /var/log/syslog[COLOR="#FF0000"].1[/COLOR] | grep ndis | tail -n20
```

---

### Post by revelias on 2013-03-03
That code returned:

Mar  3 11:11:45 daniel-Presario-F700-GR970UA-ABA kernel: [   18.278590] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
Mar  3 11:11:45 daniel-Presario-F700-GR970UA-ABA kernel: [   18.355963] usbcore: registered new interface driver ndiswrapper
Mar  3 11:13:03 daniel-Presario-F700-GR970UA-ABA kernel: [   18.280781] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
Mar  3 11:13:03 daniel-Presario-F700-GR970UA-ABA kernel: [   18.440984] usbcore: registered new interface driver ndiswrapper
Mar  3 11:15:57 daniel-Presario-F700-GR970UA-ABA kernel: [   19.125667] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
Mar  3 11:15:57 daniel-Presario-F700-GR970UA-ABA kernel: [   19.319255] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2013-03-03
As you can see, there is nothing significant here. How about:```
cat /var/log/syslog | grep -i 330d | tail -n20
cat /var/log/syslog | grep -i usb | tail -n20
```If we can't identify and correct the crash, we ought to remove ndiswrapper and try another approach. I am rather unclear, at this point, what other approach is even available!

Is your a 64-bit system?```
uname -a
```

---

### Post by revelias on 2013-03-03
So I did some research and it seems that there was a bug in the kernel that caused the crash with the DWA-131 plugged in once the system begin to recognize it. To fix this I upgraded to the newest kernel version (3.7.4). Unfortunately, this only fixed the crashing issue. The device still is working.

Also to answer your question my processor is 64bit.

---

### Post by chili555 on 2013-03-03
> To fix this I upgraded to the newest kernel version (3.7.4).May we see:```
modinfo rtl8192cu | grep 330D
sudo modprobe ndiswrapper
```Thanks.

---

### Post by revelias on 2013-03-03
> **chili555 said:**
> May we see:```
modinfo rtl8192cu | grep 330D
sudo modprobe ndiswrapper
```Thanks.

```
modinfo rtl8192cu | grep 330D
``` returned nothing and ```
sudo modprobe ndiswrapper
``` returned "FATAL: Module ndiswrapper not found."

---

### Post by chili555 on 2013-03-03
Let's try an old trick since we know ndiswrapper is out of the picture for now:```
sudo modprobe rtl8192cu
echo "2001 330D" | sudo tee /sys/bus/usb/drivers/rtl8192cu/new_id
```Now let's see if there is any action in the message logs:```
dmesg | grep 8192
```And if a wireless interface, ideally wlan0, was created:```
iwconfig
```And if it scans and sees networks:```
sudo iwlist wlan0 scan
```

---

### Post by revelias on 2013-03-03
> **chili555 said:**
> Let's try an old trick since we know ndiswrapper is out of the picture for now:```
sudo modprobe rtl8192cu
echo "2001 330D" | sudo tee /sys/bus/usb/drivers/rtl8192cu/new_id
```Now let's see if there is any action in the message logs:```
dmesg | grep 8192
```And if a wireless interface, ideally wlan0, was created:```
iwconfig
```And if it scans and sees networks:```
sudo iwlist wlan0 scan
```

```
echo "2001 330D" | sudo tee /sys/bus/usb/drivers/rtl8192cu/new_id
``` returned "2001 330D" 
```
dmesg | grep 8192
``` returned "[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff88005bc00000 s84736 r8192 d21760 u1048576[    0.000000] pcpu-alloc: s84736 r8192 d21760 u1048576 alloc=1*2097152
[ 2826.250156] usbcore: registered new interface driver rtl8192cu"

```
iwconfig
``` returned "eth0      no wireless extensions.


lo        no wireless extensions." 
and ```
sudo iwlist wlan0 scan
``` returned "Interface doesn't support scanning."

---

### Post by chili555 on 2013-03-03
The next thing I suggest is compiling ndiswrapper against your new kernel version. Then see if ndiswrapper and the Windows XP .inf will finally succeed. Here is an outline: [http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981](http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981) Please see post #122. Since you already have the .inf and .sys files installed, it ought to, if it's going to, start up when you modprobe ndiswrapper.

Off for the evening. They insist I have food and sleep around here.

---

### Post by revelias on 2013-03-03
> **chili555 said:**
> The next thing I suggest is compiling ndiswrapper against your new kernel version. Then see if ndiswrapper and the Windows XP .inf will finally succeed. Here is an outline: [http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981](http://ubuntuforums.org/showthread.php?t=1695036&page=13&p=12527981#post12527981) Please see post #122. Since you already have the .inf and .sys files installed, it ought to, if it's going to, start up when you modprobe ndiswrapper.

Off for the evening. They insist I have food and sleep around here.

Followed the instructions but the device still didn't start.

---

### Post by chili555 on 2013-03-04
Are there any informative messages here?```
dmesg | grep ndis
```I have just about exhausted all my mojo except newegg.com.

---

### Post by revelias on 2013-03-04
> **chili555 said:**
> Are there any informative messages here?```
dmesg | grep ndis
```I have just about exhausted all my mojo except newegg.com.

```
dmesg | grep ndis
```
returned 
[  113.222234] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[  240.964381]  [<ffffffffa034505e>] load_wrap_device+0x18e/0x1e0 [ndiswrapper]
[  240.964430]  [<ffffffffa0353dac>] wrap_pnp_start_pci_device+0x4c/0x90 [ndiswrapper]
[  240.964940]  [<ffffffffa0345214>] loader_init+0xa4/0x150 [ndiswrapper]
[  240.964970]  [<ffffffffa0317073>] wrapper_init+0x73/0x1000 [ndiswrapper]

---

### Post by chili555 on 2013-03-04
I deeply regret that I must reluctantly add this device to my short list of only two devices that I know of no way to get working. The only suggestions I have left are to email Realtek and ask them about it:> $ modinfo rtl8192cu
filename:       /lib/modules/3.5.0-25-generic/updates/cw-3.6/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
[COLOR="#FF0000"]author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>[/COLOR]
And, finally, regrettably, return it and get a different device. I'm sorry I couldn't be of further assistance.

---

### Post by revelias on 2013-03-04
Don't worry about it. I appreciate everything you've done. Thanks.

---

### Post by wadelius on 2013-03-04
> **chili555 said:**
> The trick, of course, is whether the new kernel's version of rtl8192cu actually covers your device.```
modinfo rtl8192cu | grep 330D
```And you can get the old driver iwl3945 to not load by blacklisting it.```
sudo su
echo "blacklist iwl3945" >> /etc/modprobe.d/blacklist.conf
modprobe -r iwl3945
exit
```What was not working about your Intel? Mine works beautifully in every respect.

My intel card works well, but I want to make better use of my n-network at home.

Wow, you guys have really tried a lot of stuff, too bad the ndiswrapper solution does not work.

Meanwhile I have done my best to destroy my system :smile:.  I did a major misreading and mistook my 2001:330d for the 2001:3309 in  the most recent compat-drivers source code for rtl8192cu. To find out  what chip is powering the adapter I opened it, and it is indeed a  rtl8192cu chip. 

I then thought, hey, why not try to add the VID PID to the driver and hope? So to test this I changed the 330**9** to 330**D** and installed the drivers from source. After a reboot the connected dwa-131 lights up, but I have no grapics :confused:.

In recovery mode root console iwconfig shows 2 wireless devices! So finally it is recognised, and hopefully working. So the question is now, how do I restore the graphics? Any pointers would be very welcome!

---

### Post by chili555 on 2013-03-04
Graphics is a question for General Help. You might see a clue in:```
cat /var/log/Xorg.0.log | grep EE
```Does the device do more than light up? Does it connect??

---

### Post by wadelius on 2013-03-04
When I enable network in recovery mode it lights up. Running iwlist wlan1 scan returns
```
wlan1   No scan results
```

I'll see if I can enable the graphics somehow, that is the first priority now.

I tried starting Xorg from the recovery console, and that crashes. 

```
cat /var/log/Xorg.0.log | grep EE
``` gives
```

(EE) intel(0): failed to get resources: Invalid argument
(EE) Screen(s) found, but none have a usable configuration.

...

Fatal server error:
no screens found
(EE)
```

---

### Post by chili555 on 2013-03-04
To General Help you go, sir or madam! I am graphics-challenged. [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

### Post by wadelius on 2013-03-04
I have posted there now: [http://ubuntuforums.org/showthread.php?t=2122245](http://ubuntuforums.org/showthread.php?t=2122245)

I can boot completely with older kernels, but I want to try 3.8 since the adapter might start to work with that one.

I want to experiment a bit with recovery root console to see if I can get the dwa-131 to work. As I wrote earlier, iwlist wlan1 scan returns
```
wlan1    No scan results
```

Any ideas on stuff I can try to get it to scan?

---

### Post by chili555 on 2013-03-04
Look for informative clues:```
rfkill list all
dmesg | grep -e rtl -e wlan
iwconfig
```

---

### Post by wadelius on 2013-03-04
> **chili555 said:**
> Look for informative clues:```
rfkill list all
dmesg | grep -e rtl -e wlan
iwconfig
```

```
rfkill list all
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: acer-wireless: Wireless LAN
        Soft blocked: no
        Hard blocked: no
2: hci0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
3: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```


```
dmesg | grep -e rtl -e wlan
rtl8192cu: Chip version 0x11
rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
usbcore: registered new interface driver rtl8192cu
ieee80211 phy1:  Selected rate control algorithm 'rtl_rc'
rtlwifi: wireless switch is on
IPv6: ADDRCONF (NETDEV_UP): wlan2: link is not ready
wlan0: authenticate with 4c:60:de:2c:0a:79
wlan0: capabilities/regulatory prevented using AP HT/VHT configuraion, downgraded
wlan0: send auth to 4c:60:de:2c:0a:79 (try 1/3)
wlan0: authenticated
wlan0: associate with 4c:60:de:2c:0a:79 (try 1/3)
wlan0: RX AssocResp from 4c:60:de:2c:0a:79 (capab=0x411 status=0 aid=5)
wlan0: associated
IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
```

```
iwlist wlan2 scan
wlan2     No scan results
```

wlan0 is the old intel card, wlan2 the adapter. 

Tried: ```
modprobe -r rtl8192cu
modprobe rtl8192cu
```

After that I can scan :P! So if I could configure a wpa_supplicant.conf I guess I can use the adapter. If the graphics would start working I could try network-manager, so I'm going to focus on that now. 
Thank you for the help chili555!

---

### Post by chili555 on 2013-03-04
In order for Network Manager to manage (ha, ha!) wlan1, you'll probably need to blacklist or at least temporarily unload the driver associated with wlan0.```
sudo modprobe -r <some_driver>
```

We would love to see the details of the file(s) you modified to get rtl8192cu to drive this device. I'm sure revelias and a few dozen future searchers will appreciate it.

---

### Post by wadelius on 2013-03-05
So now I am officially giving up on this device, just cannot get it to work together with graphics. What I did to almost get it to work was:

[LIST=1]
[*]Install kernel 3.8.0-030800-generic as instructed here: [http://handytutorial.com/install-linux-kernel-3-8-in-ubuntu-12-10-12-04/](http://handytutorial.com/install-linux-kernel-3-8-in-ubuntu-12-10-12-04/) 
[*]Download compat-drivers from [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.8/) 
[*]Open [FONT=courier new]compat-drivers-3.8-1/drivers/net/wireless/rtlwifi/rtl8192cu/sw.c[/FONT] 
[*]Go to line 356 and change ```
{RTL_USB_DEVICE(0x2001, 0x330**9**, rtl92cu_hal_cfg)}, /*D-Link-Alpha*/
``` to ```
{RTL_USB_DEVICE(0x2001, 0x330**d**, rtl92cu_hal_cfg)}, /*D-Link-Alpha*/
``` 
[*]Go to compat-drivers root directory and install from source with ```
make && sudo make install
``` 
[/LIST]
  
After rebooting and starting the recovery mode, start network (that takes quite some time). Then select root console and play aroud with modprobe, iwcofig and iwlist. But now I am giving up and going to try to find another usb adapter.

Do you have any suggestions on usb-wifi-dongles that just work?

---

### Post by chili555 on 2013-03-05
> Do you have any suggestions on usb-wifi-dongles that just work? I do not, however the question has been asked many times here. A quick search will find many suggestions.

---

### Post by djonathan on 2013-03-13
I have not messed around with the compat driver, but adding the correct VID/PID to the current staging driver doesn't do it.  Might be something about reading the eeprom...

Meanwhile, I know this isn't the ideal solution, but to see the DWA-131 revB work, go to [www.realtek.com.tw]("http://www.realtek.com.tw"), navigate to the download page for the RTL8192CU, and get the version 3.4.4_4749 driver. Even it needs to be patched with the 0x330d PID.

I think the firewall is preventing my patch upload, so here it is:




diff -Naur hal/rtl8192c/usb/usb_halinit.c new/hal/rtl8192c/usb/usb_halinit.c 
--- hal/rtl8192c/usb/usb_halinit.c    2012-07-30 05:51:05.000000000 -0700
+++ new/hal/rtl8192c/usb/usb_halinit.c    2013-03-13 11:35:25.266566979 -0700
@@ -3786,6 +3786,9 @@
                 pHalData->CustomerID = RT_CID_DLINK;
             else if((pHalData->EEPROMVID == 0x2001) && (pHalData->EEPROMPID == 0x330a))
                 pHalData->CustomerID = RT_CID_DLINK;
+            // DWA-131 revB test
+            else if((pHalData->EEPROMVID == 0x2001) && (pHalData->EEPROMPID == 0x330d))
+                pHalData->CustomerID = RT_CID_DLINK;
             break;
         case EEPROM_CID_WHQL:
 /*            


diff -Naur os_dep/linux/usb_intf.c new/os_dep/linux/usb_intf.c
--- os_dep/linux/usb_intf.c    2012-07-30 05:51:05.000000000 -0700
+++ new/os_dep/linux/usb_intf.c    2013-03-13 11:34:22.626566387 -0700
@@ -137,6 +137,8 @@
     {USB_DEVICE(0x2001, 0x3307)},//D-Link - Cameo
     {USB_DEVICE(0x2001, 0x330A)},//D-Link - Alpha
     {USB_DEVICE(0x2001, 0x3309)},//D-Link - Alpha
+    // DWA-131 revB test
+    {USB_DEVICE(0x2001, 0x330d)},//DWA-131 revB
     {USB_DEVICE(0x0586, 0x341F)},//Zyxel - Abocom
     {USB_DEVICE(0x7392, 0x7822)},//Edimax - Edimax
     {USB_DEVICE(0x2019, 0xAB2B)},//Planex - Abocom

---

### Post by Pyppe on 2013-03-28
Thanks so much djonathan for the diff. Made my day. :)

---

### Post by revelias on 2013-05-13
Did you ever get the DWA-131 B to work? If so could you post exactly how you did it?

---

### Post by bladernr on 2013-05-21
FWIW, I just bought one of these tonight, also mistakenly thinking it would work out of the box.  Apparently, the older rev. worked fine, but this new rev has ... issues.

Following this thread (read all 5 pages) I discovered a couple things.
First, keep in mind, I'm running Raring with the latest updates. (3.8 kernel)
The system is an aging Thinkpad x201 with a Centrino-N onboard wireless device that is flaky.

So following the setup instructions for using ndiswrapper in this thread was a disaster.  The ndiswrapper bits worked fine, however, loading ndiswrapper caused a kernel panic and a dead machine.

So I figured this out:

1: on inserting the RWA-131, Raring loads the rt2x00* drivers (rt2800.ko, etc)
2: this loaded when you load the ndiswrapper module causes an instant kernel panic and dead GUI, with only a console visible showing the stack trace.
3: blacklisting everything in /lib/modules/<KERNEL VERSION>/kernel/drivers/net/wireless/rt2x00 directory first still resulted in a kernel panic, but it took slightly longer.
4: It's possible that by blacklisting that module the kernel is automatically trying to load some other Ralink driver as a fallback.

I didn't bother hunting down module conflicts however.  On my raring system, the following two steps were all that I needed.

modprobe rtl8192cu
echo "2001 330D" | tee /sys/bus/usb/drivers/rtl8192cu/new_id

After doing that, iwconfig showed the DWA-131 as a device:
```
wlan3     IEEE 802.11bgn  ESSID:"HIDDEN"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: E0:91:F5:XX:XX:XX   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=63/70  Signal level=-47 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:113   Missed beacon:0

```


and it scanned just fine:
```
wlan3     Scan completed :          Cell 01 - Address: XX:XX:XX:XX:XX:XX
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"HIDDEN"

```
And network-manager shows it side by side my failing Intel Centrino-N wifi card.

So I can remove iwlwifi and iwldvm and happily use hte RWA-131 now.

I am guessing that at some point in the near future, the module will be updated to include the ID for this new device revision and a future kernel update for Raring will include that.

So I just have a simple shell script to run those commands whenever I need to use the DWA-131 dongle.  When I'm at home, I use ethernet, so it's not necessary.

---

### Post by Mark_Manning on 2013-10-18
Hey Chili,
I know this post is several months old but I found that A) you have answered a ton of questions on here and have a wealth of knowledge B) I found myself in a similar situation as Revelias,  Over the last year I have learned to dislike Ndiswrapper because at every patch upgrade it seems to die.  So I recently upgraded to Ubuntu 13.04 and Ndiswrapper died again and I had trouble reinstalling and getting my D-Link DWA-131 working again.  I came back to work on it today and after uninstalling NDiswrapper I upgraded to 13.10 "Saucy Salamander".  Everything looked clean in the lsusb and dmesg but the device was not coming to life.  As I read your trick with "[COLOR=#000000][FONT=Ubuntu Mono]echo "2001 330D" | sudo tee /sys/bus/usb/drivers/rtl8192cu/new_id [SIZE=2][FONT=arial]I thought your trick just might work for me but all the lsusb and dmeg result referred to the device with a lower case "d"; "2001 330d" so I tried that and it immediately came to life.  Thanks for all your help to the community and I hope this helps someone.[/FONT][/SIZE][/FONT][/COLOR]

---

### Post by Spirit of Yggdrasill on 2013-12-25
> **bladernr said:**
> 
modprobe rtl8192cu
echo "2001 330D" | tee /sys/bus/usb/drivers/rtl8192cu/new_id


Man, thanks, I can't believe that this is all that is needed. It worked like a charm!!!

I'm on Mint Petra using KDE (just for records).

---

