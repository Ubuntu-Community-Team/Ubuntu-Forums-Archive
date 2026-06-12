---
title: "Netgear WNA1100 usb - no go Aidez moi! please"
date: 2012-01-22
forum: Networking &amp; Wireless
---

### Post by Tjewit on 2012-01-22
I have an old (2003) used to run Win2000 from work - loaded Linux - it is 35 years since I dabbled with unix and feel a little lost - cannot get USB NetGear WNA1100 to work at all spent whole w/e so far am determined so .... tried a fix:   [http://ubuntuforums.org/showthread.php?t=1584859&highlight=wna1100](http://ubuntuforums.org/showthread.php?t=1584859&highlight=wna1100) - was unable to "untar" either of the tarred files neededd - decided the approach of piggy backing my solution is going to get me more lost so please help .... as far as I can make out info so far:

                     p { margin-bottom: 0.21cm; }  ubi01@ubi01-desktop:~$ lspci 
 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01) 
 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) 
 00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) 
 00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) 
 00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) 
 00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) 
 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) 
 00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01) 
 00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) 
 00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01) 
 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01) 
 01:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
 

 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 002: ID 0846:9030 NetGear, Inc.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 

 ubi01@ubi01-desktop:~$ ifconfig 
 eth0      Link encap:Ethernet  HWaddr 00:08:74:ef:cf:07   
           inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0 
           inet6 addr: fe80::208:74ff:feef:cf07/64 Scope:Link 
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
           RX packets:6035 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:4168 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:100  
           RX bytes:4991719 (4.9 MB)  TX bytes:617511 (617.5 KB) 
  
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0 
           inet6 addr: ::1/128 Scope:Host 
           UP LOOPBACK RUNNING  MTU:16436  Metric:1 
           RX packets:8 errors:0 dropped:0 overruns:0 frame:0 
           TX packets:8 errors:0 dropped:0 overruns:0 carrier:0 
           collisions:0 txqueuelen:0  
           RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B) 
  
 ubi01@ubi01-desktop:~$ iwconfig 
 lo        no wireless extensions. 
  
 eth0      no wireless extensions. 
  ubi01@ubi01-desktop:~$ iwconfig wlan0 
 wlan0     No such device 
 ubi01@ubi01-desktop:~$ lsmod 
 Module                  Size  Used by 
 binfmt_misc             6587  1  
 snd_intel8x0           25652  2  
 snd_ac97_codec        100646  1 snd_intel8x0 
 ac97_bus                1002  1 snd_ac97_codec 
 snd_pcm_oss            35308  0  
 snd_mixer_oss          13746  1 snd_pcm_oss 
 snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss 
 snd_seq_dummy           1338  0  
 snd_seq_oss            26722  0  
 snd_seq_midi            4557  0  
 snd_rawmidi            19056  1 snd_seq_midi 
 snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi 
 fbcon                  35102  71  
 tileblit                1999  1 fbcon 
 snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event 
 font                    7557  1 fbcon 
 bitblit                 4707  1 fbcon 
 softcursor              1189  1 bitblit 
 vga16fb                11385  1  
 vgastate                8961  1 vga16fb 
 snd_timer              19130  2 snd_pcm,snd_seq 
 snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq 
 i915                  289715  1  
 snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
 drm_kms_helper         29329  1 i915 
 dell_wmi                1793  0  
 ppdev                   5259  0  
 dcdbas                  5422  0  
 drm                   163747  3 i915,drm_kms_helper 
 i2c_algo_bit            5028  1 i915 
 intel_agp              24375  2 i915 
 soundcore               6620  1 snd 
 parport_pc             25962  1  
 psmouse                63677  0  
 serio_raw               3978  0  
 video                  17375  1 i915 
 snd_page_alloc          7076  2 snd_intel8x0,snd_pcm 
 shpchp                 28835  0  
 agpgart                31724  3 drm,intel_agp 
 output                  1871  1 video 
 lp                      7028  0  
 parport                32635  3 ppdev,parport_pc,lp 
 e1000                  97435  0  
 floppy                 53016  0  
 

 

 ubi01@ubi01-desktop:~$ iwlist scan 
 lo        Interface doesn't support scanning. 
  
 eth0      Interface doesn't support scanning. 
  
 ubi01@ubi01-desktop:~$ uname -mr 
 2.6.32-37-generic i686 
 ubi01@ubi01-desktop:~$ sudo /etc/init.d/networking restart 
  * Reconfiguring network interfaces...                                                                                                [ OK ]  
 
I hope this info is OK to start with - sorry if I have missed or misunderstood the fix I hope the solution is something simple - Being sunday night and having my living room carved up to connect this machine to a wired connection I know I am in for a few interesting messy days please help !.....

---

### Post by chili555 on 2012-01-22
Is there any chance you'd install the latest Ubuntu version 11.10? Your device works out of the box.

If not, let's look at what's on the CD. What is the name of the file you tried to untar? You can drag and drop it to your desktop and right-click it and select *Extract Here.* What's in there?

---

### Post by Tjewit on 2012-01-23
p { margin-bottom: 0.21cm; }a:link {  }  Thank you Chili555 Infact I installed ubuntu 10.4. The tar files I obtained from a solution suggested here [http://ubuntuforums.org/showthread.php?t=1584859&highlight=wna1100](http://ubuntuforums.org/showthread.php?t=1584859&highlight=wna1100)  I got half way through the fix and then got lost as though I thought I moved the file suggested to the right folder I couldn't untar it . The file was “compat-wireless” I think it was from here: [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=snapshot;h=HEAD;sf=tgz](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=snapshot;h=HEAD;sf=tgz) .
 

 My computer has now crashed 3 times – once replying to this ! - I think on reflection I should go and try dowload the latest version of ubuntu and start from there .  - Thanks again Chili555 – I shall get busy with the above but keep half an eye on this thread in case simpler solutions present. It is always better to do this after a nights sleep.

---

### Post by Tjewit on 2012-01-23
Many thanks downloaded latest ubhuntu and as you said automatically connected - SOLVED - many thanks Chile555:)

---

### Post by chili555 on 2012-01-23
> **Tjewit said:**
> Many thanks downloaded latest ubhuntu and as you said automatically connected - SOLVED - many thanks Chile555:)Glad it's working! Awesome.

---

