---
title: "Please help newbie with wifi"
date: 2010-12-17
forum: Networking &amp; Wireless
---

### Post by xr4ti on 2010-12-17
Hi. Thanks for reading.
 
I am brand new to ubuntu and know nothing about it. I installed 8.04 server (32 bit)yesterday on a thinkpad x61 with an intel pro 4965 AGN (or AG) wireless adapter. I dont think the adapter is working because all pings to well known internet addresses are failing. It is my understanding that the driver for this wireless adapter came with the downloaded install files. Can someone please help me (on a newbie level) or direct me in the proper direction? How do I know if I have the drivers already? How do I get wireless up and running? (My only working connection to the internet is on another laptop running Vista.)

---

### Post by Mosabama on 2010-12-17
Goto system->administration->additional drivers

and check if your wireless driver is activated. mostly it will be disables cause its closed source.
and you can check if your wireless is running by looking at the taskbar (top right corner) if you open the wireless icon there it will view the access points you can connect to.

---

### Post by xr4ti on 2010-12-17
> **Mosabama said:**
> Goto system->administration->additional drivers
 
and check if your wireless driver is activated. mostly it will be disables cause its closed source.
and you can check if your wireless is running by looking at the taskbar (top right corner) if you open the wireless icon there it will view the access points you can connect to.
 
Thanks but I dont have any GUI installed

---

### Post by chili555 on 2010-12-17
The driver for this card is already installed. Let's see if some diagnostics can tell us what's happening. If you installed the server version, may I assume you do not have a graphical interface running? If not, please enter at the command prompt:```
rfkill list all
sudo iwlist wlan0 scan
```Please jot down and post the result.

If you do have a graphical interface; that is a desktop, please open Applications > Accessories > Terminal and run the same commands.

---

### Post by xr4ti on 2010-12-17
> **chili555 said:**
> The driver for this card is already installed. Let's see if some diagnostics can tell us what's happening. If you installed the server version, may I assume you do not have a graphical interface running? If not, please enter at the command prompt:```
rfkill list all
sudo iwlist wlan0 scan
```Please jot down and post the result.
 
If you do have a graphical interface; that is a desktop, please open Applications > Accessories > Terminal and run the same commands.
 
-bash: rfkill: command not found
 
wlan0 Interface doesn't support scanning

---

### Post by Mosabama on 2010-12-17
sorry didnt notice you are running ubuntu server. I assumed you are ruuning ubuntu desktop.

can you please paste the out put of the following:
ifconfig
lsmod

---

### Post by chili555 on 2010-12-17
How about:```
dmesg | grep iwl
```The pipe symbol | is on the right of my US keyboard on the same key with \.

---

### Post by Mosabama on 2010-12-17
> **chili555 said:**
> How about:```
dmesg | grep iwl
```The pipe symbol | is on the right of my US keyboard on the same key with \.

I believe its grep wl. I did that on my laptop and returned nothing. the module name is wl isnt it?

---

### Post by chili555 on 2010-12-17
> **Mosabama said:**
> I believe its grep wl. I did that on my laptop and returned nothing. the module name is wl isnt it?

> intel pro 4965 AGNThe module is *iwlagn*. It is installed by default and need not be activated after installation.

---

### Post by Mosabama on 2010-12-17
ops. sorry didnt know about that. :)
so this driver is open source?

---

### Post by chili555 on 2010-12-17
> **Mosabama said:**
> ops. sorry didnt know about that. :)
so this driver is open source?Yes, indeed, courtesy of our fine friends at Intel!

---

### Post by xr4ti on 2010-12-18
> **Mosabama said:**
> sorry didnt notice you are running ubuntu server. I assumed you are ruuning ubuntu desktop.
 
can you please paste the out put of the following:
ifconfig
lsmod
 
 
Per your request:
 
$ ifconfig
eth0  Link encap:Ethernet  HWaddr 00:1d:72:96:e0:0a
 inet addr:192.168.1.10 Bcast:192.168.1.255 Mask:255.255.255.0
  UP BROADCAST MULTICAST  MTU:1500  Metric:1
 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000
 RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 Base address:0x1840 Memory:f8200000-f8220000
lo Link encap:Local Loopback
 inet addr:127.0.0.1  Mask:255.0.0.0
 inet6 addr:  ::1/128 Scope:host
 UP LOOPBACK RUNNING  MTU:16436  Metric:1
 RX packets:4 errors:0 dropped:0 overruns:0 frame:0
 TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:0
 RX bytes:374  (374.0 B)   TX bytes:374 (374.0 B)
 

$lsmod
Module     Size Used by
iptable_filter     3840 0
ip_tables    14820 1 iptable_filter
x_tables     16132 1 ip_tables
sbp2     24584 0
parport_pc    36644 0
lp     12324 0
parport     37704 2 parport_pc,lp
loop     19076 0
pcmcia     40876 0
ipv6          273188 10
iwl4965          106228 0
iwlwifi_mac80211  218980 1 iwl4965
cfg80211    15112 1 iwlwifi_mac80211
battery     14212 0
ac      6916 0
sdhci     19204 0
video     19856 0
serio_raw     7940 0
snd_hda_intel   346136 0
output      4736 1 video
psmouse      40208 0
mmc_core    51588 1 sdhci
yenta_socket    27404 1
rsrc_nonstatic     14336 1 yenta_socket
pcmcia_core    40596 3 pcmcia,yenta_socket,rsrc_nonstatic
thinkpad_acpi    51708 0
snd_pcm     78724 1 snd_hda_intel
snd_timer    24836 1 snd_pcm
snd_page_alloc    11528 2 snd_hda_intel, snd_pcm
snd_hwdep    10500 1 snd_hda_intel
snd      9232 0
intel_agp    25620 1
iTCO_wdt    13092 0
ITCO_vendor_support    4868 1 iTCO_wdt
soundcore     8800 1 snd
agpgart     34760 1 intel_agp
shpchp     34452 0
pci_hotplug    30880 1 shpchp
nvram     10120 1 thinkpad_acpi
evdev     12928 0
pcspkr      4224 0
ext3    136712 1
jbd     48204 1 ext3
mbcache      9600 1 ext3
sg     36496 0
ata_generic     8324 0
pata_acpi     8320 0
sd_mod     30592 3
ata_piix    19588 0
ahci      28548 2
ohci1394    33968 0
libata    159728 4 ata_generic,pata_acpi,ata_piix,ahci
scsi_mod   151436 4 sbp2,sg,sd_mod,libata
ieee1394    93752 2 sbp2,ohci1394
uhci_hcd    27152 0
ehci_hcd    38540 0
usbcore    146412 3 uhci_hcd,ehci_hcd
e1000    126784 0
thermal     16796 0
processor    36616 3 thermal
fan      5636 0
fbcon     42656 0
tileblit     3584 1 fbcon
font      9472 1 fbcon
bitblit      6784 1 fbcon
softcursor     3072 1 bitblit
fuse     50580 1

---

### Post by xr4ti on 2010-12-18
> **chili555 said:**
> How about:```
dmesg | grep iwl
```The pipe symbol | is on the right of my US keyboard on the same key with \.
 

$dmesg | grep iwl
[ 18.784321] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[ 18.784325] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[ 18.784540] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[ 19.512311] iwl4965: Radio disabled by HW RF Kill switch

---

### Post by bkratz on 2010-12-18
> **xr4ti said:**
> $dmesg | grep iwl
[ 18.784321] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[ 18.784325] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[ 18.784540] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[COLOR="Red"][ 19.512311] iwl4965: Radio disabled by HW RF Kill switch
[/COLOR]



Is there a wireless switch to turn on?

---

### Post by xr4ti on 2010-12-18
> **bkratz said:**
> [/COLOR]
 
 
 
Is there a wireless switch to turn on?
 
 
Great! Got that taken care of.  Now what?  How do I connect to a wireless network (from command line)?

---

### Post by chili555 on 2010-12-18
I assume it's your intention to have the interface connect automatically on boot without any further intervention. The traditional way is to set up /etc/network/interfaces. If it's a server, you undoubtably want a static IP address. If so, you will also need to populate /etc/resolv.conf. Select an IP address outside the range used by the DHCP server in the router. Here is a sample /etc/network/interfaces file for a WPA network:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wpa-ssid my_router
wpa-psk my_key

#auto eth0
iface eth0 inet dhcp
```Here is my sample /etc/resolv.conf:```
nameserver 192.168.1.254
```Disconnect the ethernet cable and restart networking:```
sudo /etc/init.d/networking restart
```Make sure you got the correct IP address:```
ifconfig wlan0
```Make sure you are connected correctly:```
ping -c3 192.168.1.254
ping -c3 www.google.com
```Substitute your details as needed. Post back with any errors or problems.

---

### Post by xr4ti on 2010-12-18
> **chili555 said:**
> I assume it's your intention to have the interface connect automatically on boot without any further intervention. The traditional way is to set up /etc/network/interfaces. If it's a server, you undoubtably want a static IP address. If so, you will also need to populate /etc/resolv.conf. Select an IP address outside the range used by the DHCP server in the router. Here is a sample /etc/network/interfaces file for a WPA network:```
auto lo
iface lo inet loopback
 
auto wlan0
iface wlan0 inet static
address 192.168.1.108
netmask 255.255.255.0
gateway 192.168.1.254
wpa-ssid my_router
wpa-psk my_key
 
#auto eth0
iface eth0 inet dhcp
```Here is my sample /etc/resolv.conf:```
nameserver 192.168.1.254
```Disconnect the ethernet cable and restart networking:```
sudo /etc/init.d/networking restart
```Make sure you got the correct IP address:```
ifconfig wlan0
```Make sure you are connected correctly:```
ping -c3 192.168.1.254
ping -c3 www.google.com
```Substitute your details as needed. Post back with any errors or problems.
 
 
Thanks very much!  Did all that.  Here is what I setup in /etc/network/interfaces:
 
auto wlan0
iface wlan0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid NETGEAR
 
 
In /etc/resolv.conf:
 
nameserver 192.168.1.1
 
 
I can ping 192.168.1.125 with success.
I cannot ping 192.168.1.1.  Says destination host unreachable.
 
Now here is the story.  I am in a hotel where the network name (SSID) is NETGEAR.  Wireless security type is none (Its wide open with no security).  From my Windows laptop here is the configuration (below).  Hope this helps.  Thanks very much!!!
 
Windows IP Configuration

Ethernet adapter Local Area Connection 2:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
Wireless LAN adapter Wireless Network Connection:
   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::65b4:95:1848:270b%11
   IPv4 Address. . . . . . . . . . . : 192.168.1.4
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.1
Ethernet adapter Local Area Connection:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
Tunnel adapter Local Area Connection* 6:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
Tunnel adapter Local Area Connection* 7:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
Tunnel adapter Local Area Connection* 11:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
Tunnel adapter Local Area Connection* 13:
   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:1c61:181e:3f57:fefb
   Link-local IPv6 Address . . . . . : fe80::1c61:181e:3f57:fefb%13
   Default Gateway . . . . . . . . . : ::
 
 
 
===========================================================================
Interface List
 12 ...00 a0 d5 ff ff 85 ...... Sierra Wireless 1xEV-DO Network Adapter
 11 ...00 21 5c 02 7f 6b ...... Intel(R) Wireless WiFi Link 4965AGN
 10 ...00 1c 25 be 9a 60 ...... Intel(R) 82566MM Gigabit Network Connection
  1 ........................... Software Loopback Interface 1
 14 ...00 00 00 00 00 00 00 e0  isatap.{AE4DD37A-EF69-49C8-869B-4411C05E2AFE}
 15 ...00 00 00 00 00 00 00 e0  isatap.{D4D3D7C4-6BFC-4AD3-9AA5-53210268C1BC}
 17 ...00 00 00 00 00 00 00 e0  isatap.{767FCF3C-D816-4707-BCBB-587A8CE5EF39}
 13 ...02 00 54 55 4e 01 ...... Teredo Tunneling Pseudo-Interface
===========================================================================
IPv4 Route Table
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.1.1      192.168.1.4     25
        127.0.0.0        255.0.0.0         On-link         127.0.0.1    306
        127.0.0.1  255.255.255.255         On-link         127.0.0.1    306
  127.255.255.255  255.255.255.255         On-link         127.0.0.1    306
      192.168.1.0    255.255.255.0         On-link       192.168.1.4    281
      192.168.1.4  255.255.255.255         On-link       192.168.1.4    281
    192.168.1.255  255.255.255.255         On-link       192.168.1.4    281
        224.0.0.0        240.0.0.0         On-link         127.0.0.1    306
        224.0.0.0        240.0.0.0         On-link       192.168.1.4    281
  255.255.255.255  255.255.255.255         On-link         127.0.0.1    306
  255.255.255.255  255.255.255.255         On-link       192.168.1.4    281
===========================================================================
Persistent Routes:
  None
IPv6 Route Table
===========================================================================
Active Routes:
 If Metric Network Destination      Gateway
 13     18 ::/0                     On-link
  1    306 ::1/128                  On-link
 13     18 2001::/32                On-link
 13    266 2001:0:4137:9e76:1c61:181e:3f57:fefb/128
                                    On-link
 11    281 fe80::/64                On-link
 13    266 fe80::/64                On-link
 13    266 fe80::1c61:181e:3f57:fefb/128
                                    On-link
 11    281 fe80::65b4:95:1848:270b/128
                                    On-link
  1    306 ff00::/8                 On-link
 13    266 ff00::/8                 On-link
 11    281 ff00::/8                 On-link
===========================================================================
Persistent Routes:
  None

---

### Post by xr4ti on 2010-12-18
Please help!!!

---

### Post by chili555 on 2010-12-18
With no security, the stanza should be:```
auto wlan0
iface wlan0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR="Red"]essid[/COLOR] NETGEAR

```Also, don't forget the loopback stanzas; they are critical.

Can you scan?```
sudo iwlist wlan0 scan
```Verify that the ESSID is NETGEAR and not Netgear or netgear. It must be exact.

Last, I'd try a reboot.> I can ping 192.168.1.125 with success.You are simply pinging yourself; it's meaningless.

After a reboot, look in:```
sudo cat /var/log/syslog | grep wlan
```See if there are any interesting clues.

---

### Post by xr4ti on 2010-12-18
> **chili555 said:**
> With no security, the stanza should be:```
auto wlan0
iface wlan0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR=red]essid[/COLOR] NETGEAR

```Also, don't forget the loopback stanzas; they are critical.
 
Can you scan?```
sudo iwlist wlan0 scan
```Verify that the ESSID is NETGEAR and not Netgear or netgear. It must be exact.
 
Last, I'd try a reboot.You are simply pinging yourself; it's meaningless.
 
After a reboot, look in:```
sudo cat /var/log/syslog | grep wlan
```See if there are any interesting clues.
 
thanks, made the fix then did a reboot.
 
scan says:
 
ESSID:"NETGEAR"
the ssid is NETGEAR (all caps, no double quotes)
 
syslog says:
wlan0: link is not ready
 
still not working.

---

### Post by xr4ti on 2010-12-18
One more thing, iwconfig says:
 
ESSID:""

---

### Post by xr4ti on 2010-12-19
help!

---

### Post by chili555 on 2010-12-19
I made a mistake and I apologize. Your interfaces file should read:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR="Red"]wireless-essid[/COLOR] NETGEAR
```When you scan:```
sudo iwlist wlan0 scan
```Please verify that it says Encryption key:off.

After you make the change above, please do:```
sudo ifdown wlan0 && sudo ifup wlan0
ping -c3 192.168.1.1
ping -c3 www.google.com
```Note any errors and post back.

---

### Post by xr4ti on 2010-12-19
> **chili555 said:**
> I made a mistake and I apologize. Your interfaces file should read:```
auto lo
iface lo inet loopback
 
auto wlan0
iface wlan0 inet static
address 192.168.1.125
netmask 255.255.255.0
gateway 192.168.1.1
[COLOR=red]wireless-essid[/COLOR] NETGEAR
```When you scan:```
sudo iwlist wlan0 scan
```Please verify that it says Encryption key:off.
 
After you make the change above, please do:```
sudo ifdown wlan0 && sudo ifup wlan0
ping -c3 192.168.1.1
ping -c3 www.google.com
```Note any errors and post back.
 
Chili555, you are great!  I found the problem earlier today.  The issue was wireless-essid.  Thanks very much.
 
Now I'm trying to figure out how to use aptitude to load a lightweight gui.  Does anyone know if aptitude will actually download packages from a remote host?  Again remember I'm only 3 days old at this.

---

### Post by chili555 on 2010-12-19
I will take your reply as 'Woo Hoo! It's working!' I'm very glad.

Aptitude will download files from any repository listed in /etc/apt/sources.list. ```
cat /etc/apt/sources.list
```If you are trying to download a package from elsewhere, first, be very careful, but also you can use wget:```
wget http://www.website.com/packages/filename.deb
```Then install it:```
sudo dpkg -i filename.deb
```If you need more help, please move over to [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

---

