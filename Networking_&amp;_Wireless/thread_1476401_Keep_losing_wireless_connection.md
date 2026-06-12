---
title: "Keep losing wireless connection"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by cberry78 on 2010-05-07
OK, after searching through the forums and reading what I could about other errors my wireless card has caused, I haven't been able to find one that quite fits. So below are the guidelines for getting wireless help as laid out in this thread: [http://ubuntuforums.org/showthread.php?p=6183681]("http://ubuntuforums.org/showthread.php?p=6183681").

Here's my issue.  When I boot up my laptop my wireless connects automatically to my router ("linksys"), everything seems fine and dandy for anywhere from 2-3 min to 20+ minutes, then I start losing internet connection and it will automatically reconnect for about 30 seconds and then repeat the same process until eventually my laptop shuts itself down.  If I boot my Vista side the wireless works without a hitch.

Currently using default network manager after trying wicd and switching back, I have noticed a huge improvement in reliability (almost 30 minutes without losing signal).  Any thoughts or more info needed?

Thank you all in advance!!!

```
1- Acer Aspire 5610 running Lucid Lynx w/ Vista dualboot

2- lspci
	05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

3- iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:04:FE:31   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4- lsmod
Module                  Size  Used by
aes_i586                7268  2 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
ipt_REJECT              1928  1 
ipt_LOG                 4542  5 
xt_limit                1382  7 
xt_tcpudp               2011  7 
ipt_addrtype            1631  4 
xt_state                1098  7 
ip6table_filter         2343  1 
ip6_tables             11227  1 ip6table_filter
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_hda_codec_realtek   203168  1 
snd_hda_intel          21877  2 
nf_nat_irc              1124  0 
vga16fb                11385  0 
nf_conntrack_irc        3332  1 nf_nat_irc
vgastate                8961  1 vga16fb
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
nf_nat_ftp              1836  0 
nf_nat                 15735  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      10672  9 nf_nat
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
pcmcia                 33024  0 
snd_hwdep               5412  1 snd_hda_codec
nf_conntrack_ftp        5381  1 nf_nat_ftp
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
nf_conntrack           61583  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
i915                  282354  3 
yenta_socket           20408  1 
drm_kms_helper         29297  1 i915
iptable_filter          2271  1 
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
rsrc_nonstatic         10015  1 yenta_socket
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
ip_tables               9991  1 iptable_filter
arc4                    1153  2 
x_tables               14299  8 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6_tables,ip_tables
snd_rawmidi            19056  1 snd_seq_midi
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
sdhci_pci               5470  0 
lp                      7028  0 
intel_agp              24177  2 i915
iwl3945                68727  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
video                  17375  1 i915
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  1871  1 video
sdhci                  15462  1 sdhci_pci
agpgart                31724  2 drm,intel_agp
joydev                  8708  0 
soundcore               6620  1 snd
acer_wmi               13861  0 
parport                32635  2 ppdev,lp
iwlcore               105922  1 iwl3945
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
mac80211              204922  2 iwl3945,iwlcore
cfg80211              126485  3 iwl3945,iwlcore,mac80211
led_class               2864  4 iwl3945,sdhci,acer_wmi,iwlcore
psmouse                63245  0 
serio_raw               3978  0 
b44                    25542  0 
ssb                    37336  1 b44
mii                     4381  1 b44

6- lshw
*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:37:9e:e9
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:28 memory:d0100000-d0100fff

7- iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:10:04:FE:31
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000204791c47
                    Extra: Last beacon: 8536ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018010200
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

8- lsb_release -d
Description:	Ubuntu 10.04 LTS

9- uname -mr
2.6.32-22-generic i686

10- sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
```

---

### Post by cberry78 on 2010-05-09
Bump...

I know it's a lot of information, but I really don't know what to do at this point.

Thanks again in advance.

---

### Post by bjornsol on 2010-06-13
I have the same problem, after having upgraded from 9.04 and 9.10.  The wireless worked just fine under 9.10, but now on 10.04 it is jittery to say the least.  This seems to be a known problem, but I have yet to find anyone suggesting a solution or when a fix may be available.  Help?

```

1- HP EliteBook 8530p w/ Windows XP dual-boot

2- lspci
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5300

3- iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"mynet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:5A:B8:42:BE   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

4- lsmod
Module                  Size  Used by
nfs                   310131  6 
lockd                  75015  1 nfs
nfs_acl                 2709  1 nfs
auth_rpcgss            44452  1 nfs
sunrpc                227939  21 nfs,lockd,nfs_acl,auth_rpcgss
cryptd                  8116  0 
aes_x86_64              7912  1 
aes_generic            27607  1 aes_x86_64
binfmt_misc             7960  1 
rfcomm                 40329  4 
sco                     9617  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11820  2 
l2cap                  34774  16 rfcomm,bnep
snd_hda_codec_atihdmi     3023  1 
snd_hda_codec_analog    78702  1 
snd_hda_intel          25645  2 
snd_hda_codec          85727  3 snd_hda_codec_atihdmi,snd_hda_codec_analog,snd_hda_intel
pata_pcmcia            10856  1 
arc4                    1473  2 
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_hwdep               6924  1 snd_hda_codec
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
iwlagn                121577  0 
snd_seq_midi            5829  0 
iwlcore               124955  1 iwlagn
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
fbcon                  39270  71 
pcmcia                 35548  1 pata_pcmcia
tileblit                2487  1 fbcon
snd_timer              23553  2 snd_pcm,snd_seq
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62403  0 
softcursor              1565  1 bitblit
fglrx                2353422  0 
hp_accel               12168  0 
snd                    70978  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_hwdep,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
yenta_socket           22901  3 
mac80211              238128  2 iwlagn,iwlcore
sdhci_pci               6700  0 
rsrc_nonstatic          9830  1 yenta_socket
btusb                  12969  2 
lis3lv02d               7583  1 hp_accel
sdhci                  17928  1 sdhci_pci
ricoh_mmc               3416  0 
tpm_infineon            9217  0 
soundcore               8052  1 snd
videodev               40486  1 uvcvideo
psmouse                64608  0 
video                  20623  0 
pcmcia_core            38144  3 pcmcia,yenta_socket,rsrc_nonstatic
intel_agp              29225  0 
tpm                    15780  1 tpm_infineon
qcserial                4068  0 
vga16fb                12757  1 
ppdev                   6375  0 
lp                      9336  0 
tpm_bios                6402  1 tpm
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
v4l1_compat            15495  2 uvcvideo,videodev
vgastate                9857  1 vga16fb
usbserial              39067  1 qcserial
cfg80211              148386  3 iwlagn,iwlcore,mac80211
output                  2503  1 video
v4l2_compat_ioctl32    12020  1 videodev
serio_raw               4918  0 
bluetooth              58621  9 rfcomm,sco,bnep,l2cap,btusb
input_polldev           3106  1 lis3lv02d
led_class               3732  3 iwlcore,hp_accel,sdhci
joydev                 11072  0 
parport_pc             29958  1 
parport                37160  3 ppdev,lp,parport_pc
usbhid                 40988  0 
hid                    83376  1 usbhid
ohci1394               30260  0 
ieee1394               94675  1 ohci1394
ahci                   37646  1 
e1000e                136205  0 

6- lshw
           *-network
                description: Wireless interface
                product: Wireless WiFi Link 5300
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 00
                serial: 00:21:6a:11:ae:90
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlagn ip=192.168.0.195 latency=0 multicast=yes wireless=IEEE 802.11abgn
                resources: irq:31 memory:d8100000-d8101fff


7- iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:26:5A:B8:42:BE
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"mynet"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000a057d3b0ef
                    Extra: Last beacon: 31670ms ago
                    IE: Unknown: 000B736F6C626572676E657474
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                   IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160600190000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336C101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340600010000000F000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010000000000000000000000000000000001021000E442D4C696E6B2053797374656D73102300074449522D363535102400024134104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F75746572100800020084

8- lsb_release -d
Description: Ubuntu 10.04 LTS

9- uname -mr
2.6.32-22-generic x86_64

10- sudo /etc/init.d/networking restart
* Reconfiguring network interfaces... 

```
Thanks,

Bjorn.

---

### Post by cberry78 on 2010-06-13
Please, any help would be appreciated.  I understand that this is at least a semi-known issue, but I have yet to see any truly helpful responses.  I've been forced back to my Vista Ultimate OS because 10.4 just keeps crashing once the wifi starts flickering (that's my only hint something's wrong).

Thanks again in advance.

---

### Post by Asahi on 2010-06-13
Same problem here.

I've read some of thread in the other bbs.
And I think the very reason of our problem is [COLOR=Red]**"Intel 3945ABG wireless card"**[/COLOR]. I used "wicd" Network manager via "Synaptic Package Manager" and it works for a couple week before, but not for now.
[COLOR=Gray]Ps. This wireless card worked fine back when I've using *indows7.[/COLOR]

Now I spending my time on Internet try to find the way out of this in trail and error.
And need to re-install Ubuntu 10.04 for 2 times already, because I'm new in Linux and don't have a clue what to fix if I mess up something.
[COLOR=Gray]Ps. Yes, I've 2 [/COLOR][COLOR=Gray]Ubuntu's[/COLOR][COLOR=Gray] manual books. But they're useless in this case.[/COLOR]

So, please, we need help.

Sincerely,

Mike. K.

---

### Post by suryaccnamcse on 2010-06-13
what is the kernel that you are using. There were few problems regarding intel pro/wireless 3945ABG in the previous kernel, which have been rectified in the new kernel. You would like to update via the update manager.

---

### Post by Asahi on 2010-06-14
> **suryaccnamcse said:**
> what is the kernel that you are using. There were few problems regarding intel pro/wireless 3945ABG in the previous kernel, which have been rectified in the new kernel. You would like to update via the update manager.
I'm afraid I didn't follow you. (I really new in Linux and Ubuntu)

If you mean, "what software source I update from update manager?" the answer is Thailand.
If you mean, "how do I update to Ubuntu 10.04?" the answer is I've installed completely new version at 10.04 not update from 9.xx.

Thanks in advance.

[COLOR=Red]** EDIT:**[/COLOR] I just got this url. shall we try? [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

---

### Post by cberry78 on 2010-06-14
> **suryaccnamcse said:**
> what is the kernel that you are using. There were few problems regarding intel pro/wireless 3945ABG in the previous kernel, which have been rectified in the new kernel. You would like to update via the update manager.

2.6.32-22-generic i686

Can't answer for anyone else, but that's my kernel, and according to Update Manager it's the most current available.  Thanks.

---

### Post by bjornsol on 2010-06-14
Personally I'd sooner downgrade to Ubuntu 9.10 than going Vista, but that's me. ;)  Hopefully we'll have a solution to this sooner than later, since this problem clearly lies with the 10.04 version.

Bjorn.

---

### Post by cberry78 on 2010-06-14
Unfortunately, 9.10 isn't an option for me, the wireless wouldn't work for then either, even with wicd.  Hopefully I won't be forced to live in the land of Vista forever.

---

### Post by b k on 2010-06-15
Hi there, would like to make a suggestion.

Not sure if it will help though.

If you have access to your router and if your current setting for  wireless network is with TKIP encryption, try perhaps WPA2-PSK  authentication with AES encryption.
 
In other words any combination [COLOR=red]without TKIP[/COLOR]  encryption.
 
Hope the suggestion works for you

---

### Post by okos on 2010-06-15
I also have the same problem vista work good I keep loosing connection with ubuntu 10.04.

The problem is not with tkip encryption. 
Have you had any problems with other distros?

---

### Post by cberry78 on 2010-06-15
Yeah I've tried changing the encryption, even none, on my wireless router, switched it out for a different brand, isolated the signal to just wireless-G (even tried wireless-B), and still get the same results.  I remember seeing someone mention in a post at sometime in the past that the issue was the fan not turning on to offset the rising heat change of the processor running (or some sort) and offered some sort of fix, but I can't remember what it was and have been unable to find the post.  Seem familiar to anyone?

As always, thanks again in advance!

---

### Post by bjornsol on 2010-06-26
I finally switched my router from WPA2 TKIP/AES combo to AES only, and my wireless in Ubuntu 10.04 has been stable since.  But there is obviously something bad about 10.04 given that this worked fine with all previous releases.  There are other things I have noticed too related to graphics (missing the "self" image when video conferencing with Skype) but that is for another thread.

Thanks,

Bjorn.

---

### Post by cavanholi on 2010-09-11
Well, since I installed (removing the old 8.04 completely) the Ubuntu 10.04, I'm this freak problem with losing the wireless connection.

The thing is, this only happen with my own internet, the neighbour's internet worked fine (until he change his weak password).

At windows vista I have no problem at all (which is a surprise).

At no time I have any message about losing connection, it shows as if it was all ok, but that is just no response.
If I reconnect, work only to load the first page and stopped latter.

Strangely, if I keep any program who make constant request of information, like online radio, the problem doesn't happen, but if I stopped it for even a few minutes, bye bye wirelles.

My ubuntu is fully updated, and I have no idea what to do about.

---

