---
title: "Network driver (sky2,gigabyte,marvell) failing after upgrade to new kernel"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by Mekk on 2009-04-30
I've been happily using Ubuntu for a year or so on my machine (Hardy & Intrepid). Suddenly I started to face problems with my network driver. And I am looking for any ideas how to track the problem down, or resolve it. I tried googling, there are plenty of discussions about bugginess of sky2 driver here and there, but no clear conclusion (or at least I failed tofind one).

**The problem**

Whenever I start some big download or upload, my network interface stops to work (invoke-rc.d networking restart  helps). /var/log/messages shows messages like

Apr 30 20:09:45 cauchy kernel: [ 5141.791175] sky2 0000:03:00.0: error interrupt status=0x80000000
Apr 30 20:09:45 cauchy kernel: [ 5141.791182] sky2 eth0: hw error interrupt status 0x8

Also, from time to time commands used get MAC parity errors like:

scp -l 450 big.file remote:tmp/
big.file                                          59%   20MB  56.9KB/s   04:09 ETAReceived disconnect from 10.92.32.6: 2: Corrupted MAC on input.

With kernel 2.6.27-11 system freezes also happened frequently, with 2.6.28-11 I haven't faced one yet (but I am trying it for a few hours so far)

**When it started**

The problem appeared a few days ago, when I rebooted after a long time of continuos work. IIRC some new kernel have been installed in the meantime (and that's the most likely reason), also I enabled some RAID drivers in the kernel.

**Some observations**

I succeeded performing big downloads (upgrade to 9.10) while having X switched off. Maybe there is some conflict/race condition between sky2 and nvidia graphic drivers?

**Machine details**

My hardware:

01:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)

My current kernel (stock Ubuntu):

Linux cauchy 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

Modules being loaded:

nvidia               7233756  26 
binfmt_misc            16776  1 
bnep                   20224  2 
ipt_MASQUERADE         10752  1 
iptable_nat            13700  1 
nf_nat                 25876  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      21388  4 iptable_nat,nf_nat
nf_defrag_ipv4          9984  1 nf_conntrack_ipv4
xt_state               10112  1 
nf_conntrack           72008  5 ipt_MASQUERADE,iptable_nat,nf_nat,nf_conntrack_ipv4,xt_state
ipt_REJECT             11136  2 
xt_tcpudp              11008  4 
iptable_filter         10752  1 
ip_tables              19472  2 iptable_nat,iptable_filter
x_tables               23044  6 ipt_MASQUERADE,iptable_nat,xt_state,ipt_REJECT,xt_tcpudp,ip_tables
bridge                 56340  0 
stp                    10500  1 bridge
kvm_intel              50496  0 
kvm                   152640  1 kvm_intel
video                  25360  0 
output                 11008  1 video
input_polldev          11912  0 
dm_crypt               20996  0 
sbp2                   30476  0 
lp                     17156  0 
snd_hda_intel         435636  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                82948  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  15620  0 
intel_agp              34108  0 
snd                    62628  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
pcspkr                 10496  0 
agpgart                42696  2 nvidia,intel_agp
soundcore              15200  1 snd
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usbhid                 42336  0 
ohci1394               38576  0 
ieee1394               94660  2 sbp2,ohci1394
sky2                   54916  0 
raid10                 30336  0 
raid456               134928  0 
async_xor              11392  1 raid456
async_memcpy           10112  1 raid456
async_tx               15184  3 raid456,async_xor,async_memcpy
xor                    24072  2 raid456,async_xor
raid0                  15360  0 
multipath              15232  0 
linear                 13312  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
raid1                  29952  2 
compcache              12876  1 
lzo_decompress         10880  1 compcache
lzo_compress           10880  1 compcache
tlsf                   14092  1 compcache

---

### Post by Mekk on 2009-05-04
As I failed to find any reasonable solution, I installed another network card in the machine (something handled by tulip driver). So far it seems that all the problems are gone.

PS Some corrections to the post above:
- problems showed off also with X switched off
- machine freezes happened also with 2.6.28-11-generic

---

### Post by hamannp on 2009-05-04
> **Mekk said:**
>  As I failed to find any reasonable solution, I installed another network card in the machine (something handled by tulip driver). So far it seems that all the problems are gone.

I too share the the same fear an loathing for the SKY2 driver with the Marvell Yukon.  I came to the same conclusion -- I need to get an easier NIC.  I'm running a Toshiba laptop with the Intel setup.  Can you please steer me in the right direction for an easier NIC?  I'm trying to do bridged networking for my VMs.

Here's the saga:
[http://www.uluga.ubuntuforums.org/showthread.php?p=7209357#post7209357](http://www.uluga.ubuntuforums.org/showthread.php?p=7209357#post7209357)

Cheers! Paul

---

### Post by foresto on 2011-10-23
I don't know if it works with the 88E8053 chip, but I just finished packaging the latest sk98lin driver (from August 2011) for Ubuntu Natty.  (It works with my 88E8056.)  You can find my announcement post here:

[http://ubuntuforums.org/showthread.php?p=11382042#post11382042](http://ubuntuforums.org/showthread.php?p=11382042#post11382042)

---

