---
title: "ipw2200 problems in Hardy"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by Egi_Power on 2009-05-10
Hi!

I am having problems getting wireless working on Hardy using a built in Intel PRO 2200BG wireless network adapter.
The laptop is an Acer Aspire 1690 (1692WLMi).
I'm pretty sure it worked before, but I don't use the laptop often, it's used by the wife.
Just a few days back it found wireless networks, I remember because one of them was called "ubuntu". :) It had the wireless icon on the panel. Now the Network Manager shows only the wired connection.
Recently I set up the wireless LED to light up following this thread: [ [SOLVED] Wireless LED on Acer Aspire 1690]("http://ubuntuforums.org/showthread.php?t=817777")
I'll post some outputs from the terminal, hopefully some of you would understand them better than me.
```
***@***-laptop:~$ dmesg |tail -30
[   56.061283] [fglrx] Reserve Block - 1 offset =  0X0 length = 0X40000
[   56.061289] [fglrx] Reserve Block - 2 offset =  0Xffff000 length = 0X1000
[   56.061295] [fglrx] Reserve Block - 3 offset =  0X7fbb000 length = 0X40000
[   56.175046] [fglrx] interrupt source 20008000 successfully enabled
[   56.175057] [fglrx] enable ID = 0x00000004
[   56.175610] [fglrx] Receive enable interrupt message with irqEnableMask: 20008000
[   56.175996] [fglrx] interrupt source 10000000 successfully enabled
[   56.176004] [fglrx] enable ID = 0x00000005
[   56.176423] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   56.662347] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   59.605733] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   59.814714] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   59.896484] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   60.024396] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   60.195862] NET: Registered protocol family 10
[   60.196627] lo: Disabled Privacy Extensions
[   60.197603] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   60.198232] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   60.239079] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   60.239570] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   60.247361] ipw2200: Failed to send ASSOCIATE: Already sending a command.
[   60.286800] ipw2200: Firmware error detected.  Restarting.
[   60.423049] eth1: no IPv6 routers present
[   60.447857] ipw2200: Failed to send ASSOCIATE: Already sending a command.
[   82.127302] synaptics: using relaxed packet validation
[   45.346490] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   47.121065] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   55.548936] eth1: no IPv6 routers present
[   71.513283] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  135.721817] ipw2200: Firmware error detected.  Restarting.
```
* After a restart now I don't get the ***ipw2200: Firmware error detected.  Restarting.*** error.
```
***@***-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:16:6c:aa
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:16:36:1e:6c:ca
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.86 firmware=5788-v3.01 latency=32 mingnt=64 module=tg3 multicast=yes
```
```
***@***-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port [8086:2591] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 04)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 [8086:2664] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d4)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 04)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility X700 (PCIE) [1002:5653]
06:01.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:01.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
06:08.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)
```
```
***@***-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:90:D0:DF:BD:A9
                    ESSID:"SpeedTouch4E3A16"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=31/100  Signal level=-81 dBm  
                    Extra: Last beacon: 10984ms ago
          Cell 02 - Address: 00:01:38:C5:4B:08
                    ESSID:"TN_private_09"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-74 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 10980ms ago
          Cell 03 - Address: 00:1F:9F:71:EA:61
                    ESSID:"TN_private_FB60C3"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=50/100  Signal level=-71 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 2580ms ago
etc.
etc.
etc.
```
As you can see it finds networks (17 cells total), but for some reason it can't connect to them.
*EDIT:*
```
***@***-laptop:~$ sudo /etc/init.d/networking restart
[sudo] password for ***: 
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth1.pid with pid 5965
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:16:6c:aa
Sending on   LPF/eth1/00:13:ce:16:6c:aa
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:13:ce:16:6c:aa
Sending on   LPF/eth1/00:13:ce:16:6c:aa
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```
```
***@***-laptop:~$ uname -mr
2.6.24-24-generic i686
```
```
***@***-laptop:~$ lsb_release -d
Description:	Ubuntu 8.04.2
```
```
***@***-laptop:~$ lsmod | grep ipw2200
ipw2200               146120  0 
ieee80211              35528  1 ipw2200
```
*END OF EDIT*

Any help would be greatly appreciated.

Best regards,

Egi_Power

---

### Post by chili555 on 2009-05-10
> ipw2200: Firmware error detected. Restarting.It looks to me like there was a (hopefully) one-time error loading the firmware. It is loaded correctly now, because you have a working interface, you can scan, etc. May we please see:```
cat /etc/network/interfaces
```Thanks.

---

### Post by Egi_Power on 2009-05-10
```
***@***-laptop:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback





iface eth1 inet dhcp
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid *TheNameOfMyNetwork*


auto eth1
```
In the morning when I posted the thread after a restart I didn't get the firmware error message.
Here is my dmesg again:
```
***@***-laptop:~$ dmesg |tail -30
[   34.479565] [fglrx] Receive enable interrupt message with irqEnableMask: 10000000
[   74.906267] NET: Registered protocol family 10
[   74.907293] lo: Disabled Privacy Extensions
[   74.909248] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   74.955743] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   75.588245] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   78.501913] eth0: no IPv6 routers present
[   78.507843] eth1: no IPv6 routers present
[   78.848323] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   78.970813] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   79.311420] ipw2200: Failed to send ASSOCIATE: Already sending a command.
[   79.335001] ipw2200: Firmware error detected.  Restarting.
[   79.460638] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   80.145761] ipw2200: Failed to send ASSOCIATE: Already sending a command.
[   80.160570] ipw2200: Firmware error detected.  Restarting.
[   80.806951] ipw2200: Failed to send ASSOCIATE: Already sending a command.
[   80.855655] ipw2200: Firmware error detected.  Restarting.
[   81.023763] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   81.191696] ipw2200: Failed to send ASSOCIATE: Already sending a command.
[   81.311819] ipw2200: Firmware error detected.  Restarting.
[   81.508420] ipw2200: Failed to send ASSOCIATE: Already sending a command.
[   81.543613] ipw2200: Firmware error detected.  Restarting.
[   81.665133] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   81.691390] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   83.600205] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   51.108637] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[   45.165270] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[  104.134728] ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.
[  104.212871] ipw2200: Failed to send ASSOCIATE: Already sending a command.
[  185.848000] ipw2200: Firmware error detected.  Restarting.
```

Thanks for trying to help sort out my issue.

Take it easy.

Egi_Power

---

### Post by chili555 on 2009-05-10
Having an enrty in *interfaces* for eth1 means that you will control it manually and that Network Manager, that little icon at the top, is to be 'hands off.' Unless that entry has the WPA password or has reference to a file that contains it, the access point will not be given the correct password and will not connect. Let's hand control back to Network Manager by commenting out the eth1 entries thus:```
sudo gedit /etc/network/interfaces
``````
auto lo
iface lo inet loopback

#iface eth1 inet dhcp
#wpa-driver wext
#wpa-key-mgmt WPA-PSK
#wpa-proto WPA
#wpa-ssid TheNameOfMyNetwork

#auto eth1
```Proofread, save and close gedit. It will probably take a reboot to get NM back on the job.

Next we seem to have a problem with the firmware not loading. Please do:```
sudo rmmod ipw2200 && sudo modprobe ipw2200
```Then run:```
dmesg | tail
```See if the proper firmware got loaded. Also, hope for a fix soon. I noticed that *linux-backports-modules-hardy-generic* has a newer ipw2200 module, so you might try installing that.

---

### Post by Egi_Power on 2009-05-11
Following your instructions my wireless is working now.
I edited and saved the ***interfaces*** file in ***/etc/network*** directory, and restarted the computer.
Now when I left clicked on the NM icon I could see all the networks around me.

Then
```
***@***-laptop:~$ sudo rmmod ipw2200 && sudo modprobe ipw2200
```
And finally
```
***@***-laptop:~$ dmesg | tail
[   58.836163] NET: Registered protocol family 10
[   58.836893] lo: Disabled Privacy Extensions
[   58.838729] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   61.933147] eth0: no IPv6 routers present
[   63.382329] ACPI: PCI interrupt for device 0000:06:03.0 disabled
[   63.431904] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   63.431910] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   63.432297] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 17 (level, low) -> IRQ 17
[   63.433045] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   63.563420] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
```
Then I just logged in to my router, copy and paste the password for my network.
One question: when I edited and saved the interfaces file, gedit created a hidden file called interfaces~. I guess that's for backup purposes.
Should I leave that file alone or should I delete it. It's just 144 bytes, so I would't gain any disk space if I delete it.
> I noticed that *linux-backports-modules-hardy-generic* has a newer ipw2200 module, so you might try installing that. 
I will think about it, but first I'm gonna see how it works with the existing old module.
***EDIT:***
Just one more question:
Most of the times we (mostly the wife actually) use the wired network. But when I select the wireless, every time I have to type in the password. Is there a way to set it up, so that the password is stored somehow and I don't have to retype it?
***END OF EDIT***
Thank you for your help and the time you spent sorting out my problem.

Best regards,

Egi_Power

---

### Post by chili555 on 2009-05-11
Great! Removing and reinserting the ipw2200 module produced no firmware errors.> Should I leave that file alone or should I delete it. It's just 144 bytes,I wouldn't bother. Backups are good!> Is there a way to set it up, so that the password is stored somehow and I don't have to retype it?I haven't used Hardy in quite a while, so I may be relying on a faulty memory, but I think you can right-click the Network Manager icon and select 'Edit Connections,' select the 'Wireless' tab and check 'Connect Automatically.'

We might just automate the process of removing and reinserting the ipw2200 module, so you don't have to do it every time you boot. Please edit /etc/rc.local to add four lines above 'exit 0'.:```
ifdown eth1
rmmod ipw2200
modprobe ipw2200
ifup eth1
```Proofread, save and close.

---

### Post by Egi_Power on 2009-05-12
> Is there a way to set it up, so that the password is stored somehow and I don't have to retype it?
I think I found out what caused to ask every time for password.
I had space in my network name, something like this: "***My Network Name***"
After I renamed the network (without any space in the name) and select the wireless it connects automatically.:)
> We might just automate the process of removing and reinserting the ipw2200 module, so you don't have to do it every time you boot. Please edit /etc/rc.local to add four lines above 'exit 0'.:
```
ifdown eth1
rmmod ipw2200
modprobe ipw2200
ifup eth1
```
If you could just explain the first and last line of code?
I know the ***rmmod*** command removes module from the kernel, the ***modprobe*** command inserts the specified module into the kernel.
I haven't add this 4 lines of code to the */etc/rc.local* file yet, because it seems to work now, but I will if you say it's necessary.

Best regards,

Egi_Power

---

### Post by chili555 on 2009-05-12
> If you could just explain the first and last line of code?Removing the module on an existing interface causes problems; the module doesn't want to let go because it's busy enabling the interface, in your case eth1. The answer is to bring eth1 down, remove and reinsert the module (to, hopefully resolve the firmware issue, and then bring eth1 back up.

---

### Post by Egi_Power on 2009-05-12
> **chili555 said:**
> 
We might just automate the process of removing and reinserting the ipw2200 module, so you don't have to do it every time you boot. Please edit /etc/rc.local to add four lines above 'exit 0'.:```
ifdown eth1
rmmod ipw2200
modprobe ipw2200
ifup eth1
```
I followed your advice, because I was getting the firmware error messages.
Now it looks working fine.
We'll see, hope for the best.

Take care.

Egi_Power

---

### Post by mastapat11 on 2009-07-31
this worked perfectly for me. 
thanks!  :KS

:popcorn:

---

### Post by allendevans on 2012-03-11
Hey!

I'm having the same problems with Lucid 10.04 on my Aspire 1690, with ipw2200.  I've tried the suggestions on this page without success.  I believe the problem is the ipw2200 module, and the highlighted lines below.  So far, I've not been able to rfkill from on to off.

Please assist if you have the time ...

Items to think about ...

```
XXX@XXX:~$ dmesg | tail -40
[   14.826762] ipw2200 0000:06:03.0: firmware: requesting ipw2200-bss.fw
[   14.961129] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.961138] i915 0000:00:02.0: setting latency timer to 64
[   14.984584] [drm] set up 7M of stolen space
[   15.176676] type=1505 audit(1331481720.855:5):  operation="profile_load" pid=677 name="/usr/share/gdm/guest-session/Xsession"
[   15.183541] type=1505 audit(1331481720.859:6):  operation="profile_replace" pid=679 name="/sbin/dhclient3"
[   15.199711] type=1505 audit(1331481720.875:7):  operation="profile_replace" pid=679 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   15.200197] type=1505 audit(1331481720.879:8):  operation="profile_replace" pid=679 name="/usr/lib/connman/scripts/dhclient-script"
[   15.208176] type=1505 audit(1331481720.887:9):  operation="profile_load" pid=683 name="/usr/bin/evince"
[   15.248174] type=1505 audit(1331481720.927:10):  operation="profile_load" pid=683 name="/usr/bin/evince-previewer"
[B][   15.318110] ipw2200: Radio Frequency Kill Switch is On:
[   15.318112] Kill switch must be turned off for wireless networking to work.[/B]
[   15.328082] type=1505 audit(1331481721.007:11):  operation="profile_load" pid=683 name="/usr/bin/evince-thumbnailer"
[   15.393582] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x126eb1, caps: 0xa04713/0x4000
[   15.412754] [drm] initialized overlay support
[   15.664153] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   15.665860] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   15.684124] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.684730] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.685519] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.688375] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   15.700498] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input10
[   15.763619] tg3 0000:06:08.0: firmware: requesting tigon/tg3_tso5.bin
[   16.121860] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.496378] fb0: inteldrmfb frame buffer device
[   16.496383] registered panic notifier
[   16.496394] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   16.496453] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.496479] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   16.502744] vga16fb: initializing
[   16.502749] vga16fb: mapped to 0xc00a0000
[   16.502754] vga16fb: not registering due to another framebuffer present
[   16.630251] Console: switching to colour frame buffer device 160x50
[   16.820035] intel8x0_measure_ac97_clock: measured 54214 usecs (2612 samples)
[   16.820041] intel8x0: clocking to 48000
[   17.638802] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   17.638807] tg3: eth0: Flow control is on for TX and on for RX.
[   17.639047] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.844969] ttyS1: LSR safety check engaged!
[   27.852020] eth0: no IPv6 routers present

```
```
XXX@XXX:~$ sudo lshw -C Network
[sudo] password for XXX: 
  *-network:0 DISABLED    
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:84:8a:bd
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:17 memory:b0118000-b0118fff
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 03
       serial: 00:c0:9f:a9:0f:20
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=full firmware=5788-v3.01 ip=192.168.1.103 latency=32 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:16 memory:b0100000-b010ffff

```
```
XXX@XXX:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 04)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 04)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 [8086:2664] (rev 04)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 04)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 04)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 04)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 04)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d4)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 04)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 04)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 04)
06:01.0 CardBus bridge [0607]: Texas Instruments PCIxx21/x515 Cardbus Controller [104c:8031]
06:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments OHCI Compliant IEEE 1394 Host Controller [104c:8032]
06:01.3 Mass storage controller [0180]: Texas Instruments PCIxx21 Integrated FlashMedia Controller [104c:8033]
06:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
06:08.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet [14e4:169c] (rev 03)

```
```
XXX@XXX:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

```
```
XXX@XXX:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

```
```
XXX@XXX:~$ uname -mr
2.6.32-21-generic i686

```
```
XXX@XXX:~$ lsb_release -d
Description:    Ubuntu 10.04 LTS

```
```
XXX@XXX:~$ lsmod | grep ipw2200
ipw2200               135216  0 
libipw                 39896  1 ipw2200
lib80211                5046  2 ipw2200,libipw

```
```
XXX@XXX:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```
```
XXX@XXX:~$ dmesg | tail
[   16.820035] intel8x0_measure_ac97_clock: measured 54214 usecs (2612 samples)
[   16.820041] intel8x0: clocking to 48000
[   17.638802] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   17.638807] tg3: eth0: Flow control is on for TX and on for RX.
[   17.639047] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.844969] ttyS1: LSR safety check engaged!
[   27.852020] eth0: no IPv6 routers present
[ 1195.850797] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[ 1195.850801] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[ 1195.850805] pcmcia: see http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html for details.

```
```

XXX@XXX:~$ cat /etc/rc.local
# added follow four lines 11 Mar 2012 - ade
# per http://ubuntuforums.org/showthread.php?t=1154721
ifdown eth1
rmmod ipw2200
modprobe ipw2200
ifup eth1

# following line is rc.local's default line - ade 
exit 0

```

Ok.  That's replicates pretty much everything from the thread above.  I'll be sitting by my keyboard waiting for the responses to flow in.  :)  


Thanks ... Allen.

---

### Post by oldos2er on 2012-03-11
Closed, necromancy. Please start a new thread for your question.

---

