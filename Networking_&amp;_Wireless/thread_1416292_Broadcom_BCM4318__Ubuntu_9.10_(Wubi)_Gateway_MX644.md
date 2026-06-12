---
title: "Broadcom BCM4318 / Ubuntu 9.10 (Wubi)/ Gateway MX6445 / Total beginner"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by Fazulka on 2010-02-25
I want to preface by saying that I decided to try linux the first time earlier today, so I may not understand complicated replies.
 
I have a gateway MX6445 laptop, you can find all info about it here : [http://support.gateway.com/s/Mobile/Q106/Blade/1009110nv.shtml](http://support.gateway.com/s/Mobile/Q106/Blade/1009110nv.shtml)
 
I installed Ubuntu through Wubi from [http://wubi-installer.org/](http://wubi-installer.org/)
 
So far, I haven't tried to do anything but get wireless working, and failed at that. The wireless is much less intuitive than I would have guessed.
 
From looking at HOWTO post a wireless issue here is some information, I hope it is not too much to read:
 
[FONT=Times New Roman][SIZE=3]biglaptop@ubuntu:~$ lspci[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]05:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]05:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]05:09.4 SD Host controller: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller[/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]biglaptop@ubuntu:~$ lsusb[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Bus 003 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]biglaptop@ubuntu:~$ ifconfig[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]eth0 Link encap:Ethernet HWaddr 00:e0:b8:b5:98:b8 [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]UP BROADCAST MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]collisions:0 txqueuelen:1000 [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Interrupt:18 [/FONT][/SIZE]
 
 
 
[SIZE=3][FONT=Times New Roman]lo Link encap:Local Loopback [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]inet addr:127.0.0.1 Mask:255.0.0.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]inet6 addr: ::1/128 Scope:Host[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]UP LOOPBACK RUNNING MTU:16436 Metric:1[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]collisions:0 txqueuelen:0 [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]RX bytes:240 (240.0 B) TX bytes:240 (240.0 B)[/FONT][/SIZE]
 
 
[FONT=Times New Roman][SIZE=3]biglaptop@ubuntu:~$ iwconfig [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]lo no wireless extensions.[/SIZE][/FONT]
 
 
 
[FONT=Times New Roman][SIZE=3]eth0 no wireless extensions.[/SIZE][/FONT]
 
 
 
[FONT=Times New Roman][SIZE=3]wmaster0 no wireless extensions.[/SIZE][/FONT]
 
 
 
[SIZE=3][FONT=Times New Roman]wlan0 IEEE 802.11bg ESSID:"" [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Mode:Managed Frequency:2.412 GHz Access Point: Not-Associated [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Tx-Power=0 dBm [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Retry long limit:7 RTS thr:off Fragment thr:off[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Power Management:off[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Link Quality:0 Signal level:0 Noise level:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/FONT][/SIZE]
 
 
[FONT=Times New Roman][SIZE=3]biglaptop@ubuntu:~$ lsmod[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Module Size Used by[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]usbhid 43968 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]nls_iso8859_1 5280 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]nls_cp437 6976 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]vfat 13184 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]fat 59832 1 vfat[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]usb_storage 65952 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]binfmt_misc 10220 1 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ppdev 8232 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_atiixp 19284 2 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_atiixp_modem 14604 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_ac97_codec 125720 2 snd_atiixp,snd_atiixp_modem[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_pcm_oss 44704 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_mixer_oss 18976 1 snd_pcm_oss[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ac97_bus 2176 1 snd_ac97_codec[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]arc4 2144 2 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq_dummy 3460 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_pcm 93160 4 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq_oss 33440 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ecb 3296 2 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq_midi 8192 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_rawmidi 27360 1 snd_seq_midi[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq_midi_event 8448 2 snd_seq_oss,snd_seq_midi[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq 60608 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_timer 26992 2 snd_pcm,snd_seq[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]b43 136552 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]iptable_filter 3872 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_seq_device 8308 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ip_tables 21200 1 iptable_filter[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]joydev 13088 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]x_tables 25832 1 ip_tables[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]mac80211 210104 1 b43[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd 77096 15 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]pcmcia 40116 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]soundcore 9088 1 snd[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]cfg80211 109144 2 b43,mac80211[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]sdhci_pci 8928 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]snd_page_alloc 10928 3 snd_atiixp,snd_atiixp_modem,snd_pcm[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]sdhci 20484 1 sdhci_pci[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]tifm_7xx1 6784 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]i2c_piix4 11728 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]yenta_socket 27500 1 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]tifm_core 9864 1 tifm_7xx1[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]rsrc_nonstatic 11840 1 yenta_socket[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]shpchp 37756 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]psmouse 57124 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]k8temp 5504 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]led_class 5256 2 b43,sdhci[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]pcmcia_core 41796 3 pcmcia,yenta_socket,rsrc_nonstatic[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]amd64_edac_mod 26688 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]edac_core 48876 1 amd64_edac_mod[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]serio_raw 6596 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]lp 11908 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]parport 40528 2 ppdev,lp[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ohci1394 33780 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ieee1394 100896 1 ohci1394[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ssb 40944 1 b43[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]radeon 684512 2 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]ttm 43056 1 radeon[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]drm 193856 4 radeon,ttm[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]i2c_algo_bit 7076 1 radeon[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]sky2 55556 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]video 23612 0 [/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]output 3680 1 video[/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]biglaptop@ubuntu:~$ sudo lshw -C network[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3][sudo] password for biglaptop: [/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]*-network [/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]description: Ethernet interface[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]product: 88E8036 PCI-E Fast Ethernet Controller[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]vendor: Marvell Technology Group Ltd.[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]physical id: 0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:03:00.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]logical name: eth0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]version: 10[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]serial: 00:e0:b8:b5:98:b8[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]capacity: 100MB/s[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]width: 64 bits[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]resources: irq:18 memory:d0200000-d0203fff ioport:a000(size=256)[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]*-network[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]description: Network controller[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]vendor: Broadcom Corporation[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]physical id: 2[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]bus info: pci@0000:05:02.0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]version: 02[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]width: 32 bits[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]clock: 33MHz[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]capabilities: bus_master[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]configuration: driver=b43-pci-bridge latency=64[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]resources: irq:22 memory:d0304000-d0305fff[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]*-network DISABLED[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]description: Wireless interface[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]physical id: 1[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]logical name: wlan0[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]serial: 00:c0:a8:bc:40:cd[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]capabilities: ethernet physical wireless[/FONT][/SIZE]
 
[SIZE=3][FONT=Times New Roman]configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg[/FONT][/SIZE]
 
 
[FONT=Times New Roman][SIZE=3]biglaptop@ubuntu:~$ iwlist scan[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]lo Interface doesn't support scanning.[/SIZE][/FONT]
 
 
 
[FONT=Times New Roman][SIZE=3]eth0 Interface doesn't support scanning.[/SIZE][/FONT]
 
 
 
[FONT=Times New Roman][SIZE=3]wmaster0 Interface doesn't support scanning.[/SIZE][/FONT]
 
 
 
[FONT=Times New Roman][SIZE=3]wlan0 Failed to read scan data : Network is down[/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]biglaptop@ubuntu:~$ lsb_release -d[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Description: Ubuntu 9.10[/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]biglaptop@ubuntu:~$ uname -mr[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]2.6.31-14-generic x86_64[/SIZE][/FONT]
 
 
[FONT=Times New Roman][SIZE=3]biglaptop@ubuntu:~$ sudo /etc/init.d/networking restart[/SIZE][/FONT]
 
[SIZE=3][FONT=Times New Roman]* Reconfiguring network interfaces... [ OK ][/FONT][/SIZE]
 
So, where should I start? Is it a problem with drivers or do I just not understand how to connect?

---

### Post by n0dix on 2010-02-25
Do you use netwokmanager to manage your wireless?

---

### Post by Fazulka on 2010-02-26
Is networkmanager already installed in ubuntu 9.10?  I don't think I used that.

---

### Post by Fazulka on 2010-02-26
Can anyone help?  I was really excited to try linux, but it just seems incredibly far behind since the seems to be no way to make it work.  I have tried following some of the ndiswrapper things, but with no wired connection it seems impossible, and I not able to find half the folders people talk about in posts.

---

### Post by pastalavista on 2010-02-26
Connect your PC directly to the router via ethernet. Then open System|Administration|Hardware Drivers so it can search for the "missing wireless extensions" or the drivers for your wireless card. 

This page might help: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")

---

### Post by mathgeek2000 on 2010-02-26
[QUOTE=pastalavista;8886697]Connect your PC directly to the router via ethernet [Cable]. Then open System|Administration|Hardware Drivers so it can search for the "missing wireless extensions" or the drivers for your wireless card. 

I think PastaLavista is correct here. As I recall, I had to activate the Broadcom B43 Wireless Driver, before I got Wireless working. I have an HP with a BCM4312 Wireless Card. System | Administration | Hardware Drivers brings up the B43 (Open Source), and STA (Proprietary) drivers. I've had luck with the B43 drivers, and haven't needed to try the STA one.

---

### Post by Fazulka on 2010-02-26
> **pastalavista said:**
> Connect your PC directly to the router via ethernet. Then open System|Administration|Hardware Drivers so it can search for the "missing wireless extensions" or the drivers for your wireless card. 
 
This page might help: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
 
I found this link and tied it, but now under the little connection icon it no longer shows wireless at all.  when I go to system - administration - hardware driver it now gives me a mesasge about software modem.  I have tried activating and removeing the proprietary drivers and it does not seem to change anything.
 
have i made things worse?  should i uninstall wubi and start over?

---

### Post by jdk82 on 2010-03-03
I'm not sure which section of the tutorial you followed, but it sounds like you did this:

```
~$ sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

If so, you installed a driver for a different model of card. To correct this, do the opposite:

```
sudo apt-get remove bcmwl-kernel-source && sudo apt-get autoremove
```

Reboot, and then (with a wired internet connection) either follow pastalavista's instructions, or run:

```
~$ sudo apt-get install b43-fwcutter
```

This will likely require a reboot, and you also need to make sure that any hardware switch (a button on the laptop or combination of the FN button and one of the F*) that controls the wireless NIC is set to on.

Hope this helps.

Josh

---

