---
title: "3dsp wireless and bluetooth mini pci adapter drivers"
date: 2009-08-07
forum: Networking &amp; Wireless
---

### Post by Purple8 on 2009-08-07
Hi 
I have just purchased the above card. The driver disk doesn't seem to work it says; 3DSP drivers does not support Linux 2.6.28-14-generic version now!!! 

the read me states 
Kernel Supportable
==================
ubuntu8.04 "2.6.24-16-generic" "2.6.24-19-generic" "2.6.24-23-generic" "2.6.24-24-generic" 
 Do i need to go about rebuilding the drivers for current kernal. ( have nooo Idea how to if i do.

Thanks

---

### Post by guillermolisi on 2009-10-03
> **Purple8 said:**
> Hi 
I have just purchased the above card. The driver disk doesn't seem to work it says; 3DSP drivers does not support Linux 2.6.28-14-generic version now!!! 

the read me states 
Kernel Supportable
==================
ubuntu8.04 "2.6.24-16-generic" "2.6.24-19-generic" "2.6.24-23-generic" "2.6.24-24-generic" 
 Do i need to go about rebuilding the drivers for current kernal. ( have nooo Idea how to if i do.

Thanks
Purple8

You must edit the installer script, INSTALL_3DSP.sh, and modify this line (in red colour):
```

case "${CURRENTKERNEL}" in
    [COLOR=Red]"2.6.28-11-generic" | "2.6.28-13-generic" | "2.6.28-14-generic" | "2.6.28-15-generic"[/COLOR])
      ${PRINTOK};;
    *                                        )
      ${PRINTFAIL}
      handle_error "NOTSUPPORTKERNEL";;
esac

```
As you can see, the code block I pasted is already modified to work fine with the 2.6.28-14-generic kernel.

Give a try and tell us how it goes.

---

### Post by Purple8 on 2009-10-04
Nope didnt work when booting in the WB thing fails. If you try too run it says please install drivers correctly.

---

### Post by guillermolisi on 2009-10-04
> **Purple8 said:**
> Nope didnt work when booting in the WB thing fails. If you try too run it says please install drivers correctly.
Oh, I'm sorry, I don't saw you are using 2.6.24-24-generic kernel.

In this case, try modifying the script in this way:
```
case "${CURRENTKERNEL}" in
    [COLOR=Blue]"2.6.24-24-generic"[/COLOR] | "2.6.28-11-generic" | "2.6.28-13-generic" | "2.6.28-14-generic" | "2.6.28-15-generic")
      ${PRINTOK};;
    *                                        )
      ${PRINTFAIL}
      handle_error "NOTSUPPORTKERNEL";;
esac
```This driver was built for 2.6.28-11 and next versions of kernel.

The script installs two applications, one for WiFi and one for Bluetooth conections.

The WiFi utiliy has two components: One for WiFi antenna activation (on/off software switch) and other for WiFi radar.

Did you think to upgrade to JJ from HH ?

---

### Post by Purple8 on 2009-10-06
Hi Iam on JJ. the drivers appear to install okay. But when i try and run the wb manager it says to install the drivers correctly. Is there a way i can test to see if it is found correctly by ubuntu.
Thanks

---

### Post by guillermolisi on 2009-10-06
> **Purple8 said:**
> Hi Iam on JJ. the drivers appear to install okay. But when i try and run the wb manager it says to install the drivers correctly. Is there a way i can test to see if it is found correctly by ubuntu.
Thanks
[SIZE=2]From where you have picked up this driver ?

The one I am using was built for kernel 2.6.28-11 (or superior, at least for 2.6.28-15 for shure) and the china vendor sent me by e-mail. If you wish, I can send it via PM (or any other way) to you (2.2Mb in tar.gz format)

I guess you are using an older version.

Anyway, the installation procedure must be (just for your revision):[/SIZE]

```
$ sudo chmod +x INSTALL_3DSP.sh
```[SIZE=4]
[SIZE=2]Then, execute it[/SIZE]
[/SIZE]```
$ sudo bash INSTALL_3DSP.sh
```[SIZE=4]
[SIZE=2]You may deactivate the Network Manager to avoid conflicts[/SIZE][/SIZE][SIZE=2] with the WB module[/SIZE].

The website of the vendor is [http://www.3dsp.com.cn/web_html/download.html](http://www.3dsp.com.cn/web_html/download.html) (note the .cn)

---

### Post by Purple8 on 2009-10-08
when i first made the thread i had old drivers. I have since got new ones. still dont work.
i have the pci e adapter.
Is there a way i can check if linux can see it. in case i have a broken adapter

---

### Post by guillermolisi on 2009-10-08
> **Purple8 said:**
> when i first made the thread i had old drivers. I have since got new ones. still dont work.
i have the pci e adapter.
Is there a way i can check if linux can see it. in case i have a broken adapter
First, you can run the "lspci" command in the terminal/console and paste the output here.

Other command to verify how Ubuntu recognize your hardware is "lhsw". It should run with sudo.

Run these commands with the 3DSP adapter plugged in.

---

### Post by Purple8 on 2009-10-10
xbmc@Media:~$ sudo lspci
[sudo] password for xbmc: 
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:16.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:17.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:18.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation Device 087d (rev b1)
xbmc@Media:~$ 
xbmc@Media:~$

---

### Post by guillermolisi on 2009-10-10
Could you post the output of the command "lsusb" ? Thanks !

---

### Post by Purple8 on 2009-10-11
Bus 002 Device 003: ID 05e1:0100 Syntek Semiconductor Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

by the looks of those i guess it is not being found

---

### Post by guillermolisi on 2009-10-11
> **Purple8 said:**
> Bus 002 Device 003: ID 05e1:0100 Syntek Semiconductor Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

by the looks of those i guess it is not being found
Have you 3DSP card plugged in when you run "lsusb" ?

I see a Syntek chipset webcam and a MS optical USB mouse but no network adapter at all.

---

### Post by Purple8 on 2009-10-11
yeah deefo plugged in. its  a pcie card.

---

### Post by guillermolisi on 2009-10-11
It's a pci-e card but it's not showing in the "lspci" output. Very weird.
Have you tried it in other PC, even with another OS, to confirm the card is Ok ?

---

### Post by Purple8 on 2009-10-14
defo the card. wouldn't recognize in my laptop either.
Cheers for all your help

---

### Post by ruisu on 2009-11-03
actualy, the 05e1:0100 is the wifi/bt card, you can see that in the page of the linux drivers: 

[http://translate.google.com/translate?hl=es&sl=zh-CN&tl=en&u=http%3A%2F%2F3dsp.com.cn%2Fweb_html%2Fdownload.html](http://translate.google.com/translate?hl=es&sl=zh-CN&tl=en&u=http%3A%2F%2F3dsp.com.cn%2Fweb_html%2Fdownload.html)

the first link is of STK, Syntek :O but their drivers arent free :S they are closed and they only have for a little bit old kernels.

---

### Post by jim80b on 2009-12-17
success!

we know its a pcie card... problem is it thinks its a usb one.

download the usb minicard drivers, unpack it.
i had to edit the kernal number in the install shell script to match my kernal (the .17-generic) and also renamed the kernal dir in drivers to match

install

reboot

icon appears, (three green bars)
click co-exist

BT icon appears
click it and it asks you to enable it.
it works (paired with mouse and working)

to use the wifi you need to use the scanner app, not network manager (will try this tonight)


next steps
1. need to work out how to make card default to co-exist not unplugged
2. need to make bt default to on

---

### Post by guillermolisi on 2009-12-17
> **ruisu said:**
> actualy, the 05e1:0100 is the wifi/bt card, you can see that in the page of the linux drivers: 

[http://translate.google.com/translate?hl=es&sl=zh-CN&tl=en&u=http%3A%2F%2F3dsp.com.cn%2Fweb_html%2Fdownload.html](http://translate.google.com/translate?hl=es&sl=zh-CN&tl=en&u=http%3A%2F%2F3dsp.com.cn%2Fweb_html%2Fdownload.html)

the first link is of STK, Syntek :O but their drivers arent free :S they are closed and they only have for a little bit old kernels.
Here, in Argentina, a folk had written to Syntek asking for open source drivers for the 3dsp hardware:
> Dear Sir,
 I am writing in the name of the Linux and Free Software´s comunity to ask if you could send me the SOURCE CODES which are important to the hardware´s drivers which is maked by yourself,of course, if the licence which protect them let it.
 The SOURCE CODES are very important to have the different types of distributions which are based in the FREE SOFTWARE of the drivers for each operative sistem´s version. In this way, the support of the instalations of these distributions are going to be more easily and they can safe the compatibility of them in the future.
 Also, I want to said I am very greatfull for your support to UBUNTU.
 I look forward to hearing from you soon,

Leer más:  [http://www.laconsolablog.com/2009/08/28/3dsp-sources/#ixzz0ZxfBPFN2](http://www.laconsolablog.com/2009/08/28/3dsp-sources/#ixzz0ZxfBPFN2) 
Under Creative Commons License: [Attribution Share Alike]("http://creativecommons.org/licenses/by-sa/3.0")

Someone from Syntek answered:
> Hi,
 Thanks a lot for you using our products. We would like to provide source code to you! but it will be very hard to maintain and support due to its complicacy. and I believe the day we open source code will come soon.
 Best wishes,
-----------------------------
&#32654;&#22269;3dsp&#20844;&#21496;&#35199;&#23433;&#20195;&#34920;&#22788;
&#20826;&#26144;&#21326; Debbie Dang
TEL&#65306;029-88454368-803
Mobile&#65306;13572590690
-----------------------------

Leer más:  [http://www.laconsolablog.com/2009/08/28/3dsp-sources/#ixzz0Zxh2n1NB](http://www.laconsolablog.com/2009/08/28/3dsp-sources/#ixzz0Zxh2n1NB) 
Under Creative Commons License: [Attribution Share Alike]("http://creativecommons.org/licenses/by-sa/3.0")

Few days after, Syntek released new drivers for kernel 2.6.31 in [http://3dsp.com.cn/web_html/download.html](http://3dsp.com.cn/web_html/download.html)

---

### Post by doobiest on 2009-12-28
sorry, can you confirm does this card work on ubuntu? and if so is there much effort on 9.10

I just got an hp mini, and I'm going to toss the half-sized minipci wifi card it came with and throw in a regular minipci wifi/bluetooth. Seems the card you're talking about is the only combo card I can find on ebay at a decent price.

Thanks.


p.s. if anyone knows of a >>halfsized<< wifi/bluetooth card that doesnt cost a lot let me know.

---

### Post by guillermolisi on 2009-12-29
> **doobiest said:**
> sorry, can you confirm does this card work on ubuntu? and if so is there much effort on 9.10

I just got an hp mini, and I'm going to toss the half-sized minipci wifi card it came with and throw in a regular minipci wifi/bluetooth. Seems the card you're talking about is the only combo card I can find on ebay at a decent price.

Thanks.


p.s. if anyone knows of a >>halfsized<< wifi/bluetooth card that doesnt cost a lot let me know.
My wife and my brother have the same netbook model with Clevo motherboards, internal wifi 3dsp Syntek PCI hardware and JJ up to date and they do not have any problems.

My next step is to test the new driver for KK.

---

### Post by jim80b on 2010-01-18
futher update 
been having issues when using the wireless...
(i have an acer aspire one which i have swapped out the wifi card to the 3dsp mini pci one)


since installing the drivers (see previous post)
i have been having lock ups (kernal panic - flashing caps key)
have now done a full reinstall and have same issue.

i have ubuntu running on an external hdd, with win as primary os. 
win is fine...

when wired ubuntu had been stable. when NOT connected to any wifi point, its been up for at least an hour, when i connect it fails in minutes.

will check logs later

---

### Post by jim80b on 2010-01-19
its got even weirder...

karmic
2.6.31-17

on a 11b network. fine and stable...
try on my 11g (54) it connects... works then i get the kernal panic

last messages are the 3dsp driver trying to sync at higher speeds.
seems to get to 60, then trys 6c and fails
how confused am i...
6c is 108 in dec... but 60 is 96 so am really confused...


is there any way to make this stop at 0x36 (54)....


AND
2.6.31-18 doesnt work at all

---

### Post by zehdamoto on 2010-01-25
I had this message when I tried to install.

```

jose@ZehDaMoto:~/Downloads/BlueW-2310X_2.3.0_091211_ubuntu9.10_withhotkey$ sudo bash Install_3DSP.sh 
 *
 * Checking user...                    [ Ok ]
 * Verifying kernel...                    [ Ok ]
 * Checking files...                    [ Ok ]
 * Installing modules...                [ Ok ]
 * Creating boot script...                [ Ok ]
 * Installing utilities...                [ Ok ]
 * Installing 3dsp-wifi-radar...            [ Ok ]
 * Installing Blueman-manager...
                            [ Ok ]
 * Loading modules...insmod: error inserting '/usr/local/3DSP/pci/3dspbus.ko': -1 Invalid module format
insmod: error inserting '/usr/local/3DSP/pci/3dspbtpriv.ko': -1 Invalid module format
insmod: error inserting '/usr/local/3DSP/pci/3dspbt.ko': -1 Invalid module format
insmod: error inserting '/usr/local/3DSP/pci/3dspwlanpriv.ko': -1 Invalid module format
insmod: error inserting '/usr/local/3DSP/pci/3dspwlan.ko': -1 Invalid module format
mknod: missing operand after `0'
Try `mknod --help' for more information.
Installation completed. Exit.
Please restart your computer to use 3DSP card.
Startup 3DSP card throuth Applications->Accessories->3DSP WB.
Thanks for using 3DSP card. Have a good day!

```

and this message when rebooted my machine.

```

WB Notice
FAIL!
Please check 3DSP Card and its drivers

```

What do I have to do with the Install_3DSP.sh to correct that error? ```
 mknod: missing operand after `0' 
```

---

### Post by zehdamoto on 2010-01-25
I have this web-site telling me that I probably have differences on the gcc version from my drivers with my Ubuntu distro, but what should I need to do?

[http://www.nvnews.net/vbulletin/showthread.php?t=77907](http://www.nvnews.net/vbulletin/showthread.php?t=77907)
```

"...The compiler used to compile the kernel (gcc 4.0) does not exactly match the
current compiler (gcc 4.1). The Linux 2.6 kernel module loader rejects kernel modules built with a version of gcc that does not exactly match that of the compiler used to build the running kernel..."

"...nvidia: version magic '2.6.16-2-686 686 gcc-4.1' should be '2.6.16-2-686 686
 gcc-4.0'..."

Try getting a newer gcc for your distro, or simply install a precompiled version of the driver.

```

---

### Post by bernt_ on 2010-02-19
Has anyone get the source code from 3dsp?
Because, when I try to connect to the web site, I get:

The connection has timed out
The server at [www.3dsp.com.cn](www.3dsp.com.cn) is taking too long to respond.

So no source code, no binary code :-(

---

### Post by guillermolisi on 2010-02-19
> **doobiest said:**
> sorry, can you confirm does this card work on ubuntu? and if so is there much effort on 9.10

I just got an hp mini, and I'm going to toss the half-sized minipci wifi card it came with and throw in a regular minipci wifi/bluetooth. Seems the card you're talking about is the only combo card I can find on ebay at a decent price.

Thanks.


p.s. if anyone knows of a >>halfsized<< wifi/bluetooth card that doesnt cost a lot let me know.
I can confirm the miniPCI drivers from Syntek (3DSP) works fine with 9.10 2.6.31-19 kernel.
I've tested in LiveCD mode (using a USB pendrive as hard disk on a netbook) and then upgrading from 9.04 to 9.10. Works fine, as I said.

Edit: If you have a miniPCI 3DSP card try the drivers from [here]("http://dl.dropbox.com/u/737884/BlueW-2310X_2.3.0_091211_ubuntu9.10_MiniPCI_2.6.31-16.tar.gz") (the same link from I've downloaded it).

If the netbook has miniPCIe card, download from [here]("http://dl.dropbox.com/u/737884/BlueW-2310X_2.3.0_091211_ubuntu9.10_withhotkey_2.6.31-16.tar.gz").
If it is USB card, from [here]("http://dl.dropbox.com/u/737884/bluewu2.3.0.04.20091106_ubuntu9.10_withhotkey_USB_32Bits.tar.gz") and if it is USB dongle from [here]("http://dl.dropbox.com/u/737884/bluewu2.3.0.04.20091106_ubuntu9.10_withouthotkey_USBDongle_32Bits.tar.gz").

All of them for 32 bits.

---

### Post by doobiest on 2010-02-23
> **guillermolisi said:**
> My wife and my brother have the same netbook model with Clevo motherboards, internal wifi 3dsp Syntek PCI hardware and JJ up to date and they do not have any problems.

My next step is to test the new driver for KK.

Hi, Are you certain they did it on an HP Mini?  Did they have to hack the bios?

When I plug my card into the 3nd mini pci slot of the hp mini the bios halts saying its an invalid card. According to google you need to open the bios in a hex editor and change from values around. Did you do that?

Thanks,

---

### Post by guillermolisi on 2010-02-24
> **doobiest said:**
> Hi, Are you certain they did it on an HP Mini?  Did they have to hack the bios?

When I plug my card into the 3nd mini pci slot of the hp mini the bios halts saying its an invalid card. According to google you need to open the bios in a hex editor and change from values around. Did you do that?

Thanks,
No, I'm not certain about this miniPCI card and HP Mini hardware. I have a successful experience on Clevo motherboard in netbooks, not with HP Mini.

I did not because the Syntek 3DSP miniPCI card runs without any BIOS problems. I do not remember just now the BIOS version & revision but it's a Phoenix BIOS for netbooks (Atom processors).

---

### Post by daddyd on 2010-03-23
I have this card in a toshiba a105 and i can get the drivers to install but the card will not work. I lsusb and the symtech chip is there. although it is a pci card??? Also I don't get the led on the edge of the laptop when i turn the wifi switch to on. Any ideas? Oh, the wifi that was originally in there worked in 8.04 but I never tried the 3dsp card in 8.04.

---

### Post by guillermolisi on 2010-03-24
> **daddyd said:**
> I have this card in a toshiba a105 and i can get the drivers to install but the card will not work. I lsusb and the symtech chip is there. although it is a pci card??? Also I don't get the led on the edge of the laptop when i turn the wifi switch to on. Any ideas? Oh, the wifi that was originally in there worked in 8.04 but I never tried the 3dsp card in 8.04.
Show to us the output from "lsusb" and "lspci" (without inverted commas) to determine what kind of card it is, please.

---

### Post by daddyd on 2010-03-25
okay here is lspci, lsusb and lshw output
```

david@david-laptop-toshiba:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
david@david-laptop-toshiba:~$ lsusb
Bus 001 Device 002: ID 05e1:0100 Syntek Semiconductor Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
david@david-laptop-toshiba:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:09:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:95:3b:ce
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:b5:44:a7:f4:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: twifiu0
       serial: 00:21:c5:10:d8:89
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```the syntek card is the 3dsp wifi/bt combo card. As it shows up as usb I installed usb drivers. I tried the pci drivers but got errors and problems. As you can see the twifiu0 interface is shown in lshw but no driver is associated with it.

---

### Post by daddyd on 2010-03-25
I'm running JJ right now BTW

---

### Post by likedbuttonorder on 2010-04-13
3DSP has released drivers!
I have posted them on launchpad

[https://answers.edge.launchpad.net/u...question/78047](https://answers.edge.launchpad.net/u...question/78047)

I can't do anything with them! But I hope someone can one day plug these into the Kernel.

(Yes, I'm letting people know about this, so i'm posting this message on every 3dsp related topic...!)

---

### Post by yannis on 2010-04-26
> **daddyd said:**
> okay here is lspci, lsusb and lshw output
```

david@david-laptop-toshiba:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:04.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
david@david-laptop-toshiba:~$ lsusb
Bus 001 Device 002: ID 05e1:0100 Syntek Semiconductor Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
david@david-laptop-toshiba:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:09:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:95:3b:ce
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=10MB/s
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 86:b5:44:a7:f4:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  ]the syntek card is the 3dsp wifi/bt combo card. As it shows up as usb I installed usb drivers. I tried the pci drivers but got errors and problems. As you can see the twifiu0 interface is shown in lshw but no driver is associated with it.

I have a netbook(Turbo-X) with preinstalled dual boot (XP+Ubuntu 9.04)
I also tried first the lspci and lsusb commands.
the syntek card was shown in usb. so i decided to go for the usb driver(that was logical in xp i have bluew2310**U**).

The driver was for Ubuntu 9.10 and 2.6.31 kernel so i upgraded to 9.10

I now have the Bluetooth O.K. and working but the wifi:( no!

The lshw shows
[CODE]*-network:1 **DISABLED**
       description: Ethernet interface
       physical id: 1
       logical name: twifiu0
       serial: 00:21:c5:10:d8:89
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

the rfkill list
```
Bluetooth
Software block:no
Hardware block:no
```

i'm concerned about the keyboard combination the enables the Wifi in XP but in Ubuntu is innopperative

also the iwconfig shows the twifiu0

any ideas?

---

### Post by emmir on 2010-04-30
On the same netbook (Turbo-X mininote II), only with UNR 9.10 installed, only thing I had to do was to download the drivers from here: [ftp://3dsp.com.cn/Ubuntu/BlueW-2310U_2.3.3_100303_Ubuntu9.10_withhotkey.tar.gz](ftp://3dsp.com.cn/Ubuntu/BlueW-2310U_2.3.3_100303_Ubuntu9.10_withhotkey.tar.gz) and follow included instructions.

Works like a charm!!! There's a catch though: It does not support Kernel 2.6.31-21, so you either have to wait until it does, or don't do any Kernel upgrades until then..... 

Good luck....

---

### Post by ruisu on 2010-05-02
Hi, just dropping in by to let you know that there is a petition and 3dsp should already be aware of this:
[www.petitiononline.com/3dsp/petition.html]("www.petitiononline.com/3dsp/petition.html")

---

### Post by likedbuttonorder on 2010-05-18
> **yannis said:**
> I have a netbook(Turbo-X) with preinstalled dual boot (XP+Ubuntu 9.04)
I also tried first the lspci and lsusb commands.
the syntek card was shown in usb. so i decided to go for the usb driver(that was logical in xp i have bluew2310**U**).

The driver was for Ubuntu 9.10 and 2.6.31 kernel so i upgraded to 9.10

I now have the Bluetooth O.K. and working but the wifi:( no!

The lshw shows
```
*-network:1 **DISABLED**
       description: Ethernet interface
       physical id: 1
       logical name: twifiu0
       serial: 00:21:c5:10:d8:89
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

the rfkill list
```
Bluetooth
Software block:no
Hardware block:no
```

i'm concerned about the keyboard combination the enables the Wifi in XP but in Ubuntu is innopperative

also the iwconfig shows the twifiu0

any ideas?
Hi, sorry that it took me so long to answer, I've only just noticed.
I see you "upgraded", sadly that is often a bit of a mess...
Try doing a fresh install of 9.10, and then install the drivers.
It should work with no problems, I've done it tens of times now!!!

---

### Post by likedbuttonorder on 2010-05-18
The other way of doing this is installing the 2.6.31-14 kernel in 10.04.

1) Fresh Install of 10.04

2) Get [http://mirror.globo.com/ubuntu/archive/pool/main/l/linux/linux-image-2.6.31-14-generic_2.6.31-14.48_i386.deb](http://mirror.globo.com/ubuntu/archive/pool/main/l/linux/linux-image-2.6.31-14-generic_2.6.31-14.48_i386.deb)
(via a wired connection or by having it on another drive!)

3)Install the package

4)Reboot, install the drivers

Cd to the folder and then 
```
sudo bash Install_3DSP.sh
```

(If it takes veeeery long just close the terminal and try again)

5) Enjoy!

---

### Post by macrules on 2010-10-01
> **likedbuttonorder said:**
> The other way of doing this is installing the 2.6.31-14 kernel in 10.04.

1) Fresh Install of 10.04

2) Get [http://mirror.globo.com/ubuntu/archive/pool/main/l/linux/linux-image-2.6.31-14-generic_2.6.31-14.48_i386.deb](http://mirror.globo.com/ubuntu/archive/pool/main/l/linux/linux-image-2.6.31-14-generic_2.6.31-14.48_i386.deb)
(via a wired connection or by having it on another drive!)

3)Install the package

4)Reboot, install the drivers

Cd to the folder and then 
```
sudo bash Install_3DSP.sh
```(If it takes veeeery long just close the terminal and try again)

5) Enjoy!


Did anyone get the source already?
That launchpad link was dead.
The installer has nothing for the 2.6.35 kernel in Maverick.
Has anyone got it working?

I use that kernel in 10.04 because of the multitouch patches.

---

### Post by macrules on 2010-10-01
> **likedbuttonorder said:**
> The other way of doing this is installing the 2.6.31-14 kernel in 10.04.

1) Fresh Install of 10.04

2) Get [http://mirror.globo.com/ubuntu/archive/pool/main/l/linux/linux-image-2.6.31-14-generic_2.6.31-14.48_i386.deb](http://mirror.globo.com/ubuntu/archive/pool/main/l/linux/linux-image-2.6.31-14-generic_2.6.31-14.48_i386.deb)
(via a wired connection or by having it on another drive!)

3)Install the package

4)Reboot, install the drivers

Cd to the folder and then 
```
sudo bash Install_3DSP.sh
```(If it takes veeeery long just close the terminal and try again)

5) Enjoy!

I got it working on the Maverick Meerkat kernel too now (2.6.35-22).
This is how:

1. get the source  [ftp://3dsp_lpkt_usb:m4rt9s@3dsp.com.cn/Open%20Source%20Code/Sectional%20Open%20source%20code/BlueW-2310U_3.0.4_100820.tar.gz]("ftp://3dsp_lpkt_usb:m4rt9s@3dsp.com.cn/Open%20Source%20Code/Sectional%20Open%20source%20code/BlueW-2310U_3.0.4_100820.tar.gz")

and unpack it.

 If you blindly install, you will find errors in the logfile.
Compilation fails because of 'kfree' not found and after that some 'type' that fails.
I fixed it like this:

2. go to the directory you unpacked the source and goto sub dir: driver_src/new_bluetooth
3. now in there, open tdsp_bus.c and add this after the last include line:
#include <linux/slab.h>
Do the same for that file in the driver_src/wlan (not sure if needed but i already did it)
4. then in the new_bluetooth dir find this file:
lbluetooth_entry
Edit line 556 by commenting it out, so it becomes :
    //hdev->type = HCI_USB;
With this on it does not compile.
Please know that I have no clue what this does, and I do not care now, because it works. Remember this if you get other trouble and don't blame me :).
5. run the installscript from the directory like described in the README:
sudo bash Install_3DSPUSB.sh

That did it for me.
I write this from the wireless connection of the device and I succesfully send a file by bluetooth to my HTC Desire.

The BlueW tool must be set to Coexist, which will enable both WLAN and bluetooth.
After that you can switch bluetooth.
From the software:

3DSP BlueW-2310UU 
Release 3.0.4.100820

Hopefully they will release the full source so we will have network-manager integration and less trouble getting it to compile.

Does anyone know how to put this in DKMS?
:guitar:

---

### Post by macrules on 2010-10-01
I signed the partition and mailed them a request for the full source so it can be integrated into the kernel.
Lets hope we do not have to do this hacking in the future and Ubuntu will be even better !

Sign the parttion:
[http://www.petitiononline.com/3dsp/](http://www.petitiononline.com/3dsp/)

Request the source:
[http://translate.google.com/translate?hl=es&sl=zh-CN&tl=en&u=http%3A%2F%2F3dsp.com.cn%2Fweb_html%2Fdownload.html](http://translate.google.com/translate?hl=es&sl=zh-CN&tl=en&u=http%3A%2F%2F3dsp.com.cn%2Fweb_html%2Fdownload.html)

You will need to fill in the form which can be found on their FTP.

Go community!:P

---

### Post by aku-aku on 2010-11-01
> **macrules said:**
> I got it working on the Maverick Meerkat kernel too now (2.6.35-22).
This is how:

Thanks for these instructions - they were a great help.  I've got wireless and bluetooth connections working.  I'll leave aside the NetworkManager stuff for now, but I'm getting problems with the connection to my bluetooth mouse.  It'll lose the connection after a while, and there are thousands of the following line in /var/log/messages:

```
Task_CreateDelayTask: Task_CreateDelayTask()--get task block from pool fails, alloc it directly, eventCode = 0x6000c
```which appears in some of the private binary code that 3DSP haven't released.  I also get a lot of messages about "Sending LMP - not enough space".

On a hopefully simpler note, NetworkManager's auto-configuration of DNS and the default route interfere with the wireless connection.  Any ideas?

Edited to add: Having investigated what's going on with NetworkManager, it's warning the following in the log:
```
NetworkManager: <WARN>  device_creator(): /sys/devices/virtual/net/twifiu0: couldn't determine device driver; ignoring...
```...and again.  I've managed to get NetworkManager recognising the card by adding a call to SET_NETDEV_DEV in lwlan_netdev.c just before it calls register_netdev.  Unfortunately the 3DSP code isn't that great (and some of it is private), and I'm not a C programmer, so this solution is somewhat inelegant; the 3DSP code spews masses of log output into kern.log and /var/log/messages.  Also, I haven't got it working completely with WPA yet: it takes an age to negotiate the connection; there's something weird with the signal strength too, where it'll alternate between reporting full signal and zero.  I don't seem to lose the connection though.

If anyone's interested in getting this working properly, please shout on this thread - I feel like I've nearly got a solution...

---

### Post by aku-aku on 2010-11-07
Turns out that the 3dsp card doesn't properly support scanning for networks, which has an effect on how NetworkManager deals with connecting to hidden SSIDs.  The code that handles scanning is in the private code so I can't add support for it.  Basically, you can't expect it to connect properly to a hidden network when using NetworkManager.  However, I seem to have a decent WPA connection.

Because scanning doesn't work properly, you won't get signal strength reported properly in NetworkManager - but you can connect, it works, and you don't need the wifi-radar.

Still, the level of logging in the code is just ridiculous.  The bus code has a mechanism to turn off debug-level logging, but the WLAN code all gets dumped out using printk.  Once I've done that I'll get a patch on here if anyone's interested.

---

### Post by del_Brujo on 2010-11-10
> **aku-aku said:**
> Once I've done that I'll get a patch on here if anyone's interested.

Yes, I'm interested.

---

### Post by aku-aku on 2010-11-10
> **del_Brujo said:**
> Yes, I'm interested.

OK - please grab the attached patch file, and apply it by running:
```
patch -u -p1 -i aku-aku.patch.txt
```in the BlueW-2310U directory.  Note: you should apply the changes at [http://ubuntuforums.org/showpost.php?p=9912936&postcount=40](http://ubuntuforums.org/showpost.php?p=9912936&postcount=40) first.

**What this patch does**
- Enables support for configuring of this card in NetworkManager
- Suppresses the verbose log messages, but keeps most one-off and serious log messages
- Initialises the card in the /etc/init.d script, so you don't need the uWB tool starting up when the desktop loads (For PCI-E devices only!  Users of USB cards will not want the change to the "tdspusbcardinit" file).  

**Known issues**
- No support for hidden networks.
- Signal strength isn't reported by NetworkManager.  The icon will alternate between showing full and no signal.  Operation of the connection is unaffected.
- You may get "Failed to initiate AP scan" messages coming out of NetworkManager in /var/log/daemon.log.  Apparently you can patch NetworkManager so it doesn't scan so frequently.
- I haven't touched the Bluetooth section.  I find my Bluetooth mouse periodically cuts out, then comes back of its own accord.

I'll do my best to answer any questions relating to this patch, but you use it at your own risk.  Good luck!

---

### Post by macrules on 2010-11-14
mmm, dunno if i missed something, but I cannot use network manager for wireless after the patch.
I simply have no wireless card to operate.
It does work with the 3DSP tools

---

### Post by aku-aku on 2010-11-14
> **macrules said:**
> mmm, dunno if i missed something, but I cannot use network manager for wireless after the patch.
I simply have no wireless card to operate.
It does work with the 3DSP tools

NetworkManager will only pick up the card if the device has had its physical address set - this is what the SET_NETDEV_DEV lines in the patch do.  If you could try stopping and restarting the network-manager service, and paste the part of /var/log/daemon.log, I can try to help.  Also, can you confirm the card appears when you run lsusb?  I don't know if there are different cards running against the same chip, but my PCI-E card appears as a USB device.  At least if the patched version works with the 3DSP tools, the card's still working with the patched code...

---

### Post by Vovaldo on 2010-11-15
[http://forum.ubuntu.ru/index.php?topic=108129.msg883894#msg883894](http://forum.ubuntu.ru/index.php?topic=108129.msg883894#msg883894)

---

### Post by Emblema on 2010-11-20
Hi people,

After reading so much, I realized that this ticket was not really a good buy, but let's get to work, I installed this on a PCI Express mini PC with Geode processor, in other words those who are used to make the router or Serverin household with low consumption.
After having tried several 'times to install the drivers for pci-express I had a doubt, I identify with the command lsusb, so I tried to install on ubuntu 10.04 usb driver for this is the result:

```

[   24.069739] **************                                *******************
[   24.069758] **************        3DSP BUS Driver         *******************
[   24.069776] **************                                *******************
[   24.069792]
[   24.069803] tdspbus_init_module() enter!
[   24.069818] 3DSP USB Bus Driver   Build 12:06:24, Aug 23 2010
[   24.069833]    Version : BusU090716
[   24.069845]
[   24.069869] tdspbus_init_module() exit,ret=0!
[   24.122361] 3dspusbwlanpriv: module license 'Proprietary' taints kernel.
[   24.122384] Disabling lock debugging due to kernel taint
[   24.358379] Enter [_wlan_usb_probe]
[   24.358403] 3dsp usb wlan device found:) intf 0, alt configs 1, endpoints 5
[   24.358425] ep addr 1, type 2, in/out  IN
[   24.358441] ep addr 2, type 2, in/out OUT
[   24.358457] ep addr 3, type 2, in/out  IN
[   24.358473] ep addr 4, type 2, in/out OUT
[   24.358490] ep addr 9, type 3, in/out  IN
[   24.358506] tdsp_spin_lock_init is d0a563e0,syscall's is d0a563e0
[   24.358770] sc is d0a5bae0
[   24.358784] usb_info is cdb95e0f
[   24.358801] 3D[T:WMAIN:01069][Adap_Create]  dsp Initialize start...!
[   24.358825] 3D[T:WMAIN:01075]Adap_Create usbinfo is cdb95e0f,EP_control is 0,EP_bulkout_HEAD is 4!
[   24.365094] WLAN: Bus_new_interface:  dev = cdb76000, intf = cf927700;
[   24.365126] WLAN: Bus_openInterface:  enter;
[   24.365149] register_tdspbus_usbdev be called,SerialNo = 2,version=WLU100811!
[   24.365161]
[   24.365181] Exit register_tdspbus_usbdev with success, SerialNo = 2!state_old_from_wb = 0, devstate = 0 ParaFlag = 0
[   24.365197]
[   24.365210] Leave [_wlan_usb_probe]
[   24.365272] Enter [_wlan_usb_probe]
[   24.365287] intf 1 is not 3dsp wlan interface
[   24.365425] usbcore: registered new interface driver 3DSP_WLAN_USB
[   24.741637] _bluetooth_usb_probe: ep addr 5, type 2, in/out  IN
[   24.741660] _bluetooth_usb_probe: ep addr 6, type 2, in/out OUT
[   24.741680] _bluetooth_usb_probe: ep addr 7, type 2, in/out  IN
[   24.741700] _bluetooth_usb_probe: ep addr 8, type 2, in/out OUT
[   24.741720] _bluetooth_usb_probe: ep addr 10, type 3, in/out  IN
[   24.741739] _bluetooth_usb_probe: sc is d0dc89a0
[   24.741756] _bluetooth_usb_probe: usb_info is cd9ade04
[   24.741797] BLUETOOTH: Bus_new_interface:  enter, dev = cf930000, intf = cd9fc980;
[   24.741831] register_tdspbus_usbdev be called,SerialNo = 1,version=BTU100723!
[   24.741843]
[   24.741864] Exit register_tdspbus_usbdev with success, SerialNo = 1!state_old_from_wb = 0, devstate = 0 ParaFlag = 0
[   24.741881]
[   24.741998] usbcore: registered new interface driver 3DSP_BLUETOOTH_USB


```

so it seems that everything is looking good but looking with iwconfig tells me that there are no wifi devices.

On this server I do not have physical access with keyboard, mouse and screen, but I use ssh, I installed for testing and vnc4server fluxbox so I have no way to have graphics software, but I can use the shell.


Does anyone have any advice for me to make another small step forward?


Thanks You all

---

### Post by Emblema on 2010-11-22
Ok people, it's work, whit and whitout gnome.

locate uwbtool (/usr/bin)

whit command line:

[COLOR="Red"]uwbtool --download=combo[/COLOR]  

```
the devices you want to add:---combo

Start rfcomm/pand server......
sudo: pand: command not found
Add SDP services......
Serial Port service registered
call after system
^_^ add bluetooth&wlan success!

```

It's OK


for remove:

[COLOR="red"]uwbtool -r[/COLOR]


Device is removed!!


Work!!

Ubuntu 10.04

---

### Post by mowi on 2010-11-25
> **jim80b said:**
> ...
..
next steps
1. need to work out how to make card default to co-exist not unplugged
2. need to make bt default to on

Hi Jim, 
did you succeed with the next steps? That would be great! everytime I start 3dsp UWB so it changes to coexist it asks for my passw and blocks everything else. I cannot even use my virtual keyboard to enter the passw. This is very frustating because I have a tabletpc and I normally do  not have a normal keyboard. No way to get on wlan with this setup. When I made it past uwb with my external keyboard  I still need to start the radar and set firefox to work online again. I'am dreaming off a way to get the 3dsp card to go on the wlan totally automatically. 
anybody have an idea?

---

### Post by aku-aku on 2010-11-27
> **mowi said:**
> Hi Jim, 
did you succeed with the next steps? That would be great! everytime I start 3dsp UWB so it changes to coexist it asks for my passw and blocks everything else. I cannot even use my virtual keyboard to enter the passw. This is very frustating because I have a tabletpc and I normally do  not have a normal keyboard. No way to get on wlan with this setup. When I made it past uwb with my external keyboard  I still need to start the radar and set firefox to work online again. I'am dreaming off a way to get the 3dsp card to go on the wlan totally automatically. 
anybody have an idea?

Add the call to uwbtool in the post previous to yours into your /etc/init.d/tdspusbcardinit.  That way, it'll be executed as root so it won't need to ask for your password - and you won't need to start the UWB tool.

That fix is included in the patch I made.

---

### Post by bourlias7 on 2010-11-28
Hi i am new in ubuntu i have fresh install ubuntu 10.10 net-book (maverick)

I have net-book (turbo-x) with dual boot windows7 and the wifi with card 3dsp usb(the card is inserting as pci-e not usb but windows as usb driver.

at the windows is working WiFi and bloutooth with bluesoleil software IVT

for more help post icon for Bluetooth and report from everest home edition

i try to install with BlueW-2310U_3.0.4_100820

and sudo bash install 3dsp.sh it intall it but when run wifi radar in accessorize  no device detecting and can not detecting

can help me for to fix this?

and bluetooth can not  detecting he wired connection is ok

I have download all updates

and to add devises on hardware not found any devices


please help me I am new in Ubuntu but i known the dos and UNIX commands and little Linux servers but i have long time to working with it

I tried to fix if any idea

---

### Post by bourlias7 on 2010-11-28
i tried all method for install user [Emblema]("http://ubuntuforums.org/member.php?u=665860") and report please insert a 3dsp device

try and user [marules]("http://ubuntuforums.org/member.php?u=887844") but 3dsp wifi radar nothing no wireless card detecting after run

this report for lspci and lsusb and report for lswh

please help to try fix this if any idea to fix this

---

### Post by mikewhatever on 2010-11-28
> **macrules said:**
> I signed the partition and mailed them a request for the full source so it can be integrated into the kernel.
Lets hope we do not have to do this hacking in the future and Ubuntu will be even better !

Sign the parttion:
[http://www.petitiononline.com/3dsp/](http://www.petitiononline.com/3dsp/)

Request the source:
[http://translate.google.com/translate?hl=es&sl=zh-CN&tl=en&u=http%3A%2F%2F3dsp.com.cn%2Fweb_html%2Fdownload.html](http://translate.google.com/translate?hl=es&sl=zh-CN&tl=en&u=http%3A%2F%2F3dsp.com.cn%2Fweb_html%2Fdownload.html)

You will need to fill in the form which can be found on their FTP.

Go community!:P

Any replies yet?

---

### Post by bourlias7 on 2010-11-28
> **mikewhatever said:**
> Any replies yet?

i am not sure for replies but and my signature are 180 Signatures Total [FONT=Helvetica,Arial][SIZE=+6]
[/SIZE][/FONT]i am a 180 th! :D

hope me to a resolved problem for this card

is difficult to fix it the problem

---

### Post by mowi on 2010-11-28
> **bourlias7 said:**
> Hi i am new in ubuntu i have fresh install ubuntu 10.10 net-book (maverick)

I have net-book (turbo-x) with dual boot windows7 and the wifi with card 3dsp usb(the card is inserting as pci-e not usb but windows as usb driver.

at the windows is working WiFi and bloutooth with bluesoleil software IVT

for more help post icon for Bluetooth and report from everest home edition



Hi Bourlias,
I have exactly same setup you have. for me this worked:
[https://github.com/franciscosouza/3dsp](https://github.com/franciscosouza/3dsp)
l had to install aptitude and git  to get it done.
 wlan works now, I didn't try bluetooth yet

---

### Post by bourlias7 on 2010-11-28
> **mowi said:**
> Hi Bourlias,
I have exactly same setup you have. for me this worked:
[https://github.com/franciscosouza/3dsp](https://github.com/franciscosouza/3dsp)
l had to install aptitude and git  to get it done.
 wlan works now, I didn't try bluetooth yet

sudo aptitude install build-essential linux-headers-`uname -r`

the terminal[FONT=Verdana] in sudo:aptitude :unknown command 

why this? 

[FONT=monospace]First, please inform another  way to install to all dependencies[/FONT][/FONT]?

---

### Post by mikewhatever on 2010-11-28
> **bourlias7 said:**
> i am not sure for replies but and my signature are 180 Signatures Total [FONT=Helvetica,Arial][SIZE=+6]
[/SIZE][/FONT]i am a 180 th! :D

hope me to a resolved problem for this card

is difficult to fix it the problem

180 signatures in about two years. I don't think they are going to even sneeze at us because of that.

---

### Post by Vovaldo on 2010-11-29
> **bourlias7 said:**
> i am not sure for replies but and my signature are 180 Signatures Total [FONT=Helvetica,Arial][SIZE=+6]
[/SIZE][/FONT]i am a 180 th! :D

hope me to a resolved problem for this card

is difficult to fix it the problem
Did you install all required packets? (See file Readme.txt in drivers pack)
Unpack attached file to /BlueW-2310U_3.0.4_100820/driver_src/new_bluetooth  and try to run install script again.

---

### Post by bourlias7 on 2010-11-29
> **Vovaldo said:**
> Did you install all required packets? (See file Readme.txt in drivers pack)
Unpack attached file to /BlueW-2310U_3.0.4_100820/driver_src/new_bluetooth  and try to run install script again.

ok i tried and results soon....

any idea to install [FONT=Verdana][FONT=monospace] all dependencies?[/FONT][/FONT]

---

### Post by Vovaldo on 2010-11-29
> **bourlias7 said:**
> ok i tried and results soon....

any idea to install [FONT=Verdana][FONT=monospace] all dependencies?[/FONT][/FONT]

Which distribution of Linux are you using?

---

### Post by bourlias7 on 2010-11-29
> **Vovaldo said:**
> Which distribution of Linux are you using?

I have Ubuntu 10.10 Netbook Edition(maverick) with this kernel 2.6.35-23 generic 
for more info look               #[**53**]("http://ubuntuforums.org/showpost.php?p=10172645&postcount=53") post and              #[**54**]("http://ubuntuforums.org/showpost.php?p=10172806&postcount=54")

maybe i install but any idea to check this?

or idea to install  this if not installing?

btw the linux kerner if very fast the netbook like laptop  now :P 

off topic: open windows 10 minutes open linux less 1 minute

shut down windows 5  minutes shut down linux 20 sec!!!! :P

---

### Post by bourlias7 on 2010-11-29
after searging the google for this Bus 001 Device 004: ID 05e1:0100 Syntek Semiconductor Co., Ltd 
[http://tinyurl.com/2ufw55q](http://tinyurl.com/2ufw55q)
**1.USB dongle/USB miniCard (Bluew-2310u) WLAN and Bluetooth Combo Card** 
is comparative  3dsp dri ver but only support ubuntu 10.04


i tried to install some methods i installed but the wifi radar no wireless cadd o wireless card and 3wu tool not working

i think no way to fix this 


now can clean install ubuntu 10.04?
if try to install 10.04  the new version will formating automatically?

or formating ?

because i think nothing solutions in ubuntu 10.10

if any idea to work i tried absolute it if user you known it work

but it tired

---

### Post by Vovaldo on 2010-11-29
> **bourlias7 said:**
> 
i think no way to fix this 

I have Xubuntu 10.10 installed on my netbook. WiFi works.

> 
because i think nothing solutions in ubuntu 10.10


Place here file with .log extension from driver folder.

---

### Post by bourlias7 on 2010-11-30
> **Vovaldo said:**
> I have Xubuntu 10.10 installed on my netbook. WiFi works.



Place here file with .log extension from driver folder.

2 questions the ubunu 10.10 netbook same with xubuntu 10.10?

what command to log driver?(or how the driver foler?) i newbie in ubuntu i known commands but some items no known yin ubuntu os

maybe lswh?mean?

on post #[**54**]("http://ubuntuforums.org/showpost.php?p=10172806&postcount=54") the 3d zip it is?

---

### Post by Vovaldo on 2010-11-30
> **bourlias7 said:**
> 2 questions the ubunu 10.10 netbook same with xubuntu 10.10?
I think it must work properly.
Install build-essential and linux-headers-(kernel version) packets.

> 
what command to log driver?(or how the driver foler?) i newbie in ubuntu i known commands but some items no known yin ubuntu osI mean *.log file created by install script.

---

### Post by bourlias7 on 2010-11-30
> **Vovaldo said:**
> I think it must work properly.
Install build-essential and linux-headers-(kernel version) packets.

I mean *.log file created by install script.

i don't find the driver folde but all logs to can copy from all .logs for all logs and is down in archive rename.zip with .rar to extrack

i hope help you to help me :)

---

### Post by bourlias7 on 2010-11-30
> **guillermolisi said:**
> Have you 3DSP card plugged in when you run "lsusb" ?

I see a Syntek chipset webcam and a MS optical USB mouse but no network adapter at all.
[[COLOR=#339900]**guillermolisi the network adapet is here **[/COLOR]Bus 001 Device 004: ID 05e1:0100 Syntek Semiconductor Co., Ltd can help ?]("http://ubuntuforums.org/member.php?u=299461")

the netbooks clevo motherboards and look post [**54**]("http://ubuntuforums.org/showpost.php?p=10172806&postcount=54") and #[**53**]("http://ubuntuforums.org/showpost.php?p=10172645&postcount=53")

---

### Post by guillermolisi on 2010-11-30
Unless 3DSP manufacturers have released a driver for the kernel version 2.6.32.25 or later, those WiFi adapters will not work with 10.10 or 10.04.1 with kernels 2.6.32.25 or higher. I am currently using Ubuntu 10.04.1 up to date but still with kernel 2.6.32.24 (Syntek miniPCI adapter).

I have not tried the suggestions made here yet.

---

### Post by aku-aku on 2010-12-01
> **guillermolisi said:**
> Unless 3DSP manufacturers have released a driver for the kernel version 2.6.32.25 or later, those WiFi adapters will not work with 10.10 or 10.04.1 with kernels 2.6.32.25 or higher. I am currently using Ubuntu 10.04.1 up to date but still with kernel 2.6.32.24 (Syntek miniPCI adapter).

Building the driver from source does work - though when you update the kernel version you do have to rebuild the driver.

---

### Post by bourlias7 on 2010-12-02
hi to all the wifi now is working after modified the script(me patent) and two difereds ways at soon the solution for all because something wrong the kerner shell is missing now and if fixing the solution post here or another treat to all for solved at this card



I am happy to all share this patent to work usb dongle or usb wifi

please soon as posible


btw 3 days to fix the script!!! :P

---

### Post by teciman on 2011-01-07
Hi friends, 
3dsp.cn   released latest driver for us .
For example ; 


    [ftp://3dsp.com.cn]("ftp://3dsp.com.cn/")

    user: 3dsp_lpkt_pci

    passwd: fw1qa8

choice Ubuntu ...

---

### Post by Emblema on 2011-01-23
> **bourlias7 said:**
> i tried all method for install user [Emblema]("http://ubuntuforums.org/member.php?u=665860") and report please insert a 3dsp device

try and user [marules]("http://ubuntuforums.org/member.php?u=887844") but 3dsp wifi radar nothing no wireless card detecting after run

this report for lspci and lsusb and report for lswh

please help to try fix this if any idea to fix this

DSP WLAN&BT card
*****************
Copyright (c) 2003-2010, 3DSP Corporation, all rights reserved. 


Note: For compiling the drivers, the following components are required:
	[B]build-essential
	linux-headers-(kernel version)[/B]

---

### Post by Blackleker on 2011-02-21
Hello I have downloaded these modified drivers: [https://github.com/franciscosouza/3dsp/tree/master/driver_src/](https://github.com/franciscosouza/3dsp/tree/master/driver_src/) and I have been working  with ubuntu 10.10 32-bit and 64-bit when installing a new kernel may not  work and will have to uninstall the drivers have to reinstall I have  them running in 2.6.35-25-generic kernel and have worked me in all  previous versions of ubuntu 10.10 kernel more information here: [http://www.microsofttranslator.com/bv.aspx?ref=Internal&from=&to=en&a=http://bydemon007.blogspot.com/2010/10/ubuntu-ml-6200-3dsp-conexion-autamatica.html](http://www.microsofttranslator.com/bv.aspx?ref=Internal&from=&to=en&a=http://bydemon007.blogspot.com/2010/10/ubuntu-ml-6200-3dsp-conexion-autamatica.html)

---

### Post by pieterho on 2012-01-08
Is there a way to make this card work in ubuntu 11.10?

I tried the version for 10.10, but if I start the WIFI radar, nothing happens.

---

### Post by Blackleker on 2012-01-08
> **pieterho said:**
> Is there a way to make this card work in ubuntu 11.10?

I tried the version for 10.10, but if I start the WIFI radar, nothing happens.
[URL="https://github.com/reyiyo/3dsp/tarball/master"]
[/URL]For ubuntu 11.10 drivers that may work are these [https://github.com/reyiyo/3dsp/tarball/master](https://github.com/reyiyo/3dsp/tarball/master) now with the U 11.10, a problem arises with unity does not show the wifi-radar icon. I have not tried to solve this

---

### Post by pieterho on 2012-01-09
Ok thanks, but how can I connect to the wifi if there is no wifi-radar? Or is this not yet possible?

---

### Post by tuxmouraille on 2012-01-28
Hello,
Same question as pieterho.

---

### Post by Blackleker on 2012-02-20
> **pieterho said:**
> Ok thanks, but how can I connect to the wifi if there is no wifi-radar? Or is this not yet possible?

Yes is possible, these are the steps

1. go to Applications to startup applications preferences and delete **3dsp UwB** or disable.

The replacement of this tool is uwbtool that serves the same purpose of raising the interface but this is by commands.

To make up the interface uwbtool twifiu0 the start we have to edit the rc.local file open a terminal and do the command:
```
sudo gedit /etc/rc.local
```Before la linea "exit 0" put:
```
uwbtool --download=combo >/dev/null 2>&1
```So we have something like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

uwbtool --download=combo >/dev/null 2>&1
exit 0 
```

Ready every time you start the interface is started without running the graphical tool UWB.

2. Configuring the file wpa_supplicant.conf

Edit the configuration file /etc/wpa_supplicant/wpa_supplicant.conf:
```
sudo gedit /etc/wpa_supplicant/wpa_supplicant.conf

``````
ctrl_interface =/var/run/wpa_supplicant
     ctrl_interface_group = 0

     network = {
     ssid = "put your ssid"
     key_mgmt = WPA-PSK # (or WEP - according to the AP configurations)
     proto = WPA (or WPA2 # according to the AP configurations)
     pairwise = CCMP # (or TKIP settings according to the AP)
     group = CCMP # (or TKIP settings according to the AP)
     psk = "put your password"

```more info [https://wiki.archlinux.org/index.php/WPA_supplicant](https://wiki.archlinux.org/index.php/WPA_supplicant) a example:
```
ctrl_interface=/run/wpa_supplicant
ctrl_interface_group=network
update_config=1

network={
    ssid="Name of wifi"
    psk="pasword"
    proto=RSN
    key_mgmt=WPA-PSK
    pairwise=CCMP
    group=CCMP
}
```3. Now try to connect with the command:
```
sudo wpa_supplicant -Dwext -itwifiu0 -c/etc/wpa_supplicant/wpa_supplicant.conf
```

If not connected, try on another console the command:
```
sudo dhcpcd3 twifiu0
```

Perhaps with a gui for wpa_supplicant be easier or a tool such as netcfg.

Sorry for my bad english

Source: ```
http://bydemon007.blogspot.com//2010/10/ubuntu-ml-6200-3dsp-conexion-autamatica.html
```

[B][COLOR=#FFFFCC][/COLOR]

[COLOR=SpringGreen][/COLOR]
[COLOR=#FF4500][/COLOR]
[COLOR=#F7EF09][/COLOR]
[/B]

---

### Post by Alamot on 2013-04-30
I patched and compiled the 3dsp driver for Ubuntu 13.04. I tested it with network manager and it works fine! :D  You can find it here: [https://github.com/Alamot/3dsp](https://github.com/Alamot/3dsp)

Edit: [COLOR=#000000] I tested the USB adapter version in Ubuntu 13.04 (32bit) kernel 3.8.0.19-generic and the wifi works just fine with network manager. Bluetooth doesn't work.[/COLOR]

---

### Post by evandromr on 2013-05-02
Hi Alamot,

It didn't work for me. I'm attaching the logfile. If there is any other way that i can help to fix this, just tell me.

I'm using Ubuntu 13.04; kernel: 3.8.0-19-generic; 64bit


[ATTACH]242112[/ATTACH]

---

### Post by Blackleker on 2013-05-03
> **Alamot said:**
> I patched and compiled the 3dsp driver for Ubuntu 13.04. I tested it with network manager and it works fine! :D  You can find it here: [https://github.com/Alamot/3dsp](https://github.com/Alamot/3dsp)

Thanks... in what kernel work? bluetooth work?

---

### Post by guillermolisi on 2013-05-03
> **Alamot said:**
> I patched and compiled the 3dsp driver for Ubuntu 13.04. I tested it with network manager and it works fine! :D  You can find it here: [https://github.com/Alamot/3dsp](https://github.com/Alamot/3dsp)
It is for USB adapter version only, isn't it ? (despite the thread title)

---

### Post by evandromr on 2013-05-06
Hi there,

Report:

When I tried to compile the drivers it returned an error for not finding the following files:

/home/evandro/3dsp_alamot/driver_src/private/new_bluetooth_priv/3dspusbbtlib64.a
/home/evandro/3dsp_alamot/driver_src/private/wlan_priv/3dspusbbtlib64.a

I copied them from the [COLOR=#333333][FONT=Helvetica]Reyiyo version ([/FONT][/COLOR][https://github.com/reyiyo/3dsp](https://github.com/reyiyo/3dsp)) and it worked for the latest version of Ubuntu 12.04.2, with network manager integration, but my Bluetooth doesn't seem to work.

And still not working in Ubuntu 13.04.

o/

---

### Post by Alamot on 2013-05-07
@evandromr: Are you sure you didn't mess the files? Because your log file reports errors like "‘struct hci_dev’ has no member named ‘driver_data". I had corrected these lines in lbluetooth_entry.c. Make sure you compile my files.

@Blackleker: I test it and wifi works perfectly with the original kernel of Ubuntu 13.04 (32bit) and the recent update (kernel 3.8.0.19-generic). Bluetooth doesn't seem to work.

@Guillermo: Yes, sorry. My mistake. I have the USB adapter version.

To sum up: I tested the USB adapter version in Ubuntu 13.04 (32bit) kernel 3.8.0.19-generic and the wifi works just fine with network manager. Bluetooth doesn't work. Sorry for any trouble I caused.

---

### Post by matipsy on 2013-09-25
Translate from: Galician
  I'm sorry I do not speak English using translator
These drivers may not work really well as in window? Noto unlike windows that the connection is much more dim and I must restart each both the OS to get it working again.
They have made some modification to work in post-3.8 generic kernel.
It can operate in the 3.11 kernel?

---

### Post by Thedemon007 on 2014-01-27
> **Alamot said:**
> Sorry for any trouble I caused.

> **guillermolisi said:**
> It is for USB adapter version only, isn't it ? (despite the thread title)

In my opinion is a usb device, even if internally installed using mini pci-e because it uses USB 2.0 connectivity of mini-pcie slot. This is why it is shown with the command lsusb and lspci not.

[http://www.allpinouts.org/index.php/PCI_Express_Card_and_PCI_Express_Mini_Card](http://www.allpinouts.org/index.php/PCI_Express_Card_and_PCI_Express_Mini_Card)

@[COLOR=#000000]alamot [/COLOR]these drivers are based on those of reyiyo?

I attached them [3.0.5_101015 original drivers]("http://www.4shared.com/archive/Yrjd4w7Sce/BlueW-2310U_305_101015tar.html") were launched in the ftp perhaps be useful for someone wanting to mod.

Someone will have drivers they released [here]("http://www.stk.com.tw/product-stk9120.html") for ubuntu 12.04? the download link is broken. It is version 3.0.10_130306

---

### Post by Marcio_Jesus on 2014-06-28
Friends, I don't know if I'm helping but I'm working with 14LTS and Alamot works if we change:
   [FONT=courier new] //hdev->ioctl        = hci_usb_ioctl;[/FONT]
in the file driver_src/new_bluetooth/lbluetooth_entry.c There are other comments like this.
I've tried to compile compiling and looking the logfile in driver_src directory.
I hope it helps.
Cheers

---

### Post by matias8 on 2014-07-16
Los drivers Oficiales para UBuntu 12.04 están disponibles Aquí, es un dispositivo que utiliza este Chipset. 
También puede ver el manual en la página 22 para ver como se compila el Driver.

 Los Drivers  están en la seccion de sofware

[http://www.axiomtek.com/products/ViewDownload.asp?View=PID-rBOX610](http://www.axiomtek.com/products/ViewDownload.asp?View=PID-rBOX610)

Manual en página 22
 [http://axiomtek.com/Download/Download/rBOX610/rBOX610%20Linux%20User's%20Manual%20VA2_04-02-2014.pdf](http://axiomtek.com/Download/Download/rBOX610/rBOX610%20Linux%20User's%20Manual%20VA2_04-02-2014.pdf)

$uwbtool -a wlan 

):P

---

### Post by alamot2 on 2014-12-03
[COLOR=#000000]I have update the driver in [/COLOR][https://github.com/Alamot/3dsp](https://github.com/Alamot/3dsp)[COLOR=#000000]. [/COLOR]

[COLOR=#000000]Tested on Ubuntu 14.04. USB 3DSP Wifi is working. Bluetooth is not.[/COLOR]

---

