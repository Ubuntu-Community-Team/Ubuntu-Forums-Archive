---
title: "Wifi 'hard blocked' on Lenovo T420s, Realtek 8188CE"
date: 2011-09-28
forum: Networking &amp; Wireless
---

### Post by Xisiqomelir on 2011-09-28
Hi everyone, been having difficulty with my Lenovo T420S' wifi. It shows up as hard and soft blocked on rfkill, and needless to say the Fn+F5 key combo does nothing, and neither does the switch on the side. I tried reinstalling the kernel and installing the drivers from the Realtek website here (), but no luck with that either.

The wireless router definitely works because my Debian box and my parents Macintoshes get on and stay on without any problems.

Would appreciate any help.

Commands I see requested as diagnostics and output:

sudo rfkill list all

```
0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes

```
Note: If I repeat 'sudo rfkill unblock all' about 20x, then I get a spotty connection for about 10 mins before it goes back to double-blocked.

lspci -nn|grep 0280

```
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)

```

iwconfig (disconnected)
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

```

iwconfig (connected)
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Home"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:F8:F5:3F:4A   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lsmod
```
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
joydev                 17322  0 
arc4                   12473  2 
rtl8192ce             131689  0 
rtlwifi               106737  1 rtl8192ce
snd_hda_intel          28209  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
thinkpad_acpi          73750  0 
i915                  451068  3 
uvcvideo               66851  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  2 rtl8192ce,rtlwifi
videodev               75143  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                59039  0 
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 i915
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 rtlwifi,mac80211
drm                   184164  4 i915,drm_kms_helper
snd                    55295  15 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
tpm_tis                18089  0 
video                  18951  1 i915
nvram                  14035  1 thinkpad_acpi
tpm                    21251  1 tpm_tis
tpm_bios               13460  1 tpm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  3 
libahci                25548  1 ahci
xhci_hcd               72190  0 
e1000e                138627  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci

```

dmesg | egrep 'rtl|firm|radio|switch|wlan0'

```
[ 1641.780512] wlan0: associated
[ 1667.891896] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 1694.012167] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 1694.014501] wlan0: authenticated
[ 1694.014518] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 1694.018478] wlan0: deauthenticated from 00:18:f8:f5:3f:4a (Reason: 6)
[ 1704.896722] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 1705.096031] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 2)
[ 1705.295944] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 3)
[ 1705.495877] wlan0: authentication with 00:18:f8:f5:3f:4a timed out
[ 1715.781321] wlan0: direct probe to 00:18:f8:f5:3f:4a (try 1/3)
[ 1715.980552] wlan0: direct probe to 00:18:f8:f5:3f:4a (try 2/3)
[ 1716.180531] wlan0: direct probe to 00:18:f8:f5:3f:4a (try 3/3)
[ 1716.380420] wlan0: direct probe to 00:18:f8:f5:3f:4a timed out
[ 4264.974604] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4267.677929] wlan0: direct probe to 00:18:f8:f5:3f:4a (try 1/3)
[ 4267.877155] wlan0: direct probe to 00:18:f8:f5:3f:4a (try 2/3)
[ 4268.077103] wlan0: direct probe to 00:18:f8:f5:3f:4a (try 3/3)
[ 4268.277038] wlan0: direct probe to 00:18:f8:f5:3f:4a timed out
[ 4285.108176] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 4285.110366] wlan0: authenticated
[ 4285.110420] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 4285.128647] wlan0: deauthenticated from 00:18:f8:f5:3f:4a (Reason: 6)
[ 4295.992912] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 4296.192162] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 2)
[ 4296.392097] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 3)
[ 4296.591982] wlan0: authentication with 00:18:f8:f5:3f:4a timed out
[ 4306.869447] wlan0: direct probe to 00:18:f8:f5:3f:4a (try 1/3)
[ 4307.068703] wlan0: direct probe to 00:18:f8:f5:3f:4a (try 2/3)
[ 4307.071214] wlan0: direct probe responded
[ 4307.073259] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 4307.074829] wlan0: authenticated
[ 4307.074868] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 4307.078631] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 4307.078637] wlan0: associated
[ 4307.079355] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4554.356781] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 4579.792366] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4582.655152] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 4582.656851] wlan0: authenticated
[ 4582.656892] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 4582.658922] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 4582.658930] wlan0: associated
[ 4582.659641] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4600.861197] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 4601.543957] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4603.876547] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4604.576584] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4606.855381] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 4606.857203] wlan0: authenticated
[ 4606.857263] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 4606.859269] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 4606.859277] wlan0: associated
[ 4606.859982] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4613.829983] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 4624.787363] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4627.636810] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 4627.638515] wlan0: authenticated
[ 4627.638557] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 4627.640638] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 4627.640646] wlan0: associated
[ 4627.641128] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4660.888444] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 4661.851371] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4662.709820] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4684.752923] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4687.604976] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 4687.606715] wlan0: authenticated
[ 4687.606757] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 4687.609541] wlan0: deauthenticated from 00:18:f8:f5:3f:4a (Reason: 6)
[ 4698.480020] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 4698.481615] wlan0: authenticated
[ 4698.481684] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 4698.483700] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 4698.483713] wlan0: associated
[ 4698.484504] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 4698.488801] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 4699.831004] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 4699.832661] wlan0: authenticated
[ 4699.832712] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 4699.834771] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 4699.834780] wlan0: associated
[ 4995.647749] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 4996.680509] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4999.497575] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 4999.499317] wlan0: authenticated
[ 4999.499353] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 4999.501384] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 4999.501393] wlan0: associated
[ 4999.502074] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5009.393431] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 5010.176758] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5011.993603] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5014.488601] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 5014.490173] wlan0: authenticated
[ 5014.490192] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 5014.494621] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 5014.494630] wlan0: associated
[ 5014.495109] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5025.624631] rtlwifi-0:rtl_watchdog_wq_callback():<0-0> AP off, try to reconnect now
[ 5359.519428] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5360.504114] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5361.875146] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5362.542350] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5362.922690] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5365.377001] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 5365.378672] wlan0: authenticated
[ 5365.378716] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 5365.380692] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 5365.380695] wlan0: associated
[ 5365.381049] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5367.465645] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 5368.134435] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5368.562052] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5369.298722] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5380.520612] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5383.371394] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 5383.372938] wlan0: authenticated
[ 5383.372973] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 5383.374990] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 5383.374993] wlan0: associated
[ 5383.375659] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5422.098244] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 5422.811500] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5423.475967] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5423.878919] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5425.130269] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5426.901846] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 5426.903459] wlan0: authenticated
[ 5426.903503] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 5426.905466] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 5426.905473] wlan0: associated
[ 5426.906270] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 5430.191124] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 5525.460508] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 5528.321655] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 5528.323323] wlan0: authenticated
[ 5528.323379] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 5528.325423] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 5528.325432] wlan0: associated
[ 5528.325957] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6482.316216] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 6483.095913] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6483.482652] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6486.015720] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 6486.017376] wlan0: authenticated
[ 6486.017437] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 6486.019399] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 6486.019408] wlan0: associated
[ 6486.020219] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6488.468611] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 6489.148484] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6492.017514] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 6492.019213] wlan0: authenticated
[ 6492.019271] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 6492.021209] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 6492.021212] wlan0: associated
[ 6492.021960] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6859.912319] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 6876.224150] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6877.102877] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 6877.104478] wlan0: authenticated
[ 6877.104521] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 6877.110826] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 6877.110835] wlan0: associated
[ 6877.111264] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6912.752954] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 6913.722612] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6915.526659] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 6915.528466] wlan0: authenticated
[ 6915.528509] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 6915.530588] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 6915.530597] wlan0: associated
[ 6915.531314] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6921.486353] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 6927.016591] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7051.983679] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7053.920995] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7054.590982] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7071.977375] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7092.987248] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7176.933546] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7411.865938] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7412.638557] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7414.891304] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 7414.892838] wlan0: authenticated
[ 7414.892863] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 7414.894929] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 7414.894932] wlan0: associated
[ 7414.895439] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7495.520045] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 7696.767292] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7697.425821] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7699.688981] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 7699.691324] wlan0: authenticated
[ 7699.691386] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 7699.693443] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 7699.693452] wlan0: associated
[ 7699.694278] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7710.110330] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 7711.484136] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7716.759729] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7719.526421] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7720.937911] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7723.616544] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 7723.618280] wlan0: authenticated
[ 7723.618345] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 7723.620315] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 7723.620324] wlan0: associated
[ 7723.621146] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7741.622989] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 7743.986500] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7756.750171] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7781.747613] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7785.666196] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7796.733844] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7799.592848] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 7799.594721] wlan0: authenticated
[ 7799.594771] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 7799.596758] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 7799.596767] wlan0: associated
[ 7799.597187] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7801.468144] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 7804.132540] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7811.737334] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7814.686260] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7815.385468] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7816.148001] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7816.551687] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7818.095404] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7820.588754] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7821.519676] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7891.711240] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7892.256269] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7892.825102] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7893.578242] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7895.178865] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7901.708033] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7911.704088] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7914.559596] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 7914.561293] wlan0: authenticated
[ 7914.561339] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 7914.563323] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 7914.563334] wlan0: associated
[ 7914.564179] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7915.814925] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 7921.701654] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7924.560393] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 7924.562075] wlan0: authenticated
[ 7924.562111] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 7924.564188] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 7924.564197] wlan0: associated
[ 7924.564679] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7937.914130] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 7940.623883] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7941.107878] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7941.487904] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7943.282525] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 7943.284163] wlan0: authenticated
[ 7943.284209] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 7943.286172] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 7943.286184] wlan0: associated
[ 7943.286613] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 7971.118021] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 7981.682528] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7984.174286] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7986.386577] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7989.658095] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7990.336052] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7990.727659] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7991.391066] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7991.753245] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7992.570492] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7992.950926] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7995.868956] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7997.209980] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7998.699622] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7999.372538] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7999.732954] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8001.600278] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8003.581699] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8004.084128] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8004.472734] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8006.266514] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 8006.268139] wlan0: authenticated
[ 8006.268193] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 8006.270281] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 8006.270290] wlan0: associated
[ 8006.270767] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 8574.542540] wlan0: deauthenticating from 00:18:f8:f5:3f:4a by local choice (reason=3)
[ 8576.906198] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8587.488762] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8822.407452] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8917.385314] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 8920.240450] wlan0: authenticate with 00:18:f8:f5:3f:4a (try 1)
[ 8920.242148] wlan0: authenticated
[ 8920.242194] wlan0: associate with 00:18:f8:f5:3f:4a (try 1)
[ 8920.244238] wlan0: RX AssocResp from 00:18:f8:f5:3f:4a (capab=0x421 status=0 aid=1)
[ 8920.244247] wlan0: associated
[ 8920.244666] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by chili555 on 2011-09-29
> the Fn+F5 key combo does nothing, and neither does the switch on the side.You ought to be able to manipulate the switch on the side and get 'hard blocked: no' after you run:```
rfkill list all
```Can you? Then run:```
rfkill unblock all
```Then can you connect normally?

Isn't there one position of the switch on the side that's clearly 'wireless on?' Please don't move away from that position until we solve this case.

If not, let's try to see if the kernel recognizes the key press.```
sudo tail -f /var/log/syslog
```Leave the terminal open as you press Fn+F5 and see what the messages report. Once we have that information, we can proceed further.

For your information and that of the searchers, no newer driver is going to help rfkill hard blocked. The culprit is here:> snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
[COLOR="Red"]thinkpad_acpi[/COLOR]          73750  0 
i915                  451068  3 
uvcvideo               66851  0 
snd_seq_midi           13132  0 
<etc.>

---

### Post by elbanaan on 2011-09-29
I had a similar hard blocked=yes problem on my Dell laptop, solved it by disabling the wireless switch in BIOS (setting to always on).
Maybe worth a try?

---

### Post by Xisiqomelir on 2011-09-29
Thanks for responses, guys! I have always loved this community.

Chili555, the hardware switch doesn't change the rfkill output. Off or on, it's

```
Hard blocked: yes
```

Except randomly when it reconnects (only when close to the router). After a reboot when there's no hard block, everything is fine for a while then it starts hard blocking again, the switch remaining on the entire time.

Since you asked and I looked, I decided to check the Windows partition, and it also has problems with the switch (off/on doesn't do anything). I'm now thinking it might be a hardware problem.

elbanaan, I don't think I have that setting in BIOS. I only have the option to totall disable WiFi.

---

### Post by chili555 on 2011-09-29
> I decided to check the Windows partition, and it also has problems with the switch (off/on doesn't do anything). I'm now thinking it might be a hardware problem.Sounds likely to me.

---

