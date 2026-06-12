---
title: "frequent wifi disconnects in 11.04"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by deruberhanyok on 2011-08-17
Hello all.

I was running 10.10 until just recently. One of the updates I installed caused my wifi to disconnect with great frequency and randomness - sometimes multiple times a minute, other times it was barely noticeable. So I took the opportunity to just update to 11.04 and have found I have the same problem with the newer version. It's 64 bit.

I checked the syslog file and saw the following:

```

Aug 17 18:00:12 Symphony kernel: [236328.475200] rtl819x_TxCheckStuck: QueueID=0 tcb_desc->nStuckCount=8
Aug 17 18:00:12 Symphony kernel: [236328.503879] ===>tx queue is not empty:0, 3
Aug 17 18:00:12 Symphony kernel: [236328.606189] ===>tx queue is not empty:0, 3
Aug 17 18:00:13 Symphony kernel: [236329.221198] ===>tx queue is not empty:0, 3
Aug 17 18:00:13 Symphony kernel: [236329.322904] ===>tx queue is not empty:0, 3
Aug 17 18:00:13 Symphony kernel: [236329.527656] ===>tx queue is not empty:0, 3
Aug 17 18:00:13 Symphony kernel: [236329.630042] ===>tx queue is not empty:0, 3
Aug 17 18:00:13 Symphony kernel: [236329.732424] ===>tx queue is not empty:0, 3
Aug 17 18:00:14 Symphony kernel: [236329.834743] ===>tx queue is not empty:0, 3
Aug 17 18:00:14 Symphony kernel: [236330.244321] ===>tx queue is not empty:0, 3
Aug 17 18:00:14 Symphony kernel: [236330.346607] ===>tx queue is not empty:0, 3
Aug 17 18:00:14 Symphony kernel: [236330.449068] ===>tx queue is not empty:0, 3
Aug 17 18:00:14 Symphony kernel: [236330.474751] rtl819x_TxCheckStuck: QueueID=0 tcb_desc->nStuckCount=9
Aug 17 18:00:14 Symphony kernel: [236330.474758] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
Aug 17 18:00:15 Symphony kernel: [236331.474177] ieee->state is RTLLIB_LINKED
Aug 17 18:00:15 Symphony kernel: [236331.601446] =====>rtl8192_set_chan()====ch:9
Aug 17 18:00:15 Symphony kernel: [236331.612689] Associated successfully
Aug 17 18:00:15 Symphony kernel: [236331.612695] Using G rates:108
Aug 17 18:00:15 Symphony kernel: [236331.612697] Successfully associated, ht enabled
Aug 17 18:00:15 Symphony kernel: [236331.612702] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Aug 17 18:00:15 Symphony kernel: [236331.612705] =====>rtl8192_set_chan()====ch:9
Aug 17 18:00:15 Symphony kernel: [236331.622728] ===>rtl8192se_link_change():ieee->iw_mode is 2
Aug 17 18:00:15 Symphony kernel: [236331.622730] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
Aug 17 18:00:15 Symphony kernel: [236331.623736] silent reset associate
Aug 17 18:00:25 Symphony kernel: [236340.791085] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
Aug 17 18:00:51 Symphony kernel: [236367.189377] ===>rtl8192se_link_change():ieee->iw_mode is 2
Aug 17 18:00:51 Symphony kernel: [236367.246291] =====>rtl8192_set_chan()====ch:1
Aug 17 18:00:51 Symphony kernel: [236367.366054] =====>rtl8192_set_chan()====ch:2
Aug 17 18:00:51 Symphony kernel: [236367.486072] =====>rtl8192_set_chan()====ch:3
Aug 17 18:00:51 Symphony kernel: [236367.606026] =====>rtl8192_set_chan()====ch:4
Aug 17 18:00:51 Symphony kernel: [236367.725972] =====>rtl8192_set_chan()====ch:5
Aug 17 18:00:52 Symphony kernel: [236367.845985] =====>rtl8192_set_chan()====ch:6
Aug 17 18:00:52 Symphony kernel: [236367.969678] =====>rtl8192_set_chan()====ch:7
Aug 17 18:00:52 Symphony kernel: [236368.085949] =====>rtl8192_set_chan()====ch:8
Aug 17 18:00:52 Symphony kernel: [236368.205919] =====>rtl8192_set_chan()====ch:9
Aug 17 18:00:52 Symphony kernel: [236368.325897] =====>rtl8192_set_chan()====ch:10
Aug 17 18:00:52 Symphony kernel: [236368.445867] =====>rtl8192_set_chan()====ch:11
Aug 17 18:00:52 Symphony kernel: [236368.455960] rtl819xSE:No more TX desc@6, ring->idx = 34,idx = 35, skblen = 0x38 queuelen=1
Aug 17 18:00:52 Symphony kernel: [236368.565809] =====>rtl8192_set_chan()====ch:12
Aug 17 18:00:52 Symphony kernel: [236368.685784] =====>rtl8192_set_chan()====ch:13
Aug 17 18:00:53 Symphony kernel: [236368.805740] =====>rtl8192_set_chan()====ch:9
Aug 17 18:00:53 Symphony kernel: [236368.815994] ===>rtl8192se_link_change():ieee->iw_mode is 2
Aug 17 18:00:53 Symphony kernel: [236368.816001] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
Aug 17 18:00:53 Symphony kernel: [236369.660140] ===>tx queue is not empty:6, 2
Aug 17 18:00:54 Symphony kernel: [236369.865063] ====>rx ADDBAREQ from :00:1e:e5:56:b5:d2
Aug 17 18:00:54 Symphony kernel: [236369.865072] ====>to send ADDBARSP
Aug 17 18:00:54 Symphony kernel: [236369.865270] ===>tx queue is not empty:6, 3
Aug 17 18:00:54 Symphony kernel: [236370.069462] ===>tx queue is not empty:6, 3
Aug 17 18:00:54 Symphony kernel: [236370.171758] ===>tx queue is not empty:6, 3
Aug 17 18:00:54 Symphony kernel: [236370.274215] ===>tx queue is not empty:6, 3
Aug 17 18:00:54 Symphony kernel: [236370.376507] ===>tx queue is not empty:6, 3
Aug 17 18:00:54 Symphony kernel: [236370.478963] ===>tx queue is not empty:6, 3
Aug 17 18:00:54 Symphony kernel: [236370.581331] ===>tx queue is not empty:6, 3
Aug 17 18:00:54 Symphony kernel: [236370.683723] ===>tx queue is not empty:6, 3
Aug 17 18:00:55 Symphony kernel: [236370.786093] ===>tx queue is not empty:6, 3
Aug 17 18:00:55 Symphony kernel: [236370.888477] ===>tx queue is not empty:6, 3
Aug 17 18:00:55 Symphony kernel: [236370.990851] ===>tx queue is not empty:6, 3
Aug 17 18:00:55 Symphony kernel: [236371.093200] ===>tx queue is not empty:6, 3
Aug 17 18:00:55 Symphony kernel: [236371.195591] ===>tx queue is not empty:6, 3
Aug 17 18:00:55 Symphony kernel: [236371.297982] ===>tx queue is not empty:6, 3
Aug 17 18:00:55 Symphony kernel: [236371.400364] ===>tx queue is not empty:6, 3
Aug 17 18:00:55 Symphony kernel: [236371.502679] ===>tx queue is not empty:6, 3
Aug 17 18:00:55 Symphony kernel: [236371.585493] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=2
Aug 17 18:00:55 Symphony kernel: [236371.605103] ===>tx queue is not empty:6, 3
Aug 17 18:00:55 Symphony kernel: [236371.707501] ===>tx queue is not empty:6, 3
Aug 17 18:00:56 Symphony kernel: [236371.809881] ===>tx queue is not empty:6, 3
Aug 17 18:00:56 Symphony kernel: [236371.912189] ===>tx queue is not empty:6, 3
Aug 17 18:00:56 Symphony kernel: [236372.014585] ===>tx queue is not empty:6, 3
Aug 17 18:00:56 Symphony kernel: [236372.116935] ===>tx queue is not empty:6, 3
Aug 17 18:00:56 Symphony kernel: [236372.219391] ===>tx queue is not empty:6, 3
Aug 17 18:00:56 Symphony kernel: [236372.321810] ===>tx queue is not empty:6, 3
Aug 17 18:00:56 Symphony kernel: [236372.424143] ===>tx queue is not empty:6, 3
Aug 17 18:00:56 Symphony kernel: [236372.526453] ===>tx queue is not empty:6, 3
Aug 17 18:00:56 Symphony kernel: [236372.628907] ===>tx queue is not empty:6, 3
Aug 17 18:00:56 Symphony kernel: [236372.731285] ===>tx queue is not empty:6, 3
Aug 17 18:00:57 Symphony kernel: [236372.833637] ===>tx queue is not empty:6, 3
Aug 17 18:00:57 Symphony kernel: [236373.447911] ===>tx queue is not empty:6, 3
Aug 17 18:00:57 Symphony kernel: [236373.550248] ===>tx queue is not empty:6, 3
Aug 17 18:00:57 Symphony kernel: [236373.584963] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=3
Aug 17 18:00:57 Symphony kernel: [236373.652688] ===>tx queue is not empty:6, 3
Aug 17 18:00:57 Symphony kernel: [236373.755074] ===>tx queue is not empty:6, 3
Aug 17 18:00:58 Symphony kernel: [236373.857443] ===>tx queue is not empty:6, 3
Aug 17 18:00:58 Symphony kernel: [236374.574019] ===>tx queue is not empty:6, 3
Aug 17 18:00:58 Symphony kernel: [236374.676413] ===>tx queue is not empty:6, 3
Aug 17 18:00:59 Symphony kernel: [236374.778850] ===>tx queue is not empty:6, 3
Aug 17 18:00:59 Symphony kernel: [236374.881168] ===>tx queue is not empty:6, 3
Aug 17 18:00:59 Symphony kernel: [236375.093413] ===>tx queue is not empty:6, 3
Aug 17 18:00:59 Symphony kernel: [236375.495479] ===>tx queue is not empty:6, 3
Aug 17 18:00:59 Symphony kernel: [236375.584584] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=4
Aug 17 18:00:59 Symphony kernel: [236375.597752] ===>tx queue is not empty:6, 3
Aug 17 18:00:59 Symphony kernel: [236375.700390] ===>tx queue is not empty:6, 3
Aug 17 18:01:00 Symphony kernel: [236375.802525] ===>tx queue is not empty:6, 3
Aug 17 18:01:00 Symphony kernel: [236375.905007] ===>tx queue is not empty:6, 3
Aug 17 18:01:00 Symphony kernel: [236376.109707] ===>tx queue is not empty:6, 3
Aug 17 18:01:00 Symphony kernel: [236376.212054] ===>tx queue is not empty:6, 3
Aug 17 18:01:00 Symphony kernel: [236376.621663] ===>tx queue is not empty:6, 3
Aug 17 18:01:00 Symphony kernel: [236376.723997] ===>tx queue is not empty:6, 3
Aug 17 18:01:01 Symphony kernel: [236376.826410] ===>tx queue is not empty:6, 3
Aug 17 18:01:01 Symphony kernel: [236376.928730] ===>tx queue is not empty:6, 3
Aug 17 18:01:01 Symphony kernel: [236377.031117] ===>tx queue is not empty:6, 3
Aug 17 18:01:01 Symphony kernel: [236377.133943] ===>tx queue is not empty:6, 3
Aug 17 18:01:01 Symphony kernel: [236377.235933] ===>tx queue is not empty:6, 3
Aug 17 18:01:01 Symphony kernel: [236377.542996] ===>tx queue is not empty:6, 3
Aug 17 18:01:01 Symphony kernel: [236377.584097] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=5
Aug 17 18:01:01 Symphony kernel: [236377.645433] ===>tx queue is not empty:6, 3
Aug 17 18:01:01 Symphony kernel: [236377.747756] ===>tx queue is not empty:6, 3
Aug 17 18:01:02 Symphony kernel: [236377.850205] ===>tx queue is not empty:6, 3
Aug 17 18:01:02 Symphony kernel: [236377.952501] ===>tx queue is not empty:6, 3
Aug 17 18:01:02 Symphony kernel: [236378.054958] ===>tx queue is not empty:6, 3
Aug 17 18:01:02 Symphony kernel: [236378.157337] ===>tx queue is not empty:6, 3
Aug 17 18:01:02 Symphony kernel: [236378.259713] ===>tx queue is not empty:6, 3
Aug 17 18:01:03 Symphony kernel: [236379.583662] rtl819x_TxCheckStuck: QueueID=6 tcb_desc->nStuckCount=6
Aug 17 18:01:03 Symphony kernel: [236379.583670] rtl819x_ifcheck_resetornot(): TxResetType is 2, RxResetType is 0
Aug 17 18:01:04 Symphony kernel: [236380.582900] ieee->state is RTLLIB_LINKED
Aug 17 18:01:04 Symphony kernel: [236380.710186] =====>rtl8192_set_chan()====ch:9
Aug 17 18:01:04 Symphony kernel: [236380.721436] Associated successfully
Aug 17 18:01:04 Symphony kernel: [236380.721441] Using G rates:108
Aug 17 18:01:04 Symphony kernel: [236380.721444] Successfully associated, ht enabled
Aug 17 18:01:04 Symphony kernel: [236380.721448] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
Aug 17 18:01:04 Symphony kernel: [236380.721452] =====>rtl8192_set_chan()====ch:9
Aug 17 18:01:04 Symphony kernel: [236380.731475] ===>rtl8192se_link_change():ieee->iw_mode is 2
Aug 17 18:01:04 Symphony kernel: [236380.731478] rtl8192_update_cap(): WLAN_CAPABILITY_LONG_PREAMBLE
Aug 17 18:01:04 Symphony kernel: [236380.732484] silent reset associate
```

I can't make heads or tails of what most of it means, however, seeing the "txreset" and "rxreset" along with commands for setting channels and successful association notices leads me to believe I'm at least seeing notifications about the problem.

As I'm leaving the log file viewer open this continues to happen - it will issue that "silent reset" thing and all seems well, then after a little bit it starts displaying the "queue is not empty" and "txcheckstuck" lines, then does it all again.

I'm not sure where to go from here. Any suggestions as to what I could try?

---

