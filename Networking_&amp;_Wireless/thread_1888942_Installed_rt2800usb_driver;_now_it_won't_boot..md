---
title: "Installed rt2800usb driver; now it won't boot."
date: 2011-11-30
forum: Networking &amp; Wireless
---

### Post by 0olong on 2011-11-30
I recently purchased a Tenda W311M USB wireless adaptor, which said on the box that it's Linux-compatible. Maybe it is, but just plugging the thing in provoked no reaction at all from my installation of Ubuntu 11.10... so I grabbed the files off the CD that came with it, but they're just lots of C files and things like that, and makefiles which tell me there's nothing to compile, so I googled for a solution instead... which led me to this page: [https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M)

...so I installed the rt2800usb driver following the instructions there. I suppose it should have run some alarm bells when it still showed no signs of working, but I followed through to the bit where you make it start every time anyway. Then I restarted to see if that would make it work, as you do.

Instead, Ubuntu no longer boots at all. It just sticks on a black screen if I try to get in normally. If I try Recovery Mode, it takes me to the normal menu you get there with four options, but if I press any key, rather than responding normally it starts printing things like 'device descriptor read/64, error -110' and 'new high speed USB device number 5 using ehci_hcd' on the screen.

So... possibly some kind of keyboard conflict? It's an ACK-260U if that's any help. Unfortunately I don't have a spare.

---

### Post by praseodym on 2011-11-30
Tried the recovery mode with unplugged stick?

---

### Post by 0olong on 2011-12-01
Mm, without the dongle it just gets to the recovery menu and then doesn't do anything at all.

---

### Post by praseodym on 2011-12-01
Does it work with a Live-CD?

```
lsusb
lsmod
iwconfig
rfkill list
```
?

---

### Post by 0olong on 2011-12-04
I'm running off a live USB stick now...
lsusb gives me (among other things)
```
Bus 001 Device 005: ID 148f:5370 Ralink Technology, Corp. 

```

No idea if anything lsmod gives us is relevant, so here's all of it:

```
Module                  Size  Used by
dm_crypt               22565  0 
lp                     17455  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
ppdev                  12849  0 
snd_ens1371            24820  2 
gameport               15060  1 snd_ens1371
snd_intel8x0           33318  2 
snd_ac97_codec        106082  2 snd_ens1371,snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  3 snd_ens1371,snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  2 snd_ens1371,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73673  0 
snd                    55902  16 snd_ens1371,snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  1 
serio_raw              12990  0 
parport                40930  3 lp,ppdev,parport_pc
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
shpchp                 32356  0 
binfmt_misc            17292  1 
squashfs               36095  1 
overlayfs              27481  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 622589  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
usbhid                 41905  0 
hid                    77367  1 usbhid
usb_storage            44173  2 
uas                    17699  0 
radeon                925020  3 
r8169                  43104  0 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  5 radeon,ttm,drm_kms_helper
floppy                 60310  0 
i2c_algo_bit           13199  1 radeon

```

iwconfig:
```
lo        no wireless extensions.
eth0      no wireless extensions.

```

rfkill list doesn't say anything at all.

---

### Post by praseodym on 2011-12-04
Check this thread for your device:

[http://ubuntuforums.org/archive/index.php/t-1800178.html](http://ubuntuforums.org/archive/index.php/t-1800178.html)

and blacklist the **rt2800usb**:

```
echo "blacklist rt2800usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

---

