---
title: "Realtek Wireless not working with 10.10 netbook on Toshiba Satellite L635Hey all, Ins"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by straylight01 on 2011-03-08
Hey all, Installed 10.10 netbook on my room mates laptop, as a favor. It's been a very problematic install, But I have since gotten everything working EXCEPT for the wireless. Per the sticky on the posting guidelines, I have attached the terminal output and system specs below.  
 

 What I have tried so far has been to download the Realtek wireless driver, listed as
RTL8191SE-VA2
 

 I attempted to compile it from the source code as per the walkthru on how to compile from source and received the following output from the terminal:


 Selecting previously deselected package rtl8192se-linux-2.6.0019.1207.2010.
(Reading database ... 135775 files and directories currently installed.)
Unpacking rtl8192se-linux-2.6.0019.1207.2010 (from .../rtl8192se-linux-2.6.0019.1207.2010_20110307-1_i386.deb) ...
dpkg: error processing /usr/local/src/rtl8192se_linux_2.6.0019.1207.2010/rtl8192se-linux-2.6.0019.1207.2010_20110307-1_i386.deb (--install):
unable to create `/etc/realtek/wireless-rtl-ac-dc-power.sh.dpkg-new' (while processing `./etc/realtek/wireless-rtl-ac-dc-power.sh'): No such file or directory
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/usr/local/src/rtl8192se_linux_2.6.0019.1207.2010/rtl8192se-linux-2.6.0019.1207.2010_20110307-1_i386.deb


 Someone please HELP!  
 

 

 

 Machine Brand and Model  
 Toshiba Satellite L635
 

 Installed
 Ubuntu 10.10 Netbook Edition
 

 Wireless Brand, Model and Wireless Chipset
 

 lspci 
 00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02) 
 00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02) 
 00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06) 
 00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) 
 00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05) 
 00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05) 
 00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05) 
 00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05) 
 00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5) 
 00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05) 
 00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05) 
 00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05) 
 00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05) 
 01:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1) 
 02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01) 
 3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02) 
 3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02) 
 3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02) 
 3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02) 
 3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02) 
 3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02) 
 

 lsusb 
 Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 Bus 001 Device 003: ID 10f1:1a2a   
 Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub 
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 

 ifconfig 
 eth0      Link encap:Ethernet  HWaddr 00:26:6c:94:86:8e   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1 
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
           Interrupt:46  
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 
 

 iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions.
 

 lsmod 
 Module                  Size  Used by 
 binfmt_misc             6599  1  
 parport_pc             26378  0  
 ppdev                   5556  0  
 snd_hda_codec_conexant    30003  1  
 joydev                  8767  0  
 snd_hda_intel          22299  2  
 i915                  296139  5  
 snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel 
 snd_hwdep               5040  1 snd_hda_codec 
 snd_pcm                71603  2 snd_hda_intel,snd_hda_codec 
 drm_kms_helper         30200  1 i915 
 snd_seq_midi            4588  0  
 drm                   168732  5 i915,drm_kms_helper 
 snd_rawmidi            17783  1 snd_seq_midi 
 snd_seq_midi_event      6047  1 snd_seq_midi 
 snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event 
 uvcvideo               55847  0  
 snd_timer              19067  2 snd_pcm,snd_seq 
 snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq 
 videodev               43098  1 uvcvideo 
 v4l1_compat            13359  2 uvcvideo,videodev 
 snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 i2c_algo_bit            5168  1 i915 
 intel_agp              26926  2 i915 
 video                  18712  1 i915 
 psmouse                59033  0  
 serio_raw               4022  0  
 intel_ips              11101  0  
 soundcore                880  1 snd 
 snd_page_alloc          7216  2 snd_hda_intel,snd_pcm 
 output                  1883  1 video 
 agpgart                32075  2 drm,intel_agp 
 lp                      7342  0  
 parport                31492  3 parport_pc,ppdev,lp 
 ahci                   19198  2  
 libahci                21792  1 ahci 
 atl1c                  30173  0  
 

 sudo lshw -C network 
   *-network                
        description: Ethernet interface 
        product: AR8152 v1.1 Fast Ethernet 
        vendor: Atheros Communications 
        physical id: 0 
        bus info: pci@0000:01:00.0 
        logical name: eth0 
        version: c1 
        serial: 00:26:6c:94:86:8e 
        capacity: 100MB/s 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
        configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair 
        resources: irq:46 memory:d5400000-d543ffff ioport:3000(size=128) 
   *-network UNCLAIMED 
        description: Network controller 
        product: Realtek Semiconductor Co., Ltd. 
        vendor: Realtek Semiconductor Co., Ltd. 
        physical id: 0 
        bus info: pci@0000:02:00.0 
        version: 01 
        width: 64 bits 
        clock: 33MHz 
        capabilities: pm msi pciexpress bus_master cap_list 
        configuration: latency=0 
        resources: ioport:2000(size=256) memory:d4400000-d4403fff 
 

 iwlist scan 
 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
 

 

 uname -mr 
 2.6.35-27-generic-pae i686 
 

 sudo /ect/init.d/networking restart 
 sudo: /ect/init.d/networking: command not found

---

### Post by straylight01 on 2011-03-09
Anyone?

---

### Post by lonewolf88 on 2011-03-09
> **straylight01 said:**
> Anyone?

What kernel are you using?

---

### Post by straylight01 on 2011-03-09
A good one, if it wins...

---

### Post by lonewolf88 on 2011-03-10
> **straylight01 said:**
> A good one, if it wins...

What version number?  Does this make the question clearer?

---

### Post by bigpat7 on 2011-03-17
Hey all, I've got Realtek RTL8191SE wifi working just fine on my Toshiba Satellite A505-S6020 laptop, with Kubuntu 10.10 i386 installed.

I first ran from live CD, went into Network Manager, went thru steps to build a wifi connect to my router, I was totally amazed that I was able to scan and see my router!  So I finished building the WPA2 wifi connect, and sure enough, within a couple minutes I was connected - nothing special, just running from live CD.

So I knew it was time for install, which I did, went thru steps to build the wifi connect once more, and have been online to my router for a couple days now.

Though I've been with openSuse for a variety of years off and on, they just released 11.4 about a week back, and it still didn't have these wifi pieces I needed built into it, or even on DVD.

Over at openSuse forums I was told somebody with Ubuntu got ahold of driver from Realtek, and coded for Linux - who ever that was, I owe them a major THANK YOU!  And I just know there has to be a cute little story associated with this, please point me to it.

Having wifi was only reason I left Windows 7 installed on this laptop.  Sooo, in near future I'll probably do  reinstall and let Kubuntu have entire drive!  I've paid my dues with Windows - did tech support on some garbage real estate software for 12.4 years - it was always a crapshoot which was worse, it or Windows.

This was an awesome fix, and caught me totally offguard!  I've run probably a dozen different flavors of Linux from live CD looking to see if they coded a fix for my wifi, I've seen this nowhere else!

Back with openSuse 11.3 I was getting pointed to a development kernel - well, I've been thru upgrade cycles with development kernels before, and was lacking the huevos to subject myself to that again.

But I've become MAJOR Ubuntu/Kubuntu fan once again!

---

### Post by chili555 on 2011-03-17
> Realtek Semiconductor Co., Ltd. Device 8176 (rev 01) I don't believe r8192[COLOR="Red"]s[/COLOR]e_pci is correct for your device. Please run:```
lspci -nn
```If your pci.id is 10ec:8176 then r8192[COLOR="Red"]c[/COLOR]e_dkms is correct. Please see post #5:  [http://ubuntuforums.org/showthread.php?t=1608908](http://ubuntuforums.org/showthread.php?t=1608908)

If your pci.id is different, post it here and we'll help.> A good one, if it wins... ...not helpful.

---

### Post by straylight01 on 2011-03-21
Sorry. Total newbie. I'm trying to code 1spci -nn. Am I correct in understanding that I just type "1spci -nn" into the command line?

---

### Post by straylight01 on 2011-03-21
Ah, right the search feature. I'm on it. Thanks all.

---

### Post by straylight01 on 2011-03-21
Ok, downloaded              r8192[COLOR=Red]c[/COLOR]e_dkms
Got to  the desktop from the command line where I placed the file
ran 'Make' from the terminal

some really interesting stuff happened.
Rebooted. 
No wireless. 

What now?

---

### Post by chili555 on 2011-03-26
> **straylight01 said:**
> Sorry. Total newbie. I'm trying to code 1spci -nn. Am I correct in understanding that I just type "1spci -nn" into the command line?You type lspci -nn in the terminal and press Enter. Post the data related to your wireless card or all of it if you're in doubt.

It looks like you have a one in your version: 1spci -nn. It's not a one; it's an L: lspci -nn.

Please post the result.

---

