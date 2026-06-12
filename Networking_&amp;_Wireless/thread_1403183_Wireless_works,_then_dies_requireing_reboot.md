---
title: "Wireless works, then dies requireing reboot"
date: 2010-02-09
forum: Networking &amp; Wireless
---

### Post by narnie on 2010-02-09
Hello,

I am having a problem with my wireless. Seems to be a relatively new problem over the past few weeks. I have an intel wireless. It seems like it can be fine for days, then in will quite working to the point a reboot is necessary. It may happen once and be fine, or may happen several times in one day.

I cannot see what I may be doing that triggers it.

I have clicke on nm-applet and see my network ssid. I click on it, and it doesn't even start trying to connect. I have right-clicked and uncheck wireless followed by networking and re-enabled in reverse order. I have done sudo /etc/init.d/networking stop then start. I have done ifconfig wlan0 down then up. I have unloaded then reloaded these modules.

```
$ lsmod|grep iwl

iwlagn                124832  0 
iwlcore               133248  1 iwlagn
mac80211              210104  2 iwlagn,iwlcore
cfg80211              109144  3 iwlagn,iwlcore,mac80211
led_class               5256  2 iwlcore,sdhci

```

Nothing but a reboot will bring it back that I can figure out.

I have a laptop Karmic box (Toshiba Satellite A505-S6965)

```
$ uname -a
Linux toshiba-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

```

Here all all the modules loaded on a fresh boot.

```
$ lsmod
Module                  Size  Used by
vloopback              16672  0 
binfmt_misc            10220  1 
ppdev                   8232  0 
vboxnetadp             93292  0 
vboxnetflt            100300  0 
vboxdrv              1708492  1 vboxnetflt
autofs4                31720  0 
dm_crypt               14888  0 
nfsd                  306112  9 
exportfs                5472  1 nfsd
nfs                   315344  0 
lockd                  78068  2 nfsd,nfs
nfs_acl                 3552  2 nfsd,nfs
auth_rpcgss            47808  2 nfsd,nfs
sunrpc                225896  10 nfsd,nfs,lockd,nfs_acl,auth_rpcgss
snd_hda_codec_atihdmi     4320  1 
joydev                 13088  0 
snd_hda_codec_realtek   277860  1 
arc4                    2144  2 
ecb                     3296  2 
snd_hda_intel          31880  4 
snd_hda_codec          87584  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
iwlagn                124832  0 
iwlcore               133248  1 iwlagn
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_seq_dummy           3460  0 
snd_pcm                93160  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              210104  2 iwlagn,iwlcore
snd_timer              26992  2 snd_pcm,snd_seq
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    77096  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
psmouse                57124  0 
uvcvideo               65260  0 
x_tables               25832  1 ip_tables
serio_raw               6596  0 
cfg80211              109144  3 iwlagn,iwlcore,mac80211
soundcore               9088  1 snd
fglrx                2279192  0 
videodev               43360  2 vloopback,uvcvideo
v4l1_compat            16804  2 uvcvideo,videodev
v4l2_compat_ioctl32    13344  1 videodev
sdhci_pci               8928  0 
sdhci                  20484  1 sdhci_pci
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
lp                     11908  0 
led_class               5256  2 iwlcore,sdhci
parport                40528  2 ppdev,lp
dm_raid45              78504  0 
xor                     5456  1 dm_raid45
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
radeon                684512  1 
ttm                    43056  1 radeon
drm                   193856  3 radeon,ttm
i2c_algo_bit            7076  1 radeon
video                  23612  0 
output                  3680  1 video
r8169                  38884  0 
mii                     6368  1 r8169
intel_agp              32816  0 
```

```
$ lspci|grep Network
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

```

One time after it quit working, dmesg showed:

```
$ dmesg 
. . .
[25939.986885] wlan0: deauthenticated (Reason: 7)
[25940.981193] wlan0: direct probe to AP 00:11:50:35:4f:87 try 1
[25940.983396] wlan0 direct probe responded
[25940.983403] wlan0: authenticate with AP 00:11:50:35:4f:87
[25940.985206] wlan0: authenticated
[25940.985212] wlan0: associate with AP 00:11:50:35:4f:87
[25940.989495] wlan0: RX ReassocResp from 00:11:50:35:4f:87 (capab=0x411 status=0 aid=7)
[25940.989502] wlan0: associated
[46705.991510] wlan0: no probe response from AP 00:11:50:35:4f:87 - disassociating
[46706.590051] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46706.590057] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46707.090065] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[46707.590072] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46707.590083] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46708.091865] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46708.091876] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46712.590281] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46712.590293] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46713.090099] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[46713.590084] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46713.590095] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46714.090151] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46714.090162] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46718.590071] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46718.590084] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46719.090060] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[46719.590036] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46719.590042] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46720.090070] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46720.090082] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46724.590486] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46724.590491] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46725.094837] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[46725.600053] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46725.600059] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46726.096174] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46726.096180] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46730.600617] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46730.600629] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46731.100738] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: time out after 500ms.
[46731.600129] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46731.600134] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46732.100061] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46732.100073] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46732.100091] iwlagn 0000:03:00.0: No space for Tx
[46732.100097] iwlagn 0000:03:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[46736.600200] iwlagn 0000:03:00.0: Error sending REPLY_RXON: time out after 500ms.
[46736.600213] iwlagn 0000:03:00.0: Error setting new RXON (-110)
[46736.600278] iwlagn 0000:03:00.0: No space for Tx
[46736.600285] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[46736.600332] iwlagn 0000:03:00.0: No space for Tx
[46736.600337] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46736.600343] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46736.600349] iwlagn 0000:03:00.0: No space for Tx
[46736.600354] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46736.600360] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46736.600372] iwlagn 0000:03:00.0: No space for Tx
[46736.600378] iwlagn 0000:03:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[46741.610131] iwlagn 0000:03:00.0: No space for Tx
[46741.610138] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46741.610142] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46741.610168] iwlagn 0000:03:00.0: No space for Tx
[46741.610171] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[46741.610199] iwlagn 0000:03:00.0: No space for Tx
[46741.610201] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46741.610203] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46741.610206] iwlagn 0000:03:00.0: No space for Tx
[46741.610208] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46741.610210] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46741.610215] iwlagn 0000:03:00.0: No space for Tx
[46741.610218] iwlagn 0000:03:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[46746.630070] iwlagn 0000:03:00.0: No space for Tx
[46746.630077] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46746.630080] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46746.630106] iwlagn 0000:03:00.0: No space for Tx
[46746.630109] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[46746.630130] iwlagn 0000:03:00.0: No space for Tx
[46746.630132] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46746.630134] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46746.630137] iwlagn 0000:03:00.0: No space for Tx
[46746.630139] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46746.630141] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46746.630148] iwlagn 0000:03:00.0: No space for Tx
[46746.630150] iwlagn 0000:03:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[46751.641395] iwlagn 0000:03:00.0: No space for Tx
[46751.641408] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46751.641415] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46751.641460] iwlagn 0000:03:00.0: No space for Tx
[46751.641466] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[46751.641509] iwlagn 0000:03:00.0: No space for Tx
[46751.641514] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46751.641520] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46751.641526] iwlagn 0000:03:00.0: No space for Tx
[46751.641531] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46751.641536] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46751.641548] iwlagn 0000:03:00.0: No space for Tx
[46751.641553] iwlagn 0000:03:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[46756.650352] iwlagn 0000:03:00.0: No space for Tx
[46756.650359] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46756.650362] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46756.650384] iwlagn 0000:03:00.0: No space for Tx
[46756.650387] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[46756.650405] iwlagn 0000:03:00.0: No space for Tx
[46756.650407] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46756.650410] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46756.650412] iwlagn 0000:03:00.0: No space for Tx
[46756.650414] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46756.650416] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46756.650422] iwlagn 0000:03:00.0: No space for Tx
[46756.650424] iwlagn 0000:03:00.0: Error sending REPLY_TX_POWER_DBM_CMD: enqueue_hcmd failed: -28
[46759.990754] iwlagn 0000:03:00.0: No space for Tx
[46759.990767] iwlagn 0000:03:00.0: Error sending REPLY_STATISTICS_CMD: enqueue_hcmd failed: -28
[46761.652147] iwlagn 0000:03:00.0: No space for Tx
[46761.652159] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46761.652166] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46761.652207] iwlagn 0000:03:00.0: No space for Tx
[46761.652214] iwlagn 0000:03:00.0: Error sending REPLY_SCAN_CMD: enqueue_hcmd failed: -28
[46761.652256] iwlagn 0000:03:00.0: No space for Tx
[46761.652261] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46761.652267] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46761.652273] iwlagn 0000:03:00.0: No space for Tx
[46761.652278] iwlagn 0000:03:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -28
[46761.652284] iwlagn 0000:03:00.0: Error setting new RXON (-28)
[46761.652296] iwlagn 0000:03:00.0: No space for Tx

```

A dump of nm-applet shows (please look at very bottom, too):

```

** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/7: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): DEBUG: foo_client_state_changed_cb
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/8

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/8

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/8

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/8

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/8

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/8
** (nm-applet:14626): DEBUG: foo_client_state_changed_cb
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected

** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/9: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): DEBUG: foo_client_state_changed_cb
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: foo_client_state_changed_cb
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: foo_client_state_changed_cb
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected

** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'ServiceName' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist



** (nm-applet:14626): WARNING **: _nm_object_get_property: Error getting 'Connection' for /org/freedesktop/NetworkManager/ActiveConnection/10: Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): DEBUG: foo_client_state_changed_cb
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/11

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/11

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/11

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/11

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/11

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/11
** (nm-applet:14626): DEBUG: foo_client_state_changed_cb
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/12

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/12

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/12

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/12

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/12

** (nm-applet:14626): WARNING **: Error in getting active connection 'Vpn' property: (19) Method "Get" with signature "ss" on interface "org.freedesktop.DBus.Properties" doesn't exist


** (nm-applet:14626): WARNING **: _nm_object_array_demarshal: couldn't create object for /org/freedesktop/NetworkManager/ActiveConnection/12
** (nm-applet:14626): DEBUG: foo_client_state_changed_cb
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-disconnected
** (nm-applet:14626): DEBUG: old state indicates that this was not a disconnect 9
** (nm-applet:14626): DEBUG: foo_client_state_changed_cb
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** (nm-applet:14626): DEBUG: going for offline with icon: notification-network-wireless-disconnected
nm-applet: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.

```

I would appreciate any assistance.

With thanks,
Narnie

---

