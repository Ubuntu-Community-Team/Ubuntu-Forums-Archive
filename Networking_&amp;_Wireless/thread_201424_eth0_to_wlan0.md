---
title: "eth0 to wlan0 ?"
date: 2006-06-21
forum: Networking &amp; Wireless
---

### Post by Feppa on 2006-06-21
Im trying to get wirless to work (Ubuntu Dapper) on my Acer Aspire 5021WLMi according to the guide [https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64](https://help.ubuntu.com/community/WifiDocs/Acer5021WLMi_Amd64)

currently my wirless network is eth0

then i run command:

dmesg

i get this result

wlan0: vendor: ''
[17180796.036000] wlan0: ndiswrapper ethernet device 00:14:a4:07:b2:80 using driver bcmwl5, 14E4:4318:1468:0311.5.conf
[17180796.036000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK


how do i change so that eth0 becomes wlan0 ?

---

### Post by pmshirey on 2006-06-21
> how do i change so that eth0 becomes wlan0 ?

I just went into connection properties and typed in wlan0 where eth0 was

---

### Post by noname101 on 2006-06-21
eth0 is your ethernet card most likely. So configure wlan0.

---

### Post by Feppa on 2006-06-22
[QUOTE=pmshirey]I just went into connection properties and typed in wlan0 where eth0 was[/QUOTE]

You mean in the gui? I can't change the name there.

-----------------------------------------------------

[QUOTE=noname101]eth0 is your ethernet card most likely. So configure wlan0.[/QUOTE]

my ethernet card is eth0.

---

### Post by goodmaj on 2006-06-22
Try editing /etc/modprobe.d/ndiswrapper

You will have to sudo to do the edit.  Change wlan0 to eth0 and see if that helps.

---

### Post by Feppa on 2006-06-24
[QUOTE=goodmaj]Try editing /etc/modprobe.d/ndiswrapper

You will have to sudo to do the edit.  Change wlan0 to eth0 and see if that helps.[/QUOTE]

The wireless connection is still eth0 ](*,) .

Any more ideas?

---

### Post by wieman01 on 2006-06-24
Hi, 

Your wireless connection is definitely NOT "eth0" which happens to be your ethernet adapter. The "dmesg" message indicates that. 

> wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

So the good news is that your wireless adapter "wlan0" is recognized... the missing piece is bringing it up. Could you post the content of this file:

> sudo gedit /etc/network/interfaces

I think the issue might be wrong settings in there. 

Can you also tell us what your router's configuration is (e.g. DHCP, encryption, ESSID broadcasting). That will help a lot. Also what is the output when running this command in a terminal:

> ndiswrapper -l

Cheers, buddy, we are getting there!

N.B.: I am using the same setup as you on my desktop computer.

---

### Post by Feppa on 2006-06-25
I know you dont belive me but look here:

root@mars:/proc/acpi/acer# iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

root@mars:/proc/acpi/acer# iwlist eth0 scan
eth0      Scan completed :
          Cell 01 - Address: 00:0F:B5:AF:51:14
                    ESSID:"Hans"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:0/100  Signal level:-85 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:13:46:42:4B:64
                    ESSID:"sun"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-50 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

------

Then i use dmesg i get this at the end:

[17180513.212000] ACPI: PCI interrupt for device 0000:06:05.0 disabled
[17180526.452000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[17180526.456000] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[17180526.460000] ACPI: PCI Interrupt 0000:06:05.0[A] -> GSI 21 (level, low) -> IRQ 177
[17180526.468000] ndiswrapper: using irq 177
[17180527.472000] wlan0: vendor: ''
[17180527.472000] wlan0: ndiswrapper ethernet device 00:14:a4:07:b2:80 using driver bcmwl5, 14E4:4318:1468:0311.5.conf
[17180527.472000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[17180681.960000] acer_acpi: Acer Laptop ACPI Extras version 0.3
[17180762.504000] acer_acpi: Wireless value 1

Then i run ndiswrapper -l i get:

root@mars:/proc/acpi/acer# ndiswrapper -l
Installed ndis drivers:
bcmwl5          driver present, hardware present
root@mars:/proc/acpi/acer#

i have a d-link router 624+ and it uses wpa but i have tried wep but cannot connect. The wird thing is that the driver expects wlan0 but my wireless has eth0.

Edit:
Sorry i almost forgot the output of sudo gedit /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp

---

### Post by wieman01 on 2006-06-26
Hi Feppa, 

Oh I see... This is a strange thing to happen but apparently there is an alias for "wlan0" configured somewhere. Let me check that out tonight... Perhaps I can tell you later on where to control that bit.

Could you also post "ifconfig" please?

Have you got NetworkManager installed?

---

### Post by wieman01 on 2006-06-26
Hi, 

This may be a useful hint... 

> There is an ether= kernel command-line parameter that can control the assignment of Ethernet device names and other resources for statically linked drivers, and there are command-line options and aliases in /etc/modules.conf to control them for loadable module drivers. The bootparam(7) man page (type man 7 bootparam from a terminal) provides details on the former; and the modules.conf(5) man page explains more than you will want to know about the latter.

Can you open "/etc/modules.conf" (or similar... I am not at home to validate it) and search for "eth0"? Make a safety-copy of the file and change "eth0" to "wlan0", then reboot.

Any better now?

---

### Post by Feppa on 2006-06-26
[QUOTE=wieman01]Hi Feppa, 

Oh I see... This is a strange thing to happen but apparently there is an alias for "wlan0" configured somewhere. Let me check that out tonight... Perhaps I can tell you later on where to control that bit.

Could you also post "ifconfig" please?

Have you got NetworkManager installed?

He[/QUOTE]


My output of ifconfig is:

eth1      Link encap:Ethernet  HWaddr 00:0A:E4:E3:E7:52
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fee3:e752/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:23187 (22.6 KiB)  TX bytes:1854 (1.8 KiB)
          Interrupt:66 Base address:0xa400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:131 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6572 (6.4 KiB)  TX bytes:6572 (6.4 KiB)

I havent got Networkmanager installd, should i have?

---

### Post by Feppa on 2006-06-26
[QUOTE=wieman01]Hi, 

This may be a useful hint... 



Can you open "/etc/modules.conf" (or similar... I am not at home to validate it) and search for "eth0"? Make a safety-copy of the file and change "eth0" to "wlan0", then reboot.

Any better now?

He[/QUOTE]

It looks like this.

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod

---

### Post by Feppa on 2006-06-26
Then i run the command ifconfig -a i get this result.

 ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:14:A4:07:B2:80
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Memory:c0204000-c0206000

eth1      Link encap:Ethernet  HWaddr 00:0A:E4:E3:E7:52
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fee3:e752/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1244772 (1.1 MiB)  TX bytes:217862 (212.7 KiB)
          Interrupt:66 Base address:0xa400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:141 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7072 (6.9 KiB)  TX bytes:7072 (6.9 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by Feppa on 2006-06-26
i have installed networkmanager and the gui for gnome. it finds my wireless network but cannot connect. Maybe this is because ndiswrapper wants to bind the driver to wlan0 but my is eth0 ?

---

### Post by goodmaj on 2006-06-26
This is not strictly kosher, but it worked for an install that I did.

Assuming you have the correct drivers for ndiswrapper, you can live with the port being called eth0.  You have to change the line in /etc/modprobe.d/ndiswrapper from alias wlan0 ndiswrapper to alias eth0 ndiswrapper.  You will need to use sudo to make the change.

---

### Post by Feppa on 2006-06-26
Yes!!!! I works now! Any idea on how to make this work with WPA-PSK ? I really want this for security reasons.

---

