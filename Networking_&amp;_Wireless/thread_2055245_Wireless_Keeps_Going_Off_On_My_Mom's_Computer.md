---
title: "Wireless Keeps Going Off On My Mom's Computer"
date: 2012-09-08
forum: Networking &amp; Wireless
---

### Post by Katniss Everdeen on 2012-09-08
My Mom bought a laptop last year, it was a low end laptop. It's a Toshiba Satellite C650 I think.

I notice that once the laptop has been idle for awhile, the wireless internet disables, and I have to restart it to get it working again.

The laptop is set up the same as the rest of the computers, and non of the others have any problem with it. I have a Toshiba Satellite L775, and we also have another Toshiba Satellite C model laptop, and it works good.

What could be cuasing it?

---

### Post by shadedpixel on 2012-09-08
> **Katniss Everdeen said:**
> My Mom bought a laptop last year, it was a low end laptop. It's a Toshiba Satellite C650 I think.

I notice that once the laptop has been idle for awhile, the wireless internet disables, and I have to restart it to get it working again.

The laptop is set up the same as the rest of the computers, and non of the others have any problem with it. I have a Toshiba Satellite L775, and we also have another Toshiba Satellite C model laptop, and it works good.

What could be cuasing it?

What wireless chipset does the laptop have?

Paste your output of 
```
lspci
```

and

```
lsusb
```

---

### Post by Katniss Everdeen on 2012-09-09
Here it is.

lspci:

> username@Toshiba-Satellite-C655D:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Wrestler [Radeon HD 6250]
00:11.0 SATA controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 42)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices [AMD] nee ATI SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:16.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
06:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)

lsusb:

> Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 10f1:1a34 Importek 


---

### Post by shadedpixel on 2012-09-11
> **Katniss Everdeen said:**
> Here it is.

lspci:



lsusb:

Thanks, sorry for not getting back very quickly school gets in the way a lot. We are looking at this line in particular (below), ill get back to you when I get more info on this card.

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

---

### Post by shadedpixel on 2012-09-11
Ok, found it. And the good news is that the the manufacturer does have a Linux driver available!, It was just not included in Ubuntu or the Linux kernel because its not open source.

You can find the driver [[COLOR="Blue"]here[/COLOR]]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE"). **Make sure you are downloading the RTL8188CE Unix/Linux driver.**

And to install, you do the following.

**[-] First however make sure that the driver is downloaded and that the driver is downloaded and somewhere that is easily accessed (like your home folder). [-] **


Install Build-Essential (if you don't already have it)
```
sudo apt-get install sudo apt-get install build-essential
```

Extract the driver (make sure your in the folder where the .tar.gz that you downloaded is)
```
tar -xvf 92ce_se_de_linux_mac80211_0005.1230.2011.tar.gz
```

[B][-] Now CD into the extracted folder [-]

[-] Now we can start installing :) [-][/B]

From the drivers readme file:
```
sudo su
```

Compile the driver from the source code:
```
make
```

Install the driver to the kernel:
```
make install
```

Reboot and Enjoy!
```
reboot
```

---

### Post by Katniss Everdeen on 2012-09-22
Thank you for your reply/ I will instal it during the week and let you know how it goes.

Sorry. for taking so long to reply. I don't log on here often enough.

---

