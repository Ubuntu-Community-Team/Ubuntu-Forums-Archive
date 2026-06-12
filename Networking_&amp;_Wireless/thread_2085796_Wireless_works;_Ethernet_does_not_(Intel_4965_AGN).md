---
title: "Wireless works; Ethernet does not (Intel 4965 AGN)"
date: 2012-11-19
forum: Networking &amp; Wireless
---

### Post by xiaobi on 2012-11-19
First of all, thanks for looking at this thread! This is my first post, so I'm a bit of an amateur as far as etiquette and convention goes on this board, so please bear with me.

My current problem is as the topic title says: my wireless connection works, but my wired does not. This wouldn't be a huge issue normally, but the wireless I have access to is a bit shoddy at times, and it's a massive inconvenience at times, to say the least.

I have searched through these forums for solutions before, and through Google. Nothing's worked so far, and the reason I'm posting now is because one of the solutions perhaps was not calibrated for my computer, and I managed to disable my wireless in trying to execute it. Subsequently, I had to reinstall Ubuntu entirely just to get it to work again, so I'm a bit wary of delving into the unguided do-it-yourself realm of troubleshooting Ubuntu.

As far as my computer goes, I have an HP Pavilion dv2000, according to the little nametag above the screen, though, as I recall, when I had Windows, the Windows-Pause menu showed that it was a dv2200. Not really sure why that was.

As far as my network card goes, I have a:

Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

I don't know if that's relevant to the wired connection. I remember using some command that showed me its capabilities, and I think ethernet was listed as a function.

Any help in resolving this issue would be fantastically appreciated.

Oh, and happy early Thanksgiving!

---

### Post by ahallubuntu on 2012-11-19
The Intel 4965AGN card is your wireless card only.  It is not related to the wired connection.

To find out more information about your wired connection, try this at a terminal:

```
sudo lshw -C network
```

and

```
ifconfig
```

Is this a new installation of Ubuntu?  What version?  Did wired internet ever work in Ubuntu, or did this problem just start?  Does wired not work even when the laptop is plugged into AC power?

By the way, look on the bottom of your laptop to find out the exact model  number.

---

### Post by xiaobi on 2012-11-19
```
xiaobi@xubuntu:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:1c:a5:01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 driverversion=3.2.0-33-generic-pae firmware=228.61.2.24 ip=172.17.105.96 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:46 memory:f4200000-f4201fff
xiaobi@xubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:488252 (488.2 KB)  TX bytes:488252 (488.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:13:e8:1c:a5:01  
          inet addr:172.17.105.96  Bcast:172.17.111.255  Mask:255.255.248.0
          inet6 addr: fe80::213:e8ff:fe1c:a501/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77743 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64493 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42655673 (42.6 MB)  TX bytes:16264627 (16.2 MB)
```

This is a new install of Ubuntu, version 12.04 LTS, though it was installed as just 12, I think. As far as I know, the wired has never worked in Ubuntu, though it worked in Windows, and my laptop is always plugged into the wall.

I don't see anything about the model number on the bottom... there used to be a Windows sticker with the product or serial number, but it seems to have been worn away now. Is that important to know?

The UP BROADCAST RUNNING MULTICAST message came from one of my other attempts to fix it, I think. There was some command for the ethernet that involved the word "up". I could probably find it again, if that's relevant.

Thanks for the response, by the way!

---

### Post by ahallubuntu on 2012-11-19
No ethernet card is showing up at all - it should show in the output of "lshw."

Are you sure the card is enabled?  Please check in your BIOS Setup to make sure the card is not disabled there (there may not be an option to disable it - but check just in case).

It's always possible the ethernet card hardware has failed.  If you plug a cable from your laptop into a router, do you see a link light come on in or near the connector on your laptop?  Does a light come on on the router.  For example, a router typically has numbered lights 1 2 3 4 one for each LAN port; if you connect a cable from port 2 to the back of your laptop, the 2 light on the router should light up.  Does that happen?

If your ethernet card has failed, you have the option of getting a USB to ethernet adapter to use instead of wireless.

---

### Post by xiaobi on 2012-11-19
Okay, I checked through the BIOS setup menu, but I couldn't find anything related to the ethernet card.

I don't have a router... I live in an apartment complex, so the wireless and wired are all centralized elsewhere. My current option to connect with an ethernet cable is straight from the wall, which doesn't appear to have any lights. The TV's internet works from the wall, and I tested my laptop with that, with no results. I recall there being a light that would come on before when I was using Windows from the laptop socket itself, but it doesn't seem to go off anymore.

Is there any other way of checking the status of my ethernet card?

---

### Post by xiaobi on 2012-11-19
Um... I've no idea about the rules here about bumping topics, but I posted this a bit late at night and it's kinda getting buried. Could I get any more insight?

---

### Post by dannyboy79 on 2012-11-19
well, currerntly the lshw command which is suppose to show hardware didn't show your ethernet hardware. Does this command return any relevant info on your ethernet card?

```
sudo lspci
```


PS don't BUMP your own threads prior to it being 24 hours. Remember, everyone here helping is just doing it voluntarily.

---

### Post by xiaobi on 2012-11-19
Here's the output I get:

```
xiaobi@xubuntu:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```

Thanks for the reply!

EDIT: Sorry about the bump, I wasn't aware of the conventions here. I'll keep it in mind, though!

---

### Post by kurt18947 on 2012-11-19
If I may intrude a bit, I too don't see an ethernet card.  If there's no BIOS or physical switch disconnect, it may have failed.  Drivers are not usually an issue with Ubuntu & ethernet devices.  Wifi can be another story.   If an ethernet connection is preferable, there are ethernet-USB adapters  that are not terribly expensive, $20 U.S. and up on Newegg.com

---

### Post by xiaobi on 2012-11-19
Dang.

Well, in that case, is there any that comes particularly recommended? Like, is there a list anywhere of adapters that are known to work with Ubuntu?

Thanks everyone.

---

### Post by kurt18947 on 2012-11-19
> **xiaobi said:**
> Dang.

Well, in that case, is there any that comes particularly recommended? Like, is there a list anywhere of adapters that are known to work with Ubuntu?

Thanks everyone.

I do not have any experience with this adapter type.  My rule for Linux hardware is try for hardware that's been around for a year or more.  Bland/boring/not sexy has been good for me.  If the device supports Windows XP/Windows 2000 I'd feel pretty good about it working in linux.  No guarantees though.

[SIZE=4]**EDIT**[/SIZE]:  [SIZE=3]I ran "lspci" on [SIZE=3]my desktop to see what kind of ethernet adapter I was showing.  NO E[SIZE=3]THERNET ADAPTER SHOWS UP!!  [SIZE=3]But I know I have one though I[SIZE=3]'m not positive it works, I've never used it.  I'm going to[SIZE=3] re[SIZE=3]bo[SIZE=3]ot in[SIZE=3]to 12.04 and see if it shows up there.  I'll be back.

[SIZE=3]EDIT2:  Okay, that mystery is solved.  [SIZE=3]I had it disabled in BIOS.  Here's the relevant line from 'lspci':

[SIZE=3]02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)[/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by xiaobi on 2012-11-19
Huh.

Could you point me to where you found it in the BIOS, just so I can check and see if I've missed anything?

Thank you so much for the replies, by the way.

---

