---
title: "Total wireless drop. Why does my network card go into a deep sleep and never wake up?"
date: 2013-05-31
forum: Networking &amp; Wireless
---

### Post by fizikz on 2013-05-31
I'm using an Intel 4965 mini-PCIe adapter in my Asus G1, upgraded from an Intel 3965 which was stable and working well. I've run into a problem where the wireless connection drops and does not recover until one or more reboots. The system log shows that the card goes into a deep sleep (I was not using standby or hibernate) and then just keeps repeating the errors:

```
May 29 23:00:11 ssg1 kernel: [32228.756031] iwl4965 0000:03:00.0: Queue 7 stuck for 2000 ms.
May 29 23:00:11 ssg1 kernel: [32228.756038] iwl4965 0000:03:00.0: On demand firmware reload
May 29 23:00:11 ssg1 kernel: [32228.760012] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:11 ssg1 kernel: last message repeated 14 times
May 29 23:00:11 ssg1 kernel: [32229.063604] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:11 ssg1 kernel: [32229.084027] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:11 ssg1 kernel: [32229.104297] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:11 ssg1 kernel: [32229.121878] ieee80211 phy0: Hardware restart was requested
May 29 23:00:11 ssg1 kernel: [32229.124582] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:11 ssg1 kernel: [32229.124582] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:11 ssg1 kernel: [32229.166484] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:11 ssg1 kernel: [32229.186767] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:11 ssg1 kernel: [32229.207506] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:11 ssg1 kernel: [32229.227791] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:11 ssg1 kernel: [32229.248082] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.268362] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.288658] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.308889] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.329144] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.329144] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.369663] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.389964] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.410237] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.430527] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.450801] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.471068] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.491377] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.511634] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.531942] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.552208] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.572436] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.592698] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.612956] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.633166] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.653363] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.673597] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.693833] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.714063] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.734289] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.754487] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.774705] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.795102] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.811297] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:00:12 ssg1 kernel: [32229.811301] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:00:12 ssg1 kernel: [32229.815292] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.835498] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.855681] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.875903] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.896143] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.916461] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.932681] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:00:12 ssg1 kernel: [32229.932684] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:00:12 ssg1 kernel: [32229.936676] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.956873] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32229.977073] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.008037] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.017485] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.037885] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.054079] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:00:12 ssg1 kernel: [32230.054082] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:00:12 ssg1 kernel: [32230.058074] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.078280] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.098496] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.118676] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.138890] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.159297] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.175523] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:00:12 ssg1 kernel: [32230.175526] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:00:12 ssg1 kernel: [32230.179517] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.199736] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.219921] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:12 ssg1 kernel: [32230.240130] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:13 ssg1 kernel: [32230.260330] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:13 ssg1 kernel: [32230.280682] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:13 ssg1 kernel: [32230.296934] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:00:13 ssg1 kernel: [32230.296941] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:00:13 ssg1 kernel: [32230.300929] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:13 ssg1 kernel: last message repeated 11 times
May 29 23:00:13 ssg1 kernel: [32230.548044] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:13 ssg1 kernel: last message repeated 2 times
May 29 23:00:13 ssg1 kernel: [32230.603914] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:13 ssg1 kernel: [32230.624173] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:13 ssg1 kernel: [32230.644392] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:00:13 ssg1 kernel: [32230.660670] iwl4965 0000:03:00.0: Unable to initialize device after 5 attempts.
May 29 23:00:13 ssg1 pulseaudio[2327]: [alsa-source] alsa-source.c: ALSA woke us up to read new data from the device, but there was actually nothing to read!
May 29 23:00:13 ssg1 pulseaudio[2327]: [alsa-source] alsa-source.c: Most likely this is a bug in the ALSA driver 'snd_usb_audio'. Please report this issue to the ALSA developers.
May 29 23:00:13 ssg1 pulseaudio[2327]: [alsa-source] alsa-source.c: We were woken up with POLLIN set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
May 29 23:00:13 ssg1 kernel: [32230.660942] iwl4965 0000:03:00.0: Stopping AGG while state not ON or starting
May 29 23:00:13 ssg1 kernel: [32230.660947] iwl4965 0000:03:00.0: queue number out of range: 0, must be 7 to 14
May 29 23:00:13 ssg1 kernel: [32231.160049] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
May 29 23:00:13 ssg1 kernel: [32231.160055] HW problem - can not stop rx aggregation for tid 0
May 29 23:00:14 ssg1 kernel: [32231.660043] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
May 29 23:00:14 ssg1 kernel: [32231.660050] HW problem - can not stop rx aggregation for tid 1
May 29 23:00:14 ssg1 kernel: [32232.160048] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
May 29 23:00:14 ssg1 kernel: [32232.160055] HW problem - can not stop rx aggregation for tid 2
May 29 23:00:15 ssg1 kernel: [32232.660035] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
May 29 23:00:15 ssg1 kernel: [32232.660042] HW problem - can not stop rx aggregation for tid 3
May 29 23:00:15 ssg1 kernel: [32233.160051] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
May 29 23:00:15 ssg1 kernel: [32233.160058] HW problem - can not stop rx aggregation for tid 4
May 29 23:00:16 ssg1 kernel: [32233.660043] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
May 29 23:00:16 ssg1 kernel: [32233.660049] HW problem - can not stop rx aggregation for tid 6
May 29 23:00:16 ssg1 kernel: [32233.672314] iwl4965 0000:03:00.0: index 0 not used in uCode key table.
May 29 23:00:16 ssg1 kernel: [32234.172042] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
May 29 23:00:16 ssg1 kernel: [32234.172051] ieee80211 phy0: failed to remove key (0, a0:f3:c1:c1:18:ea) from hardware (-110)
May 29 23:00:16 ssg1 wpa_supplicant[1234]: CTRL-EVENT-DISCONNECTED bssid=a0:f3:c1:c1:18:ea reason=4
May 29 23:00:16 ssg1 kernel: [32234.220168] cfg80211: All devices are disconnected, going to restore regulatory settings
May 29 23:00:16 ssg1 kernel: [32234.220174] cfg80211: Restoring regulatory settings
May 29 23:00:16 ssg1 kernel: [32234.220179] cfg80211: Calling CRDA to update world regulatory domain
May 29 23:00:16 ssg1 NetworkManager[1042]: <info> (wlan3): supplicant interface state: completed -> disconnected
May 29 23:00:17 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:17 ssg1 kernel: [32234.292521] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:17 ssg1 kernel: [32234.580114] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
May 29 23:00:17 ssg1 kernel: [32234.580119] cfg80211: World regulatory domain updated:
May 29 23:00:17 ssg1 kernel: [32234.580121] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
May 29 23:00:17 ssg1 kernel: [32234.580125] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 29 23:00:17 ssg1 kernel: [32234.580128] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 29 23:00:17 ssg1 kernel: [32234.580131] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
May 29 23:00:17 ssg1 kernel: [32234.580134] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 29 23:00:17 ssg1 kernel: [32234.580137] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
May 29 23:00:17 ssg1 NetworkManager[1042]: <info> (wlan3): roamed from BSSID A0:F3:C1:C1:18:EA (carbon) to (none) ((none))
May 29 23:00:18 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:18 ssg1 kernel: [32235.293876] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:19 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:19 ssg1 kernel: [32236.294387] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:20 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:20 ssg1 kernel: [32237.295779] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:21 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:21 ssg1 kernel: [32238.296184] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:22 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:22 ssg1 kernel: [32239.297482] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:23 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:23 ssg1 kernel: [32240.298873] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:24 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:24 ssg1 kernel: [32241.300298] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:25 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:25 ssg1 kernel: [32242.300927] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:26 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:26 ssg1 kernel: [32243.302196] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:27 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:27 ssg1 kernel: [32244.303467] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:28 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:28 ssg1 kernel: [32245.304751] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:29 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:29 ssg1 kernel: [32246.305179] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:30 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:30 ssg1 kernel: [32247.306453] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:31 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:31 ssg1 kernel: [32248.307737] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:31 ssg1 NetworkManager[1042]: <warn> (wlan3): link timed out.
May 29 23:00:31 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: activated -> disconnected (reason 'supplicant-timeout') [100 30 11]
May 29 23:00:31 ssg1 NetworkManager[1042]: <info> (wlan3): deactivating device (reason 'supplicant-timeout') [11]
May 29 23:00:32 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:32 ssg1 kernel: [32249.308441] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> (wlan3): canceled DHCP transaction, DHCP client pid 3937
May 29 23:00:32 ssg1 dnsmasq[3942]: exiting on receipt of SIGTERM
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> DNS: starting dnsmasq...
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> (wlan3): writing resolv.conf to /sbin/resolvconf
May 29 23:00:32 ssg1 dnsmasq[6266]: started, version 2.59 cache disabled
May 29 23:00:32 ssg1 dnsmasq[6266]: compile time options: IPv6 GNU-getopt DBus i18n DHCP TFTP conntrack IDN
May 29 23:00:32 ssg1 dnsmasq[6266]: warning: no upstream servers configured
May 29 23:00:32 ssg1 dbus[995]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Auto-activating connection 'carbon (TP Link)'.
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) starting connection 'carbon (TP Link)'
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) scheduled...
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) started...
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) scheduled...
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) complete.
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) starting...
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: prepare -> config (reason 'none') [40 50 0]
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3/wireless): access point 'carbon (TP Link)' has security, but secrets are required.
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: config -> need-auth (reason 'none') [50 60 0]
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) complete.
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) scheduled...
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) started...
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) scheduled...
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) complete.
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) starting...
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: prepare -> config (reason 'none') [40 50 0]
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3/wireless): connection 'carbon (TP Link)' has security, and secrets exist.  No new secrets needed.
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Config: added 'ssid' value 'carbon'
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Config: added 'scan_ssid' value '1'
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Config: added 'bssid' value 'a0:f3:c1:c1:18:ea'
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Config: added 'psk' value '<omitted>'
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) complete.
May 29 23:00:32 ssg1 NetworkManager[1042]: <info> Config: set interface ap_scan to 1
May 29 23:00:32 ssg1 dbus[995]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
May 29 23:00:33 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:33 ssg1 kernel: [32250.309618] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:34 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:34 ssg1 kernel: [32251.310921] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:35 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:35 ssg1 kernel: [32252.312262] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:36 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:36 ssg1 kernel: [32253.313688] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:37 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:37 ssg1 kernel: [32254.315124] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:38 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:38 ssg1 kernel: [32255.316457] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:39 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:39 ssg1 kernel: [32256.317836] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:40 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:40 ssg1 kernel: [32257.319284] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:41 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:41 ssg1 kernel: [32258.320239] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:42 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:42 ssg1 kernel: [32259.321445] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:43 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:43 ssg1 kernel: [32260.322816] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:44 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:44 ssg1 kernel: [32261.324276] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:45 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:45 ssg1 kernel: [32262.325718] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:46 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:46 ssg1 kernel: [32263.327143] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:47 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:47 ssg1 kernel: [32264.328532] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:48 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:48 ssg1 kernel: [32265.329035] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:49 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:49 ssg1 kernel: [32266.330375] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:50 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:50 ssg1 kernel: [32267.331769] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:51 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:51 ssg1 kernel: [32268.333206] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:52 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:52 ssg1 kernel: [32269.334634] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:53 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:53 ssg1 kernel: [32270.336115] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:54 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:54 ssg1 kernel: [32271.337447] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:55 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:55 ssg1 kernel: [32272.338072] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:56 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:56 ssg1 kernel: [32273.339490] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:57 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:57 ssg1 kernel: [32274.340159] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:58 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:58 ssg1 kernel: [32275.341525] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:00:59 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:00:59 ssg1 kernel: [32276.342876] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:00 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:00 ssg1 kernel: [32277.344252] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:01 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:01 ssg1 kernel: [32278.345638] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:02 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:02 ssg1 kernel: [32279.346998] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:03 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:03 ssg1 kernel: [32280.348430] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:04 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:04 ssg1 kernel: [32281.349866] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:05 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:05 ssg1 kernel: [32282.351298] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:06 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:06 ssg1 kernel: [32283.352173] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:07 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:07 ssg1 kernel: [32284.353451] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:08 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:08 ssg1 kernel: [32285.354731] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:09 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:09 ssg1 kernel: [32286.356130] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:10 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:10 ssg1 kernel: [32287.357499] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:11 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:11 ssg1 kernel: [32288.358871] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:12 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:12 ssg1 kernel: [32289.360304] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:13 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:13 ssg1 kernel: [32290.361676] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:14 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:14 ssg1 kernel: [32291.362790] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:15 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:15 ssg1 kernel: [32292.364095] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:16 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:16 ssg1 kernel: [32293.365465] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:17 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:17 ssg1 kernel: [32294.366905] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:18 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:18 ssg1 kernel: [32295.368339] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:19 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:19 ssg1 kernel: [32296.369769] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:20 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:20 ssg1 kernel: [32297.371199] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:21 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:21 ssg1 kernel: [32298.372169] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:22 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:22 ssg1 kernel: [32299.373536] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:23 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:23 ssg1 kernel: [32300.374980] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:24 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:24 ssg1 kernel: [32301.376407] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:25 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:25 ssg1 kernel: [32302.377836] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:26 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:26 ssg1 kernel: [32303.379089] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:27 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:27 ssg1 kernel: [32304.380539] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:28 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:28 ssg1 kernel: [32305.381975] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:29 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:29 ssg1 kernel: [32306.383410] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:30 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:30 ssg1 kernel: [32307.384172] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:31 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:31 ssg1 kernel: [32308.385543] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:32 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:32 ssg1 kernel: [32309.386985] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:32 ssg1 NetworkManager[1042]: <warn> Activation (wlan3/wireless): association took too long.
May 29 23:01:32 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: config -> need-auth (reason 'none') [50 60 0]
May 29 23:01:32 ssg1 NetworkManager[1042]: <warn> Activation (wlan3/wireless): asking for new secrets
May 29 23:01:33 ssg1 NetworkManager[1042]: <info> (wlan3): supplicant interface state: disconnected -> inactive
May 29 23:01:37 ssg1 NetworkManager[1042]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) scheduled...
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) started...
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) scheduled...
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) complete.
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) starting...
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: prepare -> config (reason 'none') [40 50 0]
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Activation (wlan3/wireless): connection 'carbon (TP Link)' has security, and secrets exist.  No new secrets needed.
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Config: added 'ssid' value 'carbon'
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Config: added 'scan_ssid' value '1'
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Config: added 'bssid' value 'a0:f3:c1:c1:18:ea'
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Config: added 'psk' value '<omitted>'
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) complete.
May 29 23:01:37 ssg1 NetworkManager[1042]: <info> Config: set interface ap_scan to 1
May 29 23:01:37 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:37 ssg1 kernel: [32314.848977] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:38 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:38 ssg1 kernel: [32315.850751] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:39 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:39 ssg1 kernel: [32316.852194] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:40 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:40 ssg1 kernel: [32317.853617] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:41 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:41 ssg1 kernel: [32318.854153] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:42 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:42 ssg1 kernel: [32319.855480] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:43 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:43 ssg1 kernel: [32320.856187] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:44 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:44 ssg1 kernel: [32321.857547] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:45 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:45 ssg1 kernel: [32322.858429] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:46 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:46 ssg1 kernel: [32323.859372] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:47 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:47 ssg1 kernel: [32324.860731] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:48 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:48 ssg1 kernel: [32325.862078] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:49 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:49 ssg1 kernel: [32326.863507] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:50 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:50 ssg1 kernel: [32327.865009] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:51 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:51 ssg1 kernel: [32328.866407] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:52 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:52 ssg1 kernel: [32329.867841] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:53 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:53 ssg1 kernel: [32330.868277] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:54 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:54 ssg1 kernel: [32331.869703] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:55 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:55 ssg1 kernel: [32332.871029] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:56 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:56 ssg1 kernel: [32333.872392] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:57 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:57 ssg1 kernel: [32334.873839] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:58 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:58 ssg1 kernel: [32335.875272] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:01:59 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:01:59 ssg1 kernel: [32336.876707] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:00 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:00 ssg1 kernel: [32337.878137] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:01 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:01 ssg1 kernel: [32338.879578] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:02 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:02 ssg1 kernel: [32339.880270] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:03 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:03 ssg1 kernel: [32340.881657] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:04 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:04 ssg1 kernel: [32341.883012] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> (wlan3): disconnecting for new activation request.
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: config -> disconnected (reason 'none') [50 30 0]
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> (wlan3): deactivating device (reason 'none') [0]
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Activation (wlan3) starting connection 'carbon (TP Link)'
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: disconnected -> prepare (reason 'none') [30 40 0]
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) scheduled...
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) started...
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) scheduled...
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) complete.
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) starting...
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: prepare -> config (reason 'none') [40 50 0]
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Activation (wlan3/wireless): connection 'carbon (TP Link)' has security, and secrets exist.  No new secrets needed.
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Config: added 'ssid' value 'carbon'
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Config: added 'scan_ssid' value '1'
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Config: added 'bssid' value 'a0:f3:c1:c1:18:ea'
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Config: added 'psk' value '<omitted>'
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) complete.
May 29 23:02:04 ssg1 NetworkManager[1042]: <info> Config: set interface ap_scan to 1
May 29 23:02:05 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:05 ssg1 kernel: [32342.884278] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:06 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:06 ssg1 kernel: [32343.885711] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:07 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:07 ssg1 kernel: [32344.887130] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:08 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:08 ssg1 kernel: [32345.888558] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:09 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:09 ssg1 kernel: [32346.889992] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:10 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:10 ssg1 kernel: [32347.890855] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:11 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:11 ssg1 kernel: [32348.892260] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:12 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:12 ssg1 kernel: [32349.893679] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:13 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:13 ssg1 kernel: [32350.895102] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:14 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:14 ssg1 kernel: [32351.896529] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:15 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:15 ssg1 kernel: [32352.897956] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:16 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:16 ssg1 kernel: [32353.899380] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:17 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:17 ssg1 kernel: [32354.900258] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:18 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:18 ssg1 kernel: [32355.901676] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:19 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:19 ssg1 kernel: [32356.903117] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:20 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:20 ssg1 kernel: [32357.904280] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:21 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:21 ssg1 kernel: [32358.905729] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:22 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:22 ssg1 kernel: [32359.907172] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:23 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:23 ssg1 kernel: [32360.908109] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:24 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:24 ssg1 kernel: [32361.909530] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:25 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:25 ssg1 kernel: [32362.910954] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:26 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:26 ssg1 kernel: [32363.912382] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:27 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:27 ssg1 kernel: [32364.913744] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:28 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:28 ssg1 kernel: [32365.916548] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:29 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:29 ssg1 kernel: [32366.917843] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:30 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:30 ssg1 kernel: [32367.918254] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:31 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:31 ssg1 kernel: [32368.919593] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:32 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:32 ssg1 kernel: [32369.920964] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:33 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:33 ssg1 kernel: [32370.922398] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:34 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:34 ssg1 kernel: [32371.923813] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:35 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:35 ssg1 kernel: [32372.924144] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:36 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:36 ssg1 kernel: [32373.925251] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:37 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:37 ssg1 kernel: [32374.926669] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:38 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:38 ssg1 kernel: [32375.928120] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:39 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:39 ssg1 kernel: [32376.929539] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:40 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:40 ssg1 kernel: [32377.930553] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:41 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:41 ssg1 kernel: [32378.931886] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:42 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:42 ssg1 kernel: [32379.933204] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:43 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:43 ssg1 kernel: [32380.934489] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:44 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:44 ssg1 kernel: [32381.935527] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:45 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:45 ssg1 kernel: [32382.937016] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:46 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:46 ssg1 kernel: [32383.938433] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:47 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:47 ssg1 kernel: [32384.939859] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:48 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:48 ssg1 kernel: [32385.941300] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:49 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:49 ssg1 kernel: [32386.942733] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:50 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:50 ssg1 kernel: [32387.944088] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:51 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:51 ssg1 kernel: [32388.945463] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:52 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:52 ssg1 kernel: [32389.946885] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:53 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:53 ssg1 kernel: [32390.948319] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:54 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:54 ssg1 kernel: [32391.949754] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:55 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:55 ssg1 kernel: [32392.951184] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:56 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:56 ssg1 kernel: [32393.952172] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:57 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:57 ssg1 kernel: [32394.953539] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:58 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:58 ssg1 kernel: [32395.954964] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:02:59 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:02:59 ssg1 kernel: [32396.956176] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:00 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:00 ssg1 kernel: [32397.957555] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:01 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:01 ssg1 kernel: [32398.958993] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:02 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:02 ssg1 kernel: [32399.960425] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:03 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:03 ssg1 kernel: [32400.961855] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:04 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:04 ssg1 kernel: [32401.963184] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:04 ssg1 NetworkManager[1042]: <warn> Activation (wlan3/wireless): association took too long.
May 29 23:03:04 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: config -> need-auth (reason 'none') [50 60 0]
May 29 23:03:04 ssg1 NetworkManager[1042]: <warn> Activation (wlan3/wireless): asking for new secrets
May 29 23:03:07 ssg1 NetworkManager[1042]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) scheduled...
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) started...
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: need-auth -> prepare (reason 'none') [60 40 0]
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) scheduled...
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 1 of 5 (Device Prepare) complete.
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) starting...
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: prepare -> config (reason 'none') [40 50 0]
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Activation (wlan3/wireless): connection 'carbon (TP Link)' has security, and secrets exist.  No new secrets needed.
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Config: added 'ssid' value 'carbon'
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Config: added 'scan_ssid' value '1'
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Config: added 'bssid' value 'a0:f3:c1:c1:18:ea'
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Config: added 'psk' value '<omitted>'
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Activation (wlan3) Stage 2 of 5 (Device Configure) complete.
May 29 23:03:07 ssg1 NetworkManager[1042]: <info> Config: set interface ap_scan to 1
May 29 23:03:07 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:07 ssg1 kernel: [32404.913990] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:08 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:08 ssg1 kernel: [32405.915870] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:09 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:09 ssg1 kernel: [32406.917311] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:10 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:10 ssg1 kernel: [32407.918580] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:11 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:11 ssg1 kernel: [32408.920037] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:12 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:12 ssg1 kernel: [32409.921458] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:13 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:13 ssg1 kernel: [32410.922891] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:14 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:14 ssg1 kernel: [32411.924277] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:15 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:15 ssg1 kernel: [32412.925704] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:16 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:16 ssg1 kernel: [32413.927034] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:17 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:17 ssg1 kernel: [32414.928155] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:18 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:18 ssg1 kernel: [32415.929509] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:19 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:19 ssg1 kernel: [32416.930932] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:20 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:20 ssg1 kernel: [32417.932358] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:21 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:21 ssg1 kernel: [32418.933786] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:22 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:22 ssg1 kernel: [32419.935209] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:23 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:23 ssg1 kernel: [32420.936634] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:24 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:24 ssg1 kernel: [32421.938065] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:25 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:25 ssg1 kernel: [32422.939487] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:26 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:26 ssg1 kernel: [32423.940165] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:27 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:27 ssg1 kernel: [32424.941534] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:28 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:28 ssg1 kernel: [32425.942951] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:29 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:29 ssg1 kernel: [32426.944171] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:30 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:30 ssg1 kernel: [32427.944556] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:31 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:31 ssg1 kernel: [32428.945972] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:32 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:32 ssg1 kernel: [32429.947398] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:33 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:33 ssg1 kernel: [32430.948821] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:34 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:34 ssg1 kernel: [32431.950239] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:35 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:35 ssg1 kernel: [32432.951573] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:36 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:36 ssg1 kernel: [32433.952481] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:37 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:37 ssg1 kernel: [32434.953907] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:38 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:38 ssg1 kernel: [32435.955327] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:39 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:39 ssg1 kernel: [32436.956253] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:40 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:40 ssg1 kernel: [32437.957698] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:41 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:41 ssg1 kernel: [32438.959004] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:42 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:42 ssg1 kernel: [32439.959722] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:43 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:43 ssg1 kernel: [32440.960720] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:44 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:44 ssg1 kernel: [32441.962039] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:45 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:45 ssg1 kernel: [32442.962857] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:46 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:46 ssg1 kernel: [32443.964280] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:47 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:47 ssg1 kernel: [32444.965741] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:48 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:48 ssg1 kernel: [32445.967178] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:49 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:49 ssg1 kernel: [32446.968184] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:50 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:50 ssg1 kernel: [32447.969543] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:51 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:51 ssg1 kernel: [32448.970982] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:52 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:52 ssg1 kernel: [32449.972176] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:53 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:53 ssg1 kernel: [32450.972618] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:54 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:54 ssg1 kernel: [32451.973983] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:55 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:55 ssg1 kernel: [32452.975403] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:56 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:56 ssg1 kernel: [32453.976825] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:57 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:57 ssg1 kernel: [32454.978251] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:58 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:58 ssg1 kernel: [32455.979672] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:03:59 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:03:59 ssg1 kernel: [32456.981100] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:04:00 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:04:00 ssg1 kernel: [32457.982522] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:04:01 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:04:01 ssg1 kernel: [32458.983945] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:04:02 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:04:02 ssg1 kernel: [32459.985390] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:04:03 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:04:03 ssg1 kernel: [32460.986812] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:04:04 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:04:04 ssg1 kernel: [32461.988113] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:04:05 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:04:05 ssg1 kernel: [32462.989476] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:04:06 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:04:06 ssg1 kernel: [32463.990898] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:04:07 ssg1 wpa_supplicant[1234]: Failed to initiate AP scan.
May 29 23:04:07 ssg1 kernel: [32464.992319] iwl4965 0000:03:00.0: Request scan called when driver not ready.
May 29 23:04:07 ssg1 NetworkManager[1042]: <warn> Activation (wlan3/wireless): association took too long.
May 29 23:04:07 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: config -> need-auth (reason 'none') [50 60 0]
May 29 23:04:07 ssg1 NetworkManager[1042]: <warn> Activation (wlan3/wireless): asking for new secrets
May 29 23:04:11 ssg1 NetworkManager[1042]: <warn> No agents were available for this request.
May 29 23:04:11 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
May 29 23:04:11 ssg1 NetworkManager[1042]: <warn> Activation (wlan3) failed for access point (carbon)
May 29 23:04:11 ssg1 NetworkManager[1042]: <info> Marking connection 'carbon (TP Link)' invalid.
May 29 23:04:11 ssg1 NetworkManager[1042]: <warn> Activation (wlan3) failed.
May 29 23:04:11 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: failed -> disconnected (reason 'none') [120 30 0]
May 29 23:04:11 ssg1 NetworkManager[1042]: <info> (wlan3): deactivating device (reason 'none') [0]
May 29 23:04:19 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: disconnected -> unavailable (reason 'none') [30 20 0]
May 29 23:04:19 ssg1 NetworkManager[1042]: <info> (wlan3): deactivating device (reason 'none') [0]
May 29 23:04:19 ssg1 NetworkManager[1042]: <info> (wlan3): taking down device.
May 29 23:04:19 ssg1 NetworkManager[1042]: <info> WiFi hardware radio set disabled
May 29 23:04:19 ssg1 kernel: [32476.320926] ------------[ cut here ]------------
May 29 23:04:19 ssg1 kernel: [32476.320955] WARNING: at /build/buildd/linux-3.2.0/drivers/net/wireless/iwlegacy/iwl-core.c:1436 iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]()
May 29 23:04:19 ssg1 kernel: [32476.320962] Hardware name: G1                  
May 29 23:04:19 ssg1 kernel: [32476.320966] Modules linked in: nls_iso8859_1 nls_cp437 vfat fat xts gf128mul pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) rfcomm bnep parport_pc ppdev binfmt_misc dm_crypt nvidia(P) joydev arc4 asus_oled(C) btusb uvcvideo snd_usb_audio snd_hda_codec_si3054 bluetooth snd_usbmidi_lib snd_hda_codec_realtek videodev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq iwl4965 pcmcia snd_timer snd_seq_device iwl_legacy mac80211 r592 memstick yenta_socket pcmcia_rsrc psmouse pcmcia_core snd serio_raw cfg80211 asus_laptop sparse_keymap input_polldev soundcore snd_page_alloc mac_hid coretemp lp parport vesafb usbhid hid firewire_ohci firewire_core crc_itu_t video sdhci_pci sdhci r8169
May 29 23:04:19 ssg1 kernel: [32476.321092] Pid: 1042, comm: NetworkManager Tainted: P         C O 3.2.0-44-generic #69-Ubuntu
May 29 23:04:19 ssg1 kernel: [32476.321097] Call Trace:
May 29 23:04:19 ssg1 kernel: [32476.321109]  [<c1562eb9>] ? printk+0x2d/0x2f
May 29 23:04:19 ssg1 kernel: [32476.321121]  [<c104af42>] warn_slowpath_common+0x72/0xa0
May 29 23:04:19 ssg1 kernel: [32476.321136]  [<f88b5119>] ? iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]
May 29 23:04:19 ssg1 kernel: [32476.321151]  [<f88b5119>] ? iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]
May 29 23:04:19 ssg1 kernel: [32476.321163]  [<c104af92>] warn_slowpath_null+0x22/0x30
May 29 23:04:19 ssg1 kernel: [32476.321178]  [<f88b5119>] iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]
May 29 23:04:19 ssg1 kernel: [32476.321216]  [<f894cff9>] ieee80211_do_stop+0x529/0x690 [mac80211]
May 29 23:04:19 ssg1 kernel: [32476.321226]  [<c1577eb6>] ? _raw_spin_unlock_bh+0x16/0x20
May 29 23:04:19 ssg1 kernel: [32476.321267]  [<f894d177>] ieee80211_stop+0x17/0x20 [mac80211]
May 29 23:04:19 ssg1 kernel: [32476.321272]  [<c147d609>] __dev_close_many+0x69/0xb0
May 29 23:04:19 ssg1 kernel: [32476.321276]  [<c147d674>] __dev_close+0x24/0x40
May 29 23:04:19 ssg1 kernel: [32476.321280]  [<c1482f72>] __dev_change_flags+0x82/0x150
May 29 23:04:19 ssg1 kernel: [32476.321284]  [<c14830e1>] dev_change_flags+0x21/0x60
May 29 23:04:19 ssg1 kernel: [32476.321288]  [<c148d312>] do_setlink+0x2d2/0x700
May 29 23:04:19 ssg1 kernel: [32476.321293]  [<c148eef0>] ? rtnl_configure_link+0xa0/0xa0
May 29 23:04:19 ssg1 kernel: [32476.321298]  [<c12b3cdf>] ? nla_parse+0x1f/0xa0
May 29 23:04:19 ssg1 kernel: [32476.321302]  [<c148f259>] rtnl_newlink+0x369/0x540
May 29 23:04:19 ssg1 kernel: [32476.321305]  [<c148e7ab>] ? rtnl_dump_ifinfo+0x11b/0x1a0
May 29 23:04:19 ssg1 kernel: [32476.321310]  [<c148e702>] ? rtnl_dump_ifinfo+0x72/0x1a0
May 29 23:04:19 ssg1 kernel: [32476.321314]  [<c148eef0>] ? rtnl_configure_link+0xa0/0xa0
May 29 23:04:19 ssg1 kernel: [32476.321318]  [<c148eb4a>] rtnetlink_rcv_msg+0x13a/0x270
May 29 23:04:19 ssg1 kernel: [32476.321322]  [<c1474418>] ? skb_release_data.part.54+0x78/0x80
May 29 23:04:19 ssg1 kernel: [32476.321327]  [<c148ea10>] ? __rtnl_unlock+0x20/0x20
May 29 23:04:19 ssg1 kernel: [32476.321331]  [<c14a433e>] netlink_rcv_skb+0x8e/0xb0
May 29 23:04:19 ssg1 kernel: [32476.321335]  [<c148cd9c>] rtnetlink_rcv+0x1c/0x30
May 29 23:04:19 ssg1 kernel: [32476.321338]  [<c14a3cd9>] netlink_unicast+0x239/0x290
May 29 23:04:19 ssg1 kernel: [32476.321342]  [<c14a3f42>] netlink_sendmsg+0x212/0x350
May 29 23:04:19 ssg1 kernel: [32476.321347]  [<c146cfb7>] sock_sendmsg+0xf7/0x120
May 29 23:04:19 ssg1 kernel: [32476.321352]  [<c146cfb7>] ? sock_sendmsg+0xf7/0x120
May 29 23:04:19 ssg1 kernel: [32476.321356]  [<c12a702f>] ? __copy_from_user_ll+0x1f/0x40
May 29 23:04:19 ssg1 kernel: [32476.321359]  [<c12a71c2>] ? _copy_from_user+0x42/0x60
May 29 23:04:19 ssg1 kernel: [32476.321363]  [<c1478224>] ? verify_iovec+0x44/0xb0
May 29 23:04:19 ssg1 kernel: [32476.321367]  [<c146e01a>] __sys_sendmsg+0x24a/0x260
May 29 23:04:19 ssg1 kernel: [32476.321372]  [<c146c6e8>] ? sock_destroy_inode+0x28/0x30
May 29 23:04:19 ssg1 kernel: [32476.321377]  [<c114a9a1>] ? destroy_inode+0x31/0x50
May 29 23:04:19 ssg1 kernel: [32476.321381]  [<c114aaaa>] ? evict+0xea/0x170
May 29 23:04:19 ssg1 kernel: [32476.321385]  [<c11462a9>] ? __d_free+0x39/0x60
May 29 23:04:19 ssg1 kernel: [32476.321388]  [<c11462a9>] ? __d_free+0x39/0x60
May 29 23:04:19 ssg1 kernel: [32476.321391]  [<c11462a9>] ? __d_free+0x39/0x60
May 29 23:04:19 ssg1 kernel: [32476.321395]  [<c146f48b>] sys_sendmsg+0x3b/0x60
May 29 23:04:19 ssg1 kernel: [32476.321399]  [<c146fb13>] sys_socketcall+0x263/0x2c0
May 29 23:04:19 ssg1 kernel: [32476.321403]  [<c105062c>] ? sys_time+0x1c/0x50
May 29 23:04:19 ssg1 kernel: [32476.321406]  [<c1578134>] syscall_call+0x7/0xb
May 29 23:04:19 ssg1 kernel: [32476.321411]  [<c1570000>] ? setterm_command+0xc2/0x1b5
May 29 23:04:19 ssg1 kernel: [32476.321414] ---[ end trace 4ec3dc5384fbd9c6 ]---
May 29 23:04:19 ssg1 NetworkManager[1042]: <info> WiFi now disabled by radio killswitch
May 29 23:04:24 ssg1 NetworkManager[1042]: <info> (wlan3): bringing up device.
May 29 23:04:24 ssg1 NetworkManager[1042]: <info> WiFi hardware radio set enabled
May 29 23:04:24 ssg1 kernel: [32482.138516] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:24 ssg1 kernel: [32482.138516] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:24 ssg1 NetworkManager[1042]: <info> WiFi now enabled by radio killswitch
May 29 23:04:24 ssg1 NetworkManager[1042]: <info> (wlan3): bringing up device.
May 29 23:04:24 ssg1 kernel: [32482.185261] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:24 ssg1 kernel: [32482.200420] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:24 ssg1 kernel: [32482.220878] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:24 ssg1 kernel: [32482.240996] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.261097] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.285744] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.301356] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.328668] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.341711] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.341711] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.381896] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.402041] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.422143] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.442244] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.462338] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.482432] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.502533] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.522678] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.542775] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.562870] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.582985] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.603079] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.623165] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.643323] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.663420] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.683527] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.703623] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.723761] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.743852] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.764011] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.784114] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.804348] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.820463] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:04:25 ssg1 kernel: [32482.820467] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:04:25 ssg1 kernel: [32482.824454] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.844557] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.864664] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.884801] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.904899] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.925126] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.941237] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:04:25 ssg1 kernel: [32482.941240] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:04:25 ssg1 kernel: [32482.945228] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.965335] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32482.985499] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.005800] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.025955] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.046216] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.062406] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:04:25 ssg1 kernel: [32483.062410] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:04:25 ssg1 kernel: [32483.066362] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.086497] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.106618] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.126789] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.146927] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.167188] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.183369] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:04:25 ssg1 kernel: [32483.183372] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:04:25 ssg1 kernel: [32483.187322] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.207457] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.227693] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:25 ssg1 kernel: [32483.247847] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:26 ssg1 kernel: [32483.268007] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:26 ssg1 kernel: [32483.288221] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:26 ssg1 kernel: [32483.304511] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:04:26 ssg1 kernel: [32483.304515] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:04:26 ssg1 kernel: [32483.308447] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:26 ssg1 kernel: last message repeated 14 times
May 29 23:04:26 ssg1 kernel: [32483.609812] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:26 ssg1 kernel: [32483.629991] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:26 ssg1 kernel: [32483.650138] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:04:26 ssg1 kernel: [32483.666362] iwl4965 0000:03:00.0: Unable to initialize device after 5 attempts.
May 29 23:05:01 ssg1 CRON[6324]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
May 29 23:05:10 ssg1 NetworkManager[1042]: <info> disable requested (sleeping: no  enabled: yes)
May 29 23:05:10 ssg1 NetworkManager[1042]: <info> sleeping or disabling...
May 29 23:05:10 ssg1 NetworkManager[1042]: <info> (eth0): now unmanaged
May 29 23:05:10 ssg1 NetworkManager[1042]: <info> (eth0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
May 29 23:05:10 ssg1 NetworkManager[1042]: <info> (eth0): cleaning up...
May 29 23:05:10 ssg1 NetworkManager[1042]: <info> (eth0): taking down device.
May 29 23:05:10 ssg1 NetworkManager[1042]: <info> (wlan3): now unmanaged
May 29 23:05:10 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
May 29 23:05:10 ssg1 NetworkManager[1042]: <info> (wlan3): cleaning up...
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> enable requested (sleeping: no  enabled: no)
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> waking up and re-enabling...
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> WWAN now enabled by management service
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> (eth0): now managed
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> (eth0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> (eth0): bringing up device.
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> (eth0): preparing device.
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> (eth0): deactivating device (reason 'managed') [2]
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> (wlan3): now managed
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May 29 23:05:23 ssg1 NetworkManager[1042]: <info> (wlan3): bringing up device.
May 29 23:05:23 ssg1 kernel: [32540.324705] r8169 0000:02:00.0: eth0: link down
May 29 23:05:23 ssg1 kernel: [32540.324939] ADDRCONF(NETDEV_UP): eth0: link is not ready
May 29 23:05:23 ssg1 kernel: [32540.342254] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.342254] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.371491] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.392012] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.412576] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.432709] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.452836] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.473013] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.493139] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.513274] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.533431] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.533431] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.573710] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.593845] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.613978] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.634099] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.654273] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.674404] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.694536] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.730160] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.734867] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.754996] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.775157] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.795283] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.815435] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.835574] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.855700] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.875827] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.895960] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.916150] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.936293] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.956411] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.976545] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32540.996846] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.013022] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:23 ssg1 kernel: [32541.013033] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:23 ssg1 kernel: [32541.017013] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.037161] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.057280] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.077452] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.097566] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.117832] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.133968] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:23 ssg1 kernel: [32541.133971] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:23 ssg1 kernel: [32541.137962] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.158138] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.178280] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.198399] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.218599] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.238903] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:23 ssg1 kernel: [32541.255064] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:23 ssg1 kernel: [32541.255067] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:24 ssg1 kernel: [32541.259028] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.279208] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.299316] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.319457] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.339698] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.359993] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.376136] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:24 ssg1 kernel: [32541.376139] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:24 ssg1 kernel: [32541.380130] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.400264] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.420426] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.440561] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.460670] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.480921] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.497127] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:24 ssg1 kernel: [32541.497130] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:24 ssg1 kernel: [32541.501089] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: last message repeated 14 times
May 29 23:05:24 ssg1 kernel: [32541.802891] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.823057] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.843222] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.859376] iwl4965 0000:03:00.0: Unable to initialize device after 5 attempts.
May 29 23:05:24 ssg1 NetworkManager[1042]: <info> (wlan3): deactivating device (reason 'managed') [2]
May 29 23:05:24 ssg1 kernel: [32541.864451] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.864451] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.905387] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.928010] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.948492] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.968726] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32541.988970] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.009221] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.029585] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.049824] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.070062] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.070062] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.110494] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.130683] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.150836] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.170983] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.191166] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.211327] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.231433] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:24 ssg1 kernel: [32542.251549] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.271641] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.291736] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.311886] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.332073] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.352173] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.372384] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.392473] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.412568] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.432726] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.452868] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.472963] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.493066] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.513166] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.533393] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.549546] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:25 ssg1 kernel: [32542.549550] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:25 ssg1 kernel: [32542.553537] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.573643] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.593737] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.613825] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.633913] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.654154] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.670338] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:25 ssg1 kernel: [32542.670342] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:25 ssg1 kernel: [32542.674328] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.694422] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.714510] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.734618] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.754719] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.774946] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.791092] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:25 ssg1 kernel: [32542.791095] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:25 ssg1 kernel: [32542.795083] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.815181] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.835288] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.855383] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.875472] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.895698] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.911851] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:25 ssg1 kernel: [32542.911855] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:25 ssg1 kernel: [32542.915842] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.935954] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.956049] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.976284] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32542.996416] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32543.016707] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:25 ssg1 kernel: [32543.032945] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:25 ssg1 kernel: [32543.032954] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:26 ssg1 kernel: [32543.036935] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: last message repeated 14 times
May 29 23:05:26 ssg1 kernel: [32543.339367] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.359742] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.379924] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.396069] iwl4965 0000:03:00.0: Unable to initialize device after 5 attempts.
May 29 23:05:26 ssg1 wpa_supplicant[1234]: Could not set interface wlan3 flags: Input/output error
May 29 23:05:26 ssg1 wpa_supplicant[1234]: Could not set interface 'wlan3' UP
May 29 23:05:26 ssg1 kernel: [32543.400044] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.400044] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.442296] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.461232] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.481945] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.502144] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.522265] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.542435] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.562556] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.582669] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.602791] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.602791] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.643070] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.663199] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.683320] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.703466] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.723618] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.743760] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.763920] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.784039] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.804206] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.824329] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.844465] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.864589] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.884756] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.904878] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.925004] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.945315] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.965579] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32543.985737] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.005905] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.026033] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.046192] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.066476] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.082614] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:26 ssg1 kernel: [32544.082618] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:26 ssg1 kernel: [32544.086608] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.106743] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.126872] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.147135] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.167281] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.187541] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.203913] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:26 ssg1 kernel: [32544.203917] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:26 ssg1 kernel: [32544.207677] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.228084] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:26 ssg1 kernel: [32544.248254] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.268387] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.288528] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.308825] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.325034] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:27 ssg1 kernel: [32544.325039] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:27 ssg1 kernel: [32544.329028] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.349181] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.369368] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.389549] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.409688] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.429954] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.446096] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:27 ssg1 kernel: [32544.446100] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:27 ssg1 kernel: [32544.450090] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.470231] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.490408] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.510540] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.530661] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.550995] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.567212] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:05:27 ssg1 kernel: [32544.567215] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:05:27 ssg1 kernel: [32544.571205] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: last message repeated 14 times
May 29 23:05:27 ssg1 kernel: [32544.873285] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.893452] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 kernel: [32544.913623] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:05:27 ssg1 wpa_supplicant[1234]: Could not set interface wlan3 flags: Input/output error
May 29 23:05:27 ssg1 wpa_supplicant[1234]: Failed to initialize driver interface
May 29 23:05:27 ssg1 NetworkManager[1042]: <error> [1369883127.657685] [nm-supplicant-interface.c:804] interface_add_cb(): (wlan3): error adding interface: wpa_supplicant couldn't grab this interface.
May 29 23:05:27 ssg1 NetworkManager[1042]: dbus_g_proxy_cancel_call: assertion `pending != NULL' failed
May 29 23:05:27 ssg1 NetworkManager[1042]: <info> (wlan3): supplicant interface state: starting -> down
May 29 23:05:27 ssg1 NetworkManager[1042]: <warn> Trying to remove a non-existant call id.
May 29 23:05:27 ssg1 kernel: [32544.929766] iwl4965 0000:03:00.0: Unable to initialize device after 5 attempts.
May 29 23:05:38 ssg1 NetworkManager[1042]: <info> WiFi hardware radio set disabled
May 29 23:05:38 ssg1 NetworkManager[1042]: <info> WiFi now disabled by radio killswitch
May 29 23:06:01 ssg1 NetworkManager[1042]: <info> (wlan3): bringing up device.
May 29 23:06:01 ssg1 NetworkManager[1042]: <info> WiFi hardware radio set enabled
May 29 23:06:01 ssg1 NetworkManager[1042]: <info> WiFi now enabled by radio killswitch
May 29 23:06:01 ssg1 NetworkManager[1042]: <info> (wlan3): bringing up device.
May 29 23:06:01 ssg1 kernel: [32578.904009] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32578.904009] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32578.946584] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32578.966787] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32578.987219] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.007349] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.027472] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.047641] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.067767] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.087901] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.108027] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.108027] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.148286] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.168420] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.188557] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.208753] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.229118] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:01 ssg1 kernel: [32579.249254] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.269405] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.289541] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.309771] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.329951] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.350092] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.370229] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.390404] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.410579] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.430823] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.451077] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.471391] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.491724] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.512007] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.532330] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.552584] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.573027] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.589319] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:06:02 ssg1 kernel: [32579.589323] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:06:02 ssg1 kernel: [32579.593313] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.613596] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.633885] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.654155] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.674510] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.694855] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.711042] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:06:02 ssg1 kernel: [32579.711047] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:06:02 ssg1 kernel: [32579.715036] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.735161] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.755326] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.775443] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.795569] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.815824] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.831978] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:06:02 ssg1 kernel: [32579.831981] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:06:02 ssg1 kernel: [32579.835972] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.856117] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.876261] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.896371] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.916516] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.936855] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.953065] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:06:02 ssg1 kernel: [32579.953069] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:06:02 ssg1 kernel: [32579.957059] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.977202] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32579.997329] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32580.017499] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32580.037618] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32580.057865] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:02 ssg1 kernel: [32580.073992] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
May 29 23:06:02 ssg1 kernel: [32580.073995] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
May 29 23:06:03 ssg1 kernel: [32580.077986] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:03 ssg1 kernel: last message repeated 14 times
May 29 23:06:03 ssg1 kernel: [32580.380160] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:03 ssg1 kernel: [32580.400411] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:03 ssg1 kernel: [32580.420931] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:06:03 ssg1 kernel: [32580.437124] iwl4965 0000:03:00.0: Unable to initialize device after 5 attempts.
May 29 23:15:01 ssg1 CRON[6358]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
May 29 23:17:01 ssg1 CRON[6362]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 29 23:19:59 ssg1 NetworkManager[1042]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/ieee80211/phy0/rfkill1 disappeared
May 29 23:20:00 ssg1 kernel: [33417.285199] iwl4965 0000:03:00.0: PCI INT A disabled
May 29 23:20:00 ssg1 NetworkManager[1042]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0/net/wlan3, iface: wlan3)
May 29 23:20:00 ssg1 NetworkManager[1042]: <info> (wlan3): now unmanaged
May 29 23:20:00 ssg1 NetworkManager[1042]: <info> (wlan3): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
May 29 23:20:00 ssg1 NetworkManager[1042]: <warn> (3) failed to find interface name for index
May 29 23:20:00 ssg1 NetworkManager[1042]: (nm-system.c:685):nm_system_iface_get_flags: runtime check failed: (iface != NULL)
May 29 23:20:00 ssg1 NetworkManager[1042]: <error> [1369884000.50533] [nm-system.c:687] nm_system_iface_get_flags(): (unknown): failed to get interface link object
May 29 23:20:00 ssg1 NetworkManager[1042]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 29 23:20:00 ssg1 NetworkManager[1042]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
May 29 23:20:10 ssg1 kernel: [33428.092278] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
May 29 23:20:10 ssg1 kernel: [33428.092281] iwl4965: Copyright(c) 2003-2011 Intel Corporation
May 29 23:20:10 ssg1 kernel: [33428.092345] iwl4965 0000:03:00.0: enabling device (0000 -> 0002)
May 29 23:20:10 ssg1 kernel: [33428.092357] iwl4965 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
May 29 23:20:10 ssg1 kernel: [33428.092373] iwl4965 0000:03:00.0: setting latency timer to 64
May 29 23:20:10 ssg1 kernel: [33428.092405] iwl4965 0000:03:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0xFFFFFFFF
May 29 23:20:10 ssg1 kernel: [33428.096021] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:20:10 ssg1 kernel: [33428.116768] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
May 29 23:20:10 ssg1 kernel: [33428.133168] iwl4965 0000:03:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
May 29 23:20:10 ssg1 kernel: [33428.133171] iwl4965 0000:03:00.0: EEPROM not found, EEPROM_GP=0xffffffff
May 29 23:20:10 ssg1 kernel: [33428.133199] iwl4965 0000:03:00.0: Unable to init EEPROM
May 29 23:20:10 ssg1 kernel: [33428.133290] iwl4965 0000:03:00.0: PCI INT A disabled
May 29 23:20:10 ssg1 kernel: [33428.133303] iwl4965: probe of 0000:03:00.0 failed with error -2
```


Here is the output from the kernel log that might contain more clues:

```
May 31 22:47:54 ssg1 kernel: [  158.464099] ------------[ cut here ]------------
May 31 22:47:54 ssg1 kernel: [  158.464129] WARNING: at /build/buildd/linux-3.2.0/drivers/net/wireless/iwlegacy/iwl-core.c:1436 iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]()
May 31 22:47:54 ssg1 kernel: [  158.464136] Hardware name: G1                  
May 31 22:47:54 ssg1 kernel: [  158.464140] Modules linked in: pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) dm_crypt rfcomm bnep parport_pc ppdev binfmt_misc joydev nvidia(P) arc4 snd_hda_codec_si3054 asus_oled(C) snd_hda_codec_realtek uvcvideo videodev btusb snd_hda_intel snd_hda_codec snd_usb_audio bluetooth snd_hwdep snd_pcm snd_usbmidi_lib snd_seq_midi snd_rawmidi pcmcia snd_seq_midi_event snd_seq snd_timer snd_seq_device r592 psmouse memstick yenta_socket pcmcia_rsrc serio_raw pcmcia_core snd iwl4965 iwl_legacy mac80211 cfg80211 soundcore snd_page_alloc mac_hid asus_laptop sparse_keymap input_polldev coretemp lp parport vesafb usbhid hid firewire_ohci firewire_core crc_itu_t sdhci_pci sdhci video r8169
May 31 22:47:54 ssg1 kernel: [  158.464254] Pid: 1054, comm: NetworkManager Tainted: P         C O 3.2.0-45-generic #70-Ubuntu
May 31 22:47:54 ssg1 kernel: [  158.464260] Call Trace:
May 31 22:47:54 ssg1 kernel: [  158.464272]  [<c1562eb9>] ? printk+0x2d/0x2f
May 31 22:47:54 ssg1 kernel: [  158.464283]  [<c104af42>] warn_slowpath_common+0x72/0xa0
May 31 22:47:54 ssg1 kernel: [  158.464298]  [<f8859119>] ? iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]
May 31 22:47:54 ssg1 kernel: [  158.464313]  [<f8859119>] ? iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]
May 31 22:47:54 ssg1 kernel: [  158.464321]  [<c104af92>] warn_slowpath_null+0x22/0x30
May 31 22:47:54 ssg1 kernel: [  158.464335]  [<f8859119>] iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]
May 31 22:47:54 ssg1 kernel: [  158.464373]  [<f88ddff9>] ieee80211_do_stop+0x529/0x690 [mac80211]
May 31 22:47:54 ssg1 kernel: [  158.464392]  [<c1577eb6>] ? _raw_spin_unlock_bh+0x16/0x20
May 31 22:47:54 ssg1 kernel: [  158.464409]  [<f88de177>] ieee80211_stop+0x17/0x20 [mac80211]
May 31 22:47:54 ssg1 kernel: [  158.464415]  [<c147d609>] __dev_close_many+0x69/0xb0
May 31 22:47:54 ssg1 kernel: [  158.464418]  [<c147d674>] __dev_close+0x24/0x40
May 31 22:47:54 ssg1 kernel: [  158.464422]  [<c1482f72>] __dev_change_flags+0x82/0x150
May 31 22:47:54 ssg1 kernel: [  158.464427]  [<c14830e1>] dev_change_flags+0x21/0x60
May 31 22:47:54 ssg1 kernel: [  158.464431]  [<c148d312>] do_setlink+0x2d2/0x700
May 31 22:47:54 ssg1 kernel: [  158.464436]  [<c148eef0>] ? rtnl_configure_link+0xa0/0xa0
May 31 22:47:54 ssg1 kernel: [  158.464441]  [<c12b3cdf>] ? nla_parse+0x1f/0xa0
May 31 22:47:54 ssg1 kernel: [  158.464445]  [<c148f259>] rtnl_newlink+0x369/0x540
May 31 22:47:54 ssg1 kernel: [  158.464449]  [<c148e7ab>] ? rtnl_dump_ifinfo+0x11b/0x1a0
May 31 22:47:54 ssg1 kernel: [  158.464453]  [<c148e702>] ? rtnl_dump_ifinfo+0x72/0x1a0
May 31 22:47:54 ssg1 kernel: [  158.464457]  [<c148eef0>] ? rtnl_configure_link+0xa0/0xa0
May 31 22:47:54 ssg1 kernel: [  158.464461]  [<c148eb4a>] rtnetlink_rcv_msg+0x13a/0x270
May 31 22:47:54 ssg1 kernel: [  158.464466]  [<c1474418>] ? skb_release_data.part.54+0x78/0x80
May 31 22:47:54 ssg1 kernel: [  158.464470]  [<c148ea10>] ? __rtnl_unlock+0x20/0x20
May 31 22:47:54 ssg1 kernel: [  158.464475]  [<c14a433e>] netlink_rcv_skb+0x8e/0xb0
May 31 22:47:54 ssg1 kernel: [  158.464479]  [<c148cd9c>] rtnetlink_rcv+0x1c/0x30
May 31 22:47:54 ssg1 kernel: [  158.464482]  [<c14a3cd9>] netlink_unicast+0x239/0x290
May 31 22:47:54 ssg1 kernel: [  158.464486]  [<c14a3f42>] netlink_sendmsg+0x212/0x350
May 31 22:47:54 ssg1 kernel: [  158.464491]  [<c146cfb7>] sock_sendmsg+0xf7/0x120
May 31 22:47:54 ssg1 kernel: [  158.464496]  [<c146cfb7>] ? sock_sendmsg+0xf7/0x120
May 31 22:47:54 ssg1 kernel: [  158.464501]  [<c12a702f>] ? __copy_from_user_ll+0x1f/0x40
May 31 22:47:54 ssg1 kernel: [  158.464504]  [<c12a71c2>] ? _copy_from_user+0x42/0x60
May 31 22:47:54 ssg1 kernel: [  158.464508]  [<c1478224>] ? verify_iovec+0x44/0xb0
May 31 22:47:54 ssg1 kernel: [  158.464512]  [<c146e01a>] __sys_sendmsg+0x24a/0x260
May 31 22:47:54 ssg1 kernel: [  158.464517]  [<c146c6e8>] ? sock_destroy_inode+0x28/0x30
May 31 22:47:54 ssg1 kernel: [  158.464523]  [<c114a9a1>] ? destroy_inode+0x31/0x50
May 31 22:47:54 ssg1 kernel: [  158.464527]  [<c114aaaa>] ? evict+0xea/0x170
May 31 22:47:54 ssg1 kernel: [  158.464531]  [<c11462a9>] ? __d_free+0x39/0x60
May 31 22:47:54 ssg1 kernel: [  158.464534]  [<c11462a9>] ? __d_free+0x39/0x60
May 31 22:47:54 ssg1 kernel: [  158.464538]  [<c11462a9>] ? __d_free+0x39/0x60
May 31 22:47:54 ssg1 kernel: [  158.464541]  [<c146f48b>] sys_sendmsg+0x3b/0x60
May 31 22:47:54 ssg1 kernel: [  158.464545]  [<c146fb13>] sys_socketcall+0x263/0x2c0
May 31 22:47:54 ssg1 kernel: [  158.464550]  [<c105062c>] ? sys_time+0x1c/0x50
May 31 22:47:54 ssg1 kernel: [  158.464554]  [<c1578134>] syscall_call+0x7/0xb
May 31 22:47:54 ssg1 kernel: [  158.464556] ---[ end trace 333916a615d7a00b ]---
```

---

### Post by Hadaka on 2013-05-31
Hi have you set the power save mode to never?
also..please post the output of...
```
modinfo iwlwifi | grep no_sleep
```
thanks.

---

### Post by fizikz on 2013-06-01
Thanks for your reply, Hadaka.

Which power saving mode are you referring to?

```
~$ modinfo iwlwifi | grep no_sleep
parm:           no_sleep_autoadjust:don't automatically adjust sleep level according to maximum network latency (default: true) (bool)

```

---

### Post by Hadaka on 2013-06-01
The power settings when you click ..settings..and the battery/power icon
Let see what the current setting is in your iwlwifi module..
please do..
```
cat /sys/module/iwlwifi/parameters/no_sleep_autoadjust
```
thanks.

---

### Post by Hadaka on 2013-06-01
I just realized im looking at the wrong driver...you are not using
iwlwifi...you are using iwl4765 sorry about that. That driver i am
not familure with...i will need to do some research. I noticed you 
had another thread for this issue and were being helped by varunendra.
I will gather some more infor and get back with you.
thanks.

---

### Post by varunendra on 2013-06-01
@fizikz,
I may not get enough time to dig deeper if required, but you may try to 'undo' the [changes]("http://ubuntuforums.org/showthread.php?t=2143995&p=12646527#post12646527") we made in your previous thread. That is, simply delete the mac80211.cfg options file for a test. Unless it seems to help, keep it removed.

```
sudo rm /etc/modprobe.d/mac80211.conf
```
Then reboot or just remove - reload the iwl4965 driver to see if there is any positive change.

With this, thread subscribed :)

---

### Post by fizikz on 2013-06-01
The power saving settings are set to never. 

I should have mentioned that I'm using the iwl4965 driver. Yes, I do have some other threads since I have had problems upgrading to wireless N despite trying several different adapters. So far, the Intel 4965 seems to be the least problematic wireless N adapter that I've tried, since I have not gotten any full system freezes as I did with the Intel 5100 and 6200 on this laptop. 

Here is the output of the diagnostic wireless script that may be useful: [http://paste.ubuntu.com/5721937/]("http://paste.ubuntu.com/5721937/")

Thanks for looking into this.

EDIT: varunendra, I've undone the change we had made previously. Thanks for remembering and pointing it out! It is interesting that for every wirless drop, the first entry in the system log refers to a 2000ms queue, and this is the value we had used for that change in the configuration file.

---

### Post by varunendra on 2013-06-02
> **fizikz said:**
> It is interesting that for every wirless drop, the first entry in the system log refers to a 2000ms queue, and this is the value we had used for that change in the configuration file.

So.. now that it is back to default, did it make things any better? The Wireless Script results you posted look okay to me. Couldn't notice anything too bad in dmesg, although the signal quality in iwconfig DOES look bad and too much noise in the signal -
```
wlan3     IEEE 802.11abgn  ESSID:"carbon"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Bit Rate=19.5 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          **Link Quality=[COLOR="#FF0000"]23[/COLOR]/70**  **Signal level=[COLOR="#FF0000"]-87[/COLOR] dBm**  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1330  Invalid misc:32   Missed beacon:0
```
..but that doesn't seem related to your problem. You may be able to possibly improve the signal quality by using a least used channel (1 or 11 is usually recommended by top gurus here, I don't know why). If it still goes to deep sleep, or any other issue, then I think we'd also need to look into syslog, which gave us more info than dmesg in your previous outputs.

Also, since the iwl4965 driver is using iwl_legacy driver, I don't think you'd be able to get N speeds. So it is a good idea to disable it in the router (if you haven't already) and disable it in the driver too -
```
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965 11n_disable=1
```
You may also try 'swcrypto' parameter additionally to see if it helps stability -
```
sudo modprobe -v iwl4965 11n_disable=1 swcrypto=1
```

To make these parameters permanent, create a .conf file -
```
echo "options iwl4965 11n_disable=1 swcrypto=1" | sudo tee /etc/modprobe.d/iwl4964.conf
```

To go back to defaults, just delete the above file -
```
sudo rm /etc/modprobe.d/iwl4964.conf
```

And whenever a problem occurs, always take a look at dmesg and syslog. Post back if something looks suspicious.
Good Luck!

---

### Post by fizikz on 2013-06-02
Since changing back to default, I have not had the wireless drop so far. I will wait a few days and see how it does.

The reason the link rate, link quality, and signal level were poor was because for some reason my laptop had roamed to a farther AP (I have two wireless APs). Here is a more recent run of iwconfig:

```
wlan3     IEEE 802.11abgn  ESSID:"carbon"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: A0:F3:C1:C1:18:EA   
          Bit Rate=130 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:89  Invalid misc:63   Missed beacon:0

```

For both scans, the laptop was 2 floors away from the AP, so I'm quite happy with the wireless AP and network adapter performance. The bit rate does fluctuate quite a bit (say from 65Mb/s to 144Mb/s) but the actual throughput I get during file transfers is pretty good at about 30Mb/s considering the distance.

Wireless N works fine for me, so I see no need to disable it. With G I also get good performance, albeit with throughput around 20Mb/s.

What does the swcrypto option do? My guess is it toggles whether the cryptographic computations are done using hardware or software. Wouldn't using hardware reduce the load on the rest of the system?

I've been keeping a close eye on the logs. So far so good. I hope in a few days I can report this issue as solved!

---

### Post by varunendra on 2013-06-02
> **fizikz said:**
> Wireless N works fine for me, so I see no need to disable it. With G I also get good performance, albeit with throughput around 20Mb/s.
That's a nice info about the device/driver, I wasn't expecting anything above 54Mb/s with a throughput of more than 20Mb/s ! :)

> What does the swcrypto option do? My guess is it toggles whether the cryptographic computations are done using hardware or software. Wouldn't using hardware reduce the load on the rest of the system?
Yes it toggles the hardware encryption on/off. By default the encryption/decryption of the data packets is done by the wireless device. Setting swenc=1 shifts the task over to the operating system. It helps in case when the data stream is too fast for the device to keep up with, resulting in irritating speed fluctuations or even 'freezing' of data flow. It does put some 'extra' load on the system, but it is negligible considering the enormous computing power even the cheapest modern computers have.

I hope the connectivity remains good as it is now. :)

---

### Post by fizikz on 2013-06-02
I did some more network testing, this time with the swcrypto=1 option. In the usual location of this laptop which is 2 floors above the AP, I was getting faster throughput averaging around 35Mb/s, and sometimes hitting 40Mb/s. I also tested in the same room as the wireless AP, and I get an average of 42Mb/s with max rates of up to 50Mb/s. I'm not sure if it's just me, but it seems the transfer rates were a bit more stable as well. 

I should note that there is a Powerline AV segment in my network configuration that bottlenecks network speeds, so the maximum potential throughput might actually be higher! Overall, I'm quite happy with these results and I'll be keeping the swcrypto=1 option via the conf file. 

Also, my system has been stable with no wireless drops so far, so things are looking good! Thanks again, Hadaka and varunendra, for all the help!

---

### Post by varunendra on 2013-06-02
> **fizikz said:**
> I did some more network testing, this time with the swcrypto=1 option. In the usual location of this laptop which is 2 floors above the AP, I was getting faster throughput averaging around 35Mb/s, and sometimes hitting 40Mb/s. I also tested in the same room as the wireless AP, and I get an average of 42Mb/s with max rates of up to 50Mb/s. I'm not sure if it's just me, but it seems the transfer rates were a bit more stable as well. 

I should note that there is a Powerline AV segment in my network configuration that bottlenecks network speeds, so the maximum potential throughput might actually be higher! Overall, I'm quite happy with these results and I'll be keeping the swcrypto=1 option via the conf file.

Wow! Thanks for the energy booster tonic for the day !! :P

---

### Post by fizikz on 2013-06-04
My system has been totally stable since removing the custom configuration file that was applicable for the previous wireless adapter. Not only is this problem solved, but it means that the Intel 4965AGN actually works well right out of the box, at least on the Asus G1. 

No more system freezes, no more wireless drops, only good and stable performance and finally upgraded to wireless N. Thanks again!

---

### Post by varunendra on 2013-06-04
You have provided a really nice feedback with a clear set of stats possible in home conditions. Guess you have already started contributing as a 'tester' :P
Thanks!

---

### Post by fizikz on 2013-06-06
After several days of no problems, the wireless drop happened again with the queue stuck and deep sleep error messages. Here is the log from the event:

```
Jun  6 02:10:55 ssg1 kernel: [98911.012067] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
Jun  6 02:10:55 ssg1 kernel: [98911.012078] HW problem - can not stop rx aggregation for tid 0
Jun  6 02:10:56 ssg1 kernel: [98911.420051] iwl4965 0000:03:00.0: Queue 7 stuck for 2000 ms.
Jun  6 02:10:56 ssg1 kernel: [98911.420060] iwl4965 0000:03:00.0: On demand firmware reload
Jun  6 02:10:56 ssg1 kernel: [98911.512046] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
Jun  6 02:10:56 ssg1 kernel: [98911.512062] HW problem - can not stop rx aggregation for tid 1
Jun  6 02:10:57 ssg1 kernel: [98912.012066] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
Jun  6 02:10:57 ssg1 kernel: [98912.012080] HW problem - can not stop rx aggregation for tid 2
Jun  6 02:10:57 ssg1 kernel: [98912.016011] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:57 ssg1 kernel: last message repeated 14 times
Jun  6 02:10:57 ssg1 kernel: [98912.321108] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:57 ssg1 kernel: [98912.341622] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:57 ssg1 kernel: [98912.361899] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:57 ssg1 kernel: [98912.378232] ieee80211 phy0: Hardware restart was requested
Jun  6 02:10:57 ssg1 kernel: [98912.876055] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
Jun  6 02:10:57 ssg1 kernel: [98912.876066] HW problem - can not stop rx aggregation for tid 3
Jun  6 02:10:58 ssg1 kernel: [98913.376041] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
Jun  6 02:10:58 ssg1 kernel: [98913.376049] HW problem - can not stop rx aggregation for tid 4
Jun  6 02:10:58 ssg1 kernel: [98913.876043] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
Jun  6 02:10:58 ssg1 kernel: [98913.876054] HW problem - can not stop rx aggregation for tid 5
Jun  6 02:10:58 ssg1 kernel: [98913.876990] iwl4965 0000:03:00.0: Stopping AGG while state not ON or starting
Jun  6 02:10:58 ssg1 kernel: [98913.877000] iwl4965 0000:03:00.0: queue number out of range: 0, must be 7 to 14
Jun  6 02:10:59 ssg1 kernel: [98914.376043] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
Jun  6 02:10:59 ssg1 kernel: [98914.376053] HW problem - can not stop rx aggregation for tid 6
Jun  6 02:10:59 ssg1 kernel: [98914.388225] cfg80211: All devices are disconnected, going to restore regulatory settings
Jun  6 02:10:59 ssg1 kernel: [98914.388232] cfg80211: Restoring regulatory settings
Jun  6 02:10:59 ssg1 kernel: [98914.388237] cfg80211: Calling CRDA to update world regulatory domain
Jun  6 02:10:59 ssg1 kernel: [98914.392283] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.392283] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.432720] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.452963] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.473617] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.493956] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.514142] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.534353] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.554464] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.574634] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.594940] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.594940] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.635154] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.655416] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.675579] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.695704] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.715921] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.736026] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.756478] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.776583] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.796806] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.816930] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.837180] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.857294] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.877484] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.897600] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.917813] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.937927] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.958164] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.978328] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98914.998567] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.018712] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.038912] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.059303] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.075470] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
Jun  6 02:10:59 ssg1 kernel: [98915.075474] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
Jun  6 02:10:59 ssg1 kernel: [98915.079457] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.099581] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.119799] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.139908] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.160133] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.180383] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.196638] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
Jun  6 02:10:59 ssg1 kernel: [98915.196641] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
Jun  6 02:10:59 ssg1 kernel: [98915.200628] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.220741] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:10:59 ssg1 kernel: [98915.240983] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.261136] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.281341] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.301587] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.317845] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
Jun  6 02:11:00 ssg1 kernel: [98915.317848] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
Jun  6 02:11:00 ssg1 kernel: [98915.321835] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.341963] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.362171] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.382258] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.402482] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.422726] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.438957] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
Jun  6 02:11:00 ssg1 kernel: [98915.438960] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
Jun  6 02:11:00 ssg1 kernel: [98915.442945] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.463062] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.483302] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.503467] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.523668] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.543913] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.560157] iwl4965 0000:03:00.0: BSM uCode verification failed at addr 0x00003800+0 (of 788), is 0xffffffff, s/b 0xf802020
Jun  6 02:11:00 ssg1 kernel: [98915.560161] iwl4965 0000:03:00.0: Unable to set up bootstrap uCode: -5
Jun  6 02:11:00 ssg1 kernel: [98915.564144] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: last message repeated 14 times
Jun  6 02:11:00 ssg1 kernel: [98915.865516] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.885966] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.906181] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:11:00 ssg1 kernel: [98915.922378] iwl4965 0000:03:00.0: Unable to initialize device after 5 attempts.
Jun  6 02:11:00 ssg1 kernel: [98915.927785] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:01 ssg1 kernel: [98916.720677] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
Jun  6 02:11:01 ssg1 kernel: [98916.720681] cfg80211: World regulatory domain updated:
Jun  6 02:11:01 ssg1 kernel: [98916.720684] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  6 02:11:01 ssg1 kernel: [98916.720687] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  6 02:11:01 ssg1 kernel: [98916.720691] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  6 02:11:01 ssg1 kernel: [98916.720694] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  6 02:11:01 ssg1 kernel: [98916.720697] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  6 02:11:01 ssg1 kernel: [98916.720699] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  6 02:11:01 ssg1 kernel: [98916.928767] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:02 ssg1 kernel: [98917.930118] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:03 ssg1 kernel: [98918.931593] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:04 ssg1 kernel: [98919.932489] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:05 ssg1 kernel: [98920.933886] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:06 ssg1 kernel: [98921.935253] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:07 ssg1 kernel: [98922.936296] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:08 ssg1 kernel: [98923.937789] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:09 ssg1 kernel: [98924.939275] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:10 ssg1 kernel: [98925.939814] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:11 ssg1 kernel: [98926.941331] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:12 ssg1 kernel: [98927.942787] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:13 ssg1 kernel: [98928.944262] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:14 ssg1 kernel: [98929.945636] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:15 ssg1 kernel: [98930.946434] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:17 ssg1 kernel: [98932.308388] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:18 ssg1 kernel: [98933.309531] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:19 ssg1 kernel: [98934.310955] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:20 ssg1 kernel: [98935.312284] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:21 ssg1 kernel: [98936.312733] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:22 ssg1 kernel: [98937.314181] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:23 ssg1 kernel: [98938.315612] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:24 ssg1 kernel: [98939.316365] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:25 ssg1 kernel: [98940.317718] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:26 ssg1 kernel: [98941.319163] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:27 ssg1 kernel: [98942.320610] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:28 ssg1 kernel: [98943.321960] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:29 ssg1 kernel: [98944.323323] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:30 ssg1 kernel: [98945.324659] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:31 ssg1 kernel: [98946.326100] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:32 ssg1 kernel: [98947.327238] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:33 ssg1 kernel: [98948.328267] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:34 ssg1 kernel: [98949.329864] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:35 ssg1 kernel: [98950.331345] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:36 ssg1 kernel: [98951.332174] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:37 ssg1 kernel: [98952.333445] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:38 ssg1 kernel: [98953.334799] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:39 ssg1 kernel: [98954.336273] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:40 ssg1 kernel: [98955.337911] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:41 ssg1 kernel: [98956.339355] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:42 ssg1 kernel: [98957.340320] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:43 ssg1 kernel: [98958.341768] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:44 ssg1 kernel: [98959.343204] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:45 ssg1 kernel: [98960.344252] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:46 ssg1 kernel: [98961.345687] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:47 ssg1 kernel: [98962.347134] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:48 ssg1 kernel: [98963.348575] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:49 ssg1 kernel: [98964.350023] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:50 ssg1 kernel: [98965.351445] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:51 ssg1 kernel: [98966.352264] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:52 ssg1 kernel: [98967.353688] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:53 ssg1 kernel: [98968.355080] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:54 ssg1 kernel: [98969.356496] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:55 ssg1 kernel: [98970.357949] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:56 ssg1 kernel: [98971.359411] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:57 ssg1 kernel: [98972.360872] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:58 ssg1 kernel: [98973.362305] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:11:59 ssg1 kernel: [98974.363674] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:00 ssg1 kernel: [98975.364880] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:01 ssg1 kernel: [98976.365776] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:02 ssg1 kernel: [98977.367243] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:03 ssg1 kernel: [98978.368104] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:04 ssg1 kernel: [98979.369553] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:05 ssg1 kernel: [98980.370994] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:06 ssg1 kernel: [98981.372278] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:07 ssg1 kernel: [98982.373712] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:08 ssg1 kernel: [98983.375149] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:09 ssg1 kernel: [98984.376186] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:10 ssg1 kernel: [98985.377547] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:11 ssg1 kernel: [98986.378970] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:12 ssg1 kernel: [98987.380250] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:13 ssg1 kernel: [98988.381695] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:14 ssg1 kernel: [98989.383124] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:15 ssg1 kernel: [98990.384121] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:16 ssg1 kernel: [98991.384594] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:17 ssg1 kernel: [98992.386051] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:28 ssg1 kernel: [99003.751830] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:29 ssg1 kernel: [99004.752841] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:30 ssg1 kernel: [99005.754281] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:31 ssg1 kernel: [99006.755738] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:32 ssg1 kernel: [99007.756482] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:33 ssg1 kernel: [99008.757928] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:34 ssg1 kernel: [99009.759379] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:35 ssg1 kernel: [99010.760831] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:36 ssg1 kernel: [99011.762291] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:37 ssg1 kernel: [99012.763742] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:38 ssg1 kernel: [99013.764269] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:39 ssg1 kernel: [99014.765021] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:40 ssg1 kernel: [99015.766485] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:41 ssg1 kernel: [99016.767943] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:42 ssg1 kernel: [99017.769432] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:43 ssg1 kernel: [99018.770898] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:44 ssg1 kernel: [99019.772369] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:45 ssg1 kernel: [99020.773807] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:46 ssg1 kernel: [99021.775251] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:47 ssg1 kernel: [99022.776261] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:48 ssg1 kernel: [99023.777713] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:49 ssg1 kernel: [99024.779134] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:50 ssg1 kernel: [99025.780254] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:51 ssg1 kernel: [99026.781690] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:52 ssg1 kernel: [99027.783126] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:53 ssg1 kernel: [99028.784272] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:54 ssg1 kernel: [99029.785658] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:55 ssg1 kernel: [99030.787112] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:56 ssg1 kernel: [99031.788342] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:57 ssg1 kernel: [99032.789793] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:58 ssg1 kernel: [99033.791238] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:12:59 ssg1 kernel: [99034.792674] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:00 ssg1 kernel: [99035.794053] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:01 ssg1 kernel: [99036.795323] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:02 ssg1 kernel: [99037.796683] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:03 ssg1 kernel: [99038.798130] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:04 ssg1 kernel: [99039.799588] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:05 ssg1 kernel: [99040.801012] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:06 ssg1 kernel: [99041.801514] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:07 ssg1 kernel: [99042.802957] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:08 ssg1 kernel: [99043.804398] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:09 ssg1 kernel: [99044.805843] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:10 ssg1 kernel: [99045.807289] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:11 ssg1 kernel: [99046.808734] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:12 ssg1 kernel: [99047.810181] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:13 ssg1 kernel: [99048.811621] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:14 ssg1 kernel: [99049.812259] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:15 ssg1 kernel: [99050.813663] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:16 ssg1 kernel: [99051.815105] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:17 ssg1 kernel: [99052.816463] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:18 ssg1 kernel: [99053.817901] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:19 ssg1 kernel: [99054.819345] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:20 ssg1 kernel: [99055.820789] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:21 ssg1 kernel: [99056.822130] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:22 ssg1 kernel: [99057.823571] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:23 ssg1 kernel: [99058.824242] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:24 ssg1 kernel: [99059.825692] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:25 ssg1 kernel: [99060.827163] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:26 ssg1 kernel: [99061.828617] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:27 ssg1 kernel: [99062.830084] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:28 ssg1 kernel: [99063.831538] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:31 ssg1 kernel: [99066.946627] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:32 ssg1 kernel: [99067.948410] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:33 ssg1 kernel: [99068.949859] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:34 ssg1 kernel: [99069.951308] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:35 ssg1 kernel: [99070.952756] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:36 ssg1 kernel: [99071.954193] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:37 ssg1 kernel: [99072.955628] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:38 ssg1 kernel: [99073.956252] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:39 ssg1 kernel: [99074.957695] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:40 ssg1 kernel: [99075.958631] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:41 ssg1 kernel: [99076.960099] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:42 ssg1 kernel: [99077.961295] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:43 ssg1 kernel: [99078.962725] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:44 ssg1 kernel: [99079.964165] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:45 ssg1 kernel: [99080.965637] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:46 ssg1 kernel: [99081.967085] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:47 ssg1 kernel: [99082.968555] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:48 ssg1 kernel: [99083.970003] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:49 ssg1 kernel: [99084.971457] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:50 ssg1 kernel: [99085.972271] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:51 ssg1 kernel: [99086.973700] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:52 ssg1 kernel: [99087.975177] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:53 ssg1 kernel: [99088.976301] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:54 ssg1 kernel: [99089.977603] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:55 ssg1 kernel: [99090.978954] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:56 ssg1 kernel: [99091.980407] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:57 ssg1 kernel: [99092.981849] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:58 ssg1 kernel: [99093.983295] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:13:59 ssg1 kernel: [99094.984236] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:00 ssg1 kernel: [99095.985682] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:01 ssg1 kernel: [99096.987113] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:02 ssg1 kernel: [99097.988567] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:03 ssg1 kernel: [99098.990033] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:04 ssg1 kernel: [99099.991487] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:05 ssg1 kernel: [99100.992939] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:06 ssg1 kernel: [99101.994368] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:07 ssg1 kernel: [99102.995446] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:08 ssg1 kernel: [99103.996285] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:09 ssg1 kernel: [99104.997720] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:10 ssg1 kernel: [99105.999139] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:11 ssg1 kernel: [99107.000252] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:12 ssg1 kernel: [99108.001716] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:13 ssg1 kernel: [99109.003137] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:14 ssg1 kernel: [99110.004593] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:15 ssg1 kernel: [99111.006041] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:16 ssg1 kernel: [99112.007508] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:17 ssg1 kernel: [99113.008972] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:18 ssg1 kernel: [99114.010434] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:19 ssg1 kernel: [99115.011872] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:20 ssg1 kernel: [99116.012548] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:21 ssg1 kernel: [99117.013704] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:22 ssg1 kernel: [99118.015157] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:23 ssg1 kernel: [99119.016616] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:24 ssg1 kernel: [99120.018037] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:25 ssg1 kernel: [99121.019491] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:26 ssg1 kernel: [99122.020948] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:27 ssg1 kernel: [99123.022389] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:28 ssg1 kernel: [99124.023669] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:29 ssg1 kernel: [99125.025129] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:30 ssg1 kernel: [99126.026598] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:34 ssg1 kernel: [99129.835564] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:35 ssg1 kernel: [99130.837582] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:36 ssg1 kernel: [99131.839033] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:37 ssg1 kernel: [99132.840482] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:38 ssg1 kernel: [99133.841696] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:39 ssg1 kernel: [99134.843059] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:40 ssg1 kernel: [99135.844169] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:41 ssg1 kernel: [99136.845544] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:42 ssg1 kernel: [99137.847022] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:43 ssg1 kernel: [99138.848481] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:44 ssg1 kernel: [99139.849925] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:45 ssg1 kernel: [99140.851362] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:46 ssg1 kernel: [99141.852248] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:47 ssg1 kernel: [99142.853633] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:48 ssg1 kernel: [99143.855082] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:49 ssg1 kernel: [99144.856256] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:50 ssg1 kernel: [99145.857701] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:51 ssg1 kernel: [99146.859142] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:52 ssg1 kernel: [99147.860283] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:53 ssg1 kernel: [99148.861767] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:54 ssg1 kernel: [99149.862908] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:55 ssg1 kernel: [99150.863726] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:56 ssg1 kernel: [99151.864392] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:57 ssg1 kernel: [99152.865045] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:58 ssg1 kernel: [99153.866485] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:14:59 ssg1 kernel: [99154.867928] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:15:00 ssg1 kernel: [99155.869403] iwl4965 0000:03:00.0: Request scan called when driver not ready.
Jun  6 02:15:01 ssg1 kernel: [99156.796081] ------------[ cut here ]------------
Jun  6 02:15:01 ssg1 kernel: [99156.796109] WARNING: at /build/buildd/linux-3.2.0/drivers/net/wireless/iwlegacy/iwl-core.c:1436 iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]()
Jun  6 02:15:01 ssg1 kernel: [99156.796116] Hardware name: G1                  
Jun  6 02:15:01 ssg1 kernel: [99156.796119] Modules linked in: mmc_block nls_iso8859_1 nls_cp437 vfat fat xts gf128mul pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) dm_crypt nvidia(P) snd_hda_codec_si3054 snd_hda_codec_realtek pcmcia arc4 snd_hda_intel snd_hda_codec snd_usb_audio r592 iwl4965(-) snd_hwdep snd_usbmidi_lib memstick joydev asus_oled(C) yenta_socket pcmcia_rsrc btusb uvcvideo videodev snd_pcm pcmcia_core snd_seq_midi snd_seq_midi_event iwl_legacy coretemp rfcomm bnep bluetooth snd_seq parport_pc snd_rawmidi snd_timer ppdev snd_seq_device mac80211 psmouse binfmt_misc snd lp asus_laptop sparse_keymap cfg80211 soundcore snd_page_alloc input_polldev serio_raw parport mac_hid vesafb usbhid hid firewire_ohci firewire_core crc_itu_t sdhci_pci sdhci r8169 video
Jun  6 02:15:01 ssg1 kernel: [99156.796249] Pid: 13898, comm: modprobe Tainted: P         C O 3.2.0-47-generic #72-Ubuntu
Jun  6 02:15:01 ssg1 kernel: [99156.796254] Call Trace:
Jun  6 02:15:01 ssg1 kernel: [99156.796266]  [<c1563724>] ? printk+0x2d/0x2f
Jun  6 02:15:01 ssg1 kernel: [99156.796279]  [<c104b0c2>] warn_slowpath_common+0x72/0xa0
Jun  6 02:15:01 ssg1 kernel: [99156.796293]  [<f88c8119>] ? iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]
Jun  6 02:15:01 ssg1 kernel: [99156.796308]  [<f88c8119>] ? iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]
Jun  6 02:15:01 ssg1 kernel: [99156.796316]  [<c104b112>] warn_slowpath_null+0x22/0x30
Jun  6 02:15:01 ssg1 kernel: [99156.796329]  [<f88c8119>] iwl_legacy_mac_remove_interface+0x79/0x80 [iwl_legacy]
Jun  6 02:15:01 ssg1 kernel: [99156.796367]  [<f8964ff9>] ieee80211_do_stop+0x529/0x690 [mac80211]
Jun  6 02:15:01 ssg1 kernel: [99156.796377]  [<c1578776>] ? _raw_spin_unlock_bh+0x16/0x20
Jun  6 02:15:01 ssg1 kernel: [99156.796411]  [<f8965177>] ieee80211_stop+0x17/0x20 [mac80211]
Jun  6 02:15:01 ssg1 kernel: [99156.796420]  [<c147dbd9>] __dev_close_many+0x69/0xb0
Jun  6 02:15:01 ssg1 kernel: [99156.796428]  [<c1122447>] ? kfree+0xf7/0x120
Jun  6 02:15:01 ssg1 kernel: [99156.796436]  [<c129cdf5>] ? kobject_release+0x45/0x80
Jun  6 02:15:01 ssg1 kernel: [99156.796444]  [<c147dcce>] dev_close_many+0x6e/0xc0
Jun  6 02:15:01 ssg1 kernel: [99156.796451]  [<c147ddc7>] rollback_registered_many+0xa7/0x1c0
Jun  6 02:15:01 ssg1 kernel: [99156.796458]  [<c129cdb0>] ? kobject_del+0x30/0x30
Jun  6 02:15:01 ssg1 kernel: [99156.796465]  [<c147def4>] unregister_netdevice_many+0x14/0x60
Jun  6 02:15:01 ssg1 kernel: [99156.796500]  [<f89648af>] ieee80211_remove_interfaces+0x9f/0xe0 [mac80211]
Jun  6 02:15:01 ssg1 kernel: [99156.796508]  [<c1577b60>] ? down_write+0x10/0x30
Jun  6 02:15:01 ssg1 kernel: [99156.796538]  [<f895109b>] ieee80211_unregister_hw+0x4b/0x110 [mac80211]
Jun  6 02:15:01 ssg1 kernel: [99156.796554]  [<f88ce4da>] ? iwl_legacy_leds_exit+0x2a/0x3c [iwl_legacy]
Jun  6 02:15:01 ssg1 kernel: [99156.796567]  [<f95a59f4>] iwl4965_pci_remove+0x56/0x178 [iwl4965]
Jun  6 02:15:01 ssg1 kernel: [99156.796577]  [<c1371444>] ? __pm_runtime_resume+0x54/0x80
Jun  6 02:15:01 ssg1 kernel: [99156.796587]  [<c12c1318>] pci_device_remove+0x38/0xf0
Jun  6 02:15:01 ssg1 kernel: [99156.796596]  [<c1367a1b>] __device_release_driver+0x5b/0xb0
Jun  6 02:15:01 ssg1 kernel: [99156.796604]  [<c136807f>] driver_detach+0x8f/0xa0
Jun  6 02:15:01 ssg1 kernel: [99156.796611]  [<c13678f3>] bus_remove_driver+0x63/0xa0
Jun  6 02:15:01 ssg1 kernel: [99156.796619]  [<c1368718>] driver_unregister+0x48/0x80
Jun  6 02:15:01 ssg1 kernel: [99156.796629]  [<c12c0492>] pci_unregister_driver+0x32/0x90
Jun  6 02:15:01 ssg1 kernel: [99156.796642]  [<f95a5b23>] iwl4965_exit+0xd/0x4ea [iwl4965]
Jun  6 02:15:01 ssg1 kernel: [99156.796650]  [<c1085915>] sys_delete_module+0x135/0x230
Jun  6 02:15:01 ssg1 kernel: [99156.796659]  [<c110b8fa>] ? do_munmap+0x16a/0x200
Jun  6 02:15:01 ssg1 kernel: [99156.796667]  [<c15789f4>] syscall_call+0x7/0xb
Jun  6 02:15:01 ssg1 kernel: [99156.796675]  [<c1580000>] ? do_IRQ+0x10/0xc0
Jun  6 02:15:01 ssg1 kernel: [99156.796680] ---[ end trace 98456174624b5a8f ]---
Jun  6 02:15:01 ssg1 kernel: [99156.841141] iwl4965 0000:03:00.0: PCI INT A disabled
Jun  6 02:15:23 ssg1 kernel: [99179.132392] cfg80211: Calling CRDA to update world regulatory domain
Jun  6 02:15:23 ssg1 kernel: [99179.177015] cfg80211: World regulatory domain updated:
Jun  6 02:15:23 ssg1 kernel: [99179.177019] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Jun  6 02:15:23 ssg1 kernel: [99179.177022] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  6 02:15:23 ssg1 kernel: [99179.177026] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  6 02:15:23 ssg1 kernel: [99179.177029] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Jun  6 02:15:23 ssg1 kernel: [99179.177032] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  6 02:15:23 ssg1 kernel: [99179.177035] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Jun  6 02:15:23 ssg1 kernel: [99179.199494] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
Jun  6 02:15:23 ssg1 kernel: [99179.199497] iwl4965: Copyright(c) 2003-2011 Intel Corporation
Jun  6 02:15:23 ssg1 kernel: [99179.199560] iwl4965 0000:03:00.0: enabling device (0000 -> 0002)
Jun  6 02:15:23 ssg1 kernel: [99179.199572] iwl4965 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Jun  6 02:15:23 ssg1 kernel: [99179.199586] iwl4965 0000:03:00.0: setting latency timer to 64
Jun  6 02:15:23 ssg1 kernel: [99179.199618] iwl4965 0000:03:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0xFFFFFFFF
Jun  6 02:15:23 ssg1 kernel: [99179.201058] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:15:23 ssg1 kernel: [99179.224014] iwl4965 0000:03:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0xFFFFFFFF
Jun  6 02:15:23 ssg1 kernel: [99179.240642] iwl4965 0000:03:00.0: bad EEPROM signature,EEPROM_GP=0x00000007
Jun  6 02:15:23 ssg1 kernel: [99179.240654] iwl4965 0000:03:00.0: EEPROM not found, EEPROM_GP=0xffffffff
Jun  6 02:15:23 ssg1 kernel: [99179.240688] iwl4965 0000:03:00.0: Unable to init EEPROM
Jun  6 02:15:23 ssg1 kernel: [99179.241106] iwl4965 0000:03:00.0: PCI INT A disabled
Jun  6 02:15:23 ssg1 kernel: [99179.241120] iwl4965: probe of 0000:03:00.0 failed with error -2
```

Once again, only a reboot got the wireless working again. Before rebooting, I tried unloading and reloading the wireless driver module, but that failed.

On the bright side, at least these drops are not freezing my entire system, so hopefully this is just a software issue.

---

### Post by fizikz on 2013-06-07
I don't know what to make of it... the system froze again. I can't find anything in the logs that would give a hint as to the cause.

I can only suspect the freeze has something to do with the PCI bus, since it usually coincides with graphics usage (playing videos, skype video chat, scrolling a web page, etc) but I don't know for sure. As for the wireless drops that require a reboot, I have no ideas.

It's disappointing. I thought these issues were solved, but they keep recurring, although perhaps less frequently with the Intel 4965. Not sure what else to try.

---

### Post by varunendra on 2013-06-07
> **fizikz said:**
> ```
Jun  6 02:10:55 ssg1 kernel: [98911.012067] iwl4965 0000:03:00.0: Error sending REPLY_ADD_STA: time out after 500ms.
Jun  6 02:10:55 ssg1 kernel: [98911.012078] **[COLOR="#FF0000"]HW problem - can not stop rx aggregation for tid 0[/COLOR]**
Jun  6 02:10:56 ssg1 kernel: [98911.420051] **[COLOR="#FF0000"]iwl4965 0000:03:00.0: Queue 7 stuck for 2000 ms.[/COLOR]**
Jun  6 02:10:56 ssg1 kernel: [98911.420060] **[COLOR="#FF0000"]iwl4965 0000:03:00.0: On demand firmware reload[/COLOR]**
```

Apparently an old, never fixed bug in the firmware that this driver (iwl4965) uses : [https://bugzilla.redhat.com/show_bug.cgi?id=709322](https://bugzilla.redhat.com/show_bug.cgi?id=709322)

Similar issues also seem to exist in some other older intel chips and their firmware, including iwl3945. So it seems that intel never really tried to fix those bugs in their firmware *(maybe they were too preoccupied in producing & supporting newer cards)*. Accordingly, using a newer, properly supported card seems to be the only (hopefully-) permanent solution : [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

But this is just my opinion based on what all I could find in my searches. I'd be very happy, even grateful for the knowledge if someone could suggest a possibly permanent fix or workaround for the existing card.

As of now, it seems I have reached the limit of my knowledge and wits, and looking further doesn't give me any hopeful leads to work with, sorry :(

---

### Post by fizikz on 2013-06-08
An old, unfixed bug for iwl4965... not much I can do about that. Fortunately, I never experienced any bugs with the Intel 3945. I did try the Intel 5100 and 6200, and they didn't work. I've accumulated quite an assortment of wireless adapters now. All I can think of is to try an Atheros card, like the AR9280, or just live with G.

---

### Post by varunendra on 2013-06-08
> **fizikz said:**
> I did try the Intel **5100** and 6200, and they didn't work. I've accumulated quite an assortment of wireless adapters now.

Wow! I was just reading [this post]("http://ubuntuforums.org/showthread.php?t=2152478&p=12682411#post12682411") by ahallubuntu stating that -
> my **5100** card has always worked solidly in every version of Ubuntu

Maybe you should consult him on that thread or invite him at yours here (or a new one if required).

---

### Post by fizikz on 2013-06-08
For the system freezes, I don't think the issue is with Ubuntu, but rather a hardware conflict between the adapter(s) and my laptop (Asus G1). With the Intel 5100 I got system freezes in both Ubuntu and Windows XP. Same with the 6200. It's too bad, because they seemed to work fine otherwise. The 4965 only froze once (once too many) but has the wireless dropping bug. The 3945 works well but has no wireless N. I have now tested 4 generations of Intel adapters.

---

