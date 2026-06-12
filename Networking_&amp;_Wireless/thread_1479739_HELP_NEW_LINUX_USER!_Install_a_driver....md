---
title: "HELP NEW LINUX USER! Install a driver..."
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by brtnrider152 on 2010-05-11
OK you guys are going to laugh at me... I've been a windows user and just made the jump to ubuntu :) I LOVE IT! I have a dell and upgraded from 9.04 to 9.10 and my network card is not working.  So I found the driver, but as you know, its not like windows to install... here's what the README said Below. I have no idea what its saying.  Can someone dumb this driver installation down for me? I know it sounds dumb but my head is spinning! I need someone to walk me thought it.  I'm embarrassed but I can't figure it out! 

Thanks for you help!!!!!!!

<Linux device driver for Realtek Ethernet controllers>

    This is the Linux device driver released for RealTek RTL8168B/8111B, RTL8168C/8111C, RTL8168CP/8111CP, RTL8168D/8111D, RTL8168DP/8111DP, and RTL8168E/8111E Gigabit Ethernet controllers with PCI-Express interface.

<Requirements>

    - Kernel source tree (supported Linux kernel 2.6.x and 2.4.x)
    - For linux kernel 2.4.x, this driver supports 2.4.20 and latter.
    - Compiler/binutils for kernel compilation

<Quick install with proper kernel settings>
    Unpack the tarball :
        # tar vjxf r8168-8.aaa.bb.tar.bz2

    Change to the directory:
        # cd r8168-8.aaa.bb

    If you are running the target kernel, then you should be able to do :

        # ./autorun.sh    (as root or with sudo)

    You can check whether the driver is loaded by using following commands.

        # lsmod | grep r8168
        # ifconfig -a

    If there is a device name, ethX, shown on the monitor, the linux 
    driver is loaded. Then, you can use the following command to activate 
    the ethX.

        # ifconfig ethX up

        ,where X=0,1,2,...

<Set the network related information>
    1. Set manually
        a. Set the IP address of your machine.

            # ifconfig ethX "the IP address of your machine" 

        b. Set the IP address of DNS.

           Insert the following configuration in /etc/resolv.conf.
        
            nameserver "the IP address of DNS"

        c. Set the IP address of gateway.
"
            # route add default gw "the IP address of gateway

---

### Post by ankith13 on 2010-05-11
hi
    i am unable to make out your problem.... can you brief it a little more so as to what do you expect help in....the details of the installation given by you is enough and self explanatory. if still you have problem please tell me on which particular step do you need help....

---

### Post by prshah on 2010-05-11
> **brtnrider152 said:**
> I have a dell and upgraded from 9.04 to 9.10 and my network card is not working.

Before you do all this, first let's confirm that your network card actually needs a driver update. I doubt that a network card that worked in 9.04 will stop working in 9.10.

Can you please post back the output of the following terminal (Applications-Accessories-Terminal) commands```
lspci|grep -E network\|ethernet
lshw -C network
ifconfig
dmesg|grep eth

``` If the card is recognised, we can go on to solve your actual problem (net not working?) otherwise we can guide you step by step to install your new driver.

---

### Post by brtnrider152 on 2010-05-11
When I type in that command it says
"grep: Network: invalid context length argument"

---

### Post by pdc on 2010-05-11
I wonder if prshah means for the first entry

> lspci | grep Network

and for the final entry

> dmesg | grep eth

do you get any joy on those by copying and pasting them into a terminal?

---

### Post by brtnrider152 on 2010-05-11
this is what I get... not sure what it means...

                   [FONT=Courier]brennan@brennan-laptop:~$ dmesg | grep eth[/FONT]
  
  [FONT=Courier][    1.826586] eth0: RTL8168d/8111d at 0xf80dc000, 00:26:6c:10:49:26, XID 28300040 IRQ 30[/FONT]
  
  [FONT=Courier][   35.940926] r8169: eth0: link down[/FONT]
  
  [FONT=Courier][   35.941205] ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT]
  
  [FONT=Courier][  212.394799] r8169: eth0: link down[/FONT]
  
  [FONT=Courier][  212.395080] ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT]
  
  [FONT=Courier][  665.593086] r8169: eth0: link down[/FONT]
  
  [FONT=Courier][  665.593362] ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT]
  
  [FONT=Courier][  670.902869] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][  672.684452] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][  673.726748] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][  774.305321] r8169: eth0: link down[/FONT]
  
  [FONT=Courier][  774.305600] ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT]
  
  [FONT=Courier][ 4861.556317] Modules linked in: forcedeth nls_iso8859_1 nls_cp437 vfat fat binfmt_misc ppdev bridge stp bnep snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm b43 snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iptable_filter uvcvideo ip_tables snd_timer snd_seq_device dell_wmi psmouse dell_laptop btusb videodev x_tables mac80211 lp serio_raw dcdbas v4l1_compat cfg80211 snd led_class soundcore snd_page_alloc parport usbhid fbcon tileblit font bitblit softcursor usb_storage i915 drm i2c_algo_bit mii ssb video output intel_agp agpgart [last unloaded: r8169][/FONT]
  
  [FONT=Courier][ 4867.174709] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][ 4868.952988] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][ 4869.988604] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][ 6827.948298] Modules linked in: forcedeth nls_iso8859_1 nls_cp437 vfat fat binfmt_misc ppdev bridge stp bnep snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm b43 snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iptable_filter uvcvideo ip_tables snd_timer snd_seq_device dell_wmi psmouse dell_laptop btusb videodev x_tables mac80211 lp serio_raw dcdbas v4l1_compat cfg80211 snd led_class soundcore snd_page_alloc parport usbhid fbcon tileblit font bitblit softcursor usb_storage i915 drm i2c_algo_bit mii ssb video output intel_agp agpgart [last unloaded: r8169][/FONT]
  
  [FONT=Courier][ 6835.254779] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][ 7036.539279] Modules linked in: forcedeth nls_iso8859_1 nls_cp437 vfat fat binfmt_misc ppdev bridge stp bnep snd_hda_codec_realtek snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm b43 snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iptable_filter uvcvideo ip_tables snd_timer snd_seq_device dell_wmi psmouse dell_laptop btusb videodev x_tables mac80211 lp serio_raw dcdbas v4l1_compat cfg80211 snd led_class soundcore snd_page_alloc parport usbhid fbcon tileblit font bitblit softcursor usb_storage i915 drm i2c_algo_bit mii ssb video output intel_agp agpgart [last unloaded: r8169][/FONT]
  
  [FONT=Courier][ 7040.110556] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][ 7042.001622] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][ 7042.572089] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][ 7043.632302] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882), AE_TIME[/FONT]
  
  [FONT=Courier][ 7045.347706] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.LPCB.EC0_.BAT0._BST] (Node f701882, AE_TIME[/FONT]

---

### Post by prshah on 2010-05-11
> **brtnrider152 said:**
> 
  [FONT=Courier][    1.826586] eth0: RTL8168d/8111d at 0xf80dc000, 00:26:6c:10:49:26, XID 28300040 IRQ 30[/FONT]
  [FONT=Courier][   35.940926] r8169: eth0: link down[/FONT]
  
  [FONT=Courier][   35.941205] ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT]
  
  [FONT=Courier][  212.394799] r8169: eth0: link down[/FONT]
  
  [FONT=Courier][  212.395080] ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT]
  
  [FONT=Courier][  665.593086] r8169: eth0: link down[/FONT]
  
  [FONT=Courier][  665.593362] ADDRCONF(NETDEV_UP): eth0: link is not ready[/FONT]

I don't think you need to install and/or compile a custom driver. Your eth card seems to be recognized, but cannot be certain unless you post back the other outputs.

There is nothing wrong with the commands; you must have typed it in wrong to get the error that you did. However, it may be better to use "-iE" instead of "-E" in the first command; but now that commands not much required. Please post the output of the other commands, as well as ```
sudo ethtool eth0
#if you get an error with that command, try
sudo mii-tool eth0
```

---

### Post by brtnrider152 on 2010-05-11
This is what I get when I type that. 





brennan@brennan-laptop:~$ sudo ethtool eth0
  
  [sudo] password for brennan: 
  
  Settings for eth0:
  
  Cannot get device settings: No such device
  
  Cannot get wake-on-lan settings: No such device
  
  Cannot get message level: No such device
  
  Cannot get link status: No such device
  
  No data available

---

