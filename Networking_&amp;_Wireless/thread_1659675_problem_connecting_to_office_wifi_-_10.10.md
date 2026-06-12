---
title: "problem connecting to office wifi - 10.10"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by rockerZ71 on 2011-01-04
Hey everyone,

I am running 10.10 on a Toshiba NB255 netbook.  Wireless works find for me at home and worked last week at a hotel.  At home I just use WEP, and my office network uses WPA.  I can connect just fine from my work laptop but not from this netbook.  The network shows up fine in the network manager and it asks for the WPA password, but doesn't establish a connection.  Every once in a while it will say it is connected and has full strength but I can't ping anything, and within a minute or so it drops again.  IIRC yesterday it connected via wireless and actually worked for maybe a minute before dropping at it hasn't worked since.  Like I said, this has worked on other wireless networks.

Here is some output from dmesg if it helps:
```
[55086.034476] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55086.037598] wlan0: authenticated
[55086.037658] wlan0: associate with 00:15:62:ff:6e:89 (try 1)
[55086.041880] wlan0: RX AssocResp from 00:15:62:ff:6e:89 (capab=0x431 status=0 aid=4)
[55086.041891] wlan0: associated
[55089.045810] wlan0: deauthenticated from 00:15:62:ff:6e:89 (Reason: 2)
[55089.079974] cfg80211: All devices are disconnected, going to restore regulatory settings
[55089.079992] cfg80211: Restoring regulatory settings
[55089.080006] cfg80211: Calling CRDA to update world regulatory domain
[55089.094870] cfg80211: World regulatory domain updated:
[55089.094881]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[55089.094894]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55089.094905]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55089.094915]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55089.094926]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55089.094936]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55090.268191] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55090.271731] wlan0: authenticated
[55090.271792] wlan0: associate with 00:15:62:ff:6e:89 (try 1)
[55090.281947] wlan0: RX AssocResp from 00:15:62:ff:6e:89 (capab=0x431 status=0 aid=4)
[55090.281958] wlan0: associated
[55093.282742] wlan0: deauthenticated from 00:15:62:ff:6e:89 (Reason: 2)
[55093.308067] cfg80211: All devices are disconnected, going to restore regulatory settings
[55093.308088] cfg80211: Restoring regulatory settings
[55093.308103] cfg80211: Calling CRDA to update world regulatory domain
[55093.321847] cfg80211: World regulatory domain updated:
[55093.321859]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[55093.321872]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55093.321883]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55093.321893]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55093.321904]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55093.321914]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55094.479401] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55094.676090] wlan0: authenticate with 00:15:62:ff:6e:89 (try 2)
[55094.704515] wlan0: authenticated
[55094.726501] wlan0: associate with 00:15:62:ff:6e:89 (try 1)
[55094.925088] wlan0: associate with 00:15:62:ff:6e:89 (try 2)
[55094.935345] wlan0: RX AssocResp from 00:15:62:ff:6e:89 (capab=0x431 status=0 aid=4)
[55094.935358] wlan0: associated
[55096.738822] wlan0: deauthenticated from 00:15:62:ff:6e:89 (Reason: 2)
[55096.760070] cfg80211: All devices are disconnected, going to restore regulatory settings
[55096.760089] cfg80211: Restoring regulatory settings
[55096.760103] cfg80211: Calling CRDA to update world regulatory domain
[55096.774263] cfg80211: World regulatory domain updated:
[55096.774279]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[55096.774296]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55096.774310]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55096.774325]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55096.774339]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55096.774353]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55097.942373] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55098.140082] wlan0: authenticate with 00:15:62:ff:6e:89 (try 2)
[55098.340091] wlan0: authenticate with 00:15:62:ff:6e:89 (try 3)
[55098.540086] wlan0: authentication with 00:15:62:ff:6e:89 timed out
[55109.020951] wlan0: direct probe to 00:15:62:ff:6e:89 (try 1)
[55109.026113] wlan0: direct probe responded
[55109.036072] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55109.232086] wlan0: authenticate with 00:15:62:ff:6e:89 (try 2)
[55109.432072] wlan0: authenticate with 00:15:62:ff:6e:89 (try 3)
[55109.632072] wlan0: authentication with 00:15:62:ff:6e:89 timed out
[55120.083975] wlan0: direct probe to 00:15:62:ff:6e:89 (try 1)
[55120.284057] wlan0: direct probe to 00:15:62:ff:6e:89 (try 2)
[55120.484081] wlan0: direct probe to 00:15:62:ff:6e:89 (try 3)
[55120.684095] wlan0: direct probe to 00:15:62:ff:6e:89 timed out
[55129.560639] wlan0: direct probe to 00:15:62:ff:6e:89 (try 1)
[55129.565764] wlan0: direct probe responded
[55129.573084] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55129.577303] wlan0: authenticated
[55129.584935] wlan0: associate with 00:15:62:ff:6e:89 (try 1)
[55129.785087] wlan0: associate with 00:15:62:ff:6e:89 (try 2)
[55129.984093] wlan0: associate with 00:15:62:ff:6e:89 (try 3)
[55130.184083] wlan0: association with 00:15:62:ff:6e:89 timed out
[55140.631826] wlan0: direct probe to 00:15:62:ff:6e:89 (try 1)
[55140.829116] wlan0: direct probe to 00:15:62:ff:6e:89 (try 2)
[55141.028089] wlan0: direct probe to 00:15:62:ff:6e:89 (try 3)
[55141.228099] wlan0: direct probe to 00:15:62:ff:6e:89 timed out
[55157.726836] wlan0: direct probe to 00:15:62:ff:6e:89 (try 1)
[55157.731992] wlan0: direct probe responded
[55157.740062] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55157.748950] wlan0: authenticated
[55157.755847] wlan0: associate with 00:15:62:ff:6e:89 (try 1)
[55157.774999] wlan0: RX AssocResp from 00:15:62:ff:6e:89 (capab=0x431 status=0 aid=4)
[55157.775011] wlan0: associated
[55160.772979] wlan0: deauthenticated from 00:15:62:ff:6e:89 (Reason: 2)
[55160.812109] cfg80211: All devices are disconnected, going to restore regulatory settings
[55160.812129] cfg80211: Restoring regulatory settings
[55160.812143] cfg80211: Calling CRDA to update world regulatory domain
[55160.826185] cfg80211: World regulatory domain updated:
[55160.826198]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[55160.826210]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55160.826221]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55160.826232]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55160.826243]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55160.826253]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55162.006137] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55162.012178] wlan0: authenticated
[55162.012244] wlan0: associate with 00:15:62:ff:6e:89 (try 1)
[55162.016446] wlan0: RX AssocResp from 00:15:62:ff:6e:89 (capab=0x431 status=0 aid=4)
[55162.016456] wlan0: associated
[55165.018945] wlan0: deauthenticated from 00:15:62:ff:6e:89 (Reason: 2)
[55165.049039] cfg80211: All devices are disconnected, going to restore regulatory settings
[55165.049058] cfg80211: Restoring regulatory settings
[55165.049072] cfg80211: Calling CRDA to update world regulatory domain
[55165.063122] cfg80211: World regulatory domain updated:
[55165.063134]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[55165.063146]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55165.063157]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55165.063171]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55165.063184]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55165.063198]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55166.192464] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55166.195688] wlan0: authenticated
[55166.195747] wlan0: associate with 00:15:62:ff:6e:89 (try 1)
[55166.393078] wlan0: associate with 00:15:62:ff:6e:89 (try 2)
[55166.593374] wlan0: associate with 00:15:62:ff:6e:89 (try 3)
[55166.793534] wlan0: association with 00:15:62:ff:6e:89 timed out
[55177.238146] wlan0: direct probe to 00:15:62:ff:6e:89 (try 1)
[55177.436074] wlan0: direct probe to 00:15:62:ff:6e:89 (try 2)
[55177.636091] wlan0: direct probe to 00:15:62:ff:6e:89 (try 3)
[55177.836076] wlan0: direct probe to 00:15:62:ff:6e:89 timed out
[55206.442755] wlan0: direct probe to 00:15:62:ff:6e:89 (try 1)
[55206.454959] wlan0: direct probe responded
[55206.464072] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55206.466784] wlan0: authenticated
[55206.485134] wlan0: associate with 00:15:62:ff:6e:89 (try 1)
[55206.499234] wlan0: RX AssocResp from 00:15:62:ff:6e:89 (capab=0x431 status=0 aid=4)
[55206.499245] wlan0: associated
[55209.498273] wlan0: deauthenticated from 00:15:62:ff:6e:89 (Reason: 2)
[55209.534953] cfg80211: All devices are disconnected, going to restore regulatory settings
[55209.534971] cfg80211: Restoring regulatory settings
[55209.534986] cfg80211: Calling CRDA to update world regulatory domain
[55209.545783] cfg80211: World regulatory domain updated:
[55209.545790]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[55209.545798]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55209.545804]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55209.545811]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[55209.545817]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55209.545823]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[55210.661748] wlan0: authenticate with 00:15:62:ff:6e:89 (try 1)
[55210.860094] wlan0: authenticate with 00:15:62:ff:6e:89 (try 2)
[55211.060098] wlan0: authenticate with 00:15:62:ff:6e:89 (try 3)
[55211.260088] wlan0: authentication with 00:15:62:ff:6e:89 timed out
```


and here is lsmod
```
Module                  Size  Used by
ath9k                  88756  0 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
btrfs                 489451  0 
zlib_deflate           19266  1 btrfs
crc32c                  2531  1 
libcrc32c                887  1 btrfs
ufs                    73069  0 
qnx4                    6877  0 
hfsplus                71344  0 
hfs                    41250  0 
minix                  25303  0 
ntfs                   95015  0 
vfat                    9201  1 
msdos                   6436  0 
fat                    48240  2 vfat,msdos
jfs                   171034  0 
xfs                   693150  0 
exportfs                3449  1 xfs
reiserfs              225942  0 
aes_i586                7280  0 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
joydev                  8735  0 
snd_seq_midi_event      6047  1 snd_seq_midi
arc4                    1165  2 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k_common            5982  1 ath9k
ath9k_hw              292297  2 ath9k,ath9k_common
i915                  290938  3 
uvcvideo               55847  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  2 ath9k,ath9k_common
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211
drm_kms_helper         30200  1 i915
soundcore                880  1 snd
videodev               43098  1 uvcvideo
lp                      7342  0 
psmouse                59033  0 
drm                   168054  4 i915,drm_kms_helper
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
v4l1_compat            13359  2 uvcvideo,videodev
output                  1883  1 video
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
intel_agp              26360  2 i915
parport                31492  3 parport_pc,ppdev,lp
serio_raw               4022  0 
led_class               2633  1 ath9k
agpgart                32011  2 drm,intel_agp
ahci                   19013  0 
libahci                21667  2 ahci
usb_storage            40172  1 
r8169                  36489  0 
mii                     4425  1 r8169
```


Thank you in advance for any assistance offered

---

### Post by PatchesTheCaveman on 2011-01-04
A lot of people have a better experience with the *madwifi* drivers for your particular wireless card.

To install them, plug into a working wired Ethernet connection, and go to System > Administration > Additional Drivers on your top panel.  Then, select the *madwifi* driver, and click **Install**.

---

### Post by rockerZ71 on 2011-01-04
thanks for the tip, I will give it a shot at work tomorrow

---

### Post by franjesus on 2011-01-21
Exactly the same problem here.

Just fixed it by installing linux-backports-modules-wireless-maverick-generic and reloading the ath9k module.

Good luck!

---

### Post by rockerZ71 on 2011-01-21
> **franjesus said:**
> Exactly the same problem here.

Just fixed it by installing linux-backports-modules-wireless-maverick-generic and reloading the ath9k module.

Good luck!


Thanks!  That seems to have taken care of it.


Sorry I didn't update this thread earlier.  I did not try the madwifi drivers, I got the impression from reading other posts that was not the solution.

---

### Post by pcminh on 2011-01-22
> **franjesus said:**
> Exactly the same problem here.

Just fixed it by installing linux-backports-modules-wireless-maverick-generic and reloading the ath9k module.

Good luck!
I am  a newbie , could you please tell me how to reload ath9k module ? 
Thanks

---

### Post by rockerZ71 on 2011-01-22
> **pcminh said:**
> I am  a newbie , could you please tell me how to reload ath9k module ? 
Thanks

I believe the right way to do it is "sudo rmmod ath9k" and then "sudo modprobe ath9k" but I got some errors.  Rebooting took care of it.

---

### Post by pcminh on 2011-01-25
I tried to follow your instruction but nothing solved. :(

---

### Post by rockerZ71 on 2011-01-25
> **pcminh said:**
> I tried to follow your instruction but nothing solved. :(

What do you mean?  Did you have problems inserting the drivers, or does everything seem OK and you just can't connect to your network still?

---

### Post by thaiddhi on 2011-01-25
hi, i'm a new user of ubuntu.
I can't connect wifi only when i was on netbook batteries.
somebody know why is that happen.
looking forward your suggestion.

---

### Post by grahammechanical on 2011-01-25
hi thaiddhi

If you post a question on the end or even in the middle of someone else's question you will not get an answer because people will not see your question and it is confusing trying to answer two different questions at the same time.

Please post your question as a new post. Your comment is confusing. Please confirm if you can connect using WiFi when on battery power or not. Do you only have a connection when on mains power or not? I cannot understand what your problem is.

Regards.

---

### Post by rockerZ71 on 2011-02-07
Looks like my problems have returned -- I got to the office today and my netbook locked up on my soon after Gnome loaded.  I first thought it was some sort of gnome setting messing things up, so I deleted .gnome2, .gconf, etc and logged back in.  Things loaded up fine but no wireless.  So, I re-added my connection and it connected fine, but then the system locked up again a few seconds later.

This was on kernel 2.6.35-26, which I guess I upgraded to recently without paying attention.  The linux-backports-modules-wireless-maverick-generic package will not install for this kernel, apt-get says that it has unmet dependencies that are not installable (linux-backports-modules-compat-wireless-2.6.36-2.6.35-26-generic)

So, I tried rebooting back into the previous kernel (2.6.35-25) for which I had the backports package installed.  Still no luck connecting to wifi, the original problem is back.  Same with the -24 kernel.

Any ideas?

---

### Post by rockerZ71 on 2011-02-07
I removed the backports package mentioned above and rebooted using the 2.6.35-26 kernel and it seems to be okay now.  I didn't think that the package for a different kernel version should affect the running kernel but apparently it did.

Edit:  Nevermind, I replaced some of the gnome settings I had removed earlier, logged out and back in, and now it won't connect to wifi and keeps asking me for the password


Edited again:  well it ran fine for a while, and then the connection dropped and reestablished, and then the system locked up so that I had to do a hard reboot

---

