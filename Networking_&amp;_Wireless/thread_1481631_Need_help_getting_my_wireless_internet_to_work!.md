---
title: "Need help getting my wireless internet to work!"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by neonfire999 on 2010-05-12
Ok, so i have a Realtek RTL8192E Wireless LAN 802.11n PCI-E NIC card on  my Samsung r580 laptop that I just installed Ubuntu Studio 10.04 on. I  am wondering how to get the wireless card working in Ubuntu Studio 10.04. I saw some  info on my card [here]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#PCI").
here is the info I got when I typed "lspci -knn" into the terminal in Ubuntu Studio 10.04.
```
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
    Kernel modules: intel-agp
00:01.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express x16 Root Port [8086:0045] (rev 12)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 06)
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 06)
    Kernel driver in use: ahci
    Kernel modules: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
    Kernel modules: i2c-i801
02:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce 310M] [10de:0a75] (rev a2)
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau
02:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)
    Kernel driver in use: rtl819xE
    Kernel modules: r8192_pci
07:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4381] (rev 11)
    Kernel driver in use: sky2
    Kernel modules: sky2
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)

```
If anyone could help, it would be greatly appreciated. Thanks.

---

### Post by bkratz on 2010-05-12
Afraid I wouldn't be much help, but here is a thread with a lot of explanations and descriptions.

[http://art.ubuntuforums.org/showthread.php?t=1460038](http://art.ubuntuforums.org/showthread.php?t=1460038)

Probably someone there could help--it is still pretty new.

---

### Post by neonfire999 on 2010-05-17
> **bkratz said:**
> Afraid I wouldn't be much help, but here is a thread with a lot of explanations and descriptions.

[http://art.ubuntuforums.org/showthread.php?t=1460038](http://art.ubuntuforums.org/showthread.php?t=1460038)

Probably someone there could help--it is still pretty new.
ok, so no one there paid any attention at all to me, so i think i'm gonna see if anyone will find this thread and help out, and if not, il just post it again cuz i really need this so i can record music and stuff with internet access.

---

### Post by chili555 on 2010-05-17
> 03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8192] (rev 01)
    Kernel driver in use: rtl819xE
    Kernel modules: r8192_pci
It looks like you are half way there! What does this tell us?```
ifconfig
iwconfig
dmesg | grep 819
```Thanks.

---

### Post by purelinuxuser on 2010-05-17
Actually, according to the Ubuntu Wiki page you linked in your first post, you'll have to emulate a Windows wireless driver under Linux via ndiswrapper.  To do this:

[LIST=1]
[*]Plug your computer into Ethernet and get an Internet connection.
[*]Open Synaptic Package Manager (System > Administration).
[*]Perform a quick search for "ndiswrapper."
[*]Install the packages "ndiswrapper-utils-1.9," "ndiswrapper-common," and "ndisgtk" (double-click on them).
[*]Click the "Apply" button in the toolbar.
[*]Once that's done, download the **Windows XP** (it _MUST_ be XP, see 2 posts down for explanation) driver for your wireless card (seriously).
[*]The driver should have come in a self-extracting *.exe file.  Right-click it in the File Browser and hit "Extract."  If it extracts, yay.  Otherwise post back with the driver file used.
[*]Open the extracted folder and look for an *.inf file usually located in a folder called "DRIVER" (or something similar).
[*]Open ndisgtk (System > Administration).  Click "Add Driver," and browse for the *.inf file you found.
[*]After installation is complete, reboot.
[*]Enjoy your wireless!
[/LIST]
Hopefully this will help, or else I'm out of options. :)

---

### Post by Google24 on 2010-05-17
hey
I have the exact same samsung r580 labtop as you, i was having the same problems as you and non of the stuff on the ubuntu forums was helping. However I found something that worked for me and i image since you have the same system as me then well it might just work. 
1) do the same stuff as in the above post, installing the ndisgtk packets
2) I found that the windows 7 realtek driver was not working, it was actually removing my wireless altogether, so i tried the windows xp driver and poof it works great
here is the url to the driver that i used 

[http://www.samsung.com/ca/support/download/supportDownDetail.do?group=&type=mobile-computing&subtype=Notebooks&model_nm=R580-i3-330&disp_nm=R580-i3-330&language=&cate_type=all&mType=DR&dType=D&vType=&cttID=2720396&prd_ia_cd=05012600&model_cd=&menu=download&menu2=detail](http://www.samsung.com/ca/support/download/supportDownDetail.do?group=&type=mobile-computing&subtype=Notebooks&model_nm=R580-i3-330&disp_nm=R580-i3-330&language=&cate_type=all&mType=DR&dType=D&vType=&cttID=2720396&prd_ia_cd=05012600&model_cd=&menu=download&menu2=detail)

i extracted and went to the windows wireless driver setting in the admin pane. from there install the new driver from the place you extracted it. The nice thing is there is only 1 .inf file in the extract. 

Reboot and hopefully it works for ya

---

### Post by purelinuxuser on 2010-05-19
[QUOTE=Google24]2) I found that the windows 7 realtek driver was not working, it was actually removing my wireless altogether, so i tried the windows xp driver and poof it works great[/QUOTE]

Yeah, I forgot about that- ndiswrapper and ndisgtk are not yet compatible with the NDIS6 specification, so Windows Vista and Windows 7 drivers are not compatible.  You'll have to use Windows XP.  Anyway, thanks for the reminder Google24. :)

---

