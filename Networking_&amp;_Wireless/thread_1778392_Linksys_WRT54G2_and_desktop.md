---
title: "Linksys WRT54G2 and desktop"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by ghost25 on 2011-06-09
Okay, here goes an odd one for anyone who can/cares to answer.

My old Linksys WRK54G router, after 2 and a half years, finally bit the dust. So, time for a new router. I went out and bought a Belkin N150 but, one problem: every other system in the household connected instantly, except MY LAPTOP. Compaq Presario CQ62 model. Reason? Incompatible WiFi chip. I called Belkin's 800 number and was told there was nothing they could do, since I wasn't running Windows or iOS. Don't get me started on THAT one! Hardware incompatibilities do NOT equal software incompatibilities!

Anyway, I got myself (after returning the Belkin) a Linksys WRT54G2 router with WiFi, and I've been encountering serious hiccups in the setup. Not only did I have to reset my modem to "mate" it with the MAC on the router, but it seems the only computer I can access the router from is my roommate's Win7 laptop. I have my desktop wired into Port 1 on the router, along with a spare Ethernet cable that I keep on hand for emergency usage. However, I absolutely cannot access the router homepage from any Linux machine. (Odd, considering Linksys is, so I've heard, one of the most open-source friendly vendors out there!) My Chrome page just says it can't access the page, no matter if I'm using WiFi or eth0. And I am positive I'm typing in the correct IP address for access, 192.168.1.1. I don't want to use Windows if I can avoid it.

Is there any way, besides hacking the router and installing Tomato or some similar software, that I can access the router homepage so I can set up MAC address white-lists, instead of worrying about cross-platform WEP/WPA/WPA2/whatever security protocols? Can I set up a virtual machine to run WinXP/7, and do things that way? Or do I have no option except to use his Win7 laptop to access various security settings? Thanks in advance for any help y'all can provide.

---

### Post by josephmills on 2011-06-09
when you get the time could we see a ```
lsmod
``` & a ```
dmesg | grep ath 
``` & to make sure a ```
lspci -nn
``` thanks :)

---

### Post by ghost25 on 2011-06-12
Sure thing, josephmills:

lsmod -

Module                  Size  Used by
usb_storage            43946  0 
uas                    17676  0 
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_realtek   255820  1 
nfsd                  252397  11 
lockd                  74292  1 nfsd
nfs_acl                12771  1 nfsd
auth_rpcgss            39173  1 nfsd
snd_hda_intel          24140  2 
sunrpc                199096  12 nfsd,lockd,nfs_acl,auth_rpcgss
i915                  450944  3 
exportfs               12870  1 nfsd
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
drm_kms_helper         40745  1 i915
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
r8192se_pci           482505  0 
hp_wmi                 13418  0 
sparse_keymap          13666  1 hp_wmi
joydev                 17322  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  1 r8192se_pci
psmouse                73312  0 
drm                   180037  4 i915,drm_kms_helper
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
r8169                  42534  0 
libahci                25548  1 ahci



dmesg | grep ath
[    0.476390] device-mapper: multipath: version 1.2.0 loaded
[    0.476392] device-mapper: multipath round-robin: version 1.0.0 loaded



dmesg | grep ath
[    0.476390] device-mapper: multipath: version 1.2.0 loaded
[    0.476392] device-mapper: multipath round-robin: version 1.0.0 loaded


Hope this helps some.

---

### Post by ghost25 on 2011-06-18
Well, I can't quite mark this one as "solved," but I ended up having to return the router due to utter system incompatibility. So yeah, chalk this one up to some kind of bug-related failure if ya want.

---

### Post by harlock59 on 2012-03-09
Hi,

i know that now it should be too late but you could 've disabled the security for testing purpose without wep nor wpa, sometimes it works !

---

