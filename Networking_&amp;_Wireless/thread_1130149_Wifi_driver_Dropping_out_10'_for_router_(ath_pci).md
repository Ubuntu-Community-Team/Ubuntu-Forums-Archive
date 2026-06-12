---
title: "Wifi driver Dropping out 10' for router (ath_pci)"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by NoJock on 2009-04-19
The problem im having is with wifi driver in Ubuntu 9.04. 
Ubuntu 8.04 had Ar5212/ar5213 driver loaded and no problem connecting to any local wifi network. Now that i have installed 9.04 get intermittent connections and lots of dropping of the network, network driver is (ath5k_pci) never was ever droped of the network with 8.04 with the Ar5212/Ar5213 is this driver no longer supported? 


Computer HP/Compaq nx5000 Laptop all BIOS flashed up to date. Processor intel Celeron M 1300MHz, 512 ram, 60 gig,built in wifi hp w500 (Atheros chip set Ar5212A-00) hard drive.Duel booting Win_XPpro and Ubuntu 9.04

Have tested the alternative and it doesn't load, nor will it function. 

In windows there is no problem of any kind and the connection to wifi is 108mb/s to my netgear router.

It is completely awesome that an OS like Ubuntu can most of the time can just come up and run with all the drives working, just amazing!

Hope this helps Dmesg just the last section

[ 2933.319720] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 2933.331836] wlan0: authenticated
[ 2933.331842] wlan0: associate with AP 00:14:6c:a5:a3:e0
[ 2933.528044] wlan0: associate with AP 00:14:6c:a5:a3:e0
[ 2933.728160] wlan0: associate with AP 00:14:6c:a5:a3:e0
[ 2933.928142] wlan0: association with AP 00:14:6c:a5:a3:e0 timed out
[ 2941.953793] ath5k phy0: noise floor calibration failed (2412MHz)
[ 2942.445459] ath5k phy0: noise floor calibration failed (2437MHz)
[ 2961.881600] ath5k phy0: noise floor calibration failed (2432MHz)
[ 2963.321815] ath5k phy0: noise floor calibration timeout (2484MHz)
[ 3012.468573] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3012.474311] wlan0: authenticated
[ 3012.474318] wlan0: associate with AP 00:14:6c:a5:a3:e0
[ 3012.479334] wlan0: RX AssocResp from 00:14:6c:a5:a3:e0 (capab=0x431 status=0 aid=124)
[ 3012.479340] wlan0: associated
[ 3012.479952] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 3022.688138] wlan0: no IPv6 routers present
[ 3062.397849] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3067.791540] ath5k phy0: noise floor calibration failed (5755MHz)
[ 3068.071549] ath5k phy0: noise floor calibration failed (5760MHz)
[ 3068.351553] ath5k phy0: noise floor calibration failed (5765MHz)
[ 3068.631544] ath5k phy0: noise floor calibration failed (5770MHz)
[ 3068.911545] ath5k phy0: noise floor calibration failed (5775MHz)
[ 3069.191544] ath5k phy0: noise floor calibration failed (5780MHz)
[ 3069.471545] ath5k phy0: noise floor calibration failed (5785MHz)
[ 3069.751543] ath5k phy0: noise floor calibration failed (5790MHz)
[ 3070.031546] ath5k phy0: noise floor calibration failed (5795MHz)
[ 3073.892041] wlan0: No ProbeResp from current AP 00:14:6c:a5:a3:e0 - assume out of range
[ 3074.040864] __ratelimit: 1 callbacks suppressed
[ 3074.040870] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3074.125647] ath5k phy0: noise floor calibration failed (2412MHz)
[ 3074.585804] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3074.726202] ath5k phy0: noise floor calibration failed (2442MHz)
[ 3080.019566] ath5k phy0: noise floor calibration failed (5755MHz)
[ 3080.299553] ath5k phy0: noise floor calibration failed (5760MHz)
[ 3080.579543] ath5k phy0: noise floor calibration failed (5765MHz)
[ 3080.859543] ath5k phy0: noise floor calibration failed (5770MHz)
[ 3081.139546] ath5k phy0: noise floor calibration failed (5775MHz)
[ 3081.419559] ath5k phy0: noise floor calibration failed (5780MHz)
[ 3081.699544] ath5k phy0: noise floor calibration failed (5785MHz)
[ 3081.979546] ath5k phy0: noise floor calibration failed (5790MHz)
[ 3082.259530] ath5k phy0: noise floor calibration failed (5795MHz)
[ 3084.121852] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3084.123963] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3084.320139] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3084.520137] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3084.720145] wlan0: authentication with AP 00:14:6c:a5:a3:e0 timed out
[ 3089.127539] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3089.209311] ath5k phy0: noise floor calibration failed (2412MHz)
[ 3089.673614] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3089.805824] ath5k phy0: noise floor calibration failed (2442MHz)
[ 3095.400199] ath5k phy0: noise floor calibration failed (5760MHz)
[ 3095.683469] ath5k phy0: noise floor calibration failed (5765MHz)
[ 3095.963759] ath5k phy0: noise floor calibration failed (5770MHz)
[ 3096.243564] ath5k phy0: noise floor calibration failed (5775MHz)
[ 3096.523564] ath5k phy0: noise floor calibration failed (5780MHz)
[ 3096.803589] ath5k phy0: noise floor calibration failed (5785MHz)
[ 3097.083563] ath5k phy0: noise floor calibration failed (5790MHz)
[ 3097.363557] ath5k phy0: noise floor calibration failed (5795MHz)
[ 3099.225918] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3099.298242] ath5k phy0: noise floor calibration failed (2412MHz)
[ 3105.415573] __ratelimit: 2 callbacks suppressed
[ 3105.415578] ath5k phy0: noise floor calibration failed (5760MHz)
[ 3105.695477] ath5k phy0: noise floor calibration failed (5765MHz)
[ 3105.975564] ath5k phy0: noise floor calibration failed (5770MHz)
[ 3106.255563] ath5k phy0: noise floor calibration failed (5775MHz)
[ 3106.535466] ath5k phy0: noise floor calibration failed (5780MHz)
[ 3106.815563] ath5k phy0: noise floor calibration failed (5785MHz)
[ 3107.095572] ath5k phy0: noise floor calibration failed (5790MHz)
[ 3107.375467] ath5k phy0: noise floor calibration failed (5795MHz)
[ 3109.237877] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3109.284100] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3109.289268] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3109.289333] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3109.488162] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3109.688057] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3109.888064] wlan0: authentication with AP 00:14:6c:a5:a3:e0 timed out
[ 3114.040979] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3119.382950] ath5k phy0: noise floor calibration failed (2412MHz)
[ 3129.073084] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3129.078465] wlan0: authenticated
[ 3129.078471] wlan0: associate with AP 00:14:6c:a5:a3:e0
[ 3129.082412] wlan0: RX AssocResp from 00:14:6c:a5:a3:e0 (capab=0x431 status=0 aid=124)
[ 3129.082416] wlan0: associated
[ 3162.405856] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3164.322434] ath5k phy0: noise floor calibration timeout (5185MHz)
[ 3168.059557] ath5k phy0: noise floor calibration failed (5755MHz)
[ 3168.339546] ath5k phy0: noise floor calibration failed (5760MHz)
[ 3168.619543] ath5k phy0: noise floor calibration failed (5765MHz)
[ 3168.899676] ath5k phy0: noise floor calibration failed (5770MHz)
[ 3169.179544] ath5k phy0: noise floor calibration failed (5775MHz)
[ 3169.459546] ath5k phy0: noise floor calibration failed (5780MHz)
[ 3169.739546] ath5k phy0: noise floor calibration failed (5785MHz)
[ 3170.019556] ath5k phy0: noise floor calibration failed (5790MHz)
[ 3170.299544] ath5k phy0: noise floor calibration failed (5795MHz)
[ 3172.161695] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3174.160144] wlan0: No ProbeResp from current AP 00:14:6c:a5:a3:e0 - assume out of range
[ 3174.387383] ath5k phy0: noise floor calibration failed (2412MHz)
[ 3174.849804] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3180.235547] ath5k phy0: noise floor calibration failed (5755MHz)
[ 3180.515572] ath5k phy0: noise floor calibration failed (5760MHz)
[ 3180.795547] ath5k phy0: noise floor calibration failed (5765MHz)
[ 3181.075434] ath5k phy0: noise floor calibration failed (5770MHz)
[ 3181.355536] ath5k phy0: noise floor calibration failed (5775MHz)
[ 3181.635537] ath5k phy0: noise floor calibration failed (5780MHz)
[ 3181.915543] ath5k phy0: noise floor calibration failed (5785MHz)
[ 3182.195549] ath5k phy0: noise floor calibration failed (5790MHz)
[ 3182.475546] ath5k phy0: noise floor calibration failed (5795MHz)
[ 3184.340049] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3184.540140] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3184.740138] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3184.940147] wlan0: authentication with AP 00:14:6c:a5:a3:e0 timed out
[ 3190.126551] __ratelimit: 2 callbacks suppressed
[ 3190.126557] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3190.215369] ath5k phy0: noise floor calibration failed (2412MHz)
[ 3190.689789] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3190.802609] ath5k phy0: noise floor calibration failed (2442MHz)
[ 3196.331573] ath5k phy0: noise floor calibration failed (5760MHz)
[ 3196.611579] ath5k phy0: noise floor calibration failed (5765MHz)
[ 3196.891476] ath5k phy0: noise floor calibration failed (5770MHz)
[ 3197.171563] ath5k phy0: noise floor calibration failed (5775MHz)
[ 3197.451564] ath5k phy0: noise floor calibration failed (5780MHz)
[ 3197.731483] ath5k phy0: noise floor calibration failed (5785MHz)
[ 3198.011565] ath5k phy0: noise floor calibration failed (5790MHz)
[ 3198.291566] ath5k phy0: noise floor calibration failed (5795MHz)
[ 3200.153877] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3200.406721] ath5k phy0: noise floor calibration failed (2412MHz)
[ 3206.591563] __ratelimit: 5 callbacks suppressed
[ 3206.591569] ath5k phy0: noise floor calibration failed (5760MHz)
[ 3206.871572] ath5k phy0: noise floor calibration failed (5765MHz)
[ 3207.151589] ath5k phy0: noise floor calibration failed (5770MHz)
[ 3207.431573] ath5k phy0: noise floor calibration failed (5775MHz)
[ 3207.711563] ath5k phy0: noise floor calibration failed (5780MHz)
[ 3207.991476] ath5k phy0: noise floor calibration failed (5785MHz)
[ 3208.271564] ath5k phy0: noise floor calibration failed (5790MHz)
[ 3208.551573] ath5k phy0: noise floor calibration failed (5795MHz)
[ 3210.413862] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3215.040897] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3215.489664] ath5k phy0: noise floor calibration failed (2412MHz)
[ 3215.953749] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3221.544557] ath5k phy0: noise floor calibration failed (5760MHz)
[ 3221.827563] ath5k phy0: noise floor calibration failed (5765MHz)
[ 3222.107563] ath5k phy0: noise floor calibration failed (5770MHz)
[ 3222.387483] ath5k phy0: noise floor calibration failed (5775MHz)
[ 3222.667563] ath5k phy0: noise floor calibration failed (5780MHz)
[ 3222.947564] ath5k phy0: noise floor calibration failed (5785MHz)
[ 3223.227476] ath5k phy0: noise floor calibration failed (5790MHz)
[ 3223.507573] ath5k phy0: noise floor calibration failed (5795MHz)
[ 3225.369877] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3225.418546] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3225.421609] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3225.421672] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3225.620152] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3225.820154] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3226.020148] wlan0: authentication with AP 00:14:6c:a5:a3:e0 timed out
[ 3235.040980] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3235.502408] ath5k phy0: noise floor calibration failed (2412MHz)
[ 3245.193793] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3245.199180] wlan0: authenticated
[ 3245.199186] wlan0: associate with AP 00:14:6c:a5:a3:e0
[ 3245.207135] wlan0: RX AssocResp from 00:14:6c:a5:a3:e0 (capab=0x431 status=0 aid=124)
[ 3245.207139] wlan0: associated
[ 3271.624254] wlan0 direct probe responded
[ 3271.624263] wlan0: authenticate with AP 00:14:6c:a5:a3:e0
[ 3271.631727] wlan0: authenticated
[ 3271.631733] wlan0: associate with AP 00:14:6c:a5:a3:e0
[ 3271.633808] wlan0: RX ReassocResp from 00:14:6c:a5:a3:e0 (capab=0x431 status=0 aid=124)
[ 3271.633812] wlan0: associated
[ 3307.975547] ath5k phy0: noise floor calibration failed (5760MHz)
[ 3308.255546] ath5k phy0: noise floor calibration failed (5765MHz)
[ 3308.535544] ath5k phy0: noise floor calibration failed (5770MHz)
[ 3308.815543] ath5k phy0: noise floor calibration failed (5775MHz)
[ 3309.095546] ath5k phy0: noise floor calibration failed (5780MHz)
[ 3309.375545] ath5k phy0: noise floor calibration failed (5785MHz)
[ 3309.655543] ath5k phy0: noise floor calibration failed (5790MHz)
[ 3309.935566] ath5k phy0: noise floor calibration failed (5795MHz)
[ 3311.808469] ath5k phy0: noise floor calibration failed (2437MHz)
[ 3361.953584] ath5k phy0: noise floor calibration failed (2412MHz)
[ 3602.910163] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 3782.041631] ath5k phy0: noise floor calibration failed (2417MHz)
[ 4147.935546] ath5k phy0: noise floor calibration failed (5760MHz)
[ 4148.215537] ath5k phy0: noise floor calibration failed (5765MHz)
[ 4148.495546] ath5k phy0: noise floor calibration failed (5770MHz)
[ 4148.775546] ath5k phy0: noise floor calibration failed (5775MHz)
[ 4149.055546] ath5k phy0: noise floor calibration failed (5780MHz)
[ 4149.335546] ath5k phy0: noise floor calibration failed (5785MHz)
[ 4149.879527] ath5k phy0: noise floor calibration failed (5795MHz)
[ 4265.322443] ath5k phy0: noise floor calibration timeout (5205MHz)
[ 4981.953555] ath5k phy0: noise floor calibration failed (2412MHz)
[ 5101.953664] ath5k phy0: noise floor calibration failed (2412MHz)
[ 5102.061649] ath5k phy0: noise floor calibration failed (2417MHz)
[ 5221.953878] ath5k phy0: noise floor calibration failed (2412MHz)
[ 5222.061633] ath5k phy0: noise floor calibration failed (2417MHz)
[ 5341.953584] ath5k phy0: noise floor calibration failed (2412MHz)
[ 5342.062396] ath5k phy0: noise floor calibration failed (2417MHz)
[ 5461.953650] ath5k phy0: noise floor calibration failed (2412MHz)
[ 5462.072069] ath5k phy0: noise floor calibration failed (2417MHz)
[ 5581.953650] ath5k phy0: noise floor calibration failed (2412MHz)
[ 5701.953669] ath5k phy0: noise floor calibration failed (2412MHz)
[ 5732.923831] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 5733.251896] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 5821.953692] ath5k phy0: noise floor calibration failed (2412MHz)
[ 6541.953682] ath5k phy0: noise floor calibration failed (2412MHz)
[ 6661.954085] ath5k phy0: noise floor calibration failed (2412MHz)
[ 6662.061650] ath5k phy0: noise floor calibration failed (2417MHz)
[ 6902.060397] ath5k phy0: noise floor calibration failed (2417MHz)

What might be causing this problem??

---

