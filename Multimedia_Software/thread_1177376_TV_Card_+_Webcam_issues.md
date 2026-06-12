---
title: "TV Card + Webcam issues"
date: 2009-06-03
forum: Multimedia Software
---

### Post by nengracia on 2009-06-03
I have a WinFast TV2000 XP installed and it works perfectly well with the aid of this thread: [http://ubuntuforums.org/showthread.php?t=647129&highlight=winfast+tv2000+xp](http://ubuntuforums.org/showthread.php?t=647129&highlight=winfast+tv2000+xp). The card works perfectly well and I can watch TV perfectly fine.

Here's the problem: When I plugin my usb webcam and try it out, it doesn't work. Then, on reboot, the camera works well but the TV doesn't.

When I boot with the webcam unplugged, TV works again. Can someone figure out what's the problem? With TV alone, there is a file called video0 under /dev. When I plugin the webcam, file video1 is created.

Need help. Thanks.

---

### Post by lovinglinux on 2009-06-03
I think they both are trying to use the /dev/video0 device, so whichever is loaded first will work and the other won't. This happened to me with an USB mic and the audio from the TV.

I don't know how to fix it, but there must be a way to set the webcam to use /dev/video1

---

### Post by dimis80 on 2009-06-03
I have the same issue with my logitech Web cam and the asus 7131 hybrid card...

I fixed though the conf file of TVTIME to load from video1

It loads Ok but i have no signal...

check out my dmseg:
```
[96534.388814] zc3xx: probe 2wr ov vga 0x0000
[96536.507851] zc3xx: probe 2wr ov vga 0x0000
[96538.587887] zc3xx: probe 2wr ov vga 0x0000
[96540.671922] zc3xx: probe 2wr ov vga 0x0000
[96542.751956] zc3xx: probe 2wr ov vga 0x0000
[96544.839996] zc3xx: probe 2wr ov vga 0x0000
[96546.927033] zc3xx: probe 2wr ov vga 0x0000
[96549.016071] zc3xx: probe 2wr ov vga 0x0000
[96551.095101] zc3xx: probe 2wr ov vga 0x0000
[96553.183140] zc3xx: probe 2wr ov vga 0x0000
[96555.275176] zc3xx: probe 2wr ov vga 0x0000
[96557.359211] zc3xx: probe 2wr ov vga 0x0000
[96559.443248] zc3xx: probe 2wr ov vga 0x0000
[96561.539283] zc3xx: probe 2wr ov vga 0x0000
[96563.628318] zc3xx: probe 2wr ov vga 0x0000
[96565.711355] zc3xx: probe 2wr ov vga 0x0000
[96567.795390] zc3xx: probe 2wr ov vga 0x0000
[96569.888428] zc3xx: probe 2wr ov vga 0x0000
[96571.979462] zc3xx: probe 2wr ov vga 0x0000
[96574.067501] zc3xx: probe 2wr ov vga 0x0000
[96576.155534] zc3xx: probe 2wr ov vga 0x0000
[96578.255573] zc3xx: probe 2wr ov vga 0x0000
[96580.339609] zc3xx: probe 2wr ov vga 0x0000
[96582.427644] zc3xx: probe 2wr ov vga 0x0000
[96584.515682] zc3xx: probe 2wr ov vga 0x0000
[96586.599717] zc3xx: probe 2wr ov vga 0x0000
[96588.691753] zc3xx: probe 2wr ov vga 0x0000
[96590.787790] zc3xx: probe 2wr ov vga 0x0000
[96592.871824] zc3xx: probe 2wr ov vga 0x0000
[96594.951860] zc3xx: probe 2wr ov vga 0x0000
[96597.039895] zc3xx: probe 2wr ov vga 0x0000
[96599.131933] zc3xx: probe 2wr ov vga 0x0000
[96601.195969] zc3xx: probe 2wr ov vga 0x0000
[96603.280003] zc3xx: probe 2wr ov vga 0x0000
[96605.372040] zc3xx: probe 2wr ov vga 0x0000
[96607.459076] zc3xx: probe 2wr ov vga 0x0000
[96609.544112] zc3xx: probe 2wr ov vga 0x0000
[96611.619149] zc3xx: probe 2wr ov vga 0x0000
[96613.703185] zc3xx: probe 2wr ov vga 0x0000
[96615.779220] zc3xx: probe 2wr ov vga 0x0000
[96617.875258] zc3xx: probe 2wr ov vga 0x0000
[96619.975293] zc3xx: probe 2wr ov vga 0x0000
[96622.051329] zc3xx: probe 2wr ov vga 0x0000
[96624.139366] zc3xx: probe 2wr ov vga 0x0000
[96626.228418] zc3xx: probe 2wr ov vga 0x0000
[96628.315437] zc3xx: probe 2wr ov vga 0x0000
[96630.404474] zc3xx: probe 2wr ov vga 0x0000
[96632.503512] zc3xx: probe 2wr ov vga 0x0000
[96636.087570] zc3xx: probe 2wr ov vga 0x0000
[96638.043605] zc3xx: probe 2wr ov vga 0x0000
[96640.131642] zc3xx: probe 2wr ov vga 0x0000
[96642.223681] zc3xx: probe 2wr ov vga 0x0000
[96644.307716] zc3xx: probe 2wr ov vga 0x0000
[96646.395748] zc3xx: probe 2wr ov vga 0x0000
[96648.483787] zc3xx: probe 2wr ov vga 0x0000
[96650.567823] zc3xx: probe 2wr ov vga 0x0000
[96652.651859] zc3xx: probe 2wr ov vga 0x0000
[96654.739894] zc3xx: probe 2wr ov vga 0x0000
[96656.827931] zc3xx: probe 2wr ov vga 0x0000
[96658.911964] zc3xx: probe 2wr ov vga 0x0000
[96660.996003] zc3xx: probe 2wr ov vga 0x0000
[96663.096042] zc3xx: probe 2wr ov vga 0x0000
[96665.187075] zc3xx: probe 2wr ov vga 0x0000
[96667.287112] zc3xx: probe 2wr ov vga 0x0000
[96669.387146] zc3xx: probe 2wr ov vga 0x0000
[96671.460184] zc3xx: probe 2wr ov vga 0x0000
[96673.544023] zc3xx: probe 2wr ov vga 0x0000
[96675.627255] zc3xx: probe 2wr ov vga 0x0000
[96677.715290] zc3xx: probe 2wr ov vga 0x0000
[96679.803328] zc3xx: probe 2wr ov vga 0x0000
[96681.875364] zc3xx: probe 2wr ov vga 0x0000
[96683.955398] zc3xx: probe 2wr ov vga 0x0000
[96686.047438] zc3xx: probe 2wr ov vga 0x0000
[96688.132471] zc3xx: probe 2wr ov vga 0x0000
[96690.216509] zc3xx: probe 2wr ov vga 0x0000
[96692.303545] zc3xx: probe 2wr ov vga 0x0000
[96694.391580] zc3xx: probe 2wr ov vga 0x0000
[96696.475615] zc3xx: probe 2wr ov vga 0x0000
[96698.567654] zc3xx: probe 2wr ov vga 0x0000
[96700.659687] zc3xx: probe 2wr ov vga 0x0000
[96702.747724] zc3xx: probe 2wr ov vga 0x0000
[96704.839760] zc3xx: probe 2wr ov vga 0x0000
[96706.923796] zc3xx: probe 2wr ov vga 0x0000
[96709.027833] zc3xx: probe 2wr ov vga 0x0000
[96711.111868] zc3xx: probe 2wr ov vga 0x0000
[96713.199905] zc3xx: probe 2wr ov vga 0x0000
[96715.287942] zc3xx: probe 2wr ov vga 0x0000
[96717.371977] zc3xx: probe 2wr ov vga 0x0000
[96719.456017] zc3xx: probe 2wr ov vga 0x0000
[96721.547050] zc3xx: probe 2wr ov vga 0x0000
[96723.636086] zc3xx: probe 2wr ov vga 0x0000
[96725.727121] zc3xx: probe 2wr ov vga 0x0000
[96727.811159] zc3xx: probe 2wr ov vga 0x0000
[96729.899192] zc3xx: probe 2wr ov vga 0x0000
[96731.988232] zc3xx: probe 2wr ov vga 0x0000
[96734.079267] zc3xx: probe 2wr ov vga 0x0000
[96736.164303] zc3xx: probe 2wr ov vga 0x0000
[96738.259339] zc3xx: probe 2wr ov vga 0x0000
[96740.351372] zc3xx: probe 2wr ov vga 0x0000
[96742.432411] zc3xx: probe 2wr ov vga 0x0000
[96744.547446] zc3xx: probe 2wr ov vga 0x0000
[96746.639484] zc3xx: probe 2wr ov vga 0x0000
[96748.740520] zc3xx: probe 2wr ov vga 0x0000
[96750.819557] zc3xx: probe 2wr ov vga 0x0000
[96752.907592] zc3xx: probe 2wr ov vga 0x0000
[96754.999627] zc3xx: probe 2wr ov vga 0x0000
[96757.091664] zc3xx: probe 2wr ov vga 0x0000
[96759.179699] zc3xx: probe 2wr ov vga 0x0000
[96761.263736] zc3xx: probe 2wr ov vga 0x0000
[96763.355774] zc3xx: probe 2wr ov vga 0x0000
[96765.443808] zc3xx: probe 2wr ov vga 0x0000
[96767.547844] zc3xx: probe 2wr ov vga 0x0000
[96769.643881] zc3xx: probe 2wr ov vga 0x0000
[96771.727917] zc3xx: probe 2wr ov vga 0x0000
[96773.819954] zc3xx: probe 2wr ov vga 0x0000
[96775.911990] zc3xx: probe 2wr ov vga 0x0000
[96778.004027] zc3xx: probe 2wr ov vga 0x0000
[96780.087062] zc3xx: probe 2wr ov vga 0x0000
[96782.175098] zc3xx: probe 2wr ov vga 0x0000
[96784.267134] zc3xx: probe 2wr ov vga 0x0000
[96786.339170] zc3xx: probe 2wr ov vga 0x0000
[96788.427206] zc3xx: probe 2wr ov vga 0x0000
[96790.511241] zc3xx: probe 2wr ov vga 0x0000
[96792.595281] zc3xx: probe 2wr ov vga 0x0000
[96794.679313] zc3xx: probe 2wr ov vga 0x0000
[96796.767350] zc3xx: probe 2wr ov vga 0x0000
[96798.851386] zc3xx: probe 2wr ov vga 0x0000
[96800.935422] zc3xx: probe 2wr ov vga 0x0000
[96803.023458] zc3xx: probe 2wr ov vga 0x0000
[96805.108494] zc3xx: probe 2wr ov vga 0x0000
[96807.215529] zc3xx: probe 2wr ov vga 0x0000
[96809.311566] zc3xx: probe 2wr ov vga 0x0000
[96811.399603] zc3xx: probe 2wr ov vga 0x0000
[96813.483640] zc3xx: probe 2wr ov vga 0x0000
[96815.575675] zc3xx: probe 2wr ov vga 0x0000
[96817.663711] zc3xx: probe 2wr ov vga 0x0000
[96819.755747] zc3xx: probe 2wr ov vga 0x0000
[96821.843784] zc3xx: probe 2wr ov vga 0x0000
[96823.939821] zc3xx: probe 2wr ov vga 0x0000
[96826.019856] zc3xx: probe 2wr ov vga 0x0000
[96828.103892] zc3xx: probe 2wr ov vga 0x0000
[96830.179929] zc3xx: probe 2wr ov vga 0x0000
[96832.263962] zc3xx: probe 2wr ov vga 0x0000
[96834.360000] zc3xx: probe 2wr ov vga 0x0000
[96836.452036] zc3xx: probe 2wr ov vga 0x0000
[96838.539072] zc3xx: probe 2wr ov vga 0x0000
[96840.627109] zc3xx: probe 2wr ov vga 0x0000
[96842.719145] zc3xx: probe 2wr ov vga 0x0000
[96844.811181] zc3xx: probe 2wr ov vga 0x0000
[96846.916216] zc3xx: probe 2wr ov vga 0x0000
[96849.023255] zc3xx: probe 2wr ov vga 0x0000
[96851.111288] zc3xx: probe 2wr ov vga 0x0000
[96853.191326] zc3xx: probe 2wr ov vga 0x0000
[96855.288362] zc3xx: probe 2wr ov vga 0x0000
[96857.384400] zc3xx: probe 2wr ov vga 0x0000
[96859.468434] zc3xx: probe 2wr ov vga 0x0000
[96861.551469] zc3xx: probe 2wr ov vga 0x0000
[96863.635506] zc3xx: probe 2wr ov vga 0x0000
[96865.723542] zc3xx: probe 2wr ov vga 0x0000
[96867.811579] zc3xx: probe 2wr ov vga 0x0000
[96869.899613] zc3xx: probe 2wr ov vga 0x0000
[96871.991652] zc3xx: probe 2wr ov vga 0x0000
[96874.075687] zc3xx: probe 2wr ov vga 0x0000
[96876.171724] zc3xx: probe 2wr ov vga 0x0000
[96878.259758] zc3xx: probe 2wr ov vga 0x0000
[96880.347795] zc3xx: probe 2wr ov vga 0x0000
[96882.439830] zc3xx: probe 2wr ov vga 0x0000
[96884.523867] zc3xx: probe 2wr ov vga 0x0000
[96886.607903] zc3xx: probe 2wr ov vga 0x0000
[96888.695940] zc3xx: probe 2wr ov vga 0x0000
[96890.787976] zc3xx: probe 2wr ov vga 0x0000
[96892.872015] zc3xx: probe 2wr ov vga 0x0000
[96894.963047] zc3xx: probe 2wr ov vga 0x0000
[96897.067084] zc3xx: probe 2wr ov vga 0x0000
[96899.176120] zc3xx: probe 2wr ov vga 0x0000
[96901.291154] zc3xx: probe 2wr ov vga 0x0000
[96903.375193] zc3xx: probe 2wr ov vga 0x0000
[96905.464231] zc3xx: probe 2wr ov vga 0x0000
[96907.559266] zc3xx: probe 2wr ov vga 0x0000
[96909.639302] zc3xx: probe 2wr ov vga 0x0000
[96911.723336] zc3xx: probe 2wr ov vga 0x0000
[96913.811372] zc3xx: probe 2wr ov vga 0x0000
[96915.895409] zc3xx: probe 2wr ov vga 0x0000
[96917.975446] zc3xx: probe 2wr ov vga 0x0000
[96920.059480] zc3xx: probe 2wr ov vga 0x0000
[96922.151517] zc3xx: probe 2wr ov vga 0x0000
[96924.231554] zc3xx: probe 2wr ov vga 0x0000
[96926.319590] zc3xx: probe 2wr ov vga 0x0000
[96928.407626] zc3xx: probe 2wr ov vga 0x0000
[96930.495662] zc3xx: probe 2wr ov vga 0x0000
[96932.583697] zc3xx: probe 2wr ov vga 0x0000
[96934.679734] zc3xx: probe 2wr ov vga 0x0000
[96936.763771] zc3xx: probe 2wr ov vga 0x0000
[96938.847806] zc3xx: probe 2wr ov vga 0x0000
[96940.931841] zc3xx: probe 2wr ov vga 0x0000
[96943.015878] zc3xx: probe 2wr ov vga 0x0000
[96945.107914] zc3xx: probe 2wr ov vga 0x0000
[96947.199951] zc3xx: probe 2wr ov vga 0x0000
[96949.287985] zc3xx: probe 2wr ov vga 0x0000
[96951.383023] zc3xx: probe 2wr ov vga 0x0000
[96953.476062] zc3xx: probe 2wr ov vga 0x0000
[96955.563097] zc3xx: probe 2wr ov vga 0x0000
[96957.659131] zc3xx: probe 2wr ov vga 0x0000
[96959.743168] zc3xx: probe 2wr ov vga 0x0000
[97418.804105] zc3xx: probe 2wr ov vga 0x0000
[97420.764139] zc3xx: probe 2wr ov vga 0x0000
[97422.856176] zc3xx: probe 2wr ov vga 0x0000
[97424.963211] zc3xx: probe 2wr ov vga 0x0000
[97427.067248] zc3xx: probe 2wr ov vga 0x0000
[97429.187289] zc3xx: probe 2wr ov vga 0x0000
[97431.279324] zc3xx: probe 2wr ov vga 0x0000
[97433.379356] zc3xx: probe 2wr ov vga 0x0000
[97435.447396] zc3xx: probe 2wr ov vga 0x0000
[97437.540433] zc3xx: probe 2wr ov vga 0x0000
[97439.635468] zc3xx: probe 2wr ov vga 0x0000
[97441.728512] zc3xx: probe 2wr ov vga 0x0000
[97443.827543] zc3xx: probe 2wr ov vga 0x0000
[97445.887576] zc3xx: probe 2wr ov vga 0x0000
[97447.983614] zc3xx: probe 2wr ov vga 0x0000
[97450.083651] zc3xx: probe 2wr ov vga 0x0000
[97452.167687] zc3xx: probe 2wr ov vga 0x0000
[97454.255722] zc3xx: probe 2wr ov vga 0x0000
[97456.355760] zc3xx: probe 2wr ov vga 0x0000
[97458.475797] zc3xx: probe 2wr ov vga 0x0000
[97460.587834] zc3xx: probe 2wr ov vga 0x0000
[97462.671865] zc3xx: probe 2wr ov vga 0x0000
[97464.771907] zc3xx: probe 2wr ov vga 0x0000
[97466.903944] zc3xx: probe 2wr ov vga 0x0000
[97468.971982] zc3xx: probe 2wr ov vga 0x0000
[97471.040019] zc3xx: probe 2wr ov vga 0x0000
[97473.136053] zc3xx: probe 2wr ov vga 0x0000
[97475.248090] zc3xx: probe 2wr ov vga 0x0000
[97477.339125] zc3xx: probe 2wr ov vga 0x0000
[97479.447162] zc3xx: probe 2wr ov vga 0x0000
[97481.547199] zc3xx: probe 2wr ov vga 0x0000
[97483.664237] zc3xx: probe 2wr ov vga 0x0000
[97485.740274] zc3xx: probe 2wr ov vga 0x0000
[97487.839310] zc3xx: probe 2wr ov vga 0x0000
[97489.912347] zc3xx: probe 2wr ov vga 0x0000
[97492.001384] zc3xx: probe 2wr ov vga 0x0000
[97494.099420] zc3xx: probe 2wr ov vga 0x0000
[97496.184458] zc3xx: probe 2wr ov vga 0x0000
[97498.287491] zc3xx: probe 2wr ov vga 0x0000
[97500.359527] zc3xx: probe 2wr ov vga 0x0000
[97502.463563] zc3xx: probe 2wr ov vga 0x0000
[97504.547601] zc3xx: probe 2wr ov vga 0x0000
[97506.639638] zc3xx: probe 2wr ov vga 0x0000
[97508.723673] zc3xx: probe 2wr ov vga 0x0000
[97510.811709] zc3xx: probe 2wr ov vga 0x0000
[97512.903747] zc3xx: probe 2wr ov vga 0x0000
[97515.003785] zc3xx: probe 2wr ov vga 0x0000
[97517.095820] zc3xx: probe 2wr ov vga 0x0000
[97519.187856] zc3xx: probe 2wr ov vga 0x0000
[97521.303893] zc3xx: probe 2wr ov vga 0x0000
[97523.375929] zc3xx: probe 2wr ov vga 0x0000
[97525.455967] zc3xx: probe 2wr ov vga 0x0000
[97527.556007] zc3xx: probe 2wr ov vga 0x0000
[97529.656041] zc3xx: probe 2wr ov vga 0x0000
[97531.743077] zc3xx: probe 2wr ov vga 0x0000
[97533.819112] zc3xx: probe 2wr ov vga 0x0000
[97535.912147] zc3xx: probe 2wr ov vga 0x0000
[97538.027186] zc3xx: probe 2wr ov vga 0x0000
[97540.115222] zc3xx: probe 2wr ov vga 0x0000
[97542.211257] zc3xx: probe 2wr ov vga 0x0000
[97544.291294] zc3xx: probe 2wr ov vga 0x0000
[97546.395330] zc3xx: probe 2wr ov vga 0x0000
[97548.507368] zc3xx: probe 2wr ov vga 0x0000
[97550.603404] zc3xx: probe 2wr ov vga 0x0000
[97552.692441] zc3xx: probe 2wr ov vga 0x0000
[97554.803475] zc3xx: probe 2wr ov vga 0x0000
[97556.892514] zc3xx: probe 2wr ov vga 0x0000
[97558.987550] zc3xx: probe 2wr ov vga 0x0000
[97561.119592] zc3xx: probe 2wr ov vga 0x0000
[97563.219625] zc3xx: probe 2wr ov vga 0x0000
[97565.323661] zc3xx: probe 2wr ov vga 0x0000
[97567.419699] zc3xx: probe 2wr ov vga 0x0000
[97569.515732] zc3xx: probe 2wr ov vga 0x0000
[97571.615772] zc3xx: probe 2wr ov vga 0x0000
[97573.707805] zc3xx: probe 2wr ov vga 0x0000
[97575.807841] zc3xx: probe 2wr ov vga 0x0000
[97577.911880] zc3xx: probe 2wr ov vga 0x0000
[97579.971914] zc3xx: probe 2wr ov vga 0x0000
[97582.143955] zc3xx: probe 2wr ov vga 0x0000
[97584.231990] zc3xx: probe 2wr ov vga 0x0000
[97586.323036] zc3xx: probe 2wr ov vga 0x0000
[97588.416065] zc3xx: probe 2wr ov vga 0x0000
[97590.503101] zc3xx: probe 2wr ov vga 0x0000
[97592.599138] zc3xx: probe 2wr ov vga 0x0000
[97594.679174] zc3xx: probe 2wr ov vga 0x0000
[97596.768210] zc3xx: probe 2wr ov vga 0x0000
[97598.852251] zc3xx: probe 2wr ov vga 0x0000
[97600.928282] zc3xx: probe 2wr ov vga 0x0000
[97603.011318] zc3xx: probe 2wr ov vga 0x0000
[97605.091356] zc3xx: probe 2wr ov vga 0x0000
[97607.179391] zc3xx: probe 2wr ov vga 0x0000
[97609.268430] zc3xx: probe 2wr ov vga 0x0000
[97611.359465] zc3xx: probe 2wr ov vga 0x0000
[97613.451500] zc3xx: probe 2wr ov vga 0x0000
[97615.515536] zc3xx: probe 2wr ov vga 0x0000
[97617.603574] zc3xx: probe 2wr ov vga 0x0000
[97619.691611] zc3xx: probe 2wr ov vga 0x0000
[97621.787646] zc3xx: probe 2wr ov vga 0x0000
[97623.867683] zc3xx: probe 2wr ov vga 0x0000
[97625.954721] zc3xx: probe 2wr ov vga 0x0000
[97628.039756] zc3xx: probe 2wr ov vga 0x0000
[97630.119794] zc3xx: probe 2wr ov vga 0x0000
[97632.203829] zc3xx: probe 2wr ov vga 0x0000
[97634.287864] zc3xx: probe 2wr ov vga 0x0000
[97636.371900] zc3xx: probe 2wr ov vga 0x0000
[97638.479937] zc3xx: probe 2wr ov vga 0x0000
[97640.567973] zc3xx: probe 2wr ov vga 0x0000
[97642.660014] zc3xx: probe 2wr ov vga 0x0000
[97644.756049] zc3xx: probe 2wr ov vga 0x0000
[97646.855132] zc3xx: probe 2wr ov vga 0x0000
[97648.943121] zc3xx: probe 2wr ov vga 0x0000
[97651.047157] zc3xx: probe 2wr ov vga 0x0000
[97653.147195] zc3xx: probe 2wr ov vga 0x0000
[97655.235231] zc3xx: probe 2wr ov vga 0x0000
[97657.303267] zc3xx: probe 2wr ov vga 0x0000
[97659.391304] zc3xx: probe 2wr ov vga 0x0000
[97661.480340] zc3xx: probe 2wr ov vga 0x0000
[97663.571377] zc3xx: probe 2wr ov vga 0x0000
[97665.663413] zc3xx: probe 2wr ov vga 0x0000
[97667.735450] zc3xx: probe 2wr ov vga 0x0000
[97669.823484] zc3xx: probe 2wr ov vga 0x0000
[97671.920523] zc3xx: probe 2wr ov vga 0x0000
[97674.011558] zc3xx: probe 2wr ov vga 0x0000
[97676.075594] zc3xx: probe 2wr ov vga 0x0000
[97678.139631] zc3xx: probe 2wr ov vga 0x0000
[97680.223667] zc3xx: probe 2wr ov vga 0x0000
[97682.307702] zc3xx: probe 2wr ov vga 0x0000
[97684.403739] zc3xx: probe 2wr ov vga 0x0000
[97686.495777] zc3xx: probe 2wr ov vga 0x0000
[97688.591814] zc3xx: probe 2wr ov vga 0x0000
[97690.683851] zc3xx: probe 2wr ov vga 0x0000
[97692.767885] zc3xx: probe 2wr ov vga 0x0000
[97694.847984] zc3xx: probe 2wr ov vga 0x0000
[97696.931959] zc3xx: probe 2wr ov vga 0x0000
[97698.995995] zc3xx: probe 2wr ov vga 0x0000
[97701.087032] zc3xx: probe 2wr ov vga 0x0000
[97703.187069] zc3xx: probe 2wr ov vga 0x0000
[97705.279102] zc3xx: probe 2wr ov vga 0x0000
[97707.375142] zc3xx: probe 2wr ov vga 0x0000
[97709.472173] zc3xx: probe 2wr ov vga 0x0000
[97711.567215] zc3xx: probe 2wr ov vga 0x0000
[97713.655252] zc3xx: probe 2wr ov vga 0x0000
[97715.723285] zc3xx: probe 2wr ov vga 0x0000
[97717.807321] zc3xx: probe 2wr ov vga 0x0000
[97719.887359] zc3xx: probe 2wr ov vga 0x0000
[97721.979395] zc3xx: probe 2wr ov vga 0x0000
[97724.071433] zc3xx: probe 2wr ov vga 0x0000
[97726.155467] zc3xx: probe 2wr ov vga 0x0000
[97728.236569] zc3xx: probe 2wr ov vga 0x0000
[97730.323543] zc3xx: probe 2wr ov vga 0x0000
[97732.423577] zc3xx: probe 2wr ov vga 0x0000
[97734.507613] zc3xx: probe 2wr ov vga 0x0000
[97736.599651] zc3xx: probe 2wr ov vga 0x0000
[97738.695687] zc3xx: probe 2wr ov vga 0x0000
[97740.779722] zc3xx: probe 2wr ov vga 0x0000
[97742.871758] zc3xx: probe 2wr ov vga 0x0000
[97744.951799] zc3xx: probe 2wr ov vga 0x0000
[97747.035834] zc3xx: probe 2wr ov vga 0x0000
[97749.119868] zc3xx: probe 2wr ov vga 0x0000
[97751.212908] zc3xx: probe 2wr ov vga 0x0000
[97753.291941] zc3xx: probe 2wr ov vga 0x0000
[97755.371976] zc3xx: probe 2wr ov vga 0x0000
[97757.456015] zc3xx: probe 2wr ov vga 0x0000
[97759.535050] zc3xx: probe 2wr ov vga 0x0000
[97761.619086] zc3xx: probe 2wr ov vga 0x0000
[97763.704124] zc3xx: probe 2wr ov vga 0x0000
[97765.787159] zc3xx: probe 2wr ov vga 0x0000
[97767.871194] zc3xx: probe 2wr ov vga 0x0000
[97769.964233] zc3xx: probe 2wr ov vga 0x0000
[97772.055268] zc3xx: probe 2wr ov vga 0x0000
[97774.143305] zc3xx: probe 2wr ov vga 0x0000
[97776.239342] zc3xx: probe 2wr ov vga 0x0000
[97778.343379] zc3xx: probe 2wr ov vga 0x0000
[97780.319413] zc3xx: probe 2wr ov vga 0x0000
[97782.407446] zc3xx: probe 2wr ov vga 0x0000
[97784.503485] zc3xx: probe 2wr ov vga 0x0000
[97786.571523] zc3xx: probe 2wr ov vga 0x0000
[97788.655559] zc3xx: probe 2wr ov vga 0x0000
[97790.751594] zc3xx: probe 2wr ov vga 0x0000
[97792.819631] zc3xx: probe 2wr ov vga 0x0000
[97794.907667] zc3xx: probe 2wr ov vga 0x0000
[97796.995703] zc3xx: probe 2wr ov vga 0x0000
[97799.079742] zc3xx: probe 2wr ov vga 0x0000
[97801.159776] zc3xx: probe 2wr ov vga 0x0000
[97803.223815] zc3xx: probe 2wr ov vga 0x0000
[97805.307844] zc3xx: probe 2wr ov vga 0x0000
[97807.399885] zc3xx: probe 2wr ov vga 0x0000
[97809.483921] zc3xx: probe 2wr ov vga 0x0000
[97811.571959] zc3xx: probe 2wr ov vga 0x0000
[97813.655995] zc3xx: probe 2wr ov vga 0x0000
[97815.724032] zc3xx: probe 2wr ov vga 0x0000
[97817.819067] zc3xx: probe 2wr ov vga 0x0000
[97819.911105] zc3xx: probe 2wr ov vga 0x0000
[97822.028143] zc3xx: probe 2wr ov vga 0x0000
[98265.079875] zc3xx: probe 2wr ov vga 0x0000
[98267.027909] zc3xx: probe 2wr ov vga 0x0000
[98269.123945] zc3xx: probe 2wr ov vga 0x0000
[98271.207982] zc3xx: probe 2wr ov vga 0x0000
[98273.299016] zc3xx: probe 2wr ov vga 0x0000
[98275.387054] zc3xx: probe 2wr ov vga 0x0000
[98277.475092] zc3xx: probe 2wr ov vga 0x0000
[98279.560129] zc3xx: probe 2wr ov vga 0x0000
[98281.651162] zc3xx: probe 2wr ov vga 0x0000
[98283.739204] zc3xx: probe 2wr ov vga 0x0000
[98285.827242] zc3xx: probe 2wr ov vga 0x0000
[98287.927273] zc3xx: probe 2wr ov vga 0x0000
[98290.016312] zc3xx: probe 2wr ov vga 0x0000
[98292.099346] zc3xx: probe 2wr ov vga 0x0000
[98294.179383] zc3xx: probe 2wr ov vga 0x0000
[98296.275420] zc3xx: probe 2wr ov vga 0x0000
[98298.359456] zc3xx: probe 2wr ov vga 0x0000
[98300.439492] zc3xx: probe 2wr ov vga 0x0000
[98302.531528] zc3xx: probe 2wr ov vga 0x0000
[98304.615566] zc3xx: probe 2wr ov vga 0x0000
[98306.695601] zc3xx: probe 2wr ov vga 0x0000
[98308.787638] zc3xx: probe 2wr ov vga 0x0000
[98310.879674] zc3xx: probe 2wr ov vga 0x0000
[98312.967711] zc3xx: probe 2wr ov vga 0x0000
[98315.055747] zc3xx: probe 2wr ov vga 0x0000
[98317.143784] zc3xx: probe 2wr ov vga 0x0000
[98319.227821] zc3xx: probe 2wr ov vga 0x0000
[98321.307856] zc3xx: probe 2wr ov vga 0x0000
[98323.387891] zc3xx: probe 2wr ov vga 0x0000
[98325.471928] zc3xx: probe 2wr ov vga 0x0000
[98327.563966] zc3xx: probe 2wr ov vga 0x0000
[98329.648002] zc3xx: probe 2wr ov vga 0x0000
[98331.739042] zc3xx: probe 2wr ov vga 0x0000
[98333.831075] zc3xx: probe 2wr ov vga 0x0000
[98335.919112] zc3xx: probe 2wr ov vga 0x0000
[98338.003148] zc3xx: probe 2wr ov vga 0x0000
[98340.087185] zc3xx: probe 2wr ov vga 0x0000
[98342.179220] zc3xx: probe 2wr ov vga 0x0000
[98344.251257] zc3xx: probe 2wr ov vga 0x0000
[98346.336293] zc3xx: probe 2wr ov vga 0x0000
[98348.423328] zc3xx: probe 2wr ov vga 0x0000
[98350.511365] zc3xx: probe 2wr ov vga 0x0000
[98352.603402] zc3xx: probe 2wr ov vga 0x0000
[98354.687439] zc3xx: probe 2wr ov vga 0x0000
[98356.775476] zc3xx: probe 2wr ov vga 0x0000
[98358.871512] zc3xx: probe 2wr ov vga 0x0000
[98360.955548] zc3xx: probe 2wr ov vga 0x0000
[98363.039584] zc3xx: probe 2wr ov vga 0x0000
[98365.131622] zc3xx: probe 2wr ov vga 0x0000
[98367.215657] zc3xx: probe 2wr ov vga 0x0000
[98369.311698] zc3xx: probe 2wr ov vga 0x0000
[98371.399729] zc3xx: probe 2wr ov vga 0x0000
[98373.483767] zc3xx: probe 2wr ov vga 0x0000
[98375.575803] zc3xx: probe 2wr ov vga 0x0000
[98377.659840] zc3xx: probe 2wr ov vga 0x0000
[98379.739877] zc3xx: probe 2wr ov vga 0x0000
[98381.819913] zc3xx: probe 2wr ov vga 0x0000
[98383.899949] zc3xx: probe 2wr ov vga 0x0000
[98385.987985] zc3xx: probe 2wr ov vga 0x0000
[98388.076023] zc3xx: probe 2wr ov vga 0x0000
[98390.163060] zc3xx: probe 2wr ov vga 0x0000
[98392.255095] zc3xx: probe 2wr ov vga 0x0000
[98394.343131] zc3xx: probe 2wr ov vga 0x0000
[98396.423166] zc3xx: probe 2wr ov vga 0x0000
[98398.516205] zc3xx: probe 2wr ov vga 0x0000
[98400.599244] zc3xx: probe 2wr ov vga 0x0000
[98402.687277] zc3xx: probe 2wr ov vga 0x0000
[98404.787314] zc3xx: probe 2wr ov vga 0x0000
[98406.867350] zc3xx: probe 2wr ov vga 0x0000
[98408.952390] zc3xx: probe 2wr ov vga 0x0000
[98411.035421] zc3xx: probe 2wr ov vga 0x0000
[98413.128576] zc3xx: probe 2wr ov vga 0x0000
[98415.208497] zc3xx: probe 2wr ov vga 0x0000
[98417.295533] zc3xx: probe 2wr ov vga 0x0000
[98419.383567] zc3xx: probe 2wr ov vga 0x0000
[98421.467605] zc3xx: probe 2wr ov vga 0x0000
[98423.551639] zc3xx: probe 2wr ov vga 0x0000
[98425.635678] zc3xx: probe 2wr ov vga 0x0000
[98427.719712] zc3xx: probe 2wr ov vga 0x0000
[99299.991944] zc3xx: probe 2wr ov vga 0x0000
[99301.951979] zc3xx: probe 2wr ov vga 0x0000
[99304.044016] zc3xx: probe 2wr ov vga 0x0000
[99306.127051] zc3xx: probe 2wr ov vga 0x0000
[99308.211088] zc3xx: probe 2wr ov vga 0x0000
[99310.304126] zc3xx: probe 2wr ov vga 0x0000
[99312.399160] zc3xx: probe 2wr ov vga 0x0000
[99314.475199] zc3xx: probe 2wr ov vga 0x0000
[99316.556237] zc3xx: probe 2wr ov vga 0x0000
[99317.145193] compiz.real[4175]: segfault at 2da0 ip b5c357d5 sp bfb58bf0 error 4 in libthumbnail.so[b5c33000+7000]
[101750.991067] usb 1-5: USB disconnect, address 5
[180968.331572] zc3xx: probe 2wr ov vga 0x0000
[180993.247983] zc3xx: probe 2wr ov vga 0x0000
[180995.240015] zc3xx: probe 2wr ov vga 0x0000
[181018.589400] zc3xx: probe 2wr ov vga 0x0000
[181020.628437] zc3xx: probe 2wr ov vga 0x0000
[181022.571466] zc3xx: probe 2wr ov vga 0x0000
[181024.571497] zc3xx: probe 2wr ov vga 0x0000
[181026.523529] zc3xx: probe 2wr ov vga 0x0000
[181050.415921] zc3xx: probe 2wr ov vga 0x0000
[181086.039510] zc3xx: probe 2wr ov vga 0x0000
[181493.760035] usb 4-2: USB disconnect, address 2
[181493.760206] gspca: disconnect complete
[181494.248011] usb 4-2: new full speed USB device using uhci_hcd and address 3
[181494.436322] usb 4-2: configuration #1 chosen from 1 choice
[181494.439286] gspca: probing 046d:08d7
[181496.068267] zc3xx: probe 2wr ov vga 0x0000
[181496.186267] zc3xx: probe 3wr vga 1 0x0000
[181496.399274] zc3xx: probe 3wr vga 2 0x0000
[181496.444272] zc3xx: Sensor UNKNOW_0 force Tas5130
[181496.449271] gspca: set interface 0 err -71
[181496.449283] zc3xx: probe of 4-2:1.0 failed with error -71
[181496.481040] usb 4-2: USB disconnect, address 3

```

not bad huh????

Still without signal....

lspci -nn
```
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port [8086:29c1] (rev 02)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 02)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 02)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 02)
00:1c.5 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 [8086:294a] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 92)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801IB (ICH9) LPC Interface Controller [8086:2918] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801IB (ICH9) 2 port SATA IDE Controller [8086:2921] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 02)
00:1f.5 IDE interface [0101]: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller [8086:2926] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation GeForce 8800 GT [10de:0611] (rev a2)
02:00.0 Ethernet controller [0200]: Attansic Technology Corp. L1 Gigabit Ethernet Adapter [1969:1048] (rev b0)
03:00.0 SATA controller [0106]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 03)
03:00.1 IDE interface [0101]: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller [197b:2363] (rev 03)
05:01.0 Multimedia audio controller [0401]: Creative Labs SB X-Fi [1102:0005]
05:02.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
05:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller [1106:3044] (rev c0)

```

any ideas?

---

### Post by dimis80 on 2009-06-04
any help, please?

---

### Post by nengracia on 2009-06-04
You're right lovinlinux that even if video1 is created when 2 capture devices are plugged in, they both seem to be using video0. How to resolve this is alien to me.

Dimis80, even if you set TVTime to use video1 and not get a signal, it still is "broken". Meaning it's still a concern. :)

Any help from the experts?

---

### Post by little_penguin on 2009-06-04
I think the solution might be to write a udev rule. I'm no expert on that, so perhaps this link might help or at least put you on the right lines:

[http://www.linuxquestions.org/questions/linux-hardware-18/how-can-i-assign-a-webcam-to-a-specific-devvideo-669507/](http://www.linuxquestions.org/questions/linux-hardware-18/how-can-i-assign-a-webcam-to-a-specific-devvideo-669507/)

Regards,
little penguin

---

### Post by cariboo on 2009-06-04
With my webcam pugged in on boot, it defaults to /dev/video1. By editting /etc/tvtime/tvtime.xml so that it uses /dev/vidoe0. I have zero problems. 

I have a Logitech Quickcam Messanger and an MSI TV@nywhere.

---

### Post by nengracia on 2009-06-05
> **cariboo907 said:**
> With my webcam pugged in on boot, it defaults to /dev/video1. By editting /etc/tvtime/tvtime.xml so that it uses /dev/vidoe0. I have zero problems. 

I have a Logitech Quickcam Messanger and an MSI TV@nywhere.


I use the same kind of webcam. Are they both working? Can you use your webcam while watching tv on TVTime?

If so, can you show us how it's done?

---

### Post by nengracia on 2009-06-10
Hi cariboo907,

When I boot with the webcam plugged in, TVTime doesn't work. What I did therefore is to direct TVTime to use video1 - it worked.

Now how do I check the webcam if it's working?

---

