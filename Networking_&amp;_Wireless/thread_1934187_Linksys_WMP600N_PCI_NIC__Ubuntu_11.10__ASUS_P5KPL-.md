---
title: "Linksys WMP600N PCI NIC / Ubuntu 11.10 / ASUS P5KPL-AM EPU MoBo"
date: 2012-03-01
forum: Networking &amp; Wireless
---

### Post by veiledvenus on 2012-03-01
**[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Linksys WMP600N PCI Card / Ubuntu 11.10 / Custom-Built Computer (ASUS P5KPL-AM EPU MoBo)[/SIZE][/FONT][/COLOR]**
  

  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]I had this card working OOB in this same computer last year under a previous version of Ubuntu (I think it was 11.04 but I'm not sure).  I took the card out at some point, and recently upgraded to 11.10.  I just reinstalled the card, and it is visible in some command outputs, but I'm still too much of an amateur to figure out how to get it working again – Networking Manager doesn't see the interface, so I'm not sure what to do next.[/SIZE][/FONT][/COLOR]
  

  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]The entry regarding this NIC in the wiki link regarding supported wireless NICs at[/SIZE][/FONT][/COLOR]
  [[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCI[/SIZE][/FONT][/COLOR]]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#PCI")
  says that the chipset is Ralink and the driver is the rt2860.  It also states that the NIC works OOB in 9.10 with WPA2... but the last comment regarding this card is from 2009, and I've long since stopped using Ubuntu 9.10.  :)

 [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Here is the information requested in “HOWTO post a Wireless issue”

[/SIZE][/FONT][/COLOR]  **[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][B]1 ) Machine Brand and Model (PC/Laptop)**[/SIZE][/FONT][/COLOR][/B][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=monospace][SIZE=2]Custom-Built desktop PC with an ASUSTeK P5KPL-AM EPU motherboard[/SIZE][/FONT][/COLOR]
  [B][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][B]
2 ) Wireless Brand, Model and Wireless Chipset:[/B][/SIZE][/FONT][/COLOR][/B]
  [COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2]Linksys WMP600N Dual-Band PCI internal NIC[/SIZE][/FONT][/COLOR]
   
lspci (snipped):[COLOR=#000000][FONT=monospace][SIZE=1]
05:00.0 Ethernet controller: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet (rev b0)[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=1]
07:00.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1]07:01.0 Network controller: Ralink corp. RT2800 802.11n PCI[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=monospace][SIZE=1]

[/SIZE][/FONT][/COLOR]lspci -v (snipped):[COLOR=#000000][FONT=monospace][SIZE=1]
[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=monospace][SIZE=1]07:01.0 Network controller: 
Ralink corp. RT2800 802.11n PCI[/SIZE][/FONT][/COLOR] [COLOR=#000000]        [FONT=monospace][SIZE=1]
Subsystem: Linksys Device 0067[/SIZE][/FONT][/COLOR] 
[COLOR=#000000]        [FONT=monospace][SIZE=1]Flags: slow devsel, IRQ 20[/SIZE][/FONT][/COLOR] 
[COLOR=#000000]        [FONT=monospace][SIZE=1]Capabilities: <access denied>[/SIZE][/FONT][/COLOR] 
[COLOR=#000000]        [FONT=monospace][SIZE=1]Kernel modules: rt2800pci[/SIZE][/FONT][/COLOR]  [COLOR=#000000][FONT=monospace][SIZE=1]

lsusb: [/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=1]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=1]
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=1]
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=1]
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1]Bus 001 Device 003: ID 059b:0253 Iomega Corp. 
[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=1]Bus 001 Device 004: ID 11b0:6587 ATECH FLASH TECHNOLOGY [/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1]Bus 002 Device 002: ID 04f9:0029 Brother Industries, Ltd Printer[/SIZE][/FONT][/COLOR] 

**[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][B]3 ) check interface:**[/SIZE][/FONT][/COLOR][/B]
 [COLOR=#000000][FONT=monospace][SIZE=2]In ifconfig, the only interfaces shown are eth1, eth2, and lo (eth1 and eth2 are two other NICs, the first is on the mobo and the second is a Netgear)[/SIZE][/FONT][/COLOR].  [COLOR=#000000][FONT=monospace][SIZE=2]In iwconfig, the same interfaces are shown as in ifconfig, each with the result “no wireless extensions.”[/SIZE][/FONT][/COLOR]  

**[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][B]4 ) Check for modules:**[/SIZE][/FONT][/COLOR][/B]
  [COLOR=#000000][FONT=monospace][SIZE=2]The rt2860 driver module (?) does not appear to be loaded:[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=monospace][SIZE=2]
lsmod (possibly related modules)[/SIZE][/FONT][/COLOR]:
  [COLOR=#000000][FONT=monospace][SIZE=2]Module                  Size  Used by[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=monospace][SIZE=2]rt2800pci              18340  0 [/SIZE][/FONT][/COLOR] 
  [COLOR=#000000][FONT=monospace][SIZE=2]rt2800lib              48909  1 rt2800pci[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=monospace][SIZE=2]rt2x00pci              14202  1 rt2800pci[/SIZE][/FONT][/COLOR]
  [COLOR=#000000][FONT=monospace][SIZE=2]rt2x00lib              48146  3 rt2800pci,rt2800lib,rt2x00pci[/SIZE][/FONT][/COLOR]

  **[COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][B]5 ) Kernel boot messages**[/SIZE][/FONT][/COLOR][/B]
 [COLOR=#000000][FONT=monospace][SIZE=2]A dmesg | grep “rt2860” [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=monospace][SIZE=2]returns nothing (goes back to prompt).[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=2]
A dmesg | grep “rt2”[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=1]returns:
[   12.625778] rt2800pci 0000:07:01.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=1]
[   12.625812] Modules linked in: rt2800pci(+) rt2800lib crc_ccitt snd_hda_codec_via rt2x00pci rt2x00lib snd_hda_intel(+) snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event mac80211 snd_seq psmouse serio_raw cfg80211 asus_atk0110 parport_pc snd_timer eeprom_93cx6 snd_seq_device snd soundcore snd_page_alloc i915 drm_kms_helper drm i2c_algo_bit video lp parport usb_storage uas natsemi xhci_hcd ahci libahci atl1e[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=1]
[   12.625884]  [<f826168a>] rt2x00pci_alloc_reg+0x1a/0xa0 [rt2x00pci][/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1][   12.625903]  [<f82617eb>] rt2x00pci_probe+0xdb/0x8f0 [rt2x00pci][/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1][   12.625914]  [<f84a3552>] rt2800pci_probe+0x12/0x20 [rt2800pci][/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1][   12.625974]  [<f813f017>] rt2800pci_init+0x17/0x1000 [rt2800pci][/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=1]
[   12.625997] rt2x00pci -> rt2x00pci_alloc_reg: Error - Failed to allocate registers.[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1][   12.626006] rt2800pci 0000:07:01.0: PCI INT A disabled[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=1][   12.626013] rt2800pci: probe of 0000:07:01.0 failed with error -12[/SIZE][/FONT][/COLOR]  [B][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][B]

6 ) Network configuration[/B][/SIZE][/FONT][/COLOR][/B]
[COLOR=#000000][FONT=monospace][SIZE=2]sudo lshw -C network (snipped)[/SIZE][/FONT][/COLOR] 
[COLOR=#000000][FONT=monospace][SIZE=2]*-network:1 UNCLAIMED[/SIZE][/FONT][/COLOR] 
[COLOR=#000000]       [FONT=monospace][SIZE=2]description: Network controller[/SIZE][/FONT][/COLOR] [COLOR=#000000]       [FONT=monospace][SIZE=2]product: RT2800 802.11n PCI[/SIZE][/FONT][/COLOR] [COLOR=#000000]       [FONT=monospace][SIZE=2]
vendor: Ralink corp.[/SIZE][/FONT][/COLOR] [COLOR=#000000]       [FONT=monospace][SIZE=2]
physical id: 1[/SIZE][/FONT][/COLOR] 
[COLOR=#000000]       [FONT=monospace][SIZE=2]bus info: pci@0000:07:01.0[/SIZE][/FONT][/COLOR] 
[COLOR=#000000]       [FONT=monospace][SIZE=2]version: 00[/SIZE][/FONT][/COLOR] [COLOR=#000000]       [FONT=monospace][SIZE=2]
width: 32 bits[/SIZE][/FONT][/COLOR] [COLOR=#000000]       [FONT=monospace][SIZE=2]
clock: 33MHz[/SIZE][/FONT][/COLOR] [COLOR=#000000]       [FONT=monospace][SIZE=2]
capabilities: pm cap_list[/SIZE][/FONT][/COLOR] [COLOR=#000000]       
[FONT=monospace][SIZE=2]configuration: 
latency=64 
maxlatency=4 
mingnt=2[/SIZE][/FONT][/COLOR]  [B][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][B]

7 ) Scan for networks:[/B][/SIZE][/FONT][/COLOR][/B]
  [COLOR=#000000][FONT=monospace][SIZE=2]iwlist scan[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=2][lo/eth1/eth2]     Interface doesn't support scanning.[/SIZE][/FONT][/COLOR]  [B][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][B]

8 ) Ubuntu Version: [/B][/SIZE][/FONT][/COLOR][/B] 
[COLOR=#000000][FONT=monospace][SIZE=2]lsb_release -d[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=2]Description:    Ubuntu 11.10[/SIZE][/FONT][/COLOR]  [B][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][B]

9 ) Kernel/architecture (including 32 vs. 64 bit): [/B][/SIZE][/FONT][/COLOR][/B] 
[COLOR=#000000][FONT=monospace][SIZE=2]uname -mr[/SIZE][/FONT][/COLOR] [COLOR=#000000][FONT=monospace][SIZE=2]3.0.0-16-generic i686[/SIZE][/FONT][/COLOR]  [B][COLOR=#000000][FONT=Verdana, Arial, Tahoma][SIZE=2][B]

10 ) Restarting the network:[/B][/SIZE][/FONT][/COLOR][/B]
  [COLOR=#000000][FONT=monospace][SIZE=2]sudo /etc/init.d/networking restart[/SIZE][/FONT][/COLOR] 
[COLOR=#000000] [FONT=monospace][SIZE=1]* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces[/SIZE][/FONT][SIZE=1][FONT=monospace]
[/FONT][/SIZE][/COLOR][COLOR=#000000][FONT=monospace][SIZE=1]* Reconfiguring network interfaces... [ OK ][/SIZE][/FONT][/COLOR]   

[FONT=Arial, sans-serif][SIZE=2][COLOR=#000000]Can anyone point me in the right direction for information (Newbie-Oriented links, please!) on how to get this running?  Although I can putz my way around bash, I really am a newbie when it comes to ubuntu (and linux) administration, despite having been a no-nothing end-user of Ubuntu since Hardy Heron.  :)  Any suggestions are [/COLOR][COLOR=#000000]**greatly**[/COLOR][COLOR=#000000] appreciated![/COLOR][/SIZE][/FONT]
 
 [FONT=Arial, sans-serif][SIZE=2][COLOR=#000000]Venus[/COLOR][/SIZE][/FONT]

---

### Post by chili555 on 2012-03-01
I believe, in Ubuntu 11.10, that rt2800pci is correct. You might check here: [http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5234](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=5234)> rt2x00pci -> rt2x00pci_alloc_reg: Error - Failed to allocate registers.And then:> That error indicates hardware problems, try putting the device in another PCI slot or try checking the device on another computer.You might also check how IRQs are set up in the BIOS; 'autoselect' seems to work best.

If those steps don't help, I understand there is newer firmware we might try.

---

### Post by veiledvenus on 2012-03-01
chili555, thank you so much!  I couldn't find any IRQ selection or choice settings in my BIOS, but I set the "PCIPnP by OS" to be enabled (allowing an OS with Plug & Play control abilities to control PCI hardware selection) - that seemed to allow Ubuntu to recognize that a wireless card existed, but I couldn't successfully sign on to the existing network.  HOWEVER, when I switched the NIC to a different PCI slot and started up the machine, it saw the network and was able to sign on.  It's possible that it wasn't a matter of which slot it was in though -- it's possible that the card may simply not have been seated properly.  Anyway, now I have another idea to try next time I have any problem with PCI hardware... something so simple I should have thought to do, but didn't (and now I will remember!)...

Thank you again, and thanks for responding so fast!  Now I need to look around the board FAQ on how I can mark your response as helpful or give you kudo points -- if you see this response before I find the answer myself, please send me a message on the best way to show my thanks in a tangible way?  I just registered as a new member today, so I'm still learning my way around.  Glad that UbuntuForums is here, hopefully I can help others here out some day like you did for me today.

edit:  I checked out the forum tutorial, and saw that the "Thank" button is the proper method... but the Thank button is not available on your post - any idea why not?

---

### Post by chili555 on 2012-03-02
> chili555, thank you so much! That and the SOLVED are all the thanks I need! I am very glad it's working. Have fun!

---

