---
title: "Can't connect to network and have no gnome network manager"
date: 2008-12-06
forum: Networking &amp; Wireless
---

### Post by boogerman2222 on 2008-12-06
Hi

i'm a complete novice with linux and have absolutely no idea what i'm doing :L

i have installed my wireless card and the drivers are working fine, but it can't seem to connect to any networks, when i first put it in it connected automatically and worked fine, but i then turned it off and when it came back on it wouldn't let me connect to any networks.

i also don't have gnome network manager on my taskbar.

Does anyone have any suggestions as to what might be wrong? Or know anything i could do in terminal to sort it out? Or could it just be i'm too far away from the router?

many thanks, gaz

---

### Post by lovelyvik293 on 2008-12-06
please post the vendor of the wifi card and the output of the lspci and iwconfig.

---

### Post by boogerman2222 on 2008-12-06
ok, this is just showing how much of a novice i am, i have absolutely no idea what that means.

sorry :/

---

### Post by lovelyvik293 on 2008-12-06
You just have to type lspci and the iwconfig in the terminal.

---

### Post by boogerman2222 on 2008-12-06
ok, i'll try it now

---

### Post by boogerman2222 on 2008-12-06
Lspci:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02) 
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) 
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) 
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02) 
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02) 
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
01:09.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01) 
 
iwconfig:

lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wifi0     no wireless extensions. 
 
ath0      IEEE 802.11g  ESSID:""  Nickname:"" 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated    
          Bit Rate:0 kb/s   Tx-Power:15 dBm   Sensitivity=1/1   
          Retry:off   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=0/70  Signal level=-95 dBm  Noise level=-95 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions.

---

### Post by lovelyvik293 on 2008-12-06
Great work..
You have the atheros wifi card.You have to install the madwifi driver for this card.
It may help [http://madwifi-project.org/](http://madwifi-project.org/)

---

### Post by hacker0wnz on 2008-12-06
help please. i have the same problem.


Ubuntu 8.10 detect my wifi card which is Atheros 802.11  

I activated from the Hardware Drivers but. it Also Says That The Driver Is In Use.

by the way

I have HP dv5z-1000 Notebook 
AMD 64-bit

I cant connect to Internet :(

---

### Post by lovelyvik293 on 2008-12-06
If it shows it is in use then it must activated the driver.hacker0wnz please post your lspci output.

---

### Post by hacker0wnz on 2008-12-06
okay here it is

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0a:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
0a:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controlle

```

I did activated and it says "This driver is activated and curently in use"

by the way i also have Vista running, Dual boot.

Is that Probaly why the driver is in use ?

---

### Post by lovelyvik293 on 2008-12-06
Vista have no effect when ubuntu is running.
From lspci it seams that the driver is there.
Do one more thing post the output of iwconfig.:p

---

### Post by hacker0wnz on 2008-12-06
okay here it is

```
zer0cool@zer0cool-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


```

---

### Post by lovelyvik293 on 2008-12-06
I think these drivers are not working you have to install the drivers for this card manually.Just install the madwifi driver for your card.
Here is the link:-http://madwifi-project.org/

---

### Post by hacker0wnz on 2008-12-06
im sorry. im a newb with Ubuntu,

can you pick the right driver for me please, and send me the download link.



thanks a lot.

---

### Post by lovelyvik293 on 2008-12-06
Hai just go to the side and there is a link for download download it and use the manual given in the site to install it.It's so easy.:popcorn:

---

### Post by hacker0wnz on 2008-12-06
i downloaded the latest one but there are to many files.

i dont know which one is it.

---

### Post by lovelyvik293 on 2008-12-06
Hai i got a how-to for u ):P
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)

Use it.

---

### Post by hacker0wnz on 2008-12-06
im really confused this is too hard for my brain :(

i typed the codes what it says on the guide.

but i got errors all the time :(

---

### Post by lovelyvik293 on 2008-12-06
Whenever you got an error just post here please.

---

### Post by hacker0wnz on 2008-12-06
```
zer0cool@zer0cool-laptop:~$ ifconfig ath0 down
ath0: ERROR while getting interface flags: No such device
zer0cool@zer0cool-laptop:~$ ifconfig wifi0 down
wifi0: ERROR while getting interface flags: No such device
```

---

### Post by lovelyvik293 on 2008-12-06
Don't panic these errors are ok because you dont have these wlan0 and the ath0.
Use the next commands.

---

### Post by hacker0wnz on 2008-12-06
OKAY!

Somehow i just got my Atheros 802.11 Wireless LAN cards. not in use

i checked on the Hardware Drivers and it says "This driver is activated but not currently in use"


but i still cant detect any wifi or route:(

here is the lspci output:

```
zer0cool@zer0cool-laptop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
08:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
0a:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
0a:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
0a:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controll
```




any idea ?

---

### Post by lovelyvik293 on 2008-12-06
This is same as shown earlier and i think the output of iwconfig is same as earlier.
Please install the madwifi driver because there are lot of devices exists for them there is no driver exist in the official ubuntu repo.

---

### Post by hacker0wnz on 2008-12-06
well the only things are

- I dont know which is the right drivers for my Atheros 802.11 LAN card

-I dont know how to install them.


Im sorry im a Neewb To Ubuntu  :(

---

### Post by lovelyvik293 on 2008-12-06
Sorry to say,but you are not pushing your self hard enough to being a good linux user.

---

### Post by hacker0wnz on 2008-12-06
okay, well i downloaded aalready and install it with the Ndiswrapper. 

and my Driver says in Use again :S

---

### Post by lovelyvik293 on 2008-12-06
And is it working??

---

### Post by hacker0wnz on 2008-12-06
No, Its Not Working :(

---

### Post by lovelyvik293 on 2008-12-06
Check this out.
[http://ubuntuforums.org/showthread.php?t=865971](http://ubuntuforums.org/showthread.php?t=865971)

---

### Post by hacker0wnz on 2008-12-06
Thank you so much!!!!


I followed that guide and it works :0

thank you!!!!


God bless you :)

---

