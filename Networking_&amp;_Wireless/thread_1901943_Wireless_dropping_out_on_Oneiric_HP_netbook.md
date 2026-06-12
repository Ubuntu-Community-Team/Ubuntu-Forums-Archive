---
title: "Wireless dropping out on Oneiric HP netbook"
date: 2011-12-29
forum: Networking &amp; Wireless
---

### Post by sai-salamander on 2011-12-29
[reposting this from the big wireless issues thread]

Hello! I hope someone can help me with this, because it's being very frustrating.

I bought a new netbook two days ago; a HP Pavilion dm1, and got my dual-boot all set up with Windows 7 on one side and Oneiric on the other. I had a lot of problems with Unity, so I reverted back to using the Classic Desktop - but that's not really the problem.

Ever since the fresh install (I installed and partitioned from a USB, since I have no disc drive), update manager has been popping up with 298 (or thereabouts) updates that need installing. Every attempt leads to a failure, with the message: failed to download package files, check your internet connection.

Now, my wireless indicator is telling me that I have signal, but it keeps dropping out on the internet too; I can access at times after restarting, then after a while it just drops out completely, but the indicator insists that I'm still connected. I am currently wired in but typing this on a different laptop, and it has the same issue with the updates, and now the internet has just dropped out as well.

I've been googling around for solutions, but none of them have worked. I tried changing the proxy settings and the connection settings, checking the updates before attempting an install (as in this thread), and a few things with the drivers on terminal but to no avail.

I'm sort of at a loose end now, so I'd appreciate it if anyone could point me in the right direction?

---

### Post by westie457 on 2011-12-29
Hi, we will get your wireless working first, then we will sort the rest one bit at a time. Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by zielstep on 2011-12-29
Hello,

I do not mean to hijack this thread, but I am having this same problem.  I can use my Compaq nc8430 laptop to access the wireless signal just fine.   But after about 10 minutes or so, sometimes a little longer, the wireless LED starts to blink and I suddenly do not have a signal.  The LED will not stop blinking and even though my signal should be very strong, I do not have internet access.  I always have to reboot to get it back.  This has been occurring within the past month or so, but not before, and I haven't found a solution online yet either.  My response to your questions are as follows (incase this helps):

```
stephen@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux ubuntu 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
stephen@ubuntu:~$ lspci -nnk | grep -iA2 net
08:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express [14e4:16fd] (rev 21)
    Kernel driver in use: tg3
    Kernel modules: tg3
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
stephen@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"NETGEAR03-5G"  
          Mode:Managed  Frequency:5.765 GHz  Access Point: 20:4E:7F:C3:07:FD   
          Bit Rate=6 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

stephen@ubuntu:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
stephen@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_analog    58598  1 
arc4                    1153  2 
snd_hda_intel          22069  5 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  6 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
iwl3945                68727  0 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
iwlcore               106149  1 iwl3945
mac80211              205402  2 iwl3945,iwlcore
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
cfg80211              126144  3 iwl3945,iwlcore,mac80211
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hp_accel               11144  0 
lis3lv02d               6096  1 hp_accel
snd                    54244  21 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
joydev                  8740  0 
tpm_infineon            7745  0 
pcmcia                 30784  0 
tifm_7xx1               3690  0 
ppdev                   5259  0 
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
tifm_core               6045  1 tifm_7xx1
psmouse                63677  0 
serio_raw               3978  0 
parport_pc             25962  1 
sdhci_pci               5470  0 
sdhci                  15494  1 sdhci_pci
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
lp                      7028  0 
tpm_tis                 7488  0 
tpm                    14000  2 tpm_infineon,tpm_tis
tpm_bios                5266  1 tpm
input_polldev           2482  1 lis3lv02d
led_class               2864  4 iwl3945,iwlcore,hp_accel,sdhci
parport                32635  3 ppdev,parport_pc,lp
sha256_generic         11191  4 
aes_i586                7268  531 
aes_generic            26863  1 aes_i586
dm_crypt               11331  2 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
usbhid                 36110  0 
hid                    67288  1 usbhid
radeon                678831  3 
ttm                    49847  1 radeon
drm_kms_helper         29329  1 radeon
ohci1394               26950  0 
video                  17375  0 
intel_agp              24375  0 
output                  1871  1 video
ieee1394               81181  1 ohci1394
drm                   163747  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
tg3                   109324  0 
agpgart                31724  3 ttm,intel_agp,drm
ahci                   32680  2 
stephen@ubuntu:~$ 
```

---

### Post by sai-salamander on 2012-01-04
I finally got chance to do this! Contents of terminal below;

```
sai@bentley:~$ cat /etc/lsb-release; uname -a 
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.10 
DISTRIB_CODENAME=oneiric 
DISTRIB_DESCRIPTION="Ubuntu 11.10" 
Linux bentley 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 athlon i386 GNU/Linux 
sai@bentley:~$ lspci -nnk | grep -iA2 net 
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) 
	Subsystem: Hewlett-Packard Company Device [103c:1795] 
	Kernel driver in use: brcmsmac 
-- 
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06) 
	Subsystem: Hewlett-Packard Company Device [103c:3387] 
	Kernel driver in use: r8169 
sai@bentley:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wlan0     IEEE 802.11bgn  ESSID:"O2wireless8FB4E1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:44:8F:B4:E1   
          Bit Rate=65 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=19/70  Signal level=-91 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:1  Invalid misc:3   Missed beacon:0 

sai@bentley:~$ rfkill list all 
0: hp-wifi: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
1: hp-bluetooth: Bluetooth 
	Soft blocked: no 
	Hard blocked: no 
2: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
sai@bentley:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat 
parport_pc             32114  0 
ppdev                  12849  0 
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_idt      60049  1 
snd_hda_codec_hdmi     31426  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi 
ums_realtek            13096  0 
usb_storage            44173  2 ums_realtek 
uas                    17699  0 
snd_seq_midi           13132  0 
joydev                 17393  0 
snd_rawmidi            25241  1 snd_seq_midi 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo 
snd_seq_midi_event     14475  1 snd_seq_midi 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
binfmt_misc            17292  1 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
radeon                925020  3 
k10temp                12990  0 
psmouse                73673  0 
serio_raw              12990  0 
snd_timer              28932  2 snd_seq,snd_pcm 
snd                    55902  14 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer 
brcmsmac              591864  0 
sp5100_tco             13495  0 
brcmutil               16885  1 brcmsmac 
mac80211              272785  1 brcmsmac 
cfg80211              172392  2 brcmsmac,mac80211 
crc_ccitt              12595  1 brcmsmac 
ttm                    65224  1 radeon 
drm_kms_helper         32889  1 radeon 
i2c_piix4              13093  0 
soundcore              12600  1 snd 
drm                   192226  5 radeon,ttm,drm_kms_helper 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm 
wmi                    18744  1 hp_wmi 
i2c_algo_bit           13199  1 radeon 
hp_accel               21632  0 
lis3lv02d              19280  1 hp_accel 
input_polldev          13648  1 lis3lv02d 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp 
usbhid                 41905  0 
hid                    77367  1 usbhid 
r8169                  43104  0 
ahci                   21634  2 
libahci                25727  1 ahci 
```

---

### Post by sai-salamander on 2012-01-09
Can anyone help me with this problem? At the moment, I'm thinking I might have to completely write off my ubuntu side, which makes me quite sad D:

---

