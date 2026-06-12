---
title: "Wireless doesn't work anymore"
date: 2011-11-26
forum: Networking &amp; Wireless
---

### Post by Buying_Some_Time on 2011-11-26
Ever since I upgraded to 11.10 my wireless has been extremely crappy it seems to only work in 10 minute spurts and after that 10 minutes I have to restart my computer to get it working again. I tried to use Wicd but that was just as bad as network manager........ it kept giving me a "bad password" error [even though I know the password was right] I've tried everything I could find on these forums but nothing seems to help. :(

Can someone please help me solve this problem? 



sudo lshw -C network:
```
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 19
       serial: 00:90:f5:4b:27:88
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:42 memory:b0000000-b0003fff ioport:2000(size=256) memory:d0000000-d001ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:06:03.0
       logical name: eth1
       version: 05
       serial: 00:15:00:11:0b:19
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.4 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11abg
       resources: irq:20 memory:b4005000-b4005fff

```


lspci -nnk | grep -iA2 net:
```
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 19)
	Subsystem: CLEVO/KAPOK Computer Device [1558:038a]
	Kernel driver in use: sky2
--
06:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection [8086:4223] (rev 05)
	Subsystem: Intel Corporation Device [8086:1000]
	Kernel driver in use: ipw2200

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"Step"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:3F:B9:A9:FC   
          Bit Rate:24 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/100  Signal level=-62 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:6

```

rfkill list all:
```
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

lsmod:
```

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
hid_microsoft          12728  0 
usbhid                 41905  0 
hid                    77367  2 hid_microsoft,usbhid
arc4                   12473  2 
lib80211_crypt_wep     12746  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
dm_crypt               22565  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  1 
snd_hda_codec          91754  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
nvidia              10390874  32 
snd_pcm                80468  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
pcmcia                 39822  0 
irda                  185428  0 
psmouse                73673  0 
binfmt_misc            17292  1 
snd_seq_midi_event     14475  1 snd_seq_midi
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
crc_ccitt              12595  1 irda
ipw2200               146148  0 
libipw                 46701  1 ipw2200
snd_timer              28932  2 snd_pcm,snd_seq
cfg80211              172392  2 ipw2200,libipw
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
lib80211               14570  3 lib80211_crypt_wep,ipw2200,libipw
snd                    55902  12 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
vesafb                 13489  1 
usb_storage            44173  1 
uas                    17699  0 
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sky2                   49317  0 
video                  18908  0 

```

sudo cat /var/log/syslog | grep -e b43 -e wl -e firmware -e wlan0 | tail -n35:

```
Nov 26 19:06:13 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:14 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:15 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:16 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:17 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:18 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:19 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:20 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:21 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:22 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:23 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:24 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:25 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:26 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:27 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:28 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:29 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:30 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:31 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:32 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:33 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:34 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:35 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:36 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:37 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:38 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:39 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:40 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:41 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:42 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:43 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:44 Moonwalker-MJ udevd[1745]: timeout: killing 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167]
Nov 26 19:06:44 Moonwalker-MJ udevd[1745]: 'firmware --firmware=ipw2200-bss.fw --devpath=/devices/pci0000:00/0000:00:1e.0/0000:06:03.0/firmware/0000:06:03.0' [2167] terminated by signal 9 (Killed)
Nov 26 20:45:14 Moonwalker-MJ NetworkManager[673]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 26 20:45:15 Moonwalker-MJ kernel: [   27.484985] elantech: assuming hardware version 1, firmware version 1.0.33

```

Any help would be greatly appreciated and if you need extra info just let me know......

---

### Post by sidzen on 2011-11-26
[**this link**]("http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=%222915ABG%22&OSVersion=Linux*&DownloadType=Drivers")

---

### Post by Buying_Some_Time on 2011-11-27
> **sidzen said:**
> [**this link**]("http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&keyword=%222915ABG%22&OSVersion=Linux*&DownloadType=Drivers")
What do I do with that? 

Thanks.

---

### Post by Buying_Some_Time on 2011-11-27
Anyone else? 

:confused:

---

### Post by praseodym on 2011-11-27
Hi,

looks like a firmware problem. Try this one:

[http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php)

Version 3.0, unpack it to /lib/firmware:

```
sudo tar -xvf ipw2200-fw-3.0 -C /lib/firmware
```

---

### Post by Buying_Some_Time on 2011-11-27
praseodym thank you for your help!

I did everything you said, but I still have the same problems as before. Do I need to remove the old firmware or something? And if so could you please show me how? Thanks in advance!

---

### Post by praseodym on 2011-11-28
Did you try to take anything off the current for 20 minutes? With a note/netbook also the battery. Password contains any blanks or strange letters?

---

### Post by Buying_Some_Time on 2011-11-28
> **praseodym said:**
> Did you try to take anything off the current for 20 minutes? With a note/netbook also the battery. Password contains any blanks or strange letters?
I turned off and unpluged evrything for a hour or so and it's still the same....

Nope my PW just has normal letters and numbers.

:confused:

---

### Post by praseodym on 2011-11-28
Try to reset the router to manufacturer settings and/or reset the BIOS, too.

---

### Post by Buying_Some_Time on 2011-11-29
> **praseodym said:**
> Try to reset the router to manufacturer settings and/or reset the BIOS, too.
Alright I did that and everything seems to be working now!

I went an entire day and no problems..... thank you very much! :D

---

