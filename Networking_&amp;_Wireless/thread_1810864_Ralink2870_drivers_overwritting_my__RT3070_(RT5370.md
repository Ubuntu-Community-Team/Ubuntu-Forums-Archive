---
title: "Ralink2870 drivers overwritting my  RT3070 (RT5370?) drivers"
date: 2011-07-23
forum: Networking &amp; Wireless
---

### Post by pedal2metal on 2011-07-23
Hi there!

I am fairly new to Linux and already loving it. I find it challenging, powerful and fun. I have been an avid reader of the forums as well, since this has been my main source of information and help. Most of the times just by reading older posts I was able to figure it out, but I have hit a wall today and need a little help. My issue is as follows: I used to have an RT2870 USB device. Recently I acquired an RT3070. However after successfully compiling and installing the driver, my device keeps connecting at 54mbps. My router is detecting my USB as b/g and not b/g/n . I am willing to provide any outputs. For now let me post a couple:

lsmod

```
~/Downloads/ralink4/os/linux$ lsmod
Module                  Size  Used by
snd_hrtimer            12680  1 
binfmt_misc            13213  1 
nfsd                  252397  13 
exportfs               12870  1 nfsd
nfs                   282952  0 
lockd                  74292  2 nfsd,nfs
fscache                50364  1 nfs
nfs_acl                12771  2 nfsd,nfs
auth_rpcgss            39173  2 nfsd,nfs
sunrpc                199096  13 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
i915                  450934  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
hisax                 505571  0 
snd_seq                51291  3 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
isdn                  133735  1 hisax
snd_timer              28659  3 snd_hrtimer,snd_pcm,snd_seq
ppdev                  12849  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
netjet                 17548  0 
isdnhdlc               13091  1 netjet
mISDNipac              26213  1 netjet
ipt_REJECT             12512  1 
ipt_LOG                12784  4 
xt_limit               12541  6 
xt_tcpudp              12531  14 
ipt_addrtype           12535  4 
usbhid                 41704  0 
xt_state               12514  9 
rt2870sta             410104  1 
snd                    55295  12 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ip6table_filter        12711  1 
ip6_tables             22545  1 ip6table_filter
nf_nat_irc             12542  0 
nf_conntrack_irc       13138  1 nf_nat_irc
nf_nat_ftp             12548  0 
nf_nat                 24827  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19024  11 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
mISDN_core             81562  2 netjet,mISDNipac
nf_conntrack_ftp       13106  1 nf_nat_ftp
nf_conntrack           69744  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18125  1 iptable_filter
x_tables               21907  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
drm                   180037  2 i915,drm_kms_helper
hid                    77084  1 usbhid
parport_pc             32111  1 
soundcore              12600  1 snd
crc_ccitt              12595  3 hisax,isdnhdlc,rt2870sta
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
shpchp                 32345  0 
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usb_storage            43946  1 
e100                   40108  0 
uas                    17676  0 
floppy                 60032  0 
 
```lsusb

```
~/Downloads/ralink4/os/linux$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter
Bus 001 Device 002: ID 059f:100c LaCie, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
iwconfig

```
~/Downloads/ralink4/os/linux$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"jj.Air.Net"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1F:F3:F6:09:37   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-61 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by chili555 on 2011-07-23
> ID 148f:3072 Ralink Technology, Corp. RT3072 Wireless Adapter```
chili@LAPTOP60:~$ modinfo rt2870sta | grep 3072
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]3072[/COLOR]d*dc*dsc*dp*ic*isc*ip*
chili@LAPTOP60:~$ modinfo rt5370sta | grep 3072
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]148F[/COLOR]p[COLOR="Red"]3072[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```Did you get rt5370sta compiled successfully? You might try unloading rt2870sta and load rt5370sta and see if it improves:```
sudo ifconfig wlan0 down
sudo rmmod -f rt2870sta
sudo modprobe rt5370sta
sudo ifconfig wlan0 up
```If it helps, we can blacklist rt2870sta and automatically load rt5370sta.

---

### Post by pedal2metal on 2011-07-25
Thank you very much for your help Chili!

I've tried that, but:

```
juan@juan-desktop:~/Downloads$ sudo ifconfig wlan0 down
[sudo] password for juansanabria: 
juan@juan-desktop:~/Downloads$ 
juan@juan-desktop:~/Downloads$ sudo rmmod -f rt2870sta
juan@juan-desktop:~/Downloads$ sudo modprobe rt5370sta
juan@juan-desktop:~/Downloads$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
```

The outputs:

```
juan@juan-desktop:~/Downloads$ modinfo rt2870sta | grep 3072
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*
juan@juan-desktop:~/Downloads$ modinfo rt5370sta | grep 3072
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*

```

The file I downloaded from Ralink is:
2011_0407_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.2_DPO.bz2

At first I had a compilation error, but I managed to work it around by editing the file: /os/linux/usb_main_dev.c. During compilation I do get a bunch of warnings, mostly about unused variables.  I also tried blacklisting rt2870sta, but this causes wlan0 disappear and instead I get ra0 with very little info shown by iwconfig.  
By the way, my only current blacklist is: rt2800usb.

---

### Post by chili555 on 2011-07-25
Let's see if there are any helpful clues in kernel messages.```
dmesg | grep -e rt2 -e rt5
iwconfig
lsmod | grep -e rt2 -e rt5
```Thanks.

---

### Post by pedal2metal on 2011-07-25
I really appreciate your help, I've gathered the outputs already:

```

juan@juan-desktop:~/Downloads/rt3070/os/linux$ dmesg | grep -e rt2 -e rt5
[   11.885966] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   13.955641] usbcore: registered new interface driver rt2870
[   14.555581] rtusb init rt2870 --->
[   14.555598] Error: Driver 'rt2870' is already registered, aborting...
[   18.703063] <==== rt28xx_init, Status=0
[   19.804906] <==== rt28xx_init, Status=0
[   76.650182] <==== rt28xx_init, Status=0
juan@juan-desktop:~/Downloads/rt3070/os/linux$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"jj.Air.Net"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:1F:F3:F6:09:37   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-51 dBm  Noise level:-63 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

juan@juan-desktop:~/Downloads/rt3070/os/linux$ lsmod | grep -e rt2 -e rt5
rt2870sta             410104  1 
crc_ccitt              12595  3 hisax,isdnhdlc,rt2870sta
juan@juan-desktop:~/Downloads/rt3070/os/linux$ 

``` 

Thanks a lot!

JJ.

---

### Post by chili555 on 2011-07-26
It looks like rt5370sta is trying to load but gets kicked out. Let's blacklist rt2870sta and load rt5370sta and see if things improve. Please do:```
sudo su
echo "blacklist rt2870sta" >> /etc/modprobe.d/blacklist.conf
echo rt5370sta >> /etc/modules
exit
```Reboot. Check to see what's loaded and what's not:```
lsmod | grep -e rt2 -e rt5
```Does it connect at N speeds?

---

### Post by pedal2metal on 2011-07-27
Thanks Chili!

Unfortunately that did not work, It took the blacklist and loaded the module without any errors, but after rebooting this is what happened:


```

juan@juan-desktop:~$ lsmod | grep -e rt2 -e rt5
rt5370sta             675238  0 
juan@juan-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

juan@juan-desktop:~$ 

```

And on the GUI no networks are detected, as if no firmware was installed (except it does not display the no-firmware message).

---

### Post by pedal2metal on 2011-07-27
oh also, just in case,

```

juan@juan-desktop:~$ dmesg | grep -e rt2 -e rt5
[   10.265549] rtusb init rt2870 --->
[   10.291818] usbcore: registered new interface driver rt2870
juan@juan-desktop:~$ modinfo rt2870sta | grep 3070
description:    RT2870/RT3070 Wireless Lan Linux Driver
firmware:       rt3070.bin
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*
juan@juan-desktop:~$ 

```

---

### Post by chili555 on 2011-07-27
Please run:```
cd ~
sudo modprobe rt5370sta > pedal.txt
iwconfig >> pedal.txt
lsmod >> pedal.txt
dmesg >> pedal.txt
zip pedal.zip pedal.txt
```In your user directory, you will find a file called pedal.zip. Attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by pedal2metal on 2011-07-27
there you go Chili,

cheers,

---

### Post by chili555 on 2011-07-28
I've compiled rt5370sta three times today; in every case, it compiles without error but dozens of warnings. I see this in your logs:> [   10.265549] rtusb init rt2870 --->
[   10.266650] 
[   10.266653] 
[   10.266655] === pAd = e070c000, size = 518512 ===
[   10.266659] 
[   10.268363] <-- RTMPAllocTxRxRingMemory, Status=0
[   10.268496] <-- RTMPAllocAdapterBlock, Status=0I have googled the last line extensively and it's always in the same post with "not working" so I'm not surprised yours is not working.

Ralink builds these for a one-size-fits-all Ubuntu, Fedora, Suse and kernels from 2.6.32 to 2.6.38, and maybe more. I think I would be shocked if it worked *perfectly* on any system. 

I'm not sure there is an N choice here; you seem to have rt2870sta = G or rt5370sta = ng. 

I have been studying this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987)> It is a misconception that rt2800usb is the wrong module. It is the right module. It is just not the only module on your system that says that it can drive hardware with this ID (which consists of vendor plus device id).The strong suggestion is that rt2800usb, ***with the right firmware***, is the preferred driver for this family of devices.

Would you care to pursue this avenue?

---

### Post by pedal2metal on 2011-07-28
Thanks a lot for taking the time to help me out.

I did get a bunch of warnings while compiling as well, "unused variable" said most of them.

Which driver I use is not important to me, as long as I can get N speed. And of course, at some point I will give up and just use G mode. But I'm not giving up yet.


I will pursue that avenue, for the sake of curiosity!


I will post my findings here.

Again, thank you very much. The bug report link is great BTW.

Cheers mate!!!!

---

### Post by pedal2metal on 2011-07-29
Issue has been FIXED. 

> ***with the right firmware***That got stuck in my head. 

Then I remembered the single reason I went to the Ralink site was because the drivers that came in the box would fail to compile. The folder that came along with the device is called: RT3070_LinuxSTA_V2.3.0.1_20100208. 

Then I encountered two compilation obstacles. First got a license error which was fixed by editing *os/linux/usb_main_dev.c*, adding one line “**MODULE_LICENSE(“GPL”)**;”

Then I got another error, it was related to the **usb_buffer_alloc** and **usb_buffer_free** functions. On this one I read that Chili suggested editing *include/os/linux_rt.h* and replacing those two (ONLY!) for: **usb_alloc_coherent** and to **usb_free_coherent** (respectively).

Then while installing I got another error. It was because RT3070STA.dat was missing. So, I had read you just have to do: 
```
cp RT2870STA.dat RT3070STA.dat. 
```
Then I took a last step, which might be unnecessary, I added the following symlink (had to deleted an old RT2870STA.dat though):

```
ln -s /etc/Wireless/RT3070STA/RT3070STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
```Of course I blacklisted rt2870sta before rebooting. 

After reboot the router negotiated N speed.

Chili, thanks for your time and great advice. I've learned quite a bit on this challenge.

CHEERS!

P2M:)

---

### Post by amuldoon on 2011-12-03
Hi All,
I'm sorry to hijack this thread but I'm fairly new to Ubuntu so my understanding a little thin.
From your conversations I gather you have the usb Ralink RT5370 drivers installed and working, if this is the case I would really appreciate instructions on how you managed this, I am really struggling.
I've tried following instructions from other posts but it seems most people have given up, something I'd rather not do so any help would be much appreciated.

Thank you.

---

