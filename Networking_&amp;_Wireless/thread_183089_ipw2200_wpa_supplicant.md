---
title: "ipw2200 wpa_supplicant"
date: 2006-05-27
forum: Networking &amp; Wireless
---

### Post by shizow on 2006-05-27
since i upgraded to dapper (kubuntu), my wpa_supplicant doesnt work anymore

```

shizow@tunein:~/wifi$ sudo wpa_supplicant -B -i eth1 -c /home/shizow/wifi/wpa_supplicant.home.conf -D ipw -w -dd
Daemonize..
shizow@tunein:~/wifi$  

```

now it just says daemonize, before there was much more output

```

dmesg | grep ipw
[4294682.313000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.1
[4294682.313000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[4294682.313000] Warning: PCI driver ipw2200 has a struct device_driver shutdown method, please update!
[4294682.563000] Modules linked in: ipw2200 snd_intel8x0 snd_ac97_codec snd_ac97_bus sir_dev nsc_ircc hci_usb irda snd_pcm_oss snd_mixer_oss ieee80211 ieee80211_crypt bluetooth crc_ccitt psmouse floppy snd_pcm yenta_socket rsrc_nonstatic rtc ieee80211_1_1_13 ieee80211_1_1_13_crypt tg3 serio_raw pcspkr parport_pc parport snd_timer pcmcia_core snd soundcore snd_page_alloc intel_agp agpgart shpchp pci_hotplug sr_mod cdrom evdev sg ext3 ide_generic ehci_hcd uhci_hcd usbcore sd_mod generic ata_piix ahci libata scsi_mod thermal processor fan jbd capability commoncap vesafb fbcon tileblit font bitblit softcursor
[4294683.234000] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[4294683.504000] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)

```

KNetworkmanager says no network device found

---

### Post by shizow on 2006-05-31
can anyone please help

---

### Post by nickle on 2006-05-31
Check out this link on the wiki:
[https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29](https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29)

Some stuff has changed since Breezy... myabe your porblem lies there...

---

### Post by emda on 2006-06-06
[QUOTE=nickle]...
[https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29](https://wiki.ubuntu.com/WPAHowto?highlight=%28wpa%29)
...
[/QUOTE]

I'm also having a problem with ipw2200 & wpa_supplicant. The way the wiki describes how its done in 6.06 conflict with what i see on my machine..

> 
For Ubuntu 6.06 this is a lot easier: If you do not see a network icon near your power information in gnome, you'll need to install network-manager-gnome. After installing the package logout and log back in (or re-start) and network manager should appear. Right click the network manager icon to enable network if necessary. Next, left click on the network manager icon and choose "Connect to other wireless network". Then, enter "YOUR-SSID" for the network name and choose your type "WPA ENTERPRISE" or "WPA PERSONAL" etc, etc ... for wireless security. Enter the password in the password text entry box. Click connect to attempt a connection.


When i  right click on the network manager icon, my wireless card (eth0) does not appear in the list, when i click configure and goto the networking app that is listed under System/Administration I dont see options for WPA ENTERPRISE nor WPA Personal, just WEP Key...

---

### Post by emda on 2006-06-06
Ok, maybe i spoke a bit prematurely before, the text on the ubuntu page stating what to do in 6.06 is insufficent however the readme.modes link on the debian site was what I needed to get this working...

[http://svn.debian.org/wsvn/pkg-wpa/trunk/wpasupplicant/debian/README.modes?op=file&rev=0&sc=0]("http://svn.debian.org/wsvn/pkg-wpa/trunk/wpasupplicant/debian/README.modes?op=file&rev=0&sc=0")
> 
example /etc/network/interfaces stanza:
   
   iface wlan0 inet dhcp
           wpa-conf /home/user/.wpa/wpa_supplicant.conf
using the above format you can get wpa working again w/o having to toss out your wpa_supplicant.conf & convert it to the 'managed' /etc/network/interface style.

---

