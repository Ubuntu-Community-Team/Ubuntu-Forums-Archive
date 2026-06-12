---
title: "Intel 4965 Wireless Card not working on Ubuntu 10.04.3"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by TheWatcher000 on 2012-01-07
I just made a fresh install of Ubuntu 10.04.3, but the wireless is not operational.
My laptop is a HP Compaq 8510w, according to linlap it has Intel 4965 802.11abgn wireless card, which should work out of the box.
The blue leds are both dark.

Here is the output of iwconfig:

```
daniel@daniel-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
tun0      no wireless extensions.

```

I also tried downloading and installing the driver manually, but there was something wrong with it, "make" always returned errors and asked me to do "make" again, and repeat... 

btw I tried booting from the livecd as well, but the wireless card still wasn't showing up.

I'm not sure what to do, can anyone help?

---

### Post by LostatAPG on 2012-01-07
I am not sure if this is going to work/help, but I had the same issue with my Rosewill RT3562... on U Server 10.04. What I had to do, is go to the web via eth0 and run Build-essential and "apt-get install gcc" plus did the same for "make".
I then copied my drive in to the user home directory unzipped it using tar.. "xjvr or xzvr" 
I  cd'd in the directory and ran "make" watched it run, looking for dependancy errors, as they happened I noted each one and had to find the right ".deb" file download it and complie it for each "make" error. Once "make" ran through succesfully, I than ran "make install" in the driver directory. You guessed it had to clear all dependency errors. All in all it was over 53 of them.... right now my system see the rosewill as ra0 but i still cant get it on the wireless, but the card is working... and will connect with no security to my router..

---

### Post by wildmanne39 on 2012-01-07
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by TheWatcher000 on 2012-01-08
Of course, here you go:

```
**daniel@daniel-laptop**:~$ sudo cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux daniel-laptop 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:35:14 UTC 2011 i686 GNU/Linux
**daniel@daniel-laptop**:~$ sudo lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
    Kernel driver in use: e1000e
    Kernel modules: e1000e
--
10:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
    Kernel driver in use: iwlagn
    Kernel modules: iwlagn
**daniel@daniel-laptop**:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

tun0      no wireless extensions.
[B]
daniel@daniel-laptop[/B]:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
daniel@daniel-laptop:~$ 
**daniel@daniel-laptop:~$** lsmod
Module                  Size  Used by
usb_storage            39969  0 
binfmt_misc             6587  1 
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               168753  2 vboxnetadp,vboxnetflt
pata_pcmcia             7824  1 
snd_hda_codec_analog    58598  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
arc4                    1153  2 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
cdc_ether               3541  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 30784  1 pata_pcmcia
tpm_infineon            7745  0 
joydev                  8740  0 
usbnet                 14943  1 cdc_ether
iwlagn                106911  0 
iwlcore               106149  1 iwlagn
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd                    54244  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
mac80211              205402  2 iwlagn,iwlcore
nvidia               9961216  44 
cdc_wdm                 8218  0 
mii                     4381  1 usbnet
ricoh_mmc               2923  0 
yenta_socket           20408  4 
rsrc_nonstatic         10015  1 yenta_socket
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
sdhci_pci               5470  0 
sdhci                  15494  1 sdhci_pci
vga16fb                11385  1 
vgastate                8961  1 vga16fb
cdc_acm                14818  0 
hp_accel               11144  0 
intel_agp              24375  0 
parport_pc             25962  1 
tpm_tis                 7488  0 
tpm                    14000  2 tpm_infineon,tpm_tis
tpm_bios                5266  1 tpm
cfg80211              126144  3 iwlagn,iwlcore,mac80211
video                  17375  0 
output                  1871  1 video
psmouse                63677  0 
soundcore               6620  1 snd
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lis3lv02d               6096  1 hp_accel
input_polldev           2482  1 lis3lv02d
led_class               2864  3 iwlcore,sdhci,hp_accel
agpgart                31724  2 nvidia,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
e1000e                119888  0
```

---

### Post by chili555 on 2012-01-08
I think the Wild Man is sleeping in today. > daniel@daniel-laptop:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    [COLOR="Red"]Hard blocked: yes[/COLOR]He's gonna tell you the hardware switch on your laptop is in the Off position. Move it to On and try again.

---

### Post by TheWatcher000 on 2012-01-08
Yeah, thought that was suspicious, but compaq 8510w has these weird led touch buttons, and they didn't seem to react until now, but indeed, after running into the same problem on windows xp (dual booting), and finding that these leds ARE actually the buttons too, it seems to be all solved!

Thank you all for your time.

---

### Post by chili555 on 2012-01-08
Glad it's working! The Wild Man will appreciate it if you use Thread Tools at the top and Mark Solved.

---

### Post by wildmanne39 on 2012-01-08
Hi, glad to see chili got you going and he was right I was sleeping in.

Thanks  Chili!

---

