---
title: "Belkin Surf N300XR (RTL8192CU) Wireless USB not recognised by nm-tool on Ubuntu 12.04"
date: 2012-05-03
forum: Networking &amp; Wireless
---

### Post by JackSpSp on 2012-05-03
Hi everybody,

I've already checked several threads related to RTL8192CU based Wireless  USB before opening a new one lest I be redundant upon the forum. However, I didn't manage to fix the connection.

The point is that despite on the fact that the RTL8192CU driver's  already included into the kernel and should work out-of-the-box, it  seems that this is not my case. Therefore, I have no network connection  at all, so that I have to post from a different machine.

Would be someone so kind to help me out with that issue? May I ask you  for the terminal's commands to get the data you might need? I enclose  you some data that I presume you could need.

```

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

``````

uname -a
Linux jack-desktop 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 athlon i386 GNU/Linux

``````

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:0103 Realtek Semiconductor Corp. USB 2.0 Card Reader
Bus 001 Device 003: ID 050d:1004 Belkin Components 

``````

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by The Cog on 2012-05-08
Moved to Networking where hopefully it won't get buried so quickly.

---

### Post by chili555 on 2012-05-08
Support for your device is being added to rtl8192cu now: [http://comments.gmane.org/gmane.linux.kernel.wireless.general/88452](http://comments.gmane.org/gmane.linux.kernel.wireless.general/88452)> {RTL_USB_DEVICE(0x[COLOR="Red"]050d[/COLOR], 0x[COLOR="Red"]1004[/COLOR], rtl92cu_hal_cfg)}, /*Belcom-SurfN300*/When it will make it to the Ubuntu kernel and out to everyday use is unknown to me. Let's see if we can do a little trick and get it recognized. Please remove the device and in a terminal, do:```

sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="050d", ATTR{idProduct}=="1004", RUN+="/sbin/modprobe -qba rtl8192cu"
```Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```

install rtl8192cu /sbin/modprobe --ignore-install rtl8192cu $CMDLINE_OPTS; /bin/echo "050d 1004" > /sys/bus/usb/drivers/rtl8192cu/new_id
```
Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:```
sudo modprobe rtl8192cu
```Please note that rtl8192cu is a bit unreliable; if this doesn't work, we will try another approach. [http://ubuntuforums.org/showthread.php?t=1949810&highlight=rtl8192cu](http://ubuntuforums.org/showthread.php?t=1949810&highlight=rtl8192cu)

---

### Post by JackSpSp on 2012-05-11
Thanks for your help! I added the lines I was told to, but the issue wasn't fixed. In fact, as soon as the USB was plugged, a kind of error screen was showed, then the screen failed. The machine had to be restarted.
Same thing happened when I ran
```
sudo modprobe rtl8192cu
```
and plugged the USB.
Is there any log you would need to figure it out a next steep?
Cheers, J.

---

### Post by chili555 on 2012-05-11
I'd love to see:```
dmesg | grep 8192
```Meanwhile, please proofread carefully the files you wrote; remember, caps, brackets, punctuation, etc. are *crucial*.

---

### Post by JackSpSp on 2012-05-13
Hi!

I copy pasted the code to avoid error when copying. I undid the changes  to be able to plug again the USB and send you the code back. I got this.

```
dmesg | grep 8192
[  949.495175] usbcore: registered new interface driver rtl8192cu

```

Thanks in advance, J.

---

### Post by chili555 on 2012-05-13
Trial number 1 didn't work. The next thing we can try is to download the driver from Realtek and, if it isn't already there, add the usb.id and compile it. Or we could try ndiswrapper. They are about equally complex. Do you have a preference?

---

### Post by JackSpSp on 2012-05-13
Hi.

I downloaded the linux driver from Realtek. I tried to install it, but an error message appeared. See bellow.
```
sudo bash /media/USBdrive/RTL8188C_8192C_8192D_USB_linux_v3.4.2_3727.20120404/install.sh
##################################################
Realtek Wi-Fi driver Auto installation script
Novembor, 21 2011 v1.1.0
##################################################
/media/USBdrive/RTL8188C_8192C_8192D_USB_linux_v3.4.2_3727.20120404/install.sh: line 17: cd: driver: No such file or directory
Decompress the driver source tar ball:
    
tar: Old option `f' requires an argument.
Try `tar --help' or `tar --usage' for more information.
Desktop
Documents
Downloads
examples.desktop
Music
Pictures
Public
Templates
Ubuntu One
Videos
Authentication requested [root] for make clean:
make: *** No rule to make target `clean'.  Stop.
Authentication requested [root] for make driver:
make: *** No targets specified and no makefile found.  Stop.
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################
```
Do you have any idea of how to avoid this error?

Thanks! J.

---

### Post by chili555 on 2012-05-13
The device ID is *NOT* included in the package you downloaded. We must add it. In the package you extracted, drill down to *driver*. Right-click the package within and select *Extract Here*. Now go to os_dep/linux and open usb_intf.c with a text editor. Add your device exactly as here:```
/*=== Customer ID ===*/	
	/****** 8188CUS Dongle ********/
	{USB_DEVICE(0x2019, 0xED17)},//PCI - Edimax
	{USB_DEVICE(0x0DF6, 0x0052)},//Sitecom - Edimax
	{USB_DEVICE(0x7392, 0x7811)},//Edimax - Edimax
	{USB_DEVICE(0x07B8, 0x8189)},//Abocom - Abocom
	{USB_DEVICE(0x0EB0, 0x9071)},//NO Brand - Etop
	{USB_DEVICE(0x06F8, 0xE033)},//Hercules - Edimax
	{USB_DEVICE(0x103C, 0x1629)},//HP - Lite-On ,8188CUS Slim Combo
	{USB_DEVICE(0x2001, 0x3308)},//D-Link - Alpha
	{USB_DEVICE(0x050D, 0x1102)},//Belkin - Edimax
	[COLOR="Red"]{USB_DEVICE(0x050D, 0x1004)},//Belkin - Surf[/COLOR]
	{USB_DEVICE(0x2019, 0xAB2A)},//Planex - Abocom
	{USB_DEVICE(0x20F4, 0x648B)},//TRENDnet - Cameo
	{USB_DEVICE(0x4855, 0x0090)},// - Feixun
```Everything before and after is unchanged. Punctuation, caps, brackets, etc. are very crucial. Proofread twice. Save and close the text editor.

Now back to the terminal and we are going to install our way, not the install.sh. Please get a temporary wired ethernet connection.```
sudo apt-get install build-essential linux-headers-generic
cd Desktop/RTL8188C_8192C_8192D_USB_linux_v3.4.2_3727.20120404/driver/rtl8188C_8192C_8192D_usb_linux_v3.4.2_3727.20120404/  <--or wherever you extracted the files
sudo su
make
make install
modprobe rtl8192cu
exit
```Any errors or warnings?

It makes perfectly for me, nary a whimper.

---

### Post by JackSpSp on 2012-05-14
Hi,

I added the USB id upon the file  and installed the package. No errors were shown. However, when I plugged the USB, nothing happened, so I restarted the machine with no success.

I repeated the operation, but just adding the USB id in a different line in the file. I don't know whether it should help or not. Despite on this change, the USB is still being unable to connect.
 ```
/****** 8192CUS Dongle ********/
    {USB_DEVICE(0x2001, 0x3307)},//D-Link - Cameo
    {USB_DEVICE(0x2001, 0x330A)},//D-Link - Alpha
    {USB_DEVICE(0x2001, 0x3309)},//D-Link - Alpha
    {USB_DEVICE(0x0586, 0x341F)},//Zyxel - Abocom
    {USB_DEVICE(0x7392, 0x7822)},//Edimax - Edimax
    {USB_DEVICE(0x2019, 0xAB2B)},//Planex - Abocom
    {USB_DEVICE(0x07B8, 0x8178)},//Abocom - Abocom
    {USB_DEVICE(0x07AA, 0x0056)},//ATKK - Gemtek
    {USB_DEVICE(0x4855, 0x0091)},// - Feixun
    {USB_DEVICE(0x2001, 0x3307)},//D-Link-Cameo
    {USB_DEVICE(0x050D, 0x1004)},//Belkin - Surf <<<<<<<<<<<<<<<<<<<
    {USB_DEVICE(0x050D, 0x2102)},//Belkin - Sercomm
    {USB_DEVICE(0x050D, 0x2103)},//Belkin - Edimax
    {USB_DEVICE(0x20F4, 0x624D)},//TRENDnet
    {USB_DEVICE(0x0DF6, 0x0061)},//Sitecom - Edimax
    {USB_DEVICE(0x0B05, 0x17AB)},//ASUS - Edimax
    {USB_DEVICE(0x0846, 0x9021)},//Netgear - Sercomm
    {USB_DEVICE(0x0E66, 0x0019)},//Hawking,Edimax 
```
On the other hand, if I do again ```
sudo dmesg | grep 8192
``` there is no answer at all, unlike before.

Thanks for your help, J.

---

### Post by chili555 on 2012-05-14
> On the other hand, if I do again

```
sudo dmesg | grep 8192
```

there is no answer at all, unlike before.Let's try again. With the device plugged in:```
sudo modprobe rtl8192cu
dmesg | grep 8192
```I hope there are some clues.

---

### Post by JackSpSp on 2012-05-15
Hi.

I paste the code.
```
sudo modprobe rtl8192cu
dmesg | grep 8192
[  250.408474] usbcore: registered new interface driver rtl8192cu
```Regards, J.

---

### Post by chili555 on 2012-05-15
Sadly, trial number 2 didn't work either. I've played with this for a couple of hours on my own system and I can't get it to recognize your usb.id either. Next, I suggest we try ndiswrapper. With the ethernet cable attached, please do:```
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```Now we blacklist the in-kernel 8192cu driver. We know it doesn't work, but it may some day and we'd like to switch over in an orderly fashion rather than a driver conflict, kernel panic, etc. or other unintended consequences.```
sudo su
echo "blacklist 8192cu" >> /etc/modprobe.d/blacklist.conf
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf
echo ndiswrapper >> /etc/modules
exit
```Now download the file I've attached to your desktop. Right-click it and select *Extract Here*. Now back to the terminal:```
cd Desktop/WinXP
sudo ndiswrapper -i netrtwlanu.inf

```Now check the installation:```
ndiswrapper -l
```It ought to report the device and driver with no errors or warnings.```
sudo depmod -a
sudo modprobe ndiswrapper
```Is it working now?

---

### Post by JackSpSp on 2012-05-16
Thanks again!

I've tried with the ndiswrapper. There were no error until last command ```
ndiswrapper -l
netrtwlanu : driver installed
    device (050D:1004) present
sudo depmod -a
sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.

```I hope fatal doesn't mean fatal...

Regards, J.

---

### Post by chili555 on 2012-05-16
Please try again:```
sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9
sudo modprobe ndiswrapper
```Weird.

---

### Post by JackSpSp on 2012-05-16
Hi,

The reinstallation has been done and no errors has been shown. However, the fatal message after the last command continues.
```
sudo apt-get install --reinstall ndiswrapper-common ndiswrapper-utils-1.9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 62 not upgraded.
Need to get 0 B/26.9 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 189714 files and directories currently installed.)
Preparing to replace ndiswrapper-common 1.57-1ubuntu1 (using .../ndiswrapper-common_1.57-1ubuntu1_all.deb) ...
Unpacking replacement ndiswrapper-common ...
Preparing to replace ndiswrapper-utils-1.9 1.57-1ubuntu1 (using .../ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb) ...
Unpacking replacement ndiswrapper-utils-1.9 ...
Processing triggers for man-db ...
Setting up ndiswrapper-common (1.57-1ubuntu1) ...
Setting up ndiswrapper-utils-1.9 (1.57-1ubuntu1) ...
sudo modprobe ndiswrapper
FATAL: Module ndiswrapper not found.


```Still weird, isn't it?

Regards.

---

### Post by chili555 on 2012-05-16
> Still weird, isn't it?Yes, indeed. Like women, the more experience I have with ndiswrapper, the less I seem to understand! In a few more years I will know nothing about either.

Please try:```
sudo apt-get install ndiswrapper-dkms
sudo modprobe ndiswrapper
```

---

### Post by JackSpSp on 2012-05-21
Many thanks!

> Yes, indeed. Like women, the more experience I have with ndiswrapper,  the less I seem to understand! In a few more years I will know nothing  about either.lol

After installing ndiswrapper-dkms, the USB is recognized by nm-tool, it shows the available networks and asks me about the password. However, it fails to connect to the router. It seems that starts some kind of looping, so I had to unplug the USB or to disable networking.

Regards, J.

---

### Post by uqbar on 2012-08-15
Is there any news in NOT using ndiswrapper?
All I get so far is:

2012-08-15T11:22:54.561873+02:00 uqbar kernel: [  550.072106] usb 2-2: new high-speed USB device number 6 using ehci_hcd
2012-08-15T11:22:54.698859+02:00 uqbar mtp-probe: checking bus 2, device 6: "/sys/devices/pci0000:00/0000:00:1d.7/usb2/2-2"
2012-08-15T11:22:54.702849+02:00 uqbar mtp-probe: bus: 2, device: 6 was not an MTP device

What'd be an MTP device?

---

