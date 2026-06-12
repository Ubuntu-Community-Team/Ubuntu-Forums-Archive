---
title: "NDISwrapper Errors/Maverick"
date: 2011-01-09
forum: Networking &amp; Wireless
---

### Post by chevyboy_0 on 2011-01-09
Hey guys, I recently installed a wireless card in my IBM Thinkpad T23 and I'm having trouble getting it to work. I have tried following the instructions that came with NDISwrapper but I cant get it to work. when I get to the 'make' part of it i get a whole bunch of errors. 

[http://pastebin.com/pnAsUKWQ](http://pastebin.com/pnAsUKWQ)

Im really hoping that someone will be able to help me with this.

and before any one asks for the lspci, and iwconfig here it is

```
00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 02)
00:01.0 PCI bridge: Intel Corporation 82830 830 Chipset AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801CA/CAM USB Controller #3 (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 41)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: S3 Inc. SuperSavage IX/C SDR (rev 05)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 41)
```
```
 lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity=1/3  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-73 dBm  Noise level=-73 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0


```

---

### Post by walt.smith1960 on 2011-01-09
Power Management: Off

What does NetworkManager show?  Right click NM-applet icon.  Are both 'enable networking' and 'enable wireless' checked?  Is there some keystroke combination to enable & disable wireless networking?

---

### Post by chevyboy_0 on 2011-01-09
> **walt.smith1960 said:**
> Power Management: Off

What does NetworkManager show?  Right click NM-applet icon.  Are both 'enable networking' and 'enable wireless' checked?  Is there some keystroke combination to enable & disable wireless networking?


They are both checked. when I left click the icon it lists Wireless Networks but under it it says disconnected.

---

### Post by chili555 on 2011-01-09
These devices work with both the orinoco and hostap drivers; ndiswrapper is generally unnecessary. Moreover, ndiswrapper is usually installed by default and, if not, is available with apt-get from the install CD or the great interwebs in the sky. There is no need to compile it from source. If you have an interface, wlan0, something is driving the device now and, likely, something is conflicting. Please post:```
lsmod
```Let's troubleshoot.

---

### Post by chevyboy_0 on 2011-01-09
```
andrew@Ubuntu:~$ lsmod
Module                  Size  Used by
xt_limit                1394  8 
xt_tcpudp               1927  10 
ipt_LOG                 4490  8 
ipt_MASQUERADE          1419  0 
xt_DSCP                 1657  0 
ipt_REJECT              2004  1 
nf_conntrack_irc        3348  0 
nf_conntrack_ftp        5361  0 
xt_state                1014  6 
binfmt_misc             6599  1 
savage                 29276  2 
drm                   168092  3 savage
iptable_nat             3752  0 
nf_nat                 16289  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      10783  9 iptable_nat,nf_nat
nf_conntrack           63258  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
iptable_mangle          1371  0 
iptable_filter          1302  1 
ip_tables              10460  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               15921  11 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,xt_DSCP,ipt_REJECT,xt_state,iptable_nat,iptable_mangle,iptable_filter,ip_tables
thinkpad_acpi          67659  0 
snd_seq_midi            4588  0 
pcmcia                 35973  0 
snd_intel8x0           25632  2 
snd_rawmidi            17783  1 snd_seq_midi
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
snd_seq_midi_event      6047  1 snd_seq_midi
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
hostap_pci             44661  2 
hostap                100441  1 hostap_pci
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
intel_agp              26694  1 
snd_timer              19067  2 snd_pcm,snd_seq
yenta_socket           21518  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211                5058  2 hostap_pci,hostap
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
pcmcia_rsrc            10566  1 yenta_socket
agpgart                32011  2 drm,intel_agp
video                  18712  0 
snd                    49038  12 thinkpad_acpi,snd_rawmidi,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_seq,snd_timer,snd_seq_device
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
shpchp                 29886  0 
nsc_ircc               18252  0 
irda                  178906  1 nsc_ircc
output                  1883  1 video
soundcore                880  1 snd
psmouse                59033  0 
lp                      7342  0 
ppdev                   5556  0 
crc_ccitt               1351  1 irda
parport_pc             26058  1 
led_class               2633  1 thinkpad_acpi
serio_raw               4022  0 
nvram                   6342  1 thinkpad_acpi
parport                31492  3 lp,ppdev,parport_pc
e100                   30356  0 
floppy                 54311  0 
mii                     4425  1 e100
andrew@Ubuntu:~$ 

```Chili, is that a 1971-1972 Chevelle in your Avatar?

Also just in case this is on an IBM Thinkpad T23, and Maverick Meerkat, the Card is an Actiontec 802MIP and the chipset is the Intersil Prism 2.5

---

### Post by chili555 on 2011-01-09
> is that a 1971-1972 Chevelle in your Avatar?Indeed. It's slowly rejoining Mother Earth in the woods near me.

I see you have hostap loaded and no conflicts. Let's see what kernel messages there are:```
rfkill list all
dmesg | grep -e host -e wlan
```Thanks.

---

### Post by chevyboy_0 on 2011-01-09
Its returning to mother earth?? thats a shame. I have a 1970 Chevelle SS myself 

```
andrew@Ubuntu:~$ rfkill list all
andrew@Ubuntu:~$ dmesg | grep -e host -e wlan
[    0.132439] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.132720] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.132731] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.132742] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.132753] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000d3fff] (ignored)
[    0.132764] pci_root PNP0A03:00: host bridge window [mem 0x000d4000-0x000d7fff] (ignored)
[    0.132774] pci_root PNP0A03:00: host bridge window [mem 0x000d8000-0x000dbfff] (ignored)
[    0.132785] pci_root PNP0A03:00: host bridge window [mem 0x20000000-0xfebfffff] (ignored)
[   20.016660] hostap_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[   20.018209] hostap_pci: Registered netdevice wifi0
[   20.256683] wifi0: registered netdevice wlan0
[   20.296255] udev[306]: renamed network interface wlan0 to wlan1
[   22.880546] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   22.972651] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[  223.231564] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[  226.687203] hostap_pci 0000:02:02.0: PCI INT A disabled
[  226.945365] PM: freeze of drv:scsi dev:host0 complete after 258.424 msecs
[  227.546168] hostap_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[  227.761318] PM: restore of drv:hostap_pci dev:0000:02:02.0 complete after 215.154 msecs
[  240.848674] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  241.089748] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[ 1969.437675] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
[ 1971.226247] hostap_pci 0000:02:02.0: PCI INT A disabled
[ 1971.700846] PM: suspend of drv:scsi dev:host0 complete after 476.559 msecs
[ 1974.214774] hostap_pci 0000:02:02.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 1974.429190] PM: resume of drv:hostap_pci dev:0000:02:02.0 complete after 214.419 msecs
[ 1979.338701] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 1979.369456] wlan1: Preferred AP (SIOCSIWAP) is used only in Managed mode when host_roaming is enabled
andrew@Ubuntu:~$ 

```

---

### Post by kimberlite on 2011-01-09
> **chevyboy_0 said:**
> 
wifi0     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  

wlan1     IEEE 802.11b  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  

[/CODE]

I am just wondering whether your ESSID character encoding could make a trouble like this... Try to avoid using non-ASCII characters like éá&#337;ú ...

---

### Post by kimberlite on 2011-01-09
Sorry for double posting...

---

### Post by chevyboy_0 on 2011-01-09
> **kimberlite said:**
> I am just wondering whether your ESSID character encoding could make a trouble like this... Try to avoid using non-ASCII characters like éá&#337;ú ...


The thing is I didnt change any thing in there..

---

### Post by chili555 on 2011-01-09
> **kimberlite said:**
> I am just wondering whether your ESSID character encoding could make a trouble like this... Try to avoid using non-ASCII characters like éá&#337;ú ...I think the ESSID looks wacky because the driver and card are not working well together.

May we see the pci.id? Please post:```
lspci -nn | grep -i network

```I wonder if we might have better luck with the orinoco drivers.

---

### Post by chevyboy_0 on 2011-01-09
Here is the output from "lspci -nn | grep -i network"

```
andrew@MaverickT23:~$ lspci -nn | grep -i network
02:02.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)
```

---

### Post by chili555 on 2011-01-10
Let's open the hood and try a new carb. I suggest you blacklist the hostap suite and load orinoco. This is all easily reversible.```
sudo gedit /etc/modprobe.d/blacklist.conf
```If there are lines in there relating to orinoco, remove them. Add these lines:```
blacklist hostap
blacklist hostap_pci
```Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/modules
```Conversely, if there are lines about hostap, remove them. Add one line:```
orinoco_pci
```Reboot and give me a good report.

---

### Post by chevyboy_0 on 2011-01-10
Chili - I followed your directions and and when I rebooted it still wasnt working. Last night I just so happened to find a Linksys WUSB600N in my drawer and plugged it in and then followed the instructions from Dev0 in post 34 of this thread 

[http://ubuntuforums.org/showthread.php?t=1487397&page=4](http://ubuntuforums.org/showthread.php?t=1487397&page=4)

So far its working nicely with the USB adapter but for some reason whenever I try to connect to our network at home which is WPA protected, I keep getting a bad password prompt from WICD. As I post this I am currently connected to a wireless network that is not protected.

---

### Post by chili555 on 2011-01-11
Either your driver, Network Manager or wpa_supplicant have problems in two areas. I don't know which. First, it can be troublesome to connect to SSIDs with a space, such as "Chili House." If yours has a space, try changing to something else, such as, "ChiliHouse."

Second, many routers have a mixed WPA and WPA2 mode. The intent, I believe, is to be backwards compatible with older hardware that may not be WPA2 capable. If yours is so configured, you will have better luck with the router set to WPA ***or*** WPA2; not both.

Finally, have you double-checked the password? Does it work seamlessly in other computers on the network?

---

