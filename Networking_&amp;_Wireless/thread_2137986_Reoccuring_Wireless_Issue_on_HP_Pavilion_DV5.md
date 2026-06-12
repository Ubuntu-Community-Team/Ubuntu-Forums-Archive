---
title: "Reoccuring Wireless Issue on HP Pavilion DV5"
date: 2013-04-22
forum: Networking &amp; Wireless
---

### Post by kevinlinux on 2013-04-22
Hello Every One, I am very new to Ubuntu. I have just installed Ubuntu 12.10 wiping off existing windows completly. I am hving wireless issues even since i installed ubuntu. I was able to get to work for a little while but i am having the same issue after i rebooted the machine.

Appreciate your help here.

---

### Post by marvselby on 2013-04-22
Okay, there are a few things we need to know.  First, was this a reboot necessitated by a kernel upgrade?  If that's the case, try booting the previous kernel from the GRUB screen.  Second, is the wireless adapter a USB dongle or a pci card?  Open a terminal and type "lsusb" (no quotes) for a USB adapter or "lspci" for a pci card.  Please post the output.  That will tell us what the adapter is.  Third, type "lsmod" which will tell us what kernel modules are loaded.  (Think of modules as drivers.)

---

### Post by kevinlinux on 2013-04-22
was this a reboot necessitated by a kernel upgrade?  If that's the case, try booting the previous kernel from the GRUB screen

I am not sure.

I dont think i am using any USB wireless adapter. Hence posting the output for "lspci"
> 
$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


output "lsmod"
> 
$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     31457  1 
snd_hda_codec_idt      59762  1 
bnep                   17708  2 
rfcomm                 37277  0 
bluetooth             183270  10 bnep,rfcomm
parport_pc             31969  0 
ppdev                  12818  0 
snd_hda_intel          32516  3 
snd_hda_codec         111548  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
arc4                   12474  2 
snd_hwdep              13273  1 snd_hda_codec
snd_pcm                80235  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ath9k                 116558  0 
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
mac80211              461261  1 ath9k
snd_timer              24412  2 snd_pcm,snd_seq
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common           13784  1 ath9k
ath9k_hw              376270  2 ath9k,ath9k_common
coretemp               13169  0 
ath                    19188  3 ath9k,ath9k_common,ath9k_hw
uvcvideo               71278  0 
lpc_ich                16926  0 
videobuf2_core         32071  1 uvcvideo
i915                  457241  8 
videodev               95842  2 uvcvideo,videobuf2_core
snd                    62146  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         47304  1 i915
videobuf2_vmalloc      12757  1 uvcvideo
videobuf2_memops       13213  1 videobuf2_vmalloc
cfg80211              175574  3 ath9k,mac80211,ath
psmouse                84878  0 
kvm                   357807  0 
drm                   238811  4 i915,drm_kms_helper
hp_accel               25729  0 
lp                     13300  0 
lis3lv02d              19230  1 hp_accel
qcserial               12663  0 
usb_wwan               19467  1 qcserial
hp_wmi                 13617  0 
sparse_keymap          13659  1 hp_wmi
joydev                 17162  0 
mac_hid                13038  0 
i2c_algo_bit           13198  1 i915
usbserial              36684  2 qcserial,usb_wwan
intel_ips              17884  0 
wmi                    18591  1 hp_wmi
parport                40754  3 parport_pc,ppdev,lp
video                  18895  1 i915
microcode              18210  0 
soundcore              14600  1 snd
snd_page_alloc         14037  2 snd_hda_intel,snd_pcm
mei                    35797  0 
serio_raw              13032  0 
input_polldev          13649  1 lis3lv02d
hid_generic            12485  0 
usbhid                 41734  0 
hid                    82179  2 hid_generic,usbhid
ahci                   25497  2 
libahci                25938  1 ahci
r8169                  55977  0 


---

### Post by ahallubuntu on 2013-04-22
~

---

### Post by kevinlinux on 2013-04-22
Thanks for your reply.

It does help and wireless seem to be working. However i also have an issue with slowness of the internet (more on wireless and little less on wired) it used to work amazing on my windows. I have another laptop and other devices they all work with great speed. Any suggestions .....

---

### Post by marvselby on 2013-04-22
Do you have any idea of the signal strength on wireless?  If you're using Network Manager, hovering over the bar graph on the taskbar will show the percentage.  Running "iwconfig" from the terminal will show it as "link quality =" something like 98/100.  That's 98%.

You might also try running a speed test on both wired and wireless.  There's one at speedtest.net.  If you're running both wired and wireless connecting to the same router, I  have to wonder if somehow that's affecting the speed.

---

### Post by kevinlinux on 2013-04-22
Sure, here you go....

> 
$ iwconfig
wlan0     IEEE 802.11bgn  ESSID:"HOME- 0607"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:D6:4D:59:80   
          Bit Rate=58.5 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:9   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.






cant get rid of the smilyes :-)

---

### Post by marvselby on 2013-04-22
Okay.  Link quality is 70/70.  That's good.  Any luck with the speed test?  What makes you think it's slower?  The rate at which web pages load?

---

### Post by kevinlinux on 2013-04-22
I am unplugging the cable before i connect to wireless

And based on speed test from speedtest.net

Wired

Download Speed :- 27.88 Mbps
Upload Speed :- 5.61 Mbps


Cant even open the website to test , I tried atleast four times. The website does not even open or its says unable to load configuration test or something...

---

### Post by marvselby on 2013-04-22
Your wired speed seems quite good.  Using my wireless, I'm getting 15.30 MBPS download and .97 MBPS upload.  That's weird about not being able to load the configuration test or something.

The numbers we're getting are not really indicative of performance.  In the real world, there are a number of things that affect performance, such as website traffic, DNS lookup, your choice of browsers, and the best one of all - whether the UFO is hovering over your house recharging its batteries from your USB port. :0 (trying to create a smiley - I figured out the combination of colon 0 :0 causes a smiley.)  Oops.  I guess it only happens when on pastes something in.

---

### Post by kevinlinux on 2013-04-23
Sure, i hear you. So, do you suggest trying out another browser like chrome or something or go with Ubuntu 12.04.2 LTS instead ? Hoping its better based on your suggestion.

---

### Post by marvselby on 2013-04-23
I personally like the long-term support versions (currently using 10.04) because of the updates and the number of postings in forums such as this.  I've also found that LTS versions tend to be less buggy.  If I remember correctly, with LTS you can upgrade to another LTS directly without going through the intervening versions.  I'm gonna find out shortly when I upgrade from 10.04 to 12.04.  We'll see how that goes.

Supposedly Chrome is fast but when I tried it I really couldn't see much difference between it and Firefox.  I'd suggest you try some of the browsers to find one you like.

BTW, since your problem appears to be solved, it might be good to mark your post as "solved".

---

### Post by kevinlinux on 2013-04-29
Many Thanks for your thoughts and taking time to help others. I really appreciate it. This is definatly solved and i am all set. Kudo's for all the work you are doing.

---

