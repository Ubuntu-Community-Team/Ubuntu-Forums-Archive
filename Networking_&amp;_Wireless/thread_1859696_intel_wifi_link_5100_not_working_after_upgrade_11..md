---
title: "intel wifi link 5100 not working after upgrade 11.10"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by amixroed on 2011-10-14
Hi, Tried out 11.10 on USB disk and discovered the wireless card doesn't work, it picks up networks but wont connect to any, with or without password.

Currently on 11.4 and its works just fine so i'm not sure what the problem is. any ideas? could i somehow try using the drivers off 11.4 with 11.10?

note: I've been registered since 2008 but consider me a total newb.

---

### Post by arivasm on 2011-10-15
I have the same problem, from yesterday, just after upgrading to Ubuntu 11.10. I found that if I boot using the previous kernel (2.6.38-12-generic) then the problem vanishes, so in my humble opinion the root of this question is in the new kernel 3.0.4

---

### Post by rogerw05465 on 2011-10-24
> **amixroed said:**
> Hi, Tried out 11.10 on USB disk and discovered the wireless card doesn't work, it picks up networks but wont connect to any, with or without password.

Currently on 11.4 and its works just fine so i'm not sure what the problem is. any ideas? could i somehow try using the drivers off 11.4 with 11.10?

note: I've been registered since 2008 but consider me a total newb.

I had similar issues with earlier releases, and the same thing seems to have fixed it this time:
- Try "sudo modprobe -v iwlagn". Normally, this should start the wireless. At first, it failed, with a message  that said to look at dmesg for info. 
- I typed "dmesg" at the prompt. The last line told me that there was a command that the system was unable to interpret. The command was in the config file for the wireless: /etc/modprobe.d/iwlagn.conf. It told me the actual command in that config file that the system didn't understand.
- Check /etc/modprobe.d/iwlagn.conf  via "sudo gedit /etc/modprobe.d/iwlagn.conf"
- See if there is a line such as "options iwlagn disable_hw_scan=1", or one that showed up in the dmesg.
- Block that faulty command by inserting a "#" in front of the line the system doesn't understand. Save the file
- Run "sudo modprobe -r -v iwlagn". This is the command to stop the wireless. Do this so you know it is properly stopped
- Then run "sudo modprobe -v iwlagn". This should reload the driver and start the wireless. At least, it did for me. Bon chance!

---

### Post by billathome65 on 2012-01-09
I've got the same problem using Acer 5735 lappy i'm running the os from cd to evaluate before installing as a duel operating system I can access the internet with it wired but not wirless?

It finds the network no problem and when I add the password just says connecting but wont connect? I tried the prompts in last post and just got the command prompt again?

I typed dmesg and got this:

r uses its own custom regulatory domain 
[ 2265.360784] cfg80211: World regulatory domain updated:
[ 2265.360787] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2265.360793] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2265.360798] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2265.360803] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2265.360808] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2265.360813] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2268.683304] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 2268.685476] wlan0: authenticated
[ 2268.686814] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 2268.691832] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 2268.691839] wlan0: associated
[ 2274.774600] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 2274.788699] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2274.788706] cfg80211: Restoring regulatory settings
[ 2274.788717] cfg80211: Calling CRDA to update world regulatory domain
[ 2274.794655] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 2274.794661] cfg80211: World regulatory domain updated:
[ 2274.794665] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2274.794670] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2274.794676] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2274.794680] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2274.794685] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2274.794690] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2278.160272] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 2278.162337] wlan0: authenticated
[ 2278.166953] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 2278.171906] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 2278.171910] wlan0: associated
[ 2284.248787] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 2284.257096] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2284.257102] cfg80211: Restoring regulatory settings
[ 2284.257108] cfg80211: Calling CRDA to update world regulatory domain
[ 2284.262038] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 2284.262046] cfg80211: World regulatory domain updated:
[ 2284.262050] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2284.262055] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2284.262060] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2284.262065] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2284.262070] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2284.262075] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2287.562474] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 2287.564667] wlan0: authenticated
[ 2287.571199] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 2287.576945] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 2287.576949] wlan0: associated
[ 2293.644493] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 2293.650470] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2293.650478] cfg80211: Restoring regulatory settings
[ 2293.650485] cfg80211: Calling CRDA to update world regulatory domain
[ 2293.657010] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 2293.657017] cfg80211: World regulatory domain updated:
[ 2293.657025] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2293.657031] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2293.657036] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2293.657041] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2293.657046] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2293.657051] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2297.001118] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 2297.003192] wlan0: authenticated
[ 2297.006425] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 2297.012838] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 2297.012846] wlan0: associated
[ 2303.091736] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 2303.102672] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2303.102680] cfg80211: Restoring regulatory settings
[ 2303.102686] cfg80211: Calling CRDA to update world regulatory domain
[ 2303.108955] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 2303.108961] cfg80211: World regulatory domain updated:
[ 2303.108964] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2303.108970] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2303.108975] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2303.108980] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2303.108985] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2303.108990] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2306.473069] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 2306.477344] wlan0: authenticated
[ 2306.480936] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 2306.487828] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 2306.487836] wlan0: associated
[ 2307.004539] wlan0: deauthenticating from 00:26:91:f7:80:b2 by local choice (reason=3)
[ 2307.030098] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 2307.030105] cfg80211: Restoring regulatory settings
[ 2307.030114] cfg80211: Calling CRDA to update world regulatory domain
[ 2307.034890] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 2307.034895] cfg80211: World regulatory domain updated:
[ 2307.034897] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2307.034900] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2307.034903] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2307.034906] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2307.034909] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2307.034912] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3082.339136] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3082.341240] wlan0: authenticated
[ 3082.356776] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3082.361771] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3082.361775] wlan0: associated
[ 3088.434200] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3088.441826] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3088.441836] cfg80211: Restoring regulatory settings
[ 3088.441843] cfg80211: Calling CRDA to update world regulatory domain
[ 3088.448326] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3088.448333] cfg80211: World regulatory domain updated:
[ 3088.448336] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3088.448342] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3088.448347] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3088.448352] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3088.448357] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3088.448362] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3091.756286] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3091.758642] wlan0: authenticated
[ 3091.761641] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3091.766598] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3091.766605] wlan0: associated
[ 3097.843106] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3097.854520] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3097.854529] cfg80211: Restoring regulatory settings
[ 3097.854536] cfg80211: Calling CRDA to update world regulatory domain
[ 3097.860801] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3097.860807] cfg80211: World regulatory domain updated:
[ 3097.860811] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3097.860816] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3097.860822] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3097.860827] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3097.860832] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3097.860837] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3101.238817] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3101.245104] wlan0: authenticated
[ 3101.246272] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3101.251197] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3101.251200] wlan0: associated
[ 3107.332217] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3107.357186] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3107.357194] cfg80211: Restoring regulatory settings
[ 3107.357202] cfg80211: Calling CRDA to update world regulatory domain
[ 3107.365846] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3107.365855] cfg80211: World regulatory domain updated:
[ 3107.365858] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3107.365864] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3107.365869] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3107.365874] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3107.365879] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3107.365884] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3110.596628] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3110.598889] wlan0: authenticated
[ 3110.602609] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3110.607579] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3110.607586] wlan0: associated
[ 3116.691245] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3116.716767] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3116.716775] cfg80211: Restoring regulatory settings
[ 3116.716786] cfg80211: Calling CRDA to update world regulatory domain
[ 3116.723458] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3116.723465] cfg80211: World regulatory domain updated:
[ 3116.723468] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3116.723474] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3116.723479] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3116.723484] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3116.723489] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3116.723494] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3120.020992] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3120.024459] wlan0: authenticated
[ 3120.028779] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3120.033749] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3120.033754] wlan0: associated
[ 3126.110349] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3126.116858] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3126.116866] cfg80211: Restoring regulatory settings
[ 3126.116873] cfg80211: Calling CRDA to update world regulatory domain
[ 3126.123564] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3126.123572] cfg80211: World regulatory domain updated:
[ 3126.123576] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3126.123581] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3126.123586] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3126.123592] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3126.123596] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3126.123601] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3129.441412] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3129.446526] wlan0: authenticated
[ 3129.447851] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3129.452789] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3129.452795] wlan0: associated
[ 3135.530472] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3135.553895] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3135.553908] cfg80211: Restoring regulatory settings
[ 3135.553915] cfg80211: Calling CRDA to update world regulatory domain
[ 3135.560996] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3135.561004] cfg80211: World regulatory domain updated:
[ 3135.561007] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3135.561013] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3135.561018] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3135.561023] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3135.561028] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3135.561033] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3138.873103] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3138.875906] wlan0: authenticated
[ 3138.877197] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3138.882145] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3138.882155] wlan0: associated
[ 3139.013131] wlan0: deauthenticating from 00:26:91:f7:80:b2 by local choice (reason=3)
[ 3139.029824] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3139.029854] cfg80211: Restoring regulatory settings
[ 3139.029874] cfg80211: Calling CRDA to update world regulatory domain
[ 3139.033894] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3139.033898] cfg80211: World regulatory domain updated:
[ 3139.033900] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3139.033904] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3139.033907] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3139.033910] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3139.033913] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3139.033916] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3145.617175] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3145.619491] wlan0: authenticated
[ 3145.621122] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3145.624590] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3145.624597] wlan0: associated
[ 3151.704782] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3151.712839] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3151.712848] cfg80211: Restoring regulatory settings
[ 3151.712857] cfg80211: Calling CRDA to update world regulatory domain
[ 3151.719974] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3151.719981] cfg80211: World regulatory domain updated:
[ 3151.719985] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3151.719991] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3151.719996] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3151.720026] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3151.720032] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3151.720038] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3155.038058] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3155.042367] wlan0: authenticated
[ 3155.044393] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3155.049381] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3155.049387] wlan0: associated
[ 3161.133700] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3161.148797] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3161.148831] cfg80211: Restoring regulatory settings
[ 3161.148835] cfg80211: Calling CRDA to update world regulatory domain
[ 3161.153143] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3161.153153] cfg80211: World regulatory domain updated:
[ 3161.153156] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3161.153159] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3161.153162] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3161.153167] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3161.153169] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3161.153172] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3164.509277] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3164.511371] wlan0: authenticated
[ 3164.513057] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3164.518049] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3164.518055] wlan0: associated
[ 3170.601603] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3170.625199] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3170.625207] cfg80211: Restoring regulatory settings
[ 3170.625214] cfg80211: Calling CRDA to update world regulatory domain
[ 3170.632232] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3170.632239] cfg80211: World regulatory domain updated:
[ 3170.632243] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3170.632248] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3170.632253] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3170.632258] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3170.632263] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3170.632268] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3173.981639] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3173.983963] wlan0: authenticated
[ 3173.985429] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3173.990576] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3173.990583] wlan0: associated
[ 3180.074004] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3180.097070] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3180.097076] cfg80211: Restoring regulatory settings
[ 3180.097080] cfg80211: Calling CRDA to update world regulatory domain
[ 3180.101151] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3180.101155] cfg80211: World regulatory domain updated:
[ 3180.101157] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3180.101161] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3180.101164] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3180.101167] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3180.101170] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3180.101173] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3183.507282] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3183.510598] wlan0: authenticated
[ 3183.514573] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3183.519544] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3183.519548] wlan0: associated
[ 3189.601019] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3189.623486] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3189.623496] cfg80211: Restoring regulatory settings
[ 3189.623503] cfg80211: Calling CRDA to update world regulatory domain
[ 3189.630016] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3189.630023] cfg80211: World regulatory domain updated:
[ 3189.630026] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3189.630033] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3189.630038] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3189.630043] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3189.630048] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3189.630053] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3192.925065] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3192.927171] wlan0: authenticated
[ 3192.930325] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3192.935768] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3192.935775] wlan0: associated
[ 3199.020062] wlan0: deauthenticated from 00:26:91:f7:80:b2 (Reason: 2)
[ 3199.038304] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3199.038313] cfg80211: Restoring regulatory settings
[ 3199.038320] cfg80211: Calling CRDA to update world regulatory domain
[ 3199.044884] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3199.044891] cfg80211: World regulatory domain updated:
[ 3199.044895] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3199.044900] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3199.044906] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3199.044911] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3199.044916] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3199.044921] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3202.416049] wlan0: authenticate with 00:26:91:f7:80:b2 (try 1)
[ 3202.419909] wlan0: authenticated
[ 3202.432236] wlan0: associate with 00:26:91:f7:80:b2 (try 1)
[ 3202.437225] wlan0: RX ReassocResp from 00:26:91:f7:80:b2 (capab=0x431 status=0 aid=1)
[ 3202.437230] wlan0: associated
[ 3203.018121] wlan0: deauthenticating from 00:26:91:f7:80:b2 by local choice (reason=3)
[ 3203.048897] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 3203.048930] cfg80211: Restoring regulatory settings
[ 3203.048952] cfg80211: Calling CRDA to update world regulatory domain
[ 3203.053347] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[ 3203.053351] cfg80211: World regulatory domain updated:
[ 3203.053353] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 3203.053357] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3203.053360] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3203.053363] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 3203.053366] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 3203.053369] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
ubuntu@ubuntu:~$ 

Now i'm lost any ideas?

---

