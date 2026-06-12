---
title: "sound enigma"
date: 2010-06-03
forum: Multimedia Software
---

### Post by wayeast on 2010-06-03
Alright, I am baffled!  I recently installed Ubuntu 10.04 onto a Dell Optiplex 380 desktop box, and could not get sound from it for the life of me.  I tried everything from every place I could find (am attaching a text file of all the steps I went through).  At last, I installed 9.04 onto the same machine, and sound worked straight "out of the box."  There are other problems on 9.04: the ethernet card is not recognized without downloading a Broadcom driver, and my microphone doesn't work, but sound does come out!

So, can somebody help me get 10.04 to do (almost) the same thing that 9.04 did?  How about just understand how this could happen?  Below is the output of _lsmod_ and _lspci | grep Audio_ from both systems on the same machine.  Thanks in advance for any suggestions.

**Ubuntu Lucid 10.04 info**

_lsmod_:

Module                  Size  Used by
btrfs                 458906  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94791  0 
vfat                    8901  0 
msdos                   6392  0 
fat                    47767  2 vfat,msdos
jfs                   172650  0 
xfs                   513904  0 
exportfs                3437  1 xfs
reiserfs              225539  0 
binfmt_misc             6587  1 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  282354  3 
ppdev                   5259  0 
drm_kms_helper         29297  1 i915
parport_pc             25962  1 
soundcore               6620  1 snd
dell_wmi                1793  0 
dcdbas                  5422  0 
psmouse                63245  0 
serio_raw               3978  0 
drm                   162471  4 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
intel_agp              24177  2 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
tg3                   109292  0 

_lspci | grep Audio:_

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)

**Ubuntu Jaunty 9.04 info:**

_lsmod_:

Module                  Size  Used by
binfmt_misc            16776  1 
i915                   67844  2 
drm                    96424  3 i915
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
video                  25872  0 
output                 11008  1 video
lp                     17156  0 
snd_hda_intel         436148  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
hid_dell               10112  0 
soundcore              15200  1 snd
psmouse                61972  0 
dcdbas                 15264  0 
intel_agp              34108  1 
agpgart                42696  3 drm,intel_agp
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
ppdev                  15620  0 
usbhid                 42336  1 hid_dell
pcspkr                 10496  0 
serio_raw              13444  0 
tg3                   142852  0 
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

_lspci | grep Audio:_

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

---

### Post by blchinezu on 2010-06-03
tried this?[URL="http://ubuntuforums.org/showthread.php?t=1483903"]
http://ubuntuforums.org/showthread.php?t=1483903[/URL]

---

### Post by wayeast on 2010-06-03
Wow!  There was one I hadn't tried?  Thanks bichinezu, I hadn't done that one, but it still doesn't work.

---

### Post by blchinezu on 2010-06-03
i don't know then... sorry. i hope you find a solution

---

### Post by wayeast on 2010-06-21
OK, found something that worked for my machine.  Those experiencing the same problem can try the fix on this forum thread:  [http://en.community.dell.com/support-forums/desktop/f/3513/t/19333189.aspx](http://en.community.dell.com/support-forums/desktop/f/3513/t/19333189.aspx)

I'll admit that I have no idea what this does, and that I haven't had time to thoroughly check its effectiveness with programs like skype, but it works for the login tone and alerts.  The tarball has a README that contains a warning: please read it before making and executing the commands (to be forewarned if nothing else).

---

