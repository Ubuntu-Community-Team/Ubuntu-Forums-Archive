---
title: "[SOLVED] (8.10) Netgear WG511 disabled after reboot."
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by sceri on 2008-12-28
Hi.

PS: {
At first I would like to say that I'm linux user for 2 days so my experience is really poor.
Secondly, sorry for my english.
}

I posting this thread because I have got a problem with my PCMCIA WiFi Adapter. ```
03:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)
```

According to description in below I installed:
[HTML]https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper
[/HTML]```
For 8.10 Intrepid Ibex
   1.http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common
   2 http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9
   3.http://packages.ubuntu.com/intrepid/net/ndisgtk
```


than I add to blacklist:
```
echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist
```

and installed: cabextract and unshield. 

Next step: [System -> Administration -> Windows Wireless Drivers], I installed driver called "smc2802wnic.inf" (*.sys and *.arm files are in same folder) and suddenly I saw box with information that my PCMCIA found my WLAN. I tape password and network was established correctly. 

I done everything depicted in 3.7. 'Automatically loading at start-up'.

Everything was working fine... until I reboot my computer.

Now, my WG511 is 'dead'. LEDs aren't shining, even if I put PCMCIA into my PC again. In Windows Wireless Driver after try to get in 'Configure Network' I see: ```
Could not find a network configuration tool.
```


[lsmod | grep ndiswrapper]
```
ndiswrapper           196380  0 
usbcore               148848  4 ndiswrapper,uhci_hcd,ehci_hcd
```

[iwconfig]
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```

[sudo lshw -C network]
```
sceri@sceri-laptop:~$ sudo lshw -C network
[sudo] password for sceri: 
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:65:84:d2
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.2.100 latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 1
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:c1:59:51:c3:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


thnx in advice,
sceri

---

### Post by pytheas22 on 2008-12-28
Please post the output of these commands:
```

dmesg | grep -e ndis -e wlan
ndiswrapper -l
```

---

### Post by sceri on 2008-12-28
```
sceri@sceri-laptop:~$ dmesg | grep -e ndis -e wlan
[   21.587279] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   21.669820] IP: [<debf1e3f>] :ndiswrapper:link_pe_images+0x3f/0x600
[   21.669870] Modules linked in: ndiswrapper(+) pcmcia(+) joydev snd_intel8x0 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm container snd_seq_dummy yenta_socket rsrc_nonstatic video output pcmcia_core wmi snd_seq_oss battery ac snd_seq_midi button snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device psmouse intel_agp snd evdev agpgart iTCO_wdt iTCO_vendor_support serio_raw soundcore snd_page_alloc shpchp pci_hotplug pcspkr ext3 jbd mbcache sr_mod cdrom sd_mod crc_t10dif sg ata_piix ata_generic 8139too pata_acpi libata 8139cp mii uhci_hcd ehci_hcd scsi_mod dock usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[   21.669945] Pid: 3430, comm: loadndisdriver- Tainted: P          (2.6.27-9-generic #1)
[   21.669969] EIP is at link_pe_images+0x3f/0x600 [ndiswrapper]
[   21.669984] Process loadndisdriver- (pid: 3430, ti=dd924000 task=db0c0000 task.ti=dd924000)
[   21.670060]  [<debe53ca>] ? load_sys_files+0x12a/0x230 [ndiswrapper]
[   21.670079]  [<debee538>] ? ExAllocatePoolWithTag+0x38/0x80 [ndiswrapper]
[   21.670114]  [<debe6331>] ? load_user_space_driver+0x131/0x420 [ndiswrapper]
[   21.670143]  [<debe66fd>] ? wrapper_ioctl+0xdd/0x1b0 [ndiswrapper]
[   21.670337] EIP: [<debf1e3f>] link_pe_images+0x3f/0x600 [ndiswrapper] SS:ESP 0068:dd925db8
[   21.670578] ndiswrapper (load_wrap_driver:108): couldn't load driver smc2802wnic; check system log for messages from 'loadndisdriver'
[   21.672310] usbcore: registered new interface driver ndiswrapper
```


```
sceri@sceri-laptop:~$ ndiswrapper -l
smc2802wnic : driver installed
	device (1260:3890) present (alternate driver: p54pci)
```

---

### Post by pytheas22 on 2008-12-28
hmmmm, it seems that there's a problem loading the ndiswrapper driver for some reason.  This is very weird since you say it worked fine the first time.

Could you please try uninstalling ndiswrapper by typing:

```
sudo apt-get remove --purge ndiswrapper*
```

Then reinstall ndiswrapper again by repeating the original steps.  Does this solve the problem?

Also, if you type this command does the card work:

```
sudo modprobe p54pci
```

---

### Post by sceri on 2008-12-28
Netgear still doesn't work.

However, maybe I should try use another driver instead of smc2802wnic.inf.
How can I take *.inf file out of *.exe?

[http://kbserver.netgear.com/release_notes/d102743.asp]("http://kbserver.netgear.com/release_notes/d102743.asp")

---

### Post by sceri on 2008-12-28
> Also, if you type this command does the card work:

```
sudo modprobe p54pci
```

YES!!

I see my network and I can connect.
>

However, after reboot it was the same, so o type this command again.
What should I do to get connected automatically?

---

### Post by pytheas22 on 2008-12-28
> However, after reboot it was the same, so o type this command again.
What should I do to get connected automatically? 

I'm glad that did it.  To make this driver load automatically at boot, try running this command once:
```

echo p54pci | sudo tee -a /etc/modules
```

Then, after a reboot, does the wireless card work automatically?

---

### Post by sceri on 2008-12-29
Works great! Thank you very much. :)

---

