---
title: "Broadcom 4313"
date: 2013-04-07
forum: Networking &amp; Wireless
---

### Post by Mensik on 2013-04-07
Hi there,

I've been trying to fix the problem by myself, reading other posts on this forum and on others (including the french one, [where I'm trying to get help]("http://forum.ubuntu-fr.org/viewtopic.php?pid=13152751")), but nothing seems to work.
My wifi simply won't connect.

Here are my specs.  I hope you can help me.
Thanks a lot for your time,

Antoine
(I'm currently wired on my Ethernet cable)

Cheers !

My computer is HP Pavillon (g series)

lspci
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9647
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:15.2 PCI bridge: Advanced Micro Devices [AMD] Device 43a2
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)

```


ifconfig

```
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:6a:60:ed  
          inet adr:192.168.0.101  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::7ae3:b5ff:fe6a:60ed/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:3930 erreurs:0 :0 overruns:0 frame:0
          TX packets:2762 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:3359744 (3.3 MB) Octets transmis:368441 (368.4 KB)
          Interruption:42 Adresse de base:0x2000 

eth1      Link encap:Ethernet  HWaddr c0:18:85:2c:62:6a  
          adr inet6: fe80::c218:85ff:fe2c:626a/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:11 erreurs:4 :0 overruns:0 frame:21562
          TX packets:147 errors:76 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1555 (1.5 KB) Octets transmis:36132 (36.1 KB)
          Interruption:17 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:308 erreurs:0 :0 overruns:0 frame:0
          TX packets:308 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:23746 (23.7 KB) Octets transmis:23746 (23.7 KB)


```

iwconfig
```
lo        no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
vesafb                 13516  1 
rfcomm                 38139  12 
bnep                   17830  2 
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_idt      60251  1 
snd_hda_codec_hdmi     31775  1 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_hda_intel          32719  5 
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_hda_codec         109562  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
k10temp                12990  0 
uvcvideo               67203  0 
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
videodev               86588  1 uvcvideo
fglrx                4323676  167 
btusb                  17948  2 
psmouse                86520  0 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth             158479  23 rfcomm,bnep,btusb
serio_raw              13027  0 
i2c_piix4              13093  0 
rts_pstor             353252  1 
snd_timer              28931  2 snd_seq,snd_pcm
wmi                    18744  1 hp_wmi
video                  19115  0 
lib80211_crypt_tkip    17275  0 
snd                    62218  20 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_rawmidi,snd_hda_intel,snd_seq,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
mac_hid                13077  0 
wl                   2906597  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cfg80211              178877  1 wl
lib80211               14040  2 lib80211_crypt_tkip,wl
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
r8169                  56368  0
```

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       produit: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:01:00.0
       nom logique: eth0
       version: 05
       numéro de série: 78:e3:b5:6a:60:ed
       taille: 100Mbit/s
       capacité: 100Mbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.0.101 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       ressources: irq:42 portE/S:3000(taille=256) mémoire:f0004000-f0004fff mémoire:f0000000-f0003fff
  *-network
       description: Interface réseau sans fil
       produit: BCM4313 802.11b/g/n Wireless LAN Controller
       fabriquant: Broadcom Corporation
       identifiant matériel: 0
       information bus: pci@0000:07:00.0
       nom logique: eth1
       version: 01
       numéro de série: c0:18:85:2c:62:6a
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       ressources: irq:17 mémoire:f0300000-f0303fff


```

iwlist scan
```
lo        Interface doesn't support scanning.

eth1      No scan results

eth0      Interface doesn't support scanning.


```

lsb_release -d
```
Description:    Ubuntu 12.04.2 LTS
```

uname -mr
```
3.2.0-39-generic-pae i686

```

---

### Post by chili555 on 2013-04-07
What does this tell us?```
lspci -nnd 14e4:
rfkill list all
dmesg | grep wl
```

---

### Post by Mensik on 2013-04-07
Hi chili555, thanks for your time.
Here are the results for the command lines :

lspci -nnd 14e4:
```
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

rfkill list all
```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```


dmesg | grep wl

```
[    0.000000] DMI: Hewlett-Packard HP Pavilion g6 Notebook PC/169B, BIOS F.44 11/14/2011
[   19.250981] wl: module license 'MIXED/Proprietary' taints kernel.
[   19.263260] wl 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.263272] wl 0000:07:00.0: setting latency timer to 64
[   19.299187] INFO @wl_cfg80211_attach : Registered CFG80211 phy

```

---

### Post by chili555 on 2013-04-07
It all looks perfect, actually. If you detach the ethernet cable so that Network manager starts managing the wireless, does it see networks when you click the Network Manager icon? Does it try to connect and fail or what, exactly, is the behavior?

May I also see:```
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
```Thanks.

---

### Post by Mensik on 2013-04-07
Yeah, I can't really understand why it doesn't work.
It worked for fifteen minutes, about an hour ago.  But the signal was so low, as soon as I got ten meters from the router, I lost connection.
Now, when I try to connect, it'll simply load forever without being able to connect even once.

[http://antoinemalette.com/ubuntu/anglais/1.png](http://antoinemalette.com/ubuntu/anglais/1.png)


cat /etc/network/interfaces

```
auto lo
iface lo inet loopback

```

(the "r" in network was missing :P )


cat /etc/NetworkManager/NetworkManager.conf
```
[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

```

---

### Post by chili555 on 2013-04-07
This device, 14e4:4727 is, in some ways, maddening. It is maddening because, for no reason I can pin down, sometimes it works well with the STA driver, also known as bcmwl-kernel-source and sometimes it just doesn't. Let's switch to the other method and see if we can get it going:```
sudo ifconfig eth1 down
sudo modprobe -r wl
sudo modprobe bcma
sudo modprobe brcmsmac
```Did an interface get created, ideally wlan0```
iwconfig
```Does it connect?

If so, we'll need to take a few steps to make it permanent. Then I will add another baffling anomaly to my files!

---

### Post by Mensik on 2013-04-07
Nothing seemed to happen, but then, the little light on my keyboard turned from white to orange.  There's no more connections available from the list.
Hmm.  Strange.

```
antoine@antoine-HP-Pavilion-g6-Notebook-PC:~$ sudo ifconfig eth1 down
[sudo] password for antoine: 
antoine@antoine-HP-Pavilion-g6-Notebook-PC:~$ sudo modprobe -r wl
antoine@antoine-HP-Pavilion-g6-Notebook-PC:~$ sudo modprobe bcma
antoine@antoine-HP-Pavilion-g6-Notebook-PC:~$ sudo modprobe brcmsmac
antoine@antoine-HP-Pavilion-g6-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

antoine@antoine-HP-Pavilion-g6-Notebook-PC:~$ 

```

[http://antoinemalette.com/ubuntu/anglais/2.png](http://antoinemalette.com/ubuntu/anglais/2.png)

Thanks for your time again, though.

EDIT:  But let me just show you my blacklist.conf file, since I've played with that a few times.  The problem might come from there ?

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
# blacklist b43
blacklist ssb
blacklist bcma

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist wl0
```

---

### Post by chili555 on 2013-04-07
Let's check the logs:```
dmesg | grep -e bcma -e brcm
```Thanks.

---

### Post by Mensik on 2013-04-07
There you go :

```
[ 4317.377513] bcma-pci-bridge 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 4317.377538] bcma-pci-bridge 0000:07:00.0: setting latency timer to 64
[ 4317.377613] bcma: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[ 4317.377640] bcma: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[ 4317.377694] bcma: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[ 4317.410258] bcma: Bus registered

```

---

### Post by chili555 on 2013-04-07
You have ethernet, so we can undo and redo easily. Please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree  [COLOR="#FF0000"]<--although I'm skeptical this is needed[/COLOR]

```Reboot, detach the ethernet cable and show us:```
iwconfig
```

---

### Post by Mensik on 2013-04-07
Ok, it seems to work for now, but it's the second time it does that today.
The signal looks very low though.

iwconfig gives this :
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"VIDEOTRON3680"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 1C:7E:E5:F8:E7:6E   
          Bit Rate=57.8 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=31/70  Signal level=-79 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:27   Missed beacon:0

eth0      no wireless extensions.
```

If I take my computer too far from the router, it'll probably let me down.  That's what happened this afternoon at least.

nm-tool shows me how low is my signal :

```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [VIDEOTRON3680] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:2C:62:6A

  Capabilities:
    Speed:           39 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *VIDEOTRON3680:  Infra, 1C:7E:E5:F8:E7:6E, Freq 2462 MHz, Rate 54 Mb/s, Strength 38 WPA2

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:6A:60:ED

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

---

### Post by chili555 on 2013-04-07
Will you try an experiment for me? Please turn off N speeds in the router and let me see the readings again:```
nm-tool
```

---

### Post by Mensik on 2013-04-07
I'll try whatever you want me to try, but could you please let me know how I should do that ? :P  What do you mean by turning off N speeds ?

---

### Post by chili555 on 2013-04-07
In the administration pages of the router, under wireless, most routers have options to use 802.11B and G; or else B, G and N. Please experimentally disable N. In the attached example, you would change 802.11N to OFF.

---

### Post by Mensik on 2013-04-07
I found it, but I'm not really sure which option I should choose :

[http://www.antoinemalette.com/ubuntu/anglais/3.png](http://www.antoinemalette.com/ubuntu/anglais/3.png)

---

### Post by chili555 on 2013-04-07
I suggest 'Mixed 802.11g and 802.11b.' Then we'll be interested to see if conditions improve or are the same.

Some Linux drivers are troubled by N speeds.

---

### Post by Mensik on 2013-04-07
```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [VIDEOTRON3680] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:2C:62:6A

  Capabilities:
    Speed:           12 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *VIDEOTRON3680:  Infra, 1C:7E:E5:F8:E7:6E, Freq 2417 MHz, Rate 54 Mb/s, Strength 39 WPA2

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:6A:60:ED

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

Here's the result.  Doesn't seem faster, on the contrary.  Another problem is that my other computer, also running under Ubuntu, can't connect on Internet anymore.
I think I'll undo that last change.

EDIT : A simple reboot allowed my other PC to connect to Internet again.  No big deal.

---

### Post by chili555 on 2013-04-07
> Strength [COLOR="#FF0000"]39[/COLOR] WPA2It's virtually the same. Would you mind using it for a while to further test?

---

### Post by Mensik on 2013-04-07
Oups, I wasn't looking at the right place.  All right, just changed it again. :)  What would you like to do next ?

---

### Post by chili555 on 2013-04-07
> **Mensik said:**
> Oups, I wasn't looking at the right place.  All right, just changed it again. :)  What would you like to do next ?I would like to continue using it for a while to further test.

---

### Post by Mensik on 2013-04-07
No problem.

---

### Post by chili555 on 2013-04-08
> **Mensik said:**
> No problem.So how is it going? Do we need to tweak it a bit more or is it working well enough?

---

### Post by Mensik on 2013-04-08
Hi,

I tryed to walk away from the router in order to test the strenght of the signal.  As I thought, just a few meters further from where I was sitting, I lost my connexion.  I had to reboot to have access to the wifi again.
The signal stil looks weak.

```
NetworkManager Tool

State: connected (global)

- Device: wlan0  [VIDEOTRON3680] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:2C:62:6A

  Capabilities:
    Speed:           18 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *VIDEOTRON3680:  Infra, 1C:7E:E5:F8:E7:6E, Freq 2417 MHz, Rate 54 Mb/s, Strength 32 WPA2

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:6A:60:ED

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off


```

Strangely, if I test **nm-tool** in my other computer's terminal, here what I get :

```
NetworkManager Tool 

State: connected (global) 

- Device: eth0  ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            tg3 
  State:             unavailable 
  Default:           no 
  HW Address:        00:1B:24:BC:05:86 

  Capabilities: 
    Carrier Detect:  yes 

  Wired Properties 
    Carrier:         off 


- Device: wlan0  [VIDEOTRON3680]  ----------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            iwl3945 
  State:             connected 
  Default:           yes 
  HW Address:        00:1B:77:E1:85:5A 

  Capabilities: 
    Speed:           54 Mb/s 

  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 

  Wireless Access Points (* = current AP) 
    Toucheatoncul:   Infra, 00:1E:E5:35:13:4F, Freq 2437 MHz, Rate 54  Mb/s, Strength 25 WPA WPA2 
    Chez Lise:       Infra, 00:1E:E5:EF:29:59, Freq 2457 MHz, Rate 54  Mb/s, Strength 20 WPA2 
    linksys:         Infra, 00:16:B6:ED:BE:76, Freq 2437 MHz, Rate 54  Mb/s, Strength 15 
    *VIDEOTRON3680:  Infra, 1C:7E:E5:F8:E7:6E, Freq 2417 MHz, Rate 54  Mb/s, Strength 73 WPA2 

  IPv4 Settings: 
    Address:         192.168.0.101 
    Prefix:          24 (255.255.255.0) 
    Gateway:         192.168.0.1 

    DNS:             192.168.0.1 

```

---

### Post by chili555 on 2013-04-08
At the suggestion of my pal Hadaka, let's try an updated driver:```
sudo apt-get install linux-backports-modules-cw-3.6-precise-generic
```After it finishes, reboot and let us see:```
nm-tool
```

---

### Post by Mensik on 2013-04-08
Didn't seem to work.

I'm connected with my ethernet cable.  The wifi doesn't seem to function anymore.  Networks are still available, but won't connect.

The Broadcom driver isn't installed anymore.
[www.antoinemalette.com/ubuntu/anglais/4.png](www.antoinemalette.com/ubuntu/anglais/4.png)

Here's my nm-tool result :

```
NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        C0:18:85:2C:62:6A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    VIDEOTRON3680:   Infra, 1C:7E:E5:F8:E7:6E, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA2


- Device: eth0  [Connexion filaire 1] ------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        78:E3:B5:6A:60:ED

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


```

---

### Post by chili555 on 2013-04-08
The Broadcom STA driver is not installed because we decided it was not performing correctly for your device and removed it in post #10. Did you try a reboot? If the backports package isn't an improvement, by all means, remove it:```
sudo apt-get remove linux-backports-modules-cw-3.6-precise-generic
```And then reboot.

---

### Post by Mensik on 2013-04-09
Hi chili555,

Sorry for the delay, and thanks again for your help.  I did the manipulation you suggested me, but it didn't seem to help.
On the french forums, [a user]("http://forum.ubuntu-fr.org/viewtopic.php?pid=13167571#p13167571") told me :

1) To do : ```
sudo rmmod brcmsmac
```

2) To "blacklist" brcmsmac

3) To make sure it wasn't in /etc/modules, but to also make sure that **b43** was on /etc/modules.

As soo as I typed the first command (rmmod brcmsmac), I lost the connection I had.  I did the other manipulations, rebooted, and since then, I've no connections available.
I must admit, I begin to loose faith... :P

Here's my blacklist.conf file :

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist ssb
blacklist bcma

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist wl0
blacklist brcmsmac
```

/etc/modules :

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl
b43
```

iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.
```

ifconfig :

```
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:6a:60:ed  
          inet adr:192.168.0.102  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::7ae3:b5ff:fe6a:60ed/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:3711 erreurs:0 :0 overruns:0 frame:0
          TX packets:3205 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:3761508 (3.7 MB) Octets transmis:440120 (440.1 KB)
          Interruption:42 Adresse de base:0x2000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:280 erreurs:0 :0 overruns:0 frame:0
          TX packets:280 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:23636 (23.6 KB) Octets transmis:23636 (23.6 KB)


```

nm-tool:

```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Connexion filaire 1] ------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        78:E3:B5:6A:60:ED

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


```

lspci :

```
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9647
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0
00:15.1 PCI bridge: Advanced Micro Devices [AMD] Device 43a1
00:15.2 PCI bridge: Advanced Micro Devices [AMD] Device 43a2
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)


```

Thank you so much for your time...

---

### Post by chili555 on 2013-04-09
> As soo as I typed the first command (rmmod brcmsmac), I lost the connection I had. I did the other manipulations, rebooted, and since then, I've no connections available.
I must admit, I begin to loose faith... I suggest you tell your French forum friend just that. And tell him or her that your device isn't covered by b43 and its sister ssb. Then I suggest you undo everything he or she suggested and we'll continue.

---

### Post by Mensik on 2013-04-09
> **chili555 said:**
> I suggest you tell your French forum friend just that. And tell him or her that your device isn't covered by b43 and its sister ssb. Then I suggest you undo everything he or she suggested and we'll continue.

Done.  I've undone the previous manipulations but couldn't manage to undo the **sudo rmmod brcmsmac**.  (You see how neophyte I am)
After a reboot, my network (VIDEOTRON3680) is detected, but I can't connect to it.

**iwconfig**
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.
```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:6a:60:ed  
          inet adr:192.168.0.102  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::7ae3:b5ff:fe6a:60ed/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:2224 erreurs:0 :0 overruns:0 frame:0
          TX packets:2036 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:1922869 (1.9 MB) Octets transmis:253535 (253.5 KB)
          Interruption:42 Adresse de base:0x2000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:374 erreurs:0 :0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:29860 (29.8 KB) Octets transmis:29860 (29.8 KB)

wlan0     Link encap:Ethernet  HWaddr c0:18:85:2c:62:6a  
          adr inet6: fe80::c218:85ff:fe2c:626a/64 Scope:Lien
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:16 erreurs:0 :0 overruns:0 frame:0
          TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:2049 (2.0 KB) Octets transmis:33505 (33.5 KB)


```

**nm-tool**
```
NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             disconnected
  Default:           no
  HW Address:        C0:18:85:2C:62:6A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    VIDEOTRON3680:   Infra, 1C:7E:E5:F8:E7:6E, Freq 2417 MHz, Rate 54 Mb/s, Strength 27 WPA2


- Device: eth0  [Connexion filaire 1] ------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        78:E3:B5:6A:60:ED

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


```

Do you have any ideas ?
I've seen a few manipulations you suggested [here]("http://ubuntuforums.org/showthread.php?t=2067185&p=12284404#post12284404").  Do you think it could work for my caste too ?

Thanks again chili555 !

---

### Post by chili555 on 2013-04-10
> I've seen a few manipulations you suggested here. Do you think it could work for my caste too ?
Not really, since we've already purged bcmwl-kernel-source and since brcmsmac is already loading as expected:> NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  [COLOR="#FF0000"]Driver:            brcmsmac[/COLOR]
  State:             disconnected
  Default:           no
  HW Address:        C0:18:85:2C:62:6A
Is the behavior better or worse with the ethernet detached?  Your router seems to be set to channel 2. Is the signal strength better at 1 or my favorite 11? If you change the channel, other computers attached to the wireless network will need to disconnect and reconnect.

EDIT: May I see:```
cat /etc/modules
```

---

### Post by Mensik on 2013-04-10
I went to my router's administration page ([http://192.168.0.1/](http://192.168.0.1/)) and changed the channel to 11.
After a reboot, I was automatically connected to the wifi.

The signal's strength is still pretty low though, but I've no problem with its speed.  It doesn't take time to load pages, and it's actually pretty fast.
I still have the proximity problem though.  If I walk less than five meters from the router, I lose my connection until I get closer to it again.

[B]cat /etc/modules


[/B]```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl

```

**iwconfig**

```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"VIDEOTRON3680"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 1C:7E:E5:F8:E7:6E   
          Bit Rate=54 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=26/70  Signal level=-84 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:237   Missed beacon:0

eth0      no wireless extensions.


```

**nm-tool**

```

NetworkManager Tool

State: connected (global)

- Device: wlan0  [VIDEOTRON3680] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            brcmsmac
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:2C:62:6A

  Capabilities:
    Speed:           9 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *VIDEOTRON3680:  Infra, 1C:7E:E5:F8:E7:6E, Freq 2462 MHz, Rate 54 Mb/s, Strength 35 WPA2

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        78:E3:B5:6A:60:ED

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


```

[B]ifconfig

[/B]```
eth0      Link encap:Ethernet  HWaddr 78:e3:b5:6a:60:ed  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:42 Adresse de base:0x2000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:373 erreurs:0 :0 overruns:0 frame:0
          TX packets:373 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:34431 (34.4 KB) Octets transmis:34431 (34.4 KB)

wlan0     Link encap:Ethernet  HWaddr c0:18:85:2c:62:6a  
          inet adr:192.168.0.100  Bcast:192.168.0.255  Masque:255.255.255.0
          adr inet6: fe80::c218:85ff:fe2c:626a/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:14989 erreurs:0 :0 overruns:0 frame:0
          TX packets:13478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:18957328 (18.9 MB) Octets transmis:1599498 (1.5 MB)
```

[B]iwlist wlan0 scan

[/B]```
wlan0     Scan completed :
          Cell 01 - Address: 1C:7E:E5:F8:E7:6E
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption key:on
                    ESSID:"VIDEOTRON3680"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000004455cd81
                    Extra: Last beacon: 20548ms ago
                    IE: Unknown: 000D564944454F54524F4E33363830
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD8F0050F204104A0001101044000102103B00010310470010BD10B9DC1DD111B2A902CDEC58CBE30610210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D383235104200046E6F6E651054000800060050F2040001101100074449522D383235100800020084103C000103104900140024E26002000101600000020001600100020001


```

I'll search other topics to see if there's something to fix the signal's strenght.  Otherwise, the wifi seems to function correctly.
Do you know how we could fix it ?

Thanks a lot for your help !

---

### Post by chili555 on 2013-04-11
Please do:```
gksudo gedit /etc/modules
```Remove the wl line so it now reads:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
```Proofread, save and close gedit. You might check your router for any method to increase transmit power, such as this: [http://cdn.howtogeek.com/wp-content/uploads/2011/03/tx-power.png](http://cdn.howtogeek.com/wp-content/uploads/2011/03/tx-power.png)

CAUTION: Some routers can be increased to unsafe levels without external cooling. Please make any changes cautiously.

The signal strength I receive in my router is quite variable depending on how it and its antennae are aligned. Currently, I get better strength with the router on it nose, like this: [http://www.practicallynetworked.com/img/prdct/010308_wrtsl54gs.jpg](http://www.practicallynetworked.com/img/prdct/010308_wrtsl54gs.jpg) 

You might experiment with positioning. Check with:```
iwconfig
``````
wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 99:13:11:62:8D:99   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
         [COLOR="#FF0000"] Link Quality=46/70[/COLOR]  Signal level=-64 dBm  

```

---

### Post by Mensik on 2013-04-11
Hi,

I've modified my **/etc/modules**file, as you suggested.
I've installed **wavemon** just to get a graphic interface for my signal's strength.

Two meters from the router:
[IMG]http://antoinemalette.com/ubuntu/anglais/5.png[/IMG]

The closest to the router I can get :
[IMG]http://antoinemalette.com/ubuntu/anglais/6.png[/IMG]

About six meters from the router (where I lose connection) :
[IMG]http://antoinemalette.com/ubuntu/anglais/7.png[/IMG]

I can't believe it's normal.  Two weeks ago, I had a better signal twenty meters from the router than now, when I'm glued to it.  I really don't understand...

---

### Post by Hadaka on 2013-04-11
Hi ,please check the following...
 check the cable at both ends modem/router
check for damage at both connectors male/female
check for damage to cable it's self. (cat,dog,bird chews)
replace cable if possible .
check antenna at router, unscrew check for clean connection
lastly...and carefully...if no above problems are found
check and reseat wifi card..make sure antenna wire is attached.
good luck.

---

