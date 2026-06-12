---
title: "Intermittent connection issues with RTL8192E in Samsung N150"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by IBBoard on 2010-11-07
Hi,

I've got UNE 10.10 installed on a Samsung N150 that uses the RTL8192E for wireless. When the wireless works then it generally works okay, but I'm having problems with reboots and long-running connections. This is different to the mass of posts (mainly from 2009) about the card not working at all, so I started a new thread.

Basically, 90%+ of cold boots result in a successful wireless connection, with Network Manager remembering my WPA password.

When the wireless is up then it never *obviously* drops out, but I've got an app with a long-running connection that seems to disconnect itself occasionally. Looking at Wireshark then it appears that there are a number of retransmits, and a big batch just before it disconnects (which implies that the app is dropping its connection because it thinks the other end disappeared). Running the app on another machine with a different card but through the same release of Ubuntu and the app and the same router doesn't result in retries or drop-outs.

On the times when a cold boot doesn't successfully reconnect then it asks for the WPA password, then continues trying, then asks for the WPA password again, then continues trying, then asks...and so on until I rmmod and modprobe the driver.

I originally had problems with the machine refusing to restore after a hibernate/suspend, but this was solved by a tip to rmmod the driver on hibernate/suspend and modprobe it on restore.

The wireless will now work okay on some restores, but is more likely to repeat the behaviour described above for the failed cold boot.

```
$ lspci -nn
...
05:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller [10ec:8192] (rev 01)
```
```
$ lsmod
Module                  Size  Used by
michael_mic             1744  12 
arc4                    1165  6 
aes_i586                7280  293 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
dm_crypt               11385  0 
snd_hda_codec_realtek   217980  1 
joydev                  8735  0 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
psmouse                59033  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r8192e_pci            249279  0 
serio_raw               4022  0 
videodev               43098  1 uvcvideo
v4l1_compat            13359  2 uvcvideo,videodev
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
i915                  291004  4 
drm_kms_helper         30200  1 i915
drm                   168054  5 i915,drm_kms_helper
intel_agp              26360  2 i915
ahci                   19013  0 
libahci                21667  3 ahci
i2c_algo_bit            5168  1 i915
sky2                   45127  0 
agpgart                32011  2 drm,intel_agp
video                  18712  1 i915
output                  1883  1 video
```
Kernel: 2.6.35-22-generic (linux-image-2.6.35-22-generic - 2.6.35-22.35)
r8192se_pci has been blacklisted manually

Attached is a file with some snippets from dmesg around the time of the wireless failure, and the log of what it does after a remove and re-add for comparison of the "correct" messages.


Anyone know what the issue might be, or whether there are any fixes or configs that I'm missing?

Thanks.

---

### Post by GuitarJim1987 on 2010-11-21
I am having the same issue, I'm a newbie when it comes to ubuntu so hopefully someone will have an answer here.

---

### Post by Kraft4406 on 2011-03-17
Having the same issues here with the RTL8192E on a Samsung N130. Most of the time it will connect from cold boot, but 1/10 will keep asking for the WPA password over and over and over, but a reboot seems to fix this.

If I can be of any help to anyone, please just let me know what it is you want me to do in ultimate beginner's terms :)

---

### Post by oneupstairs on 2011-04-19
I have the same problem.   Maybe 1 out of 5-10 reboots the wireless does not connect and will not until I reboot.  I do not know how to use the commands to remove and restart the driver from the kernel, but I bet that would work too.

I thought it had something to do with IPv6, because after unchecking the "Require IPv6 Addressing for the connection to complete" I did get it to connect once but that must have been a fluke, because since it's been unchecked it's doing the same intermittent thing, albeit infrequently.

Thanks,

Doug

---

