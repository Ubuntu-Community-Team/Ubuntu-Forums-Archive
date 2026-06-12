---
title: "Another Monitor"
date: 2012-11-17
forum: Multimedia Software
---

### Post by 01001101 on 2012-11-17
I was wondering if it was possible to use the on board graphics along with a graphics card to add an extra monitor. Is this possible? If so, how? Thanks

---

### Post by QIII on 2012-11-17
It is possible, depending on the capabilities of your hardware.

Could you give us some information about your graphics hardware?

Also, would you run

```
lspci
```in the terminal and look for a few lines that start with

```
01:00.0 VGA compatible controller: 
```and C&P the results between code tags (by clicking the "#" symbol just above the input box.)

Does your motherboard appear to have the ports that would be necessary?

---

### Post by 01001101 on 2012-11-17
Here's the information for "lspci":

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation G96 [Quadro FX 580] (rev a1)
02:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
04:00.0 Multimedia video controller: Blackmagic Design Device a117
05:00.0 USB controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

```

My motherboard is an Intel Desktop Board DH67CL Media Series and it does have the extra DVI port that I need to run another monitor. I don't think that it runs on NVidia drivers like my graphics card does (Nvidia PNY Quadro FX 580).

Thank you for responding. I've been wanting to do this for a long time.

---

### Post by 01001101 on 2013-01-01
Bump

---

### Post by QIII on 2013-01-01
From [http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-dh67cl.html](http://www.intel.com/content/www/us/en/motherboards/desktop-motherboards/desktop-board-dh67cl.html) --

"The board is featured with DVI-I and HDMI* connectors, and supports dual independent display for processors with Intel® HD Graphics."

The processor compatibility list at 
[http://processormatch.intel.com/CompDB/SearchResult.aspx?BoardName=DH67CL](http://processormatch.intel.com/CompDB/SearchResult.aspx?BoardName=DH67CL) 
seems to indicate that many of the Xeon processors do not require a dedicated graphics card.

If your Xeon features Intel HD graphics (hmmm... do any of them?  I don't know) and if you can run one monitor from either the DVI or HDMI port on the board, it seems you should be able to run another from the other port.  However, the quality may be poor.

It is probably worth a try if you have two monitors and can use an HDMI cable on one and a DVI cable on the other.  An experiment like that might also be valuable for other members of the forum community.    Shut down your computer, hook up the second monitor and boot back up.  Hopefully the default graphics driver will work (assuming you have not installed a proprietary driver.)  If you have installed a proprietary driver, it may be worthwhile to uninstall it to begin with.  If the setup doesn't work, we may be able to sort it out.

I suspect that there is a setting in the board's BIOS/EFI for using on-board or dedicated graphics.  For desktops it is usually not possible to use both.

But obviously I can't ask you to spend your money, so don't rush out and buy new cables unless you want to!

---

### Post by 01001101 on 2013-01-02
I have two monitors already plugged into my computer because my graphics card supports two monitors. I was wondering if I could add another monitor in addition to the two if I used the on-board graphics. 

You said that you didn't think it was possible to set bios to use dedicated and on-board graphics at the same time, and as far as I know, this is true. I may be wrong, but I thought that once the boot sequence was done, the OS takes over the graphics and the settings in BIOS don't matter. 

I heard that there was a feature in Windows 7 that allowed you to run two graphics drivers at once so that I could run my board graphics for one monitor and my graphics card graphics for the other two. I was wondering if this was possible in Ubuntu.

I have cords galore so there's no worries in doing experiments with them. Thanks.

---

