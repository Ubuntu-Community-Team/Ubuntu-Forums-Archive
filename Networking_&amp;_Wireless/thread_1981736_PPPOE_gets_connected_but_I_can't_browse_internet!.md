---
title: "PPPOE gets connected but I can't browse internet!"
date: 2012-05-17
forum: Networking &amp; Wireless
---

### Post by maqtanim on 2012-05-17
I am using a DSl connection in my desktop. My desktop has two OSs -  Windows 7 and Ubuntu 12.04. After installing Ubuntu 12.04 last month, I  was successfully using internet in my desktop by using the command sudo **pppoeconf**.  Today I received a update notification (via update manager) and I  clicked to update. After a while I couldn't browse the internet anymore  (and the update process didn't complete). I ran sudo **pppoeconf**, it seemed that the connection was established. To check the connection I also ran **plog** and I got the following output:
```
[FONT=monospace]tanim@maqdesktop:~$ plog
May 17 18:02:06 maqdesktop pppd[3481]: Connect: ppp3 <--> eth0
May 17 18:02:06 maqdesktop pppd[3481]: Remote message: Login ok
May 17 18:02:06 maqdesktop pppd[3481]: PAP authentication succeeded
May 17 18:02:06 maqdesktop pppd[3481]: peer from calling number 00:00:00:EE:FF:F4 authorized
May 17 18:02:06 maqdesktop pppd[3481]: not replacing existing default route through ppp0
May 17 18:02:06 maqdesktop pppd[3481]: local  IP address 10.15.29.17
May 17 18:02:06 maqdesktop pppd[3481]: remote IP address 10.15.0.1
May 17 18:02:06 maqdesktop pppd[3481]: primary   DNS address 10.15.0.10
May 17 18:02:06 maqdesktop pppd[3481]: secondary DNS address 10.15.0.11[/FONT]
```Looks like it has been connected, but I can't browse internet with  both firefox and google chrome. But I can connect to internet and browse  internet with Windows 7 in the same PC (actually I am writing this  using Windows 7).
  

Any solution to this?

Other supportive informations (that may help) are given below:

```
tanim@maqdesktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e0:69:95:90:bc:e4  
          inet6 addr: fe80::e269:95ff:fe90:bce4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:438 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17764 (17.7 KB)  TX bytes:40031 (40.0 KB)
          Interrupt:20 Memory:fe400000-fe420000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:10.15.29.17  P-t-P:10.15.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1480  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:86 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:339 (339.0 B)  TX bytes:5647 (5.6 KB)

ppp1      Link encap:Point-to-Point Protocol  
          inet addr:10.15.29.17  P-t-P:10.15.0.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1480  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:147 (147.0 B)  TX bytes:2374 (2.3 KB)
``````
tanim@maqdesktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)


``````
tanim@maqdesktop:~$ lsmod
Module                  Size  Used by
xt_TCPMSS              12619  1 
xt_tcpmss              12453  1 
xt_tcpudp              12531  1 
iptable_mangle         12646  1 
ip_tables              18106  1 iptable_mangle
x_tables               21974  5 xt_TCPMSS,xt_tcpmss,xt_tcpudp,iptable_mangle,ip_tables
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
pppoe                  17513  2 
pppox                  13158  1 pppoe
rfcomm                 38139  12 
bnep                   17830  2 
binfmt_misc            17292  1 
snd_hda_codec_realtek   174055  1 
ppdev                  12849  0 
gspca_ov519            40522  0 
gspca_main             27654  1 gspca_ov519
videodev               86588  1 gspca_main
btusb                  17912  2 
bluetooth             158438  23 rfcomm,bnep,btusb
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
parport_pc             32114  1 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 32325  0 
mac_hid                13077  0 
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
i915                  414603  3 
mei                    36570  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
w83627ehf              29485  0 
hwmon_vid              12723  1 w83627ehf
coretemp               13269  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
e1000e                140005  0  

```

---

### Post by nothingspecial on 2012-05-18
*Thread moved to **Networking & Wireless**.*

---

### Post by satish_j on 2012-05-18
Is the nm-applet showing network as connected?

---

### Post by poolet on 2012-05-18
1st: Can you ping domain names and IP addresses, If yes may your browser  corrupted files.. Try to used different browser or re-install your browser... 

2nd: Did you used any kind of firewall ?? try to configure .conifg or disable it.. (ps -A to see whats running..)

3th: Do you have any other machines connected on your network?? what about authentication of that?? try to set manually ip address of other machine as localhost and try again..

4th: did you try to ping external ip web sites?? . Try to ping [www.yahoo.com]("http://www.yahoo.com") (87.248.112.181, may is different for you),If you cannot ping the domain name, but are successful pinging the IP address, then it may be a DNS issue. To confirm the DNS problem, open your browser and type in( the ip of your country [www.yahoo.com]("http://www.yahoo.com") that you must get from pinging to [www.yahoo.com]("http://www.yahoo.com")), this will not require any DNS resolution and should open up just fine to [www.yahoo.com]("http://www.yahoo.com"). If that works, then you may want to change the DNS server you are using. also if you cannot ping  (yahoo.com ip address) then it's not a DNS resolution issue, but a communication issue....

Final:: Before you complete the above steps, did you try to clear you browser file & flush dns cache??

5) a) flush dns cache::

sudo aptitude install nscd

sudo /etc/init.d/nscd restart or &#8220;sudo bash /etc/&#8230;&#8221; (bash after sudo)

5 b) clear all files and history of your browser

Try again...

If your problem is not fixed.. Download nmap & wireshark

Capture the network at PPPOE and filter your connection at point-to-point with your default router address,
if your using cisco type, you may need to flush your firmware of your router(let me know what version you have - only if your are using cisco/linksys product..)

while your capturing the out-bounded traffic check for forwarding tcp/ip protocols by the filtering on PPPOE....
a good idea post a picture with your capturing or save the file as and share it(changing the addressing is a good idea!!! )...


Good luck!!!

---

