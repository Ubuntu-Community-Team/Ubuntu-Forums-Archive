---
title: "Kubuntu cant detect specific wifi network"
date: 2012-04-11
forum: Networking &amp; Wireless
---

### Post by Falc7 on 2012-04-11
My kubuntu install cant pick up my home wifi network. It picks up others in the area though. Other devices, such as phones, other ubuntu installs all pick up the network fine though.
I know its a hardware problem because i dual boot windows 7 on the same machine, and that connects to the network just fine.

---

### Post by praseodym on 2012-04-11
Hi,

is a MAC address filter activated in your router? Please show:

> lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list

---

### Post by Falc7 on 2012-04-11
Sure here it is

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list

jamie@jamie-Inspiron-N5010:~$ lspci -nnk | grep -iA2 net
12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
        Subsystem: Dell XPS 8300 [1028:0010]
        Kernel driver in use: brcmsmac
--
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
        Subsystem: Dell Device [1028:0447]
        Kernel driver in use: r8169
jamie@jamie-Inspiron-N5010:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               282739  3 vboxpci,vboxnetadp,vboxnetflt
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
dm_crypt               23199  0 
wl                   2568210  0 
lib80211               14991  1 wl
bcma                   20219  0 
arc4                   12529  2 
joydev                 17693  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_hdmi     32040  1 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_hda_codec_idt      70553  1 
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec                                                
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec               
snd_seq_midi           13324  0                                                              
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
fglrx                3127712  86 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              631693  0 
brcmutil               17837  1 brcmsmac
mac80211              462046  1 brcmsmac
psmouse                73882  0 
serio_raw              13166  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,sodec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              199630  2 brcmsmac,mac80211
crc_ccitt              12667  1 brcmsmac
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
wmi                    19256  1 dell_wmi
ahci                   26002  4 
video                  19412  0 
libahci                26861  1 ahci
r8169                  52788  0 
jamie@jamie-Inspiron-N5010:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
jamie@jamie-Inspiron-N5010:~$ rfkill list
0: dell-wifi: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: dell-bluetooth: Bluetooth
        Soft blocked: no
        Hard blocked: no
2: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
jamie@jamie-Inspiron-N5010:~$ 
                                                                                     
```

---

### Post by praseodym on 2012-04-11
Blacklist the modules "brcmsmac", "bcma", and "brcm80211", and "dell_laptop" via this one-liner:

```
echo -e "blacklist bcma\nblacklist brcm80211\nblacklist brcmsmac\nblacklist dell_laptop" | sudo tee /etc/modprobe.d/blacklist-bcm.conf 
```
and reboot. Which channel is your NW? Check
```

iwlist chan
sudo iwlist scan
```

---

### Post by Falc7 on 2012-04-11
```
jamie@jamie-Inspiron-N5010:~$ iwlist chan
lo        no frequency information.

eth0      no frequency information.

eth1      no frequency information.

jamie@jamie-Inspiron-N5010:~$ sudo iwlist scan
[sudo] password for jamie: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results

jamie@jamie-Inspiron-N5010:~$ 

```

---

### Post by praseodym on 2012-04-11
Change the channel fixed to 1-11, maybe the driver is buggy.

---

### Post by Falc7 on 2012-04-11
Sorry, I'm still a bit of a noob when it comes to the command line, how do i do that?

---

