---
title: "Help! Intel, Ubuntu 10.04/ Dell d630 Latitude"
date: 2011-05-26
forum: Networking &amp; Wireless
---

### Post by tomkat3 on 2011-05-26
Hello all, I am yet another linux noob having problems with wireless. I'm running ubuntu 10.04 on a Dell Latitude d630. I run Ubuntu and Windows 7 on the same computer through a hard drive partition, and I can  get to the internet from Windows normally.

I'm tryinng to connect to my university's wireless network. Its one of those cases where the wireless was working fine for months, until I came in one Monday morning and it couldn't connect. I wanted to solve the problem myself before creating yet another wireless troubleshooting thread, so went through the steps here:

[http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html](http://www.ubuntugeek.com/how-to-troubleshoot-wireless-network-connection-in-ubuntu.html)

This sort of sudden, random cutoff has happened to me before. Last time it somehow fixed itself after a few days. How can Windows connect to the internet more reliably than ubuntu? Is there something I can do to fix this? Everything else works some much better on ubuntu!

I digress...here are the fruits of my troubleshooting. Let me know if anything's missing:

$ nm-tool

NetworkManager Tool

State: disconnected

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:1F:3C:A1:D9:7A

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

$ sudo ifconfig wlan0 down
$ sudo dhclient -r wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:1f:3c:a1:d9:7a
Sending on   LPF/wlan0/00:1f:3c:a1:d9:7a
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 129.59.90.16 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.

---I probably should have stopped after I got "State: disconnected" and "Network unreachable" but just for kicks, I continued going through the commands the website gave me:

$ sudo ifconfig wlan0 up
$ sudo iwconfig wlan0 essid \x00
$ sudo iwconfig wlan0 mode Managed
$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:1f:3c:a1:d9:7a
Sending on   LPF/wlan0/00:1f:3c:a1:d9:7a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---Here's some other stuff I get from putting in the random things the help files tell me to type. I've been leaving out stuff that relates to eth0, since I can go through a wired network just fine. eth0 is for ethernet wires, right? :???:

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"x00"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:a1:d9:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19534 (19.5 KB)  TX bytes:724 (724.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3c:a1:d9:7a  
          inet addr:169.254.9.65  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

$ ping -c3 85.190.27.2
connect: Network is unreachable

$ sudo lshw -class network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:a1:d9:7a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:f9fff000-f9ffffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:9a:c4:72
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5755m-v3.29 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:f9ef0000-f9efffff


What's going on here?

---

### Post by josephmills on 2011-05-26
hi there could you please open your terminal (ctrl+alt_t)  and type in ```
lspci -nn
``` and ```
rfkill list all 
``` snd ```
lsmod | grep iw
``` and paste that all here thanks ohh and yes eth0 usually is for you cable

---

### Post by tomkat3 on 2011-05-26
Thank you sir! Here you are:

$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 [8086:2849] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Quadro NVS 135M [10de:042b] (rev a1)
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. Cardbus bridge [1217:7135] (rev 21)
03:01.4 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express [14e4:1673] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)


rfkill list all
$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


$ lsmod | grep iw
iwl3945                68727  0 
iwlcore               106050  1 iwl3945
mac80211              205402  2 iwl3945,iwlcore
led_class               2864  2 iwl3945,iwlcore
cfg80211              126528  3 iwl3945,iwlcore,mac80211

---

### Post by josephmills on 2011-05-26
```
lsmod 
``` thanks

---

### Post by tomkat3 on 2011-05-26
I'd also appreciate it if you could tell me what all these commands are supposed to show us, when practical.

$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
joydev                  8740  0 
snd_hda_codec_idt      52010  1 
dell_wmi                1793  0 
pcmcia                 30784  0 
snd_hda_intel          22069  3 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54180  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
arc4                    1153  2 
iwl3945                68727  0 
dell_laptop             6888  0 
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
iwlcore               106050  1 iwl3945
psmouse                63245  0 
soundcore               6620  1 snd
mac80211              205402  2 iwl3945,iwlcore
dcdbas                  5422  1 dell_laptop
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
serio_raw               3978  0 
nvidia               9726985  44 
led_class               2864  2 iwl3945,iwlcore
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
cfg80211              126528  3 iwl3945,iwlcore,mac80211
vga16fb                11385  0 
vgastate                8961  1 vga16fb
lp                      7028  0 
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
uvesafb                22297  1 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
video                  17375  0 
output                  1871  1 video
ahci                   32200  1 
tg3                   109324  0 
intel_agp              24375  0 
agpgart                31724  2 nvidia,intel_agp

---

### Post by josephmills on 2011-05-26
```
 sudo rmmod -f dell-laptop 
``` anything?

---

### Post by josephmills on 2011-05-26
lsmod  = is a command on Linux systems which prints the contents of the /proc/modules file. It shows which loadable kernel modules are currently loaded. 

lspci -nn = list all pci cards with name and number 

rfkill list all = shows all radio frq and shows if they are blocked 

grep = grep is a filter 
 
sudo rmmod -f dell-laptop= soft blocks that mod the dell_laptop I think that this is the one that is getting in the way;) 

here is some more info on regular expression [http://en.wikipedia.org/wiki/Regular_expression](http://en.wikipedia.org/wiki/Regular_expression)

---

### Post by chili555 on 2011-05-26
> **josephmills said:**
> ```
 sudo rmmod -f dell-laptop 
``` anything?Please check PM, Joseph.

---

### Post by tomkat3 on 2011-05-26
Hmmm, I put in what you gave me. It didn't print out anything in the terminal.

Wicd still couldn't connect, "unable to get IP address" and when I tried to ping it still said that the network was unreachable.

Thanks for the info though! Any other ideas? I need to get back to work soon:|

---

### Post by josephmills on 2011-05-26
> **chili555 said:**
> Please check PM, Joseph.

your turn chili  Tomcat chili555 has been mentoring me so that is why he sent a private message talking about the dell_laptop command and how it wont do anything. If he says to do something I would do it as he is one of the smartest people that I have meet in my life ):P

---

### Post by chili555 on 2011-05-26
> If he says to do something I would do it as he is one of the smartest people that I have meet in my lifeThanks; my ex-wife's lawyer might disagree!

When you try to connect in Wicd, what does it do or not do? Does it at least try? Is there a profile stored in Wicd for x00? Would you please try deleting it and reboot. See if that improves connectivity.

---

### Post by josephmills on 2011-05-26
tomcat is wicd and network manager installed together? I think that you might want to choose one

---

### Post by tomkat3 on 2011-05-26
wicd tries to connect. It gets stuck on the 'obtaining ip address' part.

Not sure what you mean by a profile for x00. What does that do, and where can I look at it?

Yes, I do have both wicd and network manager installed. What's the best way to get rid of network manager? Last night that didn't even recognize the ethernet wire I use at home.

Thanks again for the help!

---

### Post by josephmills on 2011-05-26
have you tried to hard line rest your router yet?

---

### Post by tomkat3 on 2011-05-26
> **josephmills said:**
> have you tried to hard line rest your router yet?

Sorry, I don't know what that means :confused:

I'm doing this at school, and there's not a lot of tinkering I can do with the school's hardware. Is that something I'd do from my laptop?

---

### Post by tomkat3 on 2011-05-26
D'oh, if you mean connect with a ethernet cable, then no. I'll have to go hunting for the outlet...

---

### Post by josephmills on 2011-05-26
> **tomkat3 said:**
> Sorry, I don't know what that means :confused:

I'm doing this at school, and there's not a lot of tinkering I can do with the school's hardware. Is that something I'd do from my laptop?

No that is something that you can not do from your laptop there is a switch under a router that lets you reset it if you hold it down for like 30 sec that will put the router back to default. I am not really sure what is going on here sorry but I have to go to work I hope that you get it straightened out. So you are in your dorm then? have you ried to connect to different hot spots also this might not do a thing but have you tried to change the mac address of the computer? also you can un-install network manager from ubuntusoftware center or synaptic package manager. Like I said I hope that you get it running. I should be out of work in like five hours or so. until then I wish you all the luck.:) 
Joseph

---

### Post by tomkat3 on 2011-05-26
I'm working in a lab that does computer simulations this summer. The software I use works a lot easier in linux. I hook up with an ethernet cable at home (off campus:)).

I ran around campus and tried to connect from other buildings, with no success. I'll google how to change the mac address, whatever that is...

Thanks for the help!

---

### Post by chili555 on 2011-05-26
> Not sure what you mean by a profile for x00. What does that do, and where can I look at it?There is a file that Wicd keeps with all your recent prior connections. Perhaps it's corrupted. Let's back it up and let Wicd start fresh. Open a terminal and back up the current file in case we need it:```
sudo mv /etc/wicd/wireless-settings.conf /etc/wicd/wireless-settings.bak
```Now reboot and see if Wicd connects. It will create a new fresh .conf file as needed.

---

### Post by tomkat3 on 2011-05-26
I removed network manager to clean things up, then I did what you said. It got stuck on the obtaining ip address part. Nothing appears to have changed.

---

### Post by josephmills on 2011-05-26
hi there again could we see a ```
ifconfig -a 
``` and also a ```
cat /etc/network/interfaces 

``` thanks 
cat =  concatenate files and print on the standard output

---

### Post by tomkat3 on 2011-05-27
Here you are:

$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:21:70:9a:c4:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1416 (1.4 KB)  TX bytes:1416 (1.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:a1:d9:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:50 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9581 (9.5 KB)  TX bytes:0 (0.0 B)

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by josephmills on 2011-05-27
```
sudo -s 
``` then ```
macchanger -r wlan0
``` then ```
exit 
```anything? Then could we see a ```
iwlist scan
```  thanks

---

### Post by tomkat3 on 2011-05-27
After I put in macchanger -r wlan0 I got this error:

# macchanger -r wlan0
The program 'macchanger' is currently not installed.  You can install it by typing:
apt-get install macchanger

Since I didn't have this internet, I couldn't install it, so I'll get back to you perhaps tomorrow (after I've installed it through my wireless at home, then tried to connect to the wireless at school)...unless there's another way to do this?

Thanks for sticking around, I'm surprised this thread has gotten to page 3 :shock:

---

### Post by josephmills on 2011-05-27
> **tomkat3 said:**
> After I put in macchanger -r wlan0 I got this error:

# macchanger -r wlan0
The program 'macchanger' is currently not installed.  You can install it by typing:
apt-get install macchanger

Since I didn't have this internet, I couldn't install it, so I'll get back to you perhaps tomorrow (after I've installed it through my wireless at home, then tried to connect to the wireless at school)...unless there's another way to do this?

Thanks for sticking around, I'm surprised this thread has gotten to page 3 :shock:

So you wireless at home works and not at school :-k I wonder if the school's poilcy is if the firewall wont understand the oses mac number that it blocks it. That would suck! do you or any one at school have a win computer with wireshark?

---

### Post by tomkat3 on 2011-05-27
> my wireless at home

WHOOOPS! I actually don't use wireless at home. I hook my laptop up to an ethernet cable. Its kinda clunky, but I haven't gotten around to setting up wireless. I totally typed the wrong thing there!:oops:

I'll have to go to a Starbucks to see if I can connect to wireless at other places.

I heard from someone that another guy in my lab I know to use Linux seemed to be having some sort of internet trouble too. I'll have to talk to him once he gets back from his conference. Could that be significant? Would a wireless modem discriminate against Linux like Netflix?

---

### Post by tomkat3 on 2011-05-28
Alright, I'm back at school today with macchanger installed. Here were the results:

# macchanger -r wlan0
Current MAC: 00:1f:3c:a1:d9:7a (unknown)
ERROR: Can't change MAC: interface up or not permission: Device or resource busy
# exit
exit
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

Would putting in sudo macchanger... make a difference?

---

### Post by tomkat3 on 2011-05-30
*bump*

---

