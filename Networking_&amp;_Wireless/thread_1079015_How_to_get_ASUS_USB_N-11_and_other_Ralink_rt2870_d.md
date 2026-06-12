---
title: "How to: get ASUS USB N-11 and other Ralink rt2870 devices to work!"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by Reiger on 2009-02-23
This guide was written for (Kubuntu) 8.10 Intrepid, but it should work on older/newer versions as well. Important is that rt2870sta driver versions **below 1.4.0.0** will NOT work with Linux kernel 2.6 (and newer). According to Ralink's website this driver ought to work with 2.4 and 2.6 kernels (up to 2.6.27).
[list="1"][*][size="3"]**Preamble**[/size]
First of all verify this how to is for 'you': 
(a) You know your USB device requires the Ralink rt2870sta driver (for instance the manufacturer gives you this driver)
(b) Or you know because if you type
```

lsusb

```
in the terminal, you get (among other) the following output (for an ASUS USB N-11 device) returned:
```

Bus 008 Device 004: ID 1761:0b05
```
[*][size="3"]**Obtain drivers and firmware**[/size]
Get the latest Ralink rt2870sta source code (as of writing that is version 1.4.0.0) and firmware. This requires a computer with a working internet connection.

[size="1"]If you find yourself puzzling over how you are going to move that heavy-weight full-tower down to the modem; fear not: you can use NDISwrapper with Windows drivers. This in turn requires that you have these drivers (for instance on a driver cd supplied by the vendor).
If you want to use ndiswrapper, use the command:
```

sudo ndiswrapper -i inf_file

```
Where inf_file is the dot inf file supplied by the windows driver.
[/size]
[*][size="3"]**Find out your vendor and device IDs**[/size]
For the ASUS USB N-11 and at least one other device (can't remember which one) you will need to obtain 'vendor' and 'device' ids. You do this as follows:
[list="1"]
[*]Make sure the device is NOT plugged into an USB port.
[*]In a terminal type ```
lsusb
```
[*]Plug in your device and type ```
lsusb
```
[*]Find the line which was missing from the output the first time you typed lsusb. This 'magic' line will look like:
```
Bus 008 Device 004: ID 1761:0b05
```
[*]Note the ID string: it is structured as by the first n digits for the vendor ID, then a colon, and the last m digits for the device ID. Remember these IDs!
[/list]
[*][size="3"]**Preparations before building and installing the driver**[/size]
[size="1"]**IF you used ndiswrapper for this device previously**
Make sure you do not use ndiswrapper to 'run' this device! Use
```

sudo ndiswrapper -r inf_file
```
Where inf_file is the dot inf file you used to install the windows driver.
[/size]
Go to the directory where you downloaded the driver source archive and extract the driver source code and change working directory to that which (will) house(s) the driver source code:
```

cd dir;
tar xjf *RT2870*tar.bz2
cd *RT2870*

```
**Read the included README_STA** and check/edit the following files:
[list]
[*]os/linux/config.mk
[*]include/rt2870.h
[*]Makefile
[/list]

If you use kate (KDE 4.2) as your preferred text editor you can do this by:
```

kate -u README_STA os/linux/config.mk include/rt2870.h Makefile
```
This will use an existing Kate session if available (the -u switch) and open those 3 files inside it. 

Edit **os/linux/config.mk** by ensuring that both HAS_WPA_SUPPLICANT and HAS_NATIVE_WPA_SUPPLICANT have the value y. This is required to make the driver work with the wpa_supplicant and wext tools: they in turn are what your network manager uses under the hood.

Check/edit **Makefile** to make sure that Makefile has RT28xx_MODE and TARGET set to STA and LINUX respectively. **If you have kernel 2.6 locate the _patch_ command! Copy this particular command!** 

Check/edit **include/rt2870.h** contains an entry for your vendor & device id:
[list]
[*]Search for Asus until you find a list of entries that look like this:
```

	{USB_DEVICE(0x0B05,0x1731)}, /* Asus */			\

```
[*]Check the list if there is an entry for USB_DEVICE(0xvendor_id:0xdevice_id) where vendor_id and device_id as the IDs found in the output of lsusb, earlier. If not, add such an entry. **WARNING: be careful here, a typo is easy to make!**[/list]

Save and close each file; and close your editor.
**If you use kernel 2.6, now issue the _patch_ command you copied from Makefile in your terminal! [size="1"]In Konsole type Ctrl+Shift+V or from the menubar select Edit -> Paste and hit Enter.[/size]**
[*]**[size="3"]Build and install the driver[/size]**
[size="1"]If you are recovering from a previously failed attempt, use
```

sudo make uninstall
sudo make clean

``` to clean up, before you continue![/size]

Use the following code to build and install the driver
```

sudo make
sudo make install
cat /etc/modules.conf | sudo tee -a /etc/modules

```
The last line is required because Ubuntu uses /etc/modules instead of /etc/modules.conf; this line copies the contents of newly generated /etc/modules.conf and appends them to /etc/modules.
[*]**[size="3"]Check that the driver will work[/size]**
```

sudo modprobe rt2870sta
```
This should return *no* output. Now try:
```

dmesg | grep rt2

```
It should output a message that it 'registered' your rt2870sta driver. For me, that was all it listed; and it should certainly not list any error messages already!
Finally unload the module again (so it will not be 'held against you' when you will want to reload it later):
```
sudo modprobe -r rt2870sta
```
[*]**[size="3"]Now make it actually work[/size]**
Go to the directory you downloaded the firmware to earlier; unzip the firmware archive and go to the directory which (will) house(s) the firmware.
```

cd firmware_download_dir
unzip RT2870_Firmware*zip
cd RT2870*

```
Install the firmware:
```

echo $PWD$(ls *bin) | sed -n 's/^\(.*\)$/sudo mv \"\1\" \"\/lib\/firmware\/\1\" /p' | sh

```
Explanation of what the above code does: it lists the firmware (ls *bin) prepends it to the current working directory ($PWD), feeds that to the program sed which in turn transforms into a shell command, finally that is executed.
[size="1"]For the curious: sed transforms it to the following shell command (assume that firmware.bin is the name of the firmware): **sudo mv "firmware.bin" "/lib/firmware/firmware.bin"** [SIZE="2"][COLOR="Red"]**It's a good idea to check that you typed it correctly, you can then execute it safely.**[/COLOR][/SIZE] To do so, merely omit the following bit: | sh. That means to run: ```
echo $PWD$(ls *bin) | sed -n 's/^\(.*\)$/sudo mv \"\1\" \"\/lib\/firmware\/\1\" /p'
``` This should output the command mentioned earlier.[/size]
[*][size="3"]**Check that it actually works!**[/size]
Load the module again:
```

sudo modprobe rt2870sta

```
Check it works:
```

ifconfig

```
The output should now list the device "ra0".
[*][size="3"]**Optional (may be required, may be not), make your driver be automatically loaded upon (re)boot.**[/size]
```

echo "rt2870sta" | sudo tee -a /etc/modules

```
And reboot to see if it works:
```
sudo reboot
```
[/list]

If all is well, you can now configure the device "ra0" using you network manager of choice.

---

### Post by Reiger on 2009-02-24
Note: this driver works well with IPv6 enabled. Yay, no more ipv6 disabling aliases in /etc/modprobe.d/aliases required!

---

### Post by Reiger on 2009-05-14
Note: if you can't find the file to edit (see post #1), then you are probably using a newer driver than 1.4.x. As of writing the file to edit is: os/linux/usb_main_dev.c

---

### Post by kevinm3574 on 2009-07-07
So I've followed all of the steps as shown in the how-to and all appears to go well but I never get an ra0 device to show up that I can ifconfig or setup with network-manager.  Any suggestions on what I'm doing wrong?  Here's my particulars:

lsusb

Bus 005 Device 003: ID 04f2:0220 Chicony Electronics Co., Ltd 
Bus 005 Device 002: ID 107b:3009  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 116f:0005 Silicon 10 Technology Corp. 
Bus 004 Device 002: ID 046d:c043 Logitech, Inc. MX320 Laser Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 1761:0b05  
Bus 001 Device 003: ID 0781:540e SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

(1761:0b05 is the USB-N11)

modinfo rt2870sta

filename:       /lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/rt2870sta.ko
version:        2.1.2.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     7BCFB6F73FD2A8A352C961B
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*
depends:        usbcore
vermagic:       2.6.27-7-generic SMP mod_unload modversions 586 
parm:           mac:rt28xx: wireless mac addr (charp)


lsmod | grep rt2

rt2870sta             509388  0 
usbcore               148848  8 rt2870sta,lirc_mceusb2,usb_storage,usbhid,libusual,uhci_hcd,ehci_hcd


dmesg | grep rt2

[   17.394892] usbcore: registered new interface driver rt2870
[ 1135.191973] usbcore: deregistering interface driver rt2870
[ 1223.677872] usbcore: registered new interface driver rt2870

This is on an Ubuntu Intrepid install (latest patches)...I would go to Jaunty but I have an Intel built-in video card that get's blown up every time I try to update to Jaunty (can't get a login screen)...but that's a story for another day and forum.

Thanks.

Kevin

---

### Post by pauloppenheim on 2009-08-15
[kevinm3574]("http://ubuntuforums.org/member.php?u=856508"), i had the same problem. I skipped the version 1.4.0.0 and got 2.1.2.0 directly from ralink, and just couldn't get it working. I decided to go back to the 1.4.0.0 supplied by Asus, and noticed the real gem when I was editing the driver file to make sure it had the correct device ID (because, as has been noted, newer adapters show up with 1761:0B05, not 1731:0B05 as they did when the author wrote this.)

the old asus-provided **include/rt2870.h** had this gem:
```

    {USB_DEVICE(0x0B05,0x1761)}, /* Asus Added by Z-Com 2008-12-15 */            \
    {USB_DEVICE(0x1761,0x0B05)}, /* Asus Added by Z-Com 2008-12-15 */            \

```that's right, some hardware has the ID in backwards. Epic.

So i just did the same in the 2.1.2.0 os/linux/usb_main_dev.c
```

    {USB_DEVICE(0x0B05,0x1761)}, /* Asus - new USB-N11 */
    {USB_DEVICE(0x1761,0x0B05)}, /* Asus - new USB-N11 (no, you're not reading it wrong. + poppy) */

```and did the uninstall / reinstall dance, and it works just fine. That's what I get for using the manufacturer-supplied source instead of the vendor-supplied source ;) I should have learned my lesson from laptop graphics drivers!

HTH

---

### Post by wesswei on 2009-09-04
Anybody know if this driver is going to be in the main kernel anytime soon? I'm getting tired of compiling ralink drivers. I thought that's what rt2x00 was for?!?! 

I was finally finished with compiling my linksys wusb54g as it now works with the kernel drivers. Now after upgrading to asus usb-n11, I find that it's complete horse$h!+ 

why!?!?! and why is the stupid device and vendor ids missing!?!?! ararhrhrh!

---

### Post by Reiger on 2009-11-15
The driver is in the kernel, (sudo modprobe rt2870sta; dmesg | grep rt2870 should print a warning about it being experimental) -- but that driver uses pretty much the same hardware signatures as the old stock Ralink driver does. Therefore it misses the required hardware signatures to detect an USB-N11 device out of the box...

---

### Post by ilna on 2010-09-13
Has anybody a lucky story (or an appropriate hrefs) of USB-N11 working as Access Point? With hostapd?

---

