---
title: "Wireless/Wired Connection Problems BCM4306"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by greg0ry on 2009-06-27
I'm new and highly confused/irritated. I'll try to make available as much info upfront as I know how. I appreciate any and all help.

I am trying to get my wireless card to work through ndiswrapper. I have checked, and the official Broadcom Linux drivers do not support my chipset. I also know about the b43 firmware option, and I would prefer to make things work with ndiswrapper instead.

I ran into what is seemingly a common problem —in that ndiswrapper could not gain control over the WLAN because other modules were taking it.

I came upon this solution added to '/etc/modprobe.d/ndiswrapper':
```
install ndiswrapper modprobe -r b43 b43legacy b44 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe b44
```This got me further than before —in that I could sometimes get an animation from NetworkManager applet. However, no wireless networks were ever auto-detected, and I cannot connect to a wireless network.

To make matters more complicated, after all of this, I finally decided to connect my hard-wired ethernet in. It does not work either. I'm hoping this is something I did while trying to get the wireless side of things to work.

Here is my info:

Machine: Dell Inspiron 8500

Ubuntu: 9.04 i686
Kernel: 2.6.28-11-generic

Wireless: Dell TrueMobile 1300 / Broadcom BCM4306 | Rev 02 | 14E4:4320

Output from 'sudo lshw -C network':
```
  *-network:0
           description: Ethernet interface
           product: BCM4401 100Base-T
           vendor: Broadcom Corporation
           physical id: 0
           bus info: pci@0000:02:00.0
           logical name: eth0
           version: 01
           serial: 00:0b:db:18:1e:a3
           size: 100MB/s
           capacity: 100MB/s
           width: 32 bits
           clock: 33MHz
           capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
           configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full latency=32 link=yes module=ssb multicast=yes 
port=twisted pair speed=100MB/s
  *-network:1
           description: Wireless interface
           product: BCM4306 802.11b/g Wireless LAN Controller
           vendor: Broadcom Corporation
           physical id: 3
           bus info: pci@0000:02:03.0
           logical name: wlan0
           version: 02
           serial: 00:90:4b:b1:df:64
           width: 32 bits
          clock: 33MHz
          capabilities: pm bus_master cap_list ethernet physical wireless
          configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+Broadcom,12/04/2006, 4.10.4 latency=32 link=no 
module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
            description: Ethernet interface
            physical id: 2
            logical name: pan0
            serial: 76:1f:26:bd:e3:1f
            capabilities: ethernet physical
            configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

Where do I go from here?

---

### Post by Ayuthia on 2009-06-27
Actually, your card should be supported by b43legacy.  The 4306 rev 02 is listed at [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) as a supported card.  However, you do need to download the firmware to make it work.

Anyway, it does look like you have ndiswrapper installed.  By any chance, are you using encryption?  If so, try turning it off and see if you can connect.  Some of the XP drivers needed for the 4306 card does not support WPA/WPA2.

As for your wired connection, I have not been able to confirm this, but it looks like there might be a bug with that.  I think that you need to install the firmware for the b43legacy card in order to get your wired card to work.  I think I have seen a few cases where people had to do that.

---

### Post by greg0ry on 2009-06-28
Hello Ayuthia, thank you for replying. :)

Interestingly enough, the BCM4306 chipset my card uses is listed further down the page as using the b43 driver and not the b43legacy when the PCI-ID is 14E4:4320 —as mine is. Perhaps some clarification is needed on that page. However I would like to avoid that route anyways, and use ndiswrapper instead.

I have turned off all encryption, turned off 4x, I have SSID broadcasting, all in an attempt to avoid as many issues as possible while trying to get the basics(detection/connection).

As for the wired connection, it uses the b44 driver and not b43, etc. So I don't know if that is the culprit.

I'm at a complete loss as to what to do next.

---

### Post by Ayuthia on 2009-06-28
Yours is actually the b43legacy because under the Supported chip types, the 4306 rev 02 is listed as the b43legacy and the 4306 rev 03 is the b43.  They both have the 4320 chipset.  That list was updated recently, but now a lot of the information is wrong.

Just to see what is happening, can you post the results of:
```
lsmod|grep -e b43 -e b44 -e ssb -e ndis -e wl
dmesg|grep -e ndis -e b43
sudo iwlist scan
```

Since you don't have a connection, it might be easier to copy them into a file and then attach them:
```
lsmod|grep -e b43 -e b44 -e ssb -e ndis -e wl > lsmod.txt
dmesg|grep -e ndis -e b43 > dmesg.txt
sudo iwlist scan > scan.txt
```

For the first command, we are check to see that only b44, ssb, and ndiswrapper are listed.  So if that is all that is listed, you don't need to attach the file.

The second command is looking for any error messages for your wireless card.  We will most likely need this attachment.

The last command is scanning for wireless sites.  Just let us know if wlan0 reports any wireless sites or says No scan results.

---

### Post by greg0ry on 2009-06-28
Removing the code I had placed in '/etc/modprobe.d/ndiswrapper' fixed my wired network problem. However ndiswrapper loses control of the wireless without the code.
```
install ndiswrapper modprobe -r b43 b43legacy b44 ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe b44
```All of the following is with the above code in place:

Output from 'lsmod|grep -e b43 -e b44 -e ssb -e ndis -e wl':
[FONT=Courier New]```

b44             35984    0
ssb             41220    1   b44
mii             13312    1   b44
ndiswrapper    193436    0

```[FONT=Verdana]Output from 'dmesg|grep -e ndis -e b43':[/FONT]
```

[    4.155045] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   13.499723] b43legacy-phy0: Broadcom 4306 WLAN found
[   13.520094] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   13.520119] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   13.544115] b43legacy-phy0 debug: Radio initialized
[   15.360996] b43-pci-bridge 0000:02:03.0: PCI INT A disabled
[   15.416105] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   15.517076] ndiswrapper: driver bcmwl5 (Broadcom,12/04/2006, 4.10.40.11) loaded
[   15.517470] ndiswrapper 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   15.522095] ndiswrapper: using IRQ 5
[   15.721234] usbcore: registered new interface driver ndiswrapper

```[FONT=Verdana]Output from 'sudo iwlist scan':
```

[FONT=Courier New]lo      Interface doesn't support scanning.

wlan0   No scan results

eth0    Interface doesn't support scanning.

pan0    Interface doesn't support scanning.[/FONT]

```[/FONT] [/FONT]

---

### Post by Ayuthia on 2009-06-28
Since you have the command taken out, can you try the following to see if you can get the wired and wireless going:
```
sudo modprobe -r b43 b43legacy b44 ssb ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44
sudo iwlist scan
```

---

### Post by greg0ry on 2009-06-29
Ayuthia, thanks so much for sticking with me through this.

The results of those procedures is exactly the same as using the code I had placed in 'etc/modprobe.d/ndiswrapper'.

Both ways, neither the wired or wireless networks work.
Both ways, the wired connection lists b44 as the 'kernel driver in use' and the 'kernel modules'
Both ways, the wireless connection lists ndiswrapper as the 'kernel driver in use' and ssb as the 'kernel modules'

The output from '[FONT=monospace]sudo iwlist scan[/FONT]' is exactly the same.

The wired connection will work using b44 if I just leave things alone. However, I do not understand why after closing then restarting b44 is does not start to work again.

The light at the end of this tunnel is getting dim.:???:

---

### Post by Ayuthia on 2009-06-29
That was expected, but I just wanted to verify that the script did not have something missing.  What this sounds like is that the ndiswrapper module is not loading properly.  If it doesn't, the b44 module isn't loading either.

Which Windows driver are you using for NDISwrapper?

Also, is there a reason for not using b43legacy instead of NDISwrapper?  This is more for reference.  I am under the impression that the b43legacy module works but I have heard that there are speed issues, but I was thinking that both ndiswrapper and b43legacy had the speed issue.

EDIT:
I am changing my answer about the first part.  It looks like the ndiswrapper module is interfering with your wired card.  You might need to try a different Windows driver.  This is the first that I have heard that NDISwrapper causing the wired card to not work so hopefully it is the Windows driver that is causing it.

---

### Post by greg0ry on 2009-06-29
I'm going to try and unload, then reload, the b44 driver without ndiswrapper ever running. Perhaps this will shed some light on things with the wired network.

The driver I'm using is from Dell. Found here: [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R143355&SystemID=INS_PNT_P4_8500&servicetag=&os=WW1&osl=en&deviceid=4394&devlib=0&typecnt=0&vercnt=15&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=191429](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R143355&SystemID=INS_PNT_P4_8500&servicetag=&os=WW1&osl=en&deviceid=4394&devlib=0&typecnt=0&vercnt=15&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=191429)

I didn't want to go the b43/b43legacy route because I thought I would have to flash a new firmware to the chip. This is correct, yes? The thought was, how could I ever flash back the original firmware on the chip since it is not available for download? Plus, I had read about connection strength/reliability not being as great as that of the ndiswrapper solution.

I'm going to try a different driver. If you, Ayuthia, or anyone else, knows of a driver that supports WPA2-PSK that would work with my chip, I would be glad to know of it.

I'll try some things later tonight and report back.

Thanks.

---

### Post by Ayuthia on 2009-06-29
> **greg0ry said:**
> I'm going to try and unload, then reload, the b44 driver without ndiswrapper ever running. Perhaps this will shed some light on things with the wired network.

The driver I'm using is from Dell. Found here: [http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R143355&SystemID=INS_PNT_P4_8500&servicetag=&os=WW1&osl=en&deviceid=4394&devlib=0&typecnt=0&vercnt=15&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=191429](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R143355&SystemID=INS_PNT_P4_8500&servicetag=&os=WW1&osl=en&deviceid=4394&devlib=0&typecnt=0&vercnt=15&catid=-1&impid=-1&formatcnt=1&libid=5&fileid=191429)

I didn't want to go the b43/b43legacy route because I thought I would have to flash a new firmware to the chip. This is correct, yes? The thought was, how could I ever flash back the original firmware on the chip since it is not available for download? Plus, I had read about connection strength/reliability not being as great as that of the ndiswrapper solution.

I'm going to try a different driver. If you, Ayuthia, or anyone else, knows of a driver that supports WPA2-PSK that would work with my chip, I would be glad to know of it.

I'll try some things later tonight and report back.

Thanks.

There is no flashing of firmware for this.  What is happening is that there are some portions of the firmware that the b43/b43legacy module needs to operate.  b43-fwcutter is the application that will capture a portion of the firmware and create a few files for the b43/b43legacy to use.

I cannot remember which Windows driver version you need to get ndiswrapper to work with WPA2.  I know that for some of the 4306 cards, we (me and a few of the other forum members) have not been able to find a working Windows driver for WPA2.  I am thinking that the b43legacy version does provide WPA2.  In order to check and see if the Windows driver provides WPA/WPA2, you will need to check:
```
sudo iwlist auth
```.

The reports of how well b43legacy works has varied from person to person.  As I mentioned earlier, there have been a few reports from people in the forum that are having problems with getting their card to turn on in Jaunty.  So far they have been the 4303 and 4318 cards.  Yours is the first 4306 rev 02 card using Jaunty I have encountered here.

---

### Post by greg0ry on 2009-06-30
I decided to try the b43/b43legacy method. For one, the odds of finding a WPA2 capable driver seemed slim. For another, there was my misconception that I would have to flash the firmware, my bad. And yet another, this is making me crazy.;)

So I disabled ndiswrapper and installed b43-fwcutter. I allowed it to fetch what it needed and it ran it's course. Still there are no wireless networks detected. The card seems to be using module 'b43-pci-bridge', which is the one that was always used by default. Is there another step I'm missing? Perhaps a way to validate the install went correctly?

Thanks again.

---

### Post by Ayuthia on 2009-06-30
> **greg0ry said:**
> I decided to try the b43/b43legacy method. For one, the odds of finding a WPA2 capable driver seemed slim. For another, there was my misconception that I would have to flash the firmware, my bad. And yet another, this is making me crazy.;)

So I disabled ndiswrapper and installed b43-fwcutter. I allowed it to fetch what it needed and it ran it's course. Still there are no wireless networks detected. The card seems to be using module 'b43-pci-bridge', which is the one that was always used by default. Is there another step I'm missing? Perhaps a way to validate the install went correctly?

Thanks again.
We need to check:
```
dmesg|grep b43
```
It will tell us if the module loaded properly and if the card was able to be turned on.

---

### Post by greg0ry on 2009-06-30
Output from 'dmesg | grep b43':

```

[    4.177146] b43-pci-bridge 0000:02:03.0: PCI INT A -> Link[LNKB] -> GSI 5 (level, low) -> IRQ 5
[   14.372536] b43legacy-phy0: Broadcom 4306 WLAN found
[   14.400309] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   14.400335] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   14.433378] b43legacy-phy0 debug: Radio initialized
[   27.375764] input: b43legacy-phy0 as /devices/virtual/input/input9
[   27.720047] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[   27.796288] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[   27.812487] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[   27.940065] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[   28.004585] b43legacy-phy0 debug: Chip initialized
[   28.004923] b43legacy-phy0 debug: 30-bit DMA initialized
[   28.005133] Registered led device: b43legacy-phy0:tx
[   28.005163] Registered led device: b43legacy-phy0:rx
[   28.005194] Registered led device: b43legacy-phy0:radio
[   28.005226] b43legacy-phy0 debug: Wireless interface started
[   28.005234] b43legacy-phy0 debug: Adding Interface type 2

```

---

### Post by Ayuthia on 2009-06-30
It all looks correct.  The card turned on like it should.  You might try to see if you can connect manually through NetworkManager.  Just go to the Create New Wireless Network and enter the information for your router and see if it connects.  You might try to see if your card will connect to just a wireless G network (change your router to G only).  Other than that, I don't have that much else to offer.

It looks like you have done everything correctly, but for some reason your card is not seeing anything.

---

### Post by greg0ry on 2009-07-07
Well, it looks like I've done everything I could. I reinstalled fresh and retried b43-fwcutter, I even installed Windows to make sure the hardware itself was capable of functioning. I think a new wireless adapter is in my future --and it will not have a Broadcom chipset.:mad:

Thanks again Ayuthia for all your help.

---

### Post by dahlsveen on 2009-09-27
This worked for my 4309 (BCM4309) card.  With some smarts you should be able to modify the instructions to work with another Broadcom device or another version of Ubuntu, or other Linux distribution, even.  Hopefully, I have captured every step:

Use Synaptic Package Manager (System->Administration->Synaptic Package Manager) to install b43-fwcutter.  You can use the Quick Search feature to locate the package.

When Synaptic Package Manager installs b43-fwcutter, click Details and make a note of what firmware package the installer downloads.  It should be one of:
    
4.80.53.0
4.150.10.5
4.174.64.19

If you leave the install window open, you do not need to actually take any notes.

If the wireless still does not work go to:
[http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new](http://linuxwireless.org/en/users/Drivers/b43#fw-b43-new)

Read the table which spells out what firmware you need for your Linux kernel version.  If you do not know your kernel version, open up a terminal window and type:
uname -r

You should see something like:
2.6.28-15-generic

If the firmware version matches what was installed with b43-fwcutter, you, uhm, have a problem.  If not, you need to get the correct firmware:

Click the Go link on the row matching your kernel version.  Read the instructions to find out at what http address the firmware is located.  Note that the first set of instructions tells you how to get b43-fwcutter, which you already have, so skip this and copy the http address from the second set of instructions.  My firmware was located at:

[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Just copy and paste this link into a new browser tab/window.  This should initiate the download.

Unpack the drivers to any directory and using a terminal window, cd your way to the /driver directory under the folder created when you unpacked the drivers.  In my case, I unpacked the firmware to my desktop:
cd /home/elmo/Desktop/broadcom-wl-4.150.10.5/driver

Then, in the same terminal window, type:
sudo b43-fwcutter -w /lib/firmware/ wl_apsta_mimo.o

If the wireless still does not work, type the following:
sudo modprobe -r b43

Then:
sudo modprobe -r b43legacy

And, finally:
sudo modprobe b43

The two first commands remove the b43 and b43legacy modules from the kernel.  The third line adds the b43 back again.

Hopefully, your wireless is now working.  Mine did, anyway :-)

---

