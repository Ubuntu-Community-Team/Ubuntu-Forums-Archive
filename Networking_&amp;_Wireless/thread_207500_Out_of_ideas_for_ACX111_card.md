---
title: "Out of ideas for ACX111 card"
date: 2006-07-02
forum: Networking &amp; Wireless
---

### Post by danj205 on 2006-07-02
After getting a new, bigger hard drive, I thought now would be best to get Linux installed for some university work. We connect to the internet via a wireless network. I have a standard, no name brand wireless card that works perfectly well under Windows XP.

I installed Ubuntu Dapper, first seeing if I could access the internet under the live CD, but couldn't. So I continued to install knowing that I'll only be able to do anything when it is fully installed.

When I first installed Ubuntu, the wireless was detected (as under Live) and "active", so I went and typed in the SSID (it is hidden) and tried connecting to no avail. I found out that the chipset is a **Texas Instruments ACX111**, which I see a lot of talk about. (104c:9066) When I type "iwlist wlan0 scan" it does show the access point.

I tried the OS drivers, they didn't work. Tried compiling drivers, they didn't work. I tried NDISWrapper with the drivers included on the CD, they didn't work. I tried again with the SSID broadcast, but that didn't work. I also tried modifying the .conf file that NDIS makes with the registry settings, and copied over most of the registry settings that are present under Windows but not the conf file.

I'm all out of ideas now, and wondering if anyone had anymore to share. I am slightly more than a n00b at Linux, as I have tried it off and on over the past few years. Any help would be greatly appreciated.

---

### Post by thedarksavant on 2006-07-02
[QUOTE=danj205]After getting a new, bigger hard drive, I thought now would be best to get Linux installed for some university work. We connect to the internet via a wireless network. I have a standard, no name brand wireless card that works perfectly well under Windows XP.

I installed Ubuntu Dapper, first seeing if I could access the internet under the live CD, but couldn't. So I continued to install knowing that I'll only be able to do anything when it is fully installed.

When I first installed Ubuntu, the wireless was detected (as under Live) and "active", so I went and typed in the SSID (it is hidden) and tried connecting to no avail. I found out that the chipset is a **Texas Instruments ACX111**, which I see a lot of talk about. (104c:9066) When I type "iwlist wlan0 scan" it does show the access point.

I tried the OS drivers, they didn't work. Tried compiling drivers, they didn't work. I tried NDISWrapper with the drivers included on the CD, they didn't work. I tried again with the SSID broadcast, but that didn't work. I also tried modifying the .conf file that NDIS makes with the registry settings, and copied over most of the registry settings that are present under Windows but not the conf file.

I'm all out of ideas now, and wondering if anyone had anymore to share. I am slightly more than a n00b at Linux, as I have tried it off and on over the past few years. Any help would be greatly appreciated.[/QUOTE]

Have you tried [https://help.ubuntu.com/community/WifiDocs/Driver/acx100?highlight=%28dwl%29%7C%28650%2B%29](https://help.ubuntu.com/community/WifiDocs/Driver/acx100?highlight=%28dwl%29%7C%28650%2B%29)

---

### Post by Agent86 on 2006-07-02
[QUOTE=danj205]I'm all out of ideas now, and wondering if anyone had anymore to share. I am slightly more than a n00b at Linux, as I have tried it off and on over the past few years. Any help would be greatly appreciated.[/QUOTE]
If you can see your access point in a scan, you're almost there.

Are you trying to use WPA, WEP, or no encryption?

---

### Post by danj205 on 2006-07-03
No encryption.

And to darksavant, yes I tried compiling the ACX drivers myself, but didn't succeed, so that's when I proceeded to install the NDIS wrapper.

---

### Post by Agent86 on 2006-07-03
[QUOTE=danj205]No encryption.[/QUOTE]OK, from a fresh reboot, what are the results from these commands```
dmesg | grep ndis
``````
lsmod | grep acx
```And what are the contents of /etc/network/interfaces (mask out any sensitive information).

Since we've got some scan results with ndiswrapper we'll try to get that working. However, if (and only if) you ever decide to reinstall Dapper, it might be better to tweak the orignal ACX drivers into shape instead; they almost always work, as long as you don't need WPA. From the way you describe things, it sounds like we might have gotten the ACX drivers from the Dapper install working with a firmware change by editing /etc/modprobe.d/options or a configuration adjustment by editing /etc/network/interfaces

---

### Post by danj205 on 2006-07-03
[QUOTE=Agent86]
However, if (and only if) you ever decide to reinstall Dapper, it might be better to tweak the orignal ACX drivers into shape instead;[/QUOTE]
I have actually been thinking about reinstalling Dapper and trying out those configs, however when I can reboot I'll do those dmsg commands and put them up here.

---

### Post by danj205 on 2006-07-03
Argh, I did something on Ubuntu and the quickest solution was to reinstall it. So this time I haven't done anything yet, except for playing around with the firmware_ver option. I tried the default... ap was detected. 1.2.0.30, detected ap, but did nothing. 1.2.1.34 did the same. I just used the Administration -> Network tool to modify the settings. wlan0 was active, and when I went to properties the access point did get onto the list.

After going iwconfig wlan0 essid "xxx xxx", and repeating it for channel, I then went iwconfig and got:

IEEE 802.11b+/g+  ESSID:"xxx xxx"  Nickname:"acx v0.3.21"
Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated
Bit Rate:1 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
Retry min limit:7   RTS thr:off
Power Management:off
Link Quality:45/100  Signal level:23/100  Noise level:0/100
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Now, the access point is still not being associated (even after giving it it's MAC), and the bit rate is wrong. Thing is the link and signal levels are better than what they were previously with NDIS and ACX driver recompilation.

lsmod | grep acx returns:
acx                   101132  0
usbcore               129668  5 acx,usbhid,ehci_hcd,uhci_hcd

---

### Post by Agent86 on 2006-07-04
[QUOTE=danj205]Now, the access point is still not being associated (even after giving it it's MAC), and the bit rate is wrong. Thing is the link and signal levels are better than what they were previously with NDIS and ACX driver recompilation.

lsmod | grep acx returns:
acx                   101132  0
usbcore               129668  5 acx,usbhid,ehci_hcd,uhci_hcd[/QUOTE]Things look pretty good, we just have to go the last few steps. You changed firmware by adding the line```
options acx firmware_ver=1.2.1.34
```to the end of /etc/modprobe.d/options ? Is it 1.2.1.34 now or 1.2.0.30 ?

Please post the results of this command```
dmesg | grep acx
```Also post the entire contents of the file /etc/network/interfaces  (mask out any sensitive information)  This file is very important, any problems in here will probably keep things from working.

---

### Post by danj205 on 2006-07-04
No :oops: , I just fixed it, it is now 1.2.1.34.

Dmesg:
```
[4294687.135000] acx: Loaded combined PCI/USB driver, firmware_ver=1.2.1.34
[4294687.135000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[4294687.135000] acx: found ACX111-based wireless network card at 0000:05:00.0, irq:58, phymem1:0xF0424000, phymem2:0xF0400000, mem1:0xf8a58000, mem1_size:8192, mem2:0xf8bc0000, mem2_size:131072
[4294688.195000] Modules linked in: irtty_sir sir_dev irda crc_ccitt parport_pc parport snd_emu10k1 snd_rawmidi snd_ac97_codec snd_ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem snd_hwdep snd emu10k1_gp acx soundcore tg3 floppy gameport nvidia i2c_core pcspkr psmouse serio_raw rtc intel_agp shpchp pci_hotplug agpgart tsdev evdev sg ext3 jbd usbhid ide_generic uhci_hcd ohci1394 ieee1394 ehci_hcd usbcore sr_mod cdrom sd_mod generic ata_piix ahci libata scsi_mod via82cxxx thermal processor fan capability commoncap vga16fb vgastate fbcon tileblit font bitblit softcursor
[4294688.815000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
[4294688.815000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-23-386
[4294688.815000] usbcore: registered new driver acx_usb
```

And my interfaces file:
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid xxx xxx
```

---

### Post by Agent86 on 2006-07-04
[QUOTE=danj205]
```
auto lo
iface lo inet loopback

iface eth0 inet dhcp

iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid xxx xxx
```[/QUOTE]Do you have another wireless card in that PC? I'm wondering where the ath0 interface came from. If you're not sure you're using it, comment the lines out with a # at the sart of each line dealing with ath0

OK, first do a```
sudo ifdown wlan0
```then edit the last group of lines in /etc/network/interfaces to read```
auto wlan0
iface wlan0 inet dhcp
wireless_essid xxx xxx
wireless_mode managed
```That's an underscore between wireless and the next word, not a hyphen. You can also comment out those ath0 lines. Now do a```
sudo ifup wlan0
```and see if you get an IP.

SANITY (mine) CHECK: your access point is set up for dhcp, right? Also, the access point essid is a single word or block of characters, right? Like My_ESS and not My ESS .

---

### Post by danj205 on 2006-07-04
> SANITY (mine) CHECK: your access point is set up for dhcp, right? Also, the access point essid is a single word or block of characters, right? Like My_ESS and not My ESS .
It is the latter. (Don't look at me, I didn't set it up :P ) Do I need to change it so then it is just one word?

And yeah, it is DHCP.

---

### Post by Agent86 on 2006-07-04
[QUOTE=danj205]It is the latter. (Don't look at me, I didn't set it up :P ) Do I need to change it so then it is just one word?

And yeah, it is DHCP.[/QUOTE]If you can do so, set it up so it's one word or block of non-space characters. I -think- you coould enclose it in double quotes like "My ESS" but I'm not sure that it would work.

---

### Post by danj205 on 2006-07-04
Nope, I got the message "No DHCPOFFER". Everything is check, except for the bandwidth (it now reports 2Mb/s, on Windows I can usually get 54Mb/s).

---

### Post by mraudiofreak on 2006-07-07
Someone in this thread already mentioned the solution, but not the easiest way. I have the same problem and all I have to do is add the line
options acx firmware_ver=1.2.1.34
to the /etc/modprobe.d/options file.

---

