---
title: "pcmcia card not working"
date: 2006-04-15
forum: Networking &amp; Wireless
---

### Post by blakken on 2006-04-15
my pcmcia card is a sitecom wl-120.It used to work and beeing recognized under old knoppix version with ndiswrapper.
So did I under ubuntu.I install ndiswrapper,pcmcia modules and so on.And here is the result:
slayer@ubuntu:~$ sudo ndiswrapper -l
Installed ndis drivers:
wlanctg         driver present, hardware present
slayer@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11b  ESSID:"linksys"  Nickname:"ipw2100"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:DC:44:6E
          Bit Rate=11 Mb/s   Tx-Power:off
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-41 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:62   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

[B]wlan0     IEEE 802.11b+/g+  ESSID:"STA00EC84"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:51/100  Signal level:32/100  Noise level:0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/B]

how come there is no mac adress?
means there it is not beeing recognized?
](*,)  please help

---

### Post by totalllama on 2006-04-15
hey blackken.  That output looks a little confusing as there appears to be a connection on eth1 and a different connection on wlan0

what is the output of a scan
sudo iwlist wlan0 scan?
do you use encryption, what type?

thanks
J

---

### Post by blakken on 2006-04-15
yes I do use encryption besides ,I tried as well opened but the wlan0 is unable to find any network!I'm using for the moment the eth1 which is slow and buggy!

slayer@ubuntu:~$ sudo iwlist wlan0 scan
Password:
wlan0     No scan results
another thing I noticed is:
slayer@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

here is the message when I remove/put back the pcmcia card:
04/15/2006 05:58:11 PM	localhost	kernel	[4308233.049000] pccard: card ejected from slot 0
04/15/2006 05:58:11 PM	localhost	kernel	[4308233.190000] ACPI: PCI interrupt for device 0000:03:00.0 disabled
04/15/2006 05:58:13 PM	localhost	kernel	[4308235.197000] ACPI: PCI Interrupt 0000:03:00.0[A] -> Link [C0C4] -> GSI 5 (level, low) -> IRQ 5
04/15/2006 05:58:13 PM	localhost	kernel	[4308235.197000] acx: found ACX111-based wireless network card at 0000:03:00.0, irq:5, phymem1:0x34020000, phymem2:0x34000000, mem1:0xe2160000, mem1_size:8192, mem2:0xe2600000, mem2_size:131072
04/15/2006 05:58:13 PM	localhost	kernel	[4308235.197000] pccard: CardBus card inserted into slot 0
04/15/2006 05:58:13 PM	localhost	kernel	[4308235.197000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
04/15/2006 05:58:13 PM	localhost	kernel	[4308235.197000] PCI: Setting latency timer of device 0000:03:00.0 to 64
04/15/2006 05:58:13 PM	localhost	kernel	[4308235.197000] yenta EnE: chaning testregister 0xC9, 04 -> 04
04/15/2006 05:58:14 PM	localhost	kernel	[4308236.196000] acx: firmware 'Rev 2.3.1.31' does not work well with this driver
04/15/2006 05:58:14 PM	localhost	kernel	[4308236.196000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 (Radia), EEPROM version 0x05, uploaded firmware 'Rev 2.3.1.31' (0x03010101)
04/15/2006 05:58:14 PM	localhost	kernel	[4308236.196000] acx v0.3.21: net device wlan0, driver compiled against wireless extensions 19 and Linux 2.6.15-20-386



Shall I make any route add to make it work?(I tried before but didn't change still no access point!)

---

