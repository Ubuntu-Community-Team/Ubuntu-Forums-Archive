---
title: "wireless stress and problems"
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by texgeis on 2010-10-29
Help i just wiped my windows to instal Ubuntu and cant get wireless to work tried Sudo lshw C-network and got this
*-network:0 UNCLAIMED   
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:c0204000-c0205fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:16:d4:39:4e:28
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.11 latency=128 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:22 ioport:a000(size=256) memory:c020a400-c020a4ff


I have downladed and installed the bcmwl-kernel-source but when I go to 3.)System/ Admin/ there is no listing for Hardware Drivers
 also tried **sudo apt-get install b43-fwcutter** but no result
also tried 
[FONT=monospace]sudo rfkill unblock all but still nothing
for a while the wireless was listed under network connections but it said firmwear was missing but could not make any progress with that either

tried lspci -nn and got
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
06:04.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:04.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:04.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:04.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 01)
bash: syntax error near unexpected token `('
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:01.0: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:04.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a36]
00:04.0: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:13.0 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4374]
00:13.0: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:13.1 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB Host Controller [1002:4375]
00:13.1: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:13.2 USB Controller [0c03]: ATI Technologies Inc IXP SB400 USB2 Host Controller [1002:4373]
00:13.2: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:14.0 SMBus [0c05]: ATI Technologies Inc IXP SB400 SMBus Controller [1002:4372] (rev 11)
bash: syntax error near unexpected token `('
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:14.1 IDE interface [0101]: ATI Technologies Inc IXP SB400 IDE Controller [1002:4376]
00:14.1: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:14.3 ISA bridge [0601]: ATI Technologies Inc IXP SB400 PCI-ISA Bridge [1002:4377]
00:14.3: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:14.4 PCI bridge [0604]: ATI Technologies Inc IXP SB400 PCI-PCI Bridge [1002:4371]
00:14.4: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:14.5 Multimedia audio controller [0401]: ATI Technologies Inc IXP SB400 AC'97 Audio Controller [1002:4370] (rev 02)
> 00:14.6 Modem [0703]: ATI Technologies Inc SB400 AC'97 Modem Controller [1002:4378] (rev 02)
bash: syntax error near unexpected token `('
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.0: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.1: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.2: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
00:18.3: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE) [1002:5955]
bash: syntax error near unexpected token `('
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
bash: syntax error near unexpected token `('
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 06:04.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:04.0: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 06:04.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
bash: syntax error near unexpected token `('
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 06:04.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:04.3: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 06:04.4 SD Host controller [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller [104c:8034]
06:04.4: command not found
home@home-Pavilion-dv8000-EZ580UA-ABA:~$ 06:06.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
bash: syntax error near unexpected token `('

thanks for any suggestions


[/FONT]

---

### Post by chicoharv on 2010-12-02
I have the same problem with my bcm4318, says it is unclaimed.My two laptops were working on 10.4 but when I upgraded to 10.10 they stopped working. The 4318 is not included with the othe bcm43xx's . Did you ever get yours working? if so how?

---

