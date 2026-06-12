---
title: "Troubleshooting Slow WiFi"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by mrbarber12 on 2013-06-07
Hello everyone,

I've had this problem for a while and have been tinkering around with it for some time. I'm not experienced enough with Ubuntu to troubleshoot the problem so I've used a lot of solutions I've found online, especially ones like typing the commands on this page: [http://askubuntu.com/questions/119578/how-to-fix-slow-wireless-on-machines-with-intel-wireless-cards](http://askubuntu.com/questions/119578/how-to-fix-slow-wireless-on-machines-with-intel-wireless-cards) 

I've been thinking that maybe randomly typing commands like these have made the problem worse than it already was. I'm 99% sure that the problem is with Ubuntu, because the WiFi is fine on the XBox in my room and fine when my computer runs Windows (Windows downloads around 20 Mb/s and Ubuntu downloads around 1-5 Mb/s). 

How can I systematically find what is wrong with my WiFi, including whether or not I've messed up .conf files by writing a bunch of terminal commands?

For reference I am using a HP Pavilion g7-1150us running Ubuntu 13.04.

---

### Post by Hadaka on 2013-06-07
Hi,
"I've been thinking that maybe randomly typing commands like these have made the problem worse than it already was"
probably.
please open a terminal and do..
```
lspci -nnk | grep -iA3 net
lsmod
```
and..
```


cat /etc/modprobe.d/iwlwifi-disable11n.conf
cat /etc/modprobe.d/iwlagn-disable11n.conf
```
 post the results.
thanks.

---

### Post by mrbarber12 on 2013-06-07
> **Hadaka said:**
> 
```
lspci -nnk | grep -iA3 net
lsmod
```


02:00.0 Network controller [0280]: Ralink corp. RT5390 Wireless 802.11n 1T/1R PCIe [1814:5390]
    Subsystem: Hewlett-Packard Company U98Z077.00 Half-size Mini PCIe Card [103c:1636]
    Kernel driver in use: rt2800pci
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:166a]
    Kernel driver in use: r8169
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)

```
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
arc4                   12543  2 
uvcvideo               71279  0 
rt2800pci              18198  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
rt2800lib              60947  1 rt2800pci
videobuf2_core         39161  1 uvcvideo
rt2x00pci              14151  1 rt2800pci
rt2x00lib              48522  3 rt2x00pci,rt2800lib,rt2800pci
i915                  535507  8 
mac80211              526519  3 rt2x00lib,rt2x00pci,rt2800lib
videodev               95806  2 uvcvideo,videobuf2_core
coretemp               13131  0 
binfmt_misc            17260  1 
kvm_intel             126842  0 
snd_hda_codec_hdmi     36185  1 
kvm                   376505  1 kvm_intel
cfg80211              436177  2 mac80211,rt2x00lib
joydev                 17097  0 
snd_hda_codec_idt      63896  1 
snd_hda_intel          38307  3 
eeprom_93cx6           13168  1 rt2800pci
snd_hda_codec         117580  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
crc_ccitt              12627  1 rt2800lib
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
drm_kms_helper         47545  1 i915
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
rtsx_pci_ms            12875  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
hp_wmi                 17712  0 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
drm                   228750  4 i915,drm_kms_helper
sparse_keymap          13658  1 hp_wmi
memstick               15842  1 rtsx_pci_ms
mei                    36197  0 
video                  18894  1 i915
snd                    56485  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
microcode              18286  0 
i2c_algo_bit           13197  1 i915
psmouse                81038  0 
wmi                    18590  1 hp_wmi
intel_ips              17666  0 
lpc_ich                16925  0 
serio_raw              13031  0 
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
rtsx_pci_sdmmc         17238  0 
r8169                  61531  0 
rtsx_pci               32018  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25507  2 
libahci                26108  1 ahci


```



> **Hadaka said:**
> 
```

cat /etc/modprobe.d/iwlwifi-disable11n.conf
cat /etc/modprobe.d/iwlagn-disable11n.conf
```
 

cat: /etc/modprobe.d/iwlwifi-disable11n.conf: No such file or directory
cat: /etc/modprobe.d/iwlagn-disable11n.conf: No such file or directory

I actually forgot to mention that I went into the /etc/modprobe.d/ directory and deleted everything that I knew was from reading solutions online, I left the other stuff alone just in case.

---

### Post by Hadaka on 2013-06-07
Thanks for deleting those..save having to do it.
lets put it in a better way..please do..
```
sudo gedit /etc/modprobe.d/rt2800pci.conf
```
Enter this one line..
```
options rt2800pci nohwcrypt=1
```
SAVE and close gedit
Then Boot the machine.
then to also help speed it up a bit,possibly..set your
connection  like the attached..
[ATTACH=CONFIG]243617[/ATTACH][ATTACH=CONFIG]243618[/ATTACH]
also if you have WPA2 and WPA mixed...if possible set it to WPA2 only
thanks.

---

### Post by mrbarber12 on 2013-06-07
> **Hadaka said:**
> 
```
sudo gedit /etc/modprobe.d/rt2800pci.conf
```
Enter this one line..
```
options rt2800pci nohwcrypt=1
```


This seemed to not make much of a difference. The IPv4 and IPv6 settings also seemed to have made it worse in my case, so I put them back the way they were. 

If it helps, the bottom of my browser seems to be stuck at "Looking for www.________.com..." or "Waiting for www.________.com..." for a few seconds every time I load a page. Once it gets past that stage, it generally starts loading at a reasonable rate, but the lag is ridiculous. Is there a way to test internet connectivity besides something like speedtest.net?

---

### Post by Hadaka on 2013-06-07
Hi, you can always ping something and see how long it takes
```
ping -c5 8.8.8.8
```
it will also tell you if there is packet loss.. to incease the number of
times it pings..change -c5 to -cX  x=1 to 100.
you might also change your setings ni the router to a different channel
1..11 if there is alot of traffic on your current channel that can cause
a slow down as well.

---

### Post by mrbarber12 on 2013-06-07
The ping test showed no packet loss. I changed my router channel to 1 and it seems to be working well now. I tried that earlier but maybe it in combination with the rt2800pci.conf solution worked better. At least now I know if it starts acting up again that it's not because of any messed up .conf files or anything like that. Thank you for all your help, Hadaka!

---

### Post by Hadaka on 2013-06-07
You are welcome. Glad to see there is some improvement.
if you are satisfied with the results, please mark this thread solved.

follow this link to.. how to -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

be sure to edit your first post to do this...
thanks.

---

