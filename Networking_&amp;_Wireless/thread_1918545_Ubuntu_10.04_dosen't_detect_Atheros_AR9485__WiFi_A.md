---
title: "Ubuntu 10.04 dosen't detect Atheros AR9485  WiFi Adapter in VMware"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by Monster Mark on 2012-02-01
Hello Guys,

Started with ubuntu and wireless networking about a week ago. facing some problems getting Ubuntu to detect my wifi adapter.

Laptop: HP g6 series
Version : Ubuntu 10.04.2 LTS
Adapter:Atheros AR9485 802.11b/g/n WiFi Adapter

Running on Windows 7 host using VMware 8.

However, ubuntu detects only the usb wireless belkin adapter as wlan0 and works perfectly.

Without the usb Belkin adapter.. and powered ON Atheros,
I ran the following and the results...

```
root@bt:~# uname -a
Linux bt 2.6.39.4 #1 SMP Thu Aug 18 13:38:02 NZST 2011 i686 GNU/Linux
root@bt:~# lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 01)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 01)
00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 08)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:07.7 System peripheral: VMware Virtual Machine Communication Interface (rev 10)
00:0f.0 VGA compatible controller: VMware SVGA II Adapter
00:10.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 01)
00:11.0 PCI bridge: VMware PCI bridge (rev 02)
00:15.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:15.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:16.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:17.7 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.0 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.1 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.2 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.3 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.4 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.5 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.6 PCI bridge: VMware PCI Express Root Port (rev 01)
00:18.7 PCI bridge: VMware PCI Express Root Port (rev 01)
02:00.0 USB Controller: VMware USB1.1 UHCI Controller
02:01.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 10)
02:02.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 02)
02:03.0 USB Controller: VMware USB2 EHCI Controller
root@bt:~# lsmod
Module                  Size  Used by
dm_crypt               14720  0 
snd_ens1371            18023  0 
gameport                7778  1 snd_ens1371
snd_ac97_codec        101869  1 snd_ens1371
ac97_bus                 982  1 snd_ac97_codec
snd_pcm_oss            36427  0 
snd_mixer_oss          13581  1 snd_pcm_oss
snd_pcm                68662  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1358  0 
snd_seq_oss            26216  0 
snd_seq_midi            4460  0 
snd_rawmidi            18745  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event      5720  2 snd_seq_oss,snd_seq_midi
snd_seq                45875  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              17803  2 snd_pcm,snd_seq
snd_seq_device          5281  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    50697  10 snd_ens1371,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtl8187                51301  0 
ppdev                   5096  0 
joydev                  8649  0 
parport_pc             26143  1 
vmw_balloon             3566  0 
mac80211              255996  1 rtl8187
soundcore               6048  1 snd
cfg80211              153414  2 rtl8187,mac80211
snd_page_alloc          6801  1 snd_pcm
rfkill                 14987  1 cfg80211
eeprom_93cx6            1292  1 rtl8187
psmouse                52655  0 
shpchp                 24986  0 
serio_raw               3744  0 
i2c_piix4               7907  0 
mac_hid                 3029  0 
lp                      7373  0 
parport                29468  3 ppdev,parport_pc,lp
vmw_pvscsi             13335  0 
vmxnet3                36703  0 
pcnet32                29779  0 
usbhid                 35443  0 
mptspi                 14781  2 
hid                    69090  1 usbhid
floppy                 54673  0 
intel_agp               9614  1 
mptscsih               29911  1 mptspi
mii                     4091  1 pcnet32
intel_gtt              13296  1 intel_agp
mptbase                86277  2 mptspi,mptscsih
agpgart                27414  2 intel_agp,intel_gtt
root@bt:~# ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:0c:29:ec:2f:00  
          inet addr:192.168.49.131  Bcast:192.168.49.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:feec:2f00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:62 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5952 (5.9 KB)  TX bytes:2152 (2.1 KB)
          Interrupt:19 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

root@bt:~# cat /etc/network/interfaces
auto lo
iface lo inet loopback
root@bt:~# cat /etc/resolv.conf
# Generated by NetworkManager
domain localdomain
search localdomain
nameserver 192.168.49.2

```
Thanks..
Regards, 
Monster Mark.

---

### Post by TheFu on 2012-02-01
I do not use VMware Player.  I don't know if I understand you, but if Ubuntu is your client OS, it only sees the virtual devices provided by VMware (assumed Player).  BTW, there are 6+ different VMware virtualization tools, so being more specific on the exact name and version could help someone help you more.

In the network settings for your VM, what network adapters are you providing to the VM?  Is the "cable connected?" Personally, I avoid bothering VMs with WiFi NICs and always choose the most-excellent Intel PRO/1000 regardless of the actual physical hardware on the system.  The hardware presented to the VM is virtual anyway.  So on my laptop, it physically has 
* Realtek GigB
* DW1501 Wireless-N mini-card

All my VMs ever see are Intel PRO/1000 NICs. These are translated by the hypervisor.

---

### Post by Monster Mark on 2012-02-01
I am using VMware Player ,Version: 4.0.0 build-471780.
In the Vm settings>network adapter settings:
1. Bridged
2. NAT   [i get internet access only thru wired ethernet]
3. Host-only
4. Lan Segments
--all of which are only for physically connected n/w adapters..


You're right, the linux vm guest can not see the wireless adapters on the host.
So i guess, if i want the wireless feature of the atheros to work, i need to fresh-install ubuntu on my hard-disk instead of  visualization. So the only solution to get wireless access on vm-ubuntu would be using my Belkin usb adapter..
   Too bad.. i cant use my internal wifi for linux in a virtual environment...

 
Did some research and found out --------
Any virtualisation software can only use USB wireless network cards as  physical devices, all other types of wireless card are seen as virtual  ethernet devices and can only be seen as a wireless device by the host  and not by the guest operating system.
-----------

Thanks for making me realize that its pointless trying to make it work in VMs. No more wasting time on this subject ;)

---

