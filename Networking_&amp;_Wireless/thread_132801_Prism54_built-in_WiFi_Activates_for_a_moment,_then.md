---
title: "Prism54 built-in WiFi Activates for a moment, then goes Inactive..."
date: 2006-02-19
forum: Networking &amp; Wireless
---

### Post by DonQuixote on 2006-02-19
I had Ubuntu installed before on this very same machine, and in the process of removing software, I blew the installation.  In that installation I had no problem, and no special configurations whatsoever to activate and use my wireless internet connection; everything ran smoothly.

Now, on this last installation, I ran the CD, formatted the hard-drive, and let the installation roll.  Everything went fine until I tried activating my WiFi card.

After a long time, the "networking settings" application tells me it's active.  I click "Ok" and wait another long time (about 2 minutes) while it closes.  I click on the network connection icon on the top bar of my default Gnome installation and my WiFi (eth1) is not in the list.  I open the "network settings" app, and see that it has become "inactive".

I tried installing Kubuntu, and the only difference was that in Kubuntu's network settings application it would show eth1 as active (when I tried activating it) only for a moment, then it would go inactive.

Here is the information from the "lshw -C network" command (something that I noticed is that the last 6 digits of the MAC address are all "0"'s... I do believe that is the incorrect number):
```

  *-network:1 DISABLED
       description: Wireless interface
       product: Intersil ISL3890 [Prism GT/Prism Duette]
       vendor: Intersil Corporation
       physical id: 4
       bus info: pci@03:04.0
       logical name: eth1
       version: 01
       serial: 00:30:b4:00:00:00
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=prism54 multicast=yes wireless=NOT READY!
       resources: iomemory:e8204000-e8205fff irq:19

```
---

And from the "lsmod" command ("*****" around the "prism54" bits):
```

Module                  Size  Used by
sg                     38080  0
rfcomm                 38460  0
l2cap                  24740  5 rfcomm
bluetooth              48356  4 rfcomm,l2cap
speedstep_lib           4228  0
cpufreq_userspace       4316  0
cpufreq_stats           5252  0
freq_table              4388  1 cpufreq_stats
cpufreq_powersave       1696  0
cpufreq_ondemand        6044  0
cpufreq_conservative     6948  0
pcmcia                 26568  2
video                  15748  0
tc1100_wmi              6692  0
sony_acpi               5324  0
pcc_acpi               11104  0
hotkey                  9284  0
dev_acpi               11108  0
i2c_acpi_ec             5472  0
i2c_core               21200  1 i2c_acpi_ec
button                  6480  0
battery                 9348  0
container               4384  0
ac                      4708  0
ipv6                  251232  6
af_packet              21768  4
irtty_sir               8512  0
sir_dev                18444  1 irtty_sir
irda                  187612  2 irtty_sir,sir_dev
crc_ccitt               1984  1 irda
floppy                 59124  0
pcspkr                  3396  0
rtc                    12344  0
*****
prism54                55912  0
firmware_class          9952  1 prism54
*****
ohci1394               34356  0
yenta_socket           25292  1
rsrc_nonstatic         13376  1 yenta_socket
pcmcia_core            49348  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_intel8x0           33248  1
snd_ac97_codec         83932  1 snd_intel8x0
snd_pcm_oss            52704  0
snd_mixer_oss          19296  1 snd_pcm_oss
snd_pcm                88840  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24164  1 snd_pcm
snd                    54884  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9600  1 snd
snd_page_alloc         10600  2 snd_intel8x0,snd_pcm
tpm_atmel               5536  0
tpm_nsc                 6656  0
tpm                     9888  2 tpm_atmel,tpm_nsc
hw_random               5172  0
shpchp                 96996  0
pci_hotplug            27508  1 shpchp
intel_agp              23164  1
agpgart                34792  1 intel_agp
dm_mod                 57692  1
joydev                  9984  0
tsdev                   7776  0
evdev                   9664  1
sr_mod                 17028  0
sbp2                   22952  0
scsi_mod              135688  3 sg,sr_mod,sbp2
ieee1394              100792  2 ohci1394,sbp2
psmouse                30116  0
mousedev               11616  1
parport_pc             35236  1
lp                     12292  0
parport                35912  2 parport_pc,lp
md                     45584  0
ext3                  136264  1
jbd                    54776  1 ext3
mbcache                 9252  1 ext3
thermal                13000  0
processor              22812  1 thermal
fan                     4484  0
r8169                  25516  0
ehci_hcd               34248  0
uhci_hcd               31184  0
usbcore               118044  3 ehci_hcd,uhci_hcd
ide_cd                 41572  0
cdrom                  39616  2 sr_mod,ide_cd
ide_disk               18464  3
ide_generic             1376  0
piix                   10372  1
ide_core              138772  4 ide_cd,ide_disk,ide_generic,piix
unix                   26896  716
vesafb                  7992  0
capability              4712  0
commoncap               6816  1 capability
vga16fb                12584  1
vgastate                9664  1 vga16fb
softcursor              2272  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3872  2 vesafb,vga16fb
cfbcopyarea             4608  2 vesafb,vga16fb
fbcon                  38496  72
tileblit                2368  1 fbcon
font                    8224  1 fbcon
bitblit                 5632  1 fbcon

```

My /etc/network/interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid AHome

auto eth0

auto eth1

```

I tell ya, any help that will help me solve this problem would be greatly appreciated.  I've been pounding at it nearly all day long, reading multiple threads in this forum and I'm at my wit's end.

John

---

### Post by bscbrit on 2006-02-19
I've got no quick fix solutions, but have you tried 'sudo ifup eht1' from the command line? If it doesn't work, try following this link until you pinpoint where the problem is ocurring:

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

Come back if you need help.

---

### Post by DonQuixote on 2006-02-19
Alright, I've gone through the troubleshooter several times, and if I knew what was supposed to be there I could find out what was missing! :)  It seems to have been written for the insertable network card, as opposed to the built-in card (such as I have).

Some additional information:

Here is the feedback from "lspci -v":
```

0000:03:04.0 Network controller: Intersil Corporation Intersil ISL3890 [Prism GT/Prism Duette] (rev 01)
        Subsystem: Intersil Corporation: Unknown device 0000
        Flags: bus master, medium devsel, latency 80, IRQ 19
        Memory at e8204000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [dc] Power Management version 1

```

From "iwconfig":
```

eth1      NOT READY!  ESSID:"AHome"
          Mode:Managed  Channel:0  Access Point: 00:00:00:00:00:00
          Tx-Power=31 dBm   Sensitivity=0/200
          Retry min limit:0   RTS thr=0 B   Fragment thr=0 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

From what I can tell, the driver is installed, and the card is recognized, but for some reason, I can not activate it.

Is there any more information that you need, or some other files to look at or commands to execute?

I really appreciate your time.

---

### Post by DonQuixote on 2006-02-19
More info (again, being inexperienced with this, I'm not sure what is supposed to be here, and what is not):
```

root@pandora:/# ifup eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
SIOCSIFFLAGS: Operation not permitted
SIOCSIFFLAGS: Operation not permitted
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:30:b4:00:00:00
Sending on   LPF/eth1/00:30:b4:00:00:00
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

 ```
root@pandora:/# ifdown eth1
There is already a pid file /var/run/dhclient.eth1.pid with pid 6563
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth1/00:30:b4:00:00:00
Sending on   LPF/eth1/00:30:b4:00:00:00
Sending on   Socket/fallback 
```

---

### Post by bscbrit on 2006-02-19
Well, I think that the big clue is the response from iwconfig - NOT READY.  It looks like it is not configured.  I take it you are using DHCP.  But (mostly guesswork I'm afraid), because it cannot connect, it cannot get an IP address.  It is using channel 0 but cannot detect the Access Point, because the MAC is 00:00:00:00:00.  Is that the channel you intended to use?

Lets have a look at your /etc/networking/interfaces file please.

Have you tried running 'sudo iwlist scan' to see what the card can hear - if anything?

---

### Post by Lambert on 2006-02-19
The first post showing DISABLED and iwconfig showing device not ready is the clue.

What's the make and model of the laptop you're using. The radio is probably turned off. Usually there is a FN+FX key press on a laptop that can turn this on and off and it is a problem area with many laptops in linux.

Depending on the make and model there might be a command something like

echo 1 >> /proc/..../...

that can enable it or another way by editing a config file.

You can post the info here and maybe somebody with the same laptop will see and post or you can search using key words such as

acer linux enable wireless

---

### Post by DonQuixote on 2006-02-19
Alright guys.

Thanks for your prodding and direction.

I found out that the card was turned off.  I never did it, yet somehow it happened.

I have a Sager 5680/Clevo D500P (these two models are the same).

I found that I have to press the "Fn" + f11 keys turn the card on and off.  The indicator is the flashing "CapsLock" LED.  Mine had to be NOT flashing in order to work.

---

### Post by bscbrit on 2006-02-20
It doesn't matter what caused the problem as long as it is now solved \\:D/ 

Good Luck

---

