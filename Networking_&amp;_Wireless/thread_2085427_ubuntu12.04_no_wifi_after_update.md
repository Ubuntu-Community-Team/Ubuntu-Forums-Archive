---
title: "ubuntu12.04 no wifi after update"
date: 2012-11-18
forum: Networking &amp; Wireless
---

### Post by Lim Chee Choon on 2012-11-18
netbook using  RTL8188CE 802.11b/g/n WiFi Adapter. it was working well before update. no problem with usb tethering.


lspci
> 00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

ifconfig
> eth0      Link encap:Ethernet  HWaddr 8c:89:a5:00:fd:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:230 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22006 (22.0 KB)  TX bytes:22006 (22.0 KB)

usb0      Link encap:Ethernet  HWaddr ae:fa:39:e0:a0:bc  
          inet addr:192.168.42.29  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::acfa:39ff:fee0:a0bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4158 errors:6 dropped:0 overruns:0 frame:6
          TX packets:3931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3209636 (3.2 MB)  TX bytes:828077 (828.0 KB)


iwconfig
>  lo        no wireless extensions.

usb0      no wireless extensions.

eth0      no wireless extensions.  


lsmod
> Module                  Size  Used by
vesafb                 13516  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
rndis_host             13560  0 
cdc_ether              13312  1 rndis_host
usbnet                 25214  2 rndis_host,cdc_ether
psmouse                86486  0 
snd_rawmidi            25424  1 snd_seq_midi
serio_raw              13027  0 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17393  0 
rtl8192ce              75491  0 
rtl8192c_common        69519  1 rtl8192ce
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rtlwifi                95804  1 rtl8192ce
mac80211              436455  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              178679  2 rtlwifi,mac80211
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  0 
video                  19068  0 
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77392  1 usbhid
r8169                  56321  0   

---

### Post by Lim Chee Choon on 2012-11-18
please helpme.

---

### Post by Lim Chee Choon on 2012-11-22
please help................

---

### Post by westie457 on 2012-11-22
Hello and welcome to the Fora.

```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```

Copy and paste the above command into a terminal, please.

It will download, install and run a script to generate a text file of what is in your system. Sensitive details (IP address and certain hardware identifiers will be ignored). Attach the text file to a new reply here by clicking in the paper-clip at the top of the message Window.

Thank you

---

### Post by Lim Chee Choon on 2012-11-23
thnkx

---

### Post by Lim Chee Choon on 2012-11-23
and then?............

---

### Post by Lim Chee Choon on 2012-11-24
please help me....thanks.

---

### Post by Lim Chee Choon on 2012-11-25
it was okay before updating........

---

### Post by NikTh on 2012-11-25
Open a terminal and try 
```
sudo apt-get install --reinstall linux-firmware linux-firmware-nonfree
``` 

Reboot your PC and see if wireless works. 

Also give the results of 
```
dmesg | grep -ie rtl
``` 
Thanks

---

### Post by wildmanne39 on 2012-11-25
Hi, do everything in post 6 of this link.
[http://ubuntuforums.org/showthread.php?p=12171877#post12171877](http://ubuntuforums.org/showthread.php?p=12171877#post12171877)
Also you will have to shutdown your computer and unplug your usb device.
Thanks

---

### Post by Lim Chee Choon on 2012-11-25
after reinstall firmware and reboot,

dmesg | grep -ie rtl
```
[    2.573901] r8169 0000:02:00.0: eth0: RTL8105e at 0xf8410000, 8c:89:a5:00:fd:fb, XID 00a00000 IRQ 43
[   15.883264] rtl8192ce 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.883289] rtl8192ce 0000:01:00.0: setting latency timer to 64
[   15.883558] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: Unknown. Bug?
[   16.507226] rtl8192ce:rtl92c_init_sw_vars():<0-0> Failed to request firmware!
[   16.507239] rtlwifi:rtl_pci_probe():<0-0> Can't init_sw_vars.
[   16.507304] rtl8192ce 0000:01:00.0: PCI INT A disabled
```

also tried gksudo gedit /etc/modprobe.d/rtl8192ce.conf


when i mouse over the wifi icon, i saw "wired network (Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller) disconnected" in grey colour

i m now using my android phone for USB tethering which is shown as Wired Connection 2

---

### Post by wildmanne39 on 2012-11-25
Did you do everything in that link? it all has to be done for this device to work properly.

Also your wireless will not connect as long as you have another device connecting to the internet on that computer.

Also make sure your router is set to just wpa2 if you have that option.
Thanks

---

### Post by wildmanne39 on 2012-11-25
Hi, also install rfkill then post the output of:
```
iwconfig
rfkill list all
```
With the usb tethering adapter disconnected, you may have to reboot before running the commands.
Thanks

---

### Post by Lim Chee Choon on 2012-11-26
sudo apt-get install rfkill
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
rfkill is already the newest version.
The following packages were automatically installed and are no longer required:
  libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-help-en-gb
  ibus-table-cangjie3 ibus-table-cangjie5 mythes-en-au mythes-en-us
  openoffice.org-hyphenation hyphen-en-us ibus-table-cangjie-big
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
```


lim@lim-netbook:~$ iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

---

### Post by NikTh on 2012-11-26
Hi ,
try this please. 
Take the tar.gz file from the attached , and save it to your Downloads/ folder. 
Then open a terminal and do 
```
cd Downloads/
tar xzvf rtlwifi.tar.gr
sudo cp rtlwifi/rtl8192*fw.bin /lib/firmware/rtlwifi/
```Then reboot your PC and unplug everything, Androind phone , Ethernet cable.. and see if working.

If not , then please run again the wireless_script with this command
```
sudo ./wireless_script
```and attach the netifno.txt again here. It would be more clear if no other devices are connected when you run the script (no phone or Ethernet cable). 

Thanks

---

### Post by westie457 on 2012-11-26
@Wild Man and @NikTh

Thanks for stepping in and helping. Have been away from computer for a few days so could not research and check terminal commands to see if they worked. Using this Forum from a phone is not ideal.

---

### Post by Lim Chee Choon on 2012-11-26
thanks for helping.....still no luck..

---

### Post by NikTh on 2012-11-26
It still asks for the firmware 
[quote="netinfo.txt"]rtl8192ce:rtl92c_init_sw_vars():<0-0> Failed to request firmware![/quote]

Are you sure commands at #15th post executed correctly ? I mean commands to copy the firmware. 

Try this and give the results back here.
```
sudo modprobe -rfv rtl8192ce
sudo modprobe rtl8192ce debug=5
dmesg | grep -ie rtl
``` 

Thanks

---

### Post by Lim Chee Choon on 2012-11-26
lim@lim-netbook:~$ sudo modprobe -rfv rtl8192ce
```

rmmod /lib/modules/3.2.0-34-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
rmmod /lib/modules/3.2.0-34-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
rmmod /lib/modules/3.2.0-34-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
rmmod /lib/modules/3.2.0-34-generic-pae/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-34-generic-pae/kernel/net/wireless/cfg80211.ko
```


lim@lim-netbook:~$ sudo modprobe rtl8192ce debug=5
lim@lim-netbook:~$ dmesg | grep -ie rtl
```

[    2.626087] r8169 0000:02:00.0: eth0: RTL8105e at 0xf8410000, 8c:89:a5:00:fd:fb, XID 00a00000 IRQ 43
[   15.892110] rtl8192ce 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   15.892135] rtl8192ce 0000:01:00.0: setting latency timer to 64
[   15.892293] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: Unknown. Bug?
[   16.417644] rtl8192ce:rtl92c_init_sw_vars():<0-0> Failed to request firmware!
[   16.417657] rtlwifi:rtl_pci_probe():<0-0> Can't init_sw_vars.
[   16.417728] rtl8192ce 0000:01:00.0: PCI INT A disabled
[17281.817984] rtl8192ce 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[17281.818014] rtl8192ce 0000:01:00.0: setting latency timer to 64
[17281.818169] rtl8192ce:_rtl92ce_read_chip_version():<0-0> Chip Version ID: Unknown. Bug?
[17281.832618] rtl8192ce:rtl92c_init_sw_vars():<0-0> Failed to request firmware!
[17281.832627] rtlwifi:rtl_pci_probe():<0-0> Can't init_sw_vars.
[17281.832686] rtl8192ce 0000:01:00.0: PCI INT A disabled
```

---

### Post by wildmanne39 on 2012-11-26
Hi,  would still be interested in seeing the text file information without the> rndis_hostbeing used to kill the wireless.

westie457 feel free to jump back in.
Thanks

---

### Post by Lim Chee Choon on 2012-11-27
still not okay.... i m thinking of reinstalling ubuntu and all the softwares....but how do i keep my wifi working if i want to update?

---

### Post by NikTh on 2012-11-28
Well , if you decide to re-install Ubuntu , do not tick(mark) the box for **3rd party software** installation during Ubuntu's Install. If you tick this box , then the wl driver will be installed to your system. 

If your wireless working OK , with the already included drivers , then do not install the additional driver for wifi (because an icon will appears and inform you for additional drivers). Just not install. 
Stay with the working one. 

Thanks

---

