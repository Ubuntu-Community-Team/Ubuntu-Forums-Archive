---
title: "MythTV: Channel Scan Timeout &quot;no tables&quot;"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by Noky on 2008-01-23
I've done a search and I'm experiencing some problems that are not exactly new as much as they are unsolved.

[http://ubuntuforums.org/showthread.php?t=641934&highlight=tables]("http://ubuntuforums.org/showthread.php?t=641934&highlight=tables") AND [http://ubuntuforums.org/showthread.php?t=643528]("http://ubuntuforums.org/showthread.php?t=643528") both seem to be the problem I'm having. I checked the thread: [http://ubuntuforums.org/showthread.php?t=646204]("http://ubuntuforums.org/showthread.php?t=646204") which points to the problem having to do with my firmware.

According to the wiki information here: [http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder]("http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder") I shouldn't have to do anything to get my HDTV wonder working but I should be able to probe it using the command: ```
# modprobe cx88-dvb
``` and check the output with ```
# dmesg
```

Currently, I have the card setup using DVB as one capture card and V4L as another capture card. V4L produces analog channels and DVB produces the ATSC OTA HD.

THe funny thing is I had the card configured as much a single capture card under DVB last night and it worked great. I woke up this morning and I couldn't get anything. I tried rescanning all my channels and started having the table issue. After awhile I tried deleting the entire configuration and readding the card but right now seeing as HD won't work I've settled with using the card to do analog (hence the two devices). I've also tried dropping the mythconverg database and re-running the mythdatabase installation in order to clear all my settings. Needless to say, nothing has worked. Also, I "repaired" all of my MYI files even though they didn't have any problems.

When I ran the modprobe and the dmseg I came up with a suprising output:
 ```
[ 3505.836384] nxt200x: error writing to tuner
[ 3505.840995] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -121)
[ 3505.977845] nxt200x: Timeout waiting for nxt2004 to init.
[ 3506.173254] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -121)
[ 3506.173257] nxt200x: error writing to tuner
[ 3506.177869] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -121)
[ 3506.316256] nxt200x: Timeout waiting for nxt2004 to init.
[ 3506.511666] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -121)
[ 3506.511668] nxt200x: error writing to tuner
[ 3506.516280] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -121)
[ 3506.653130] nxt200x: Timeout waiting for nxt2004 to init.
[ 3506.848536] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -121)
[ 3506.848539] nxt200x: error writing to tuner
[ 3506.853150] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -121)
[ 3506.990003] nxt200x: Timeout waiting for nxt2004 to init.
[ 3507.185409] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -121)
[ 3507.185412] nxt200x: error writing to tuner
[ 3507.190024] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -121)
[ 3507.326876] nxt200x: Timeout waiting for nxt2004 to init.
[ 3507.522283] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -121)
[ 3507.522286] nxt200x: error writing to tuner
[ 3507.526898] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -121)
[ 3507.665289] nxt200x: Timeout waiting for nxt2004 to init.
[ 3507.860695] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -121)
[ 3507.860698] nxt200x: error writing to tuner
[ 3507.865309] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -121)
[ 3508.003700] nxt200x: Timeout waiting for nxt2004 to init.
[ 3508.199106] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -121)
[ 3508.199109] nxt200x: error writing to tuner
[ 3508.203720] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -121)
[ 3508.342111] nxt200x: Timeout waiting for nxt2004 to init.
[ 3508.537518] nxt200x: i2c_writebytes: i2c write error (addr 0x00, err == -121)
[ 3508.537521] nxt200x: error writing to tuner
[ 3508.542132] nxt200x: i2c_readbytes: i2c read error (addr 0x00, err == -121)
[ 3508.680522] nxt200x: Timeout waiting for nxt2004 to init.
[ 9544.533854] nxt200x: Timeout waiting for nxt2004 to init.
[ 9544.916875] nxt200x: Timeout waiting for nxt2004 to init.
[ 9545.299895] nxt200x: Timeout waiting for nxt2004 to init.
[ 9545.684454] nxt200x: Timeout waiting for nxt2004 to init.
[ 9545.945954] nxt200x: Timeout waiting for nxt2004 to init.
[ 9546.328974] nxt200x: Timeout waiting for nxt2004 to init.
[ 9546.711995] nxt200x: Timeout waiting for nxt2004 to init.
[ 9547.093478] nxt200x: Timeout waiting for nxt2004 to init.
[ 9547.351900] nxt200x: Timeout waiting for nxt2004 to init.
[ 9547.719539] nxt200x: Timeout waiting for nxt2004 to init.
[ 9548.051797] nxt200x: Timeout waiting for nxt2004 to init.
[ 9548.384056] nxt200x: Timeout waiting for nxt2004 to init.
[ 9548.728623] nxt200x: Timeout waiting for nxt2004 to init.
[ 9549.060879] nxt200x: Timeout waiting for nxt2004 to init.
[ 9549.393137] nxt200x: Timeout waiting for nxt2004 to init.
[ 9549.723857] nxt200x: Timeout waiting for nxt2004 to init.
[ 9550.079190] nxt200x: Timeout waiting for nxt2004 to init.
[ 9550.408372] nxt200x: Timeout waiting for nxt2004 to init.
[ 9550.737554] nxt200x: Timeout waiting for nxt2004 to init.
[ 9551.066737] nxt200x: Timeout waiting for nxt2004 to init.
[ 9551.432837] nxt200x: Timeout waiting for nxt2004 to init.
[ 9551.762018] nxt200x: Timeout waiting for nxt2004 to init.
[ 9552.091200] nxt200x: Timeout waiting for nxt2004 to init.
[ 9552.421921] nxt200x: Timeout waiting for nxt2004 to init.
[ 9552.617276] nxt200x: Timeout waiting for nxt2004 to init.
[ 9552.946459] nxt200x: Timeout waiting for nxt2004 to init.
[ 9553.277180] nxt200x: Timeout waiting for nxt2004 to init.
[ 9553.609439] nxt200x: Timeout waiting for nxt2004 to init.
[ 9553.964771] nxt200x: Timeout waiting for nxt2004 to init.
[ 9554.293952] nxt200x: Timeout waiting for nxt2004 to init.
[ 9554.623135] nxt200x: Timeout waiting for nxt2004 to init.
[ 9554.955419] nxt200x: Timeout waiting for nxt2004 to init.
[ 9555.310752] nxt200x: Timeout waiting for nxt2004 to init.
[ 9555.643010] nxt200x: Timeout waiting for nxt2004 to init.
[ 9555.975269] nxt200x: Timeout waiting for nxt2004 to init.
[ 9556.532304] nxt200x: Timeout waiting for nxt2004 to init.
[ 9557.433152] nxt200x: Timeout waiting for nxt2004 to init.
[ 9558.031218] nxt200x: Timeout waiting for nxt2004 to init.
[ 9558.466851] nxt200x: Timeout waiting for nxt2004 to init.
[ 9558.799110] nxt200x: Timeout waiting for nxt2004 to init.
[ 9559.149827] nxt200x: Timeout waiting for nxt2004 to init.
[ 9559.482104] nxt200x: Timeout waiting for nxt2004 to init.
[ 9559.814345] nxt200x: Timeout waiting for nxt2004 to init.
[ 9560.146603] nxt200x: Timeout waiting for nxt2004 to init.
[ 9560.501936] nxt200x: Timeout waiting for nxt2004 to init.
[ 9560.834194] nxt200x: Timeout waiting for nxt2004 to init.
[ 9561.166453] nxt200x: Timeout waiting for nxt2004 to init.
[ 9561.498712] nxt200x: Timeout waiting for nxt2004 to init.
[ 9561.694067] nxt200x: Timeout waiting for nxt2004 to init.
[ 9562.026326] nxt200x: Timeout waiting for nxt2004 to init.
[ 9562.358585] nxt200x: Timeout waiting for nxt2004 to init.
[ 9562.690843] nxt200x: Timeout waiting for nxt2004 to init.
[ 9563.044640] nxt200x: Timeout waiting for nxt2004 to init.
[ 9563.243043] cx88[0]/2-mpeg: cx8802_timeout
[ 9563.438399] cx88[0]/2-mpeg: cx8802_timeout
[ 9563.630679] cx88[0]/2-mpeg: cx8802_timeout
[ 9563.822957] cx88[0]/2-mpeg: cx8802_timeout
[ 9564.015236] cx88[0]/2-mpeg: cx8802_timeout
[ 9564.207516] cx88[0]/2-mpeg: cx8802_timeout
[ 9564.399796] cx88[0]/2-mpeg: cx8802_timeout
[ 9564.592075] cx88[0]/2-mpeg: cx8802_timeout
[ 9564.784354] cx88[0]/2-mpeg: cx8802_timeout
[ 9564.976633] cx88[0]/2-mpeg: cx8802_timeout
[ 9565.168913] cx88[0]/2-mpeg: cx8802_timeout
[ 9565.361192] cx88[0]/2-mpeg: cx8802_timeout
[ 9565.541192] nxt200x: Timeout waiting for nxt2004 to init.
[ 9565.873450] nxt200x: Timeout waiting for nxt2004 to init.
[ 9566.205709] nxt200x: Timeout waiting for nxt2004 to init.
[ 9566.539506] nxt200x: Timeout waiting for nxt2004 to init.
[ 9566.890223] nxt200x: Timeout waiting for nxt2004 to init.
[ 9567.222482] nxt200x: Timeout waiting for nxt2004 to init.
[ 9567.554741] nxt200x: Timeout waiting for nxt2004 to init.
[ 9567.886999] nxt200x: Timeout waiting for nxt2004 to init.
[ 9568.237717] nxt200x: Timeout waiting for nxt2004 to init.
[ 9568.569976] nxt200x: Timeout waiting for nxt2004 to init.
[ 9568.902234] nxt200x: Timeout waiting for nxt2004 to init.
[ 9569.234493] nxt200x: Timeout waiting for nxt2004 to init.
[ 9569.588287] nxt200x: Timeout waiting for nxt2004 to init.
[ 9569.920545] nxt200x: Timeout waiting for nxt2004 to init.
[ 9570.252804] nxt200x: Timeout waiting for nxt2004 to init.
[ 9570.585063] nxt200x: Timeout waiting for nxt2004 to init.
[ 9570.935780] nxt200x: Timeout waiting for nxt2004 to init.
[ 9571.268039] nxt200x: Timeout waiting for nxt2004 to init.
[ 9571.600297] nxt200x: Timeout waiting for nxt2004 to init.
[ 9571.932556] nxt200x: Timeout waiting for nxt2004 to init.
[ 9572.126373] nxt200x: Timeout waiting for nxt2004 to init.
[ 9572.458632] nxt200x: Timeout waiting for nxt2004 to init.
[ 9572.790892] nxt200x: Timeout waiting for nxt2004 to init.
[ 9573.123151] nxt200x: Timeout waiting for nxt2004 to init.
[ 9573.472329] nxt200x: Timeout waiting for nxt2004 to init.
[ 9573.804588] nxt200x: Timeout waiting for nxt2004 to init.
[ 9574.136847] nxt200x: Timeout waiting for nxt2004 to init.
[ 9574.469105] nxt200x: Timeout waiting for nxt2004 to init.
[ 9574.818284] nxt200x: Timeout waiting for nxt2004 to init.
[ 9575.152081] nxt200x: Timeout waiting for nxt2004 to init.
[ 9575.485879] nxt200x: Timeout waiting for nxt2004 to init.
[ 9575.818136] nxt200x: Timeout waiting for nxt2004 to init.
[ 9576.165778] nxt200x: Timeout waiting for nxt2004 to init.
[ 9576.499575] nxt200x: Timeout waiting for nxt2004 to init.
[ 9576.831833] nxt200x: Timeout waiting for nxt2004 to init.
[ 9577.164092] nxt200x: Timeout waiting for nxt2004 to init.
[ 9577.359447] nxt200x: Timeout waiting for nxt2004 to init.
[ 9577.691706] nxt200x: Timeout waiting for nxt2004 to init.
[ 9578.023965] nxt200x: Timeout waiting for nxt2004 to init.
[ 9578.356225] nxt200x: Timeout waiting for nxt2004 to init.
[ 9578.710038] nxt200x: Timeout waiting for nxt2004 to init.
[ 9579.042277] nxt200x: Timeout waiting for nxt2004 to init.
[ 9579.374536] nxt200x: Timeout waiting for nxt2004 to init.
[ 9579.706795] nxt200x: Timeout waiting for nxt2004 to init.
[ 9580.057511] nxt200x: Timeout waiting for nxt2004 to init.
[ 9580.362058] cx88[0]/2-mpeg: cx8802_timeout
[ 9580.554335] cx88[0]/2-mpeg: cx8802_timeout
[ 9580.723568] nxt200x: Timeout waiting for nxt2004 to init.
[ 9580.746615] cx88[0]/2-mpeg: cx8802_timeout
[ 9580.938895] cx88[0]/2-mpeg: cx8802_timeout
[ 9581.074285] nxt200x: Timeout waiting for nxt2004 to init.
[ 9581.131173] cx88[0]/2-mpeg: cx8802_timeout
[ 9581.323453] cx88[0]/2-mpeg: cx8802_timeout
[ 9581.515732] cx88[0]/2-mpeg: cx8802_timeout
[ 9581.708012] cx88[0]/2-mpeg: cx8802_timeout
[ 9581.900291] cx88[0]/2-mpeg: cx8802_timeout
[ 9582.092571] cx88[0]/2-mpeg: cx8802_timeout
[ 9582.284849] cx88[0]/2-mpeg: cx8802_timeout
[ 9582.464849] nxt200x: Timeout waiting for nxt2004 to init.
[ 9582.797107] nxt200x: Timeout waiting for nxt2004 to init.
[ 9583.129365] nxt200x: Timeout waiting for nxt2004 to init.
[ 9583.461624] nxt200x: Timeout waiting for nxt2004 to init.
[ 9583.812342] nxt200x: Timeout waiting for nxt2004 to init.
[ 9584.144601] nxt200x: Timeout waiting for nxt2004 to init.
[ 9584.476859] nxt200x: Timeout waiting for nxt2004 to init.
[ 9584.809118] nxt200x: Timeout waiting for nxt2004 to init.
[ 9585.161373] nxt200x: Timeout waiting for nxt2004 to init.
[ 9585.493632] nxt200x: Timeout waiting for nxt2004 to init.
[ 9585.825890] nxt200x: Timeout waiting for nxt2004 to init.
[ 9586.158149] nxt200x: Timeout waiting for nxt2004 to init.
[ 9586.508867] nxt200x: Timeout waiting for nxt2004 to init.
[ 9586.841125] nxt200x: Timeout waiting for nxt2004 to init.
[ 9587.173384] nxt200x: Timeout waiting for nxt2004 to init.
[ 9587.505643] nxt200x: Timeout waiting for nxt2004 to init.
[ 9587.700998] nxt200x: Timeout waiting for nxt2004 to init.
[ 9588.033257] nxt200x: Timeout waiting for nxt2004 to init.
[ 9588.365516] nxt200x: Timeout waiting for nxt2004 to init.
[ 9588.699313] nxt200x: Timeout waiting for nxt2004 to init.
[ 9589.053107] nxt200x: Timeout waiting for nxt2004 to init.
[ 9589.345347] cx88[0]/2-mpeg: cx8802_timeout
[ 9589.537626] cx88[0]/2-mpeg: cx8802_timeout
[ 9589.729905] cx88[0]/2-mpeg: cx8802_timeout
[ 9589.922185] cx88[0]/2-mpeg: cx8802_timeout
[ 9590.114464] cx88[0]/2-mpeg: cx8802_timeout
[ 9590.306743] cx88[0]/2-mpeg: cx8802_timeout
[ 9590.499022] cx88[0]/2-mpeg: cx8802_timeout
[ 9590.691302] cx88[0]/2-mpeg: cx8802_timeout
[ 9590.883581] cx88[0]/2-mpeg: cx8802_timeout
[ 9591.075860] cx88[0]/2-mpeg: cx8802_timeout
[ 9591.268140] cx88[0]/2-mpeg: cx8802_timeout
[ 9591.448139] nxt200x: Timeout waiting for nxt2004 to init.
[ 9591.646545] cx88[0]/2-mpeg: cx8802_timeout
[ 9591.838825] cx88[0]/2-mpeg: cx8802_timeout
[ 9592.031104] cx88[0]/2-mpeg: cx8802_timeout
[ 9592.223384] cx88[0]/2-mpeg: cx8802_timeout
[ 9592.415662] cx88[0]/2-mpeg: cx8802_timeout
[ 9592.607942] cx88[0]/2-mpeg: cx8802_timeout
[ 9592.800221] cx88[0]/2-mpeg: cx8802_timeout
[ 9592.992501] cx88[0]/2-mpeg: cx8802_timeout
[ 9593.184780] cx88[0]/2-mpeg: cx8802_timeout
[ 9593.377059] cx88[0]/2-mpeg: cx8802_timeout
[ 9593.569339] cx88[0]/2-mpeg: cx8802_timeout
[ 9593.761618] cx88[0]/2-mpeg: cx8802_timeout
[ 9593.941616] nxt200x: Timeout waiting for nxt2004 to init.
[ 9594.280027] nxt200x: Timeout waiting for nxt2004 to init.
[ 9594.630745] nxt200x: Timeout waiting for nxt2004 to init.
[ 9594.829153] cx88[0]/2-mpeg: cx8802_timeout
[ 9595.021432] cx88[0]/2-mpeg: cx8802_timeout
[ 9595.213711] cx88[0]/2-mpeg: cx8802_timeout
[ 9595.405991] cx88[0]/2-mpeg: cx8802_timeout
[ 9595.598269] cx88[0]/2-mpeg: cx8802_timeout
[ 9595.790549] cx88[0]/2-mpeg: cx8802_timeout
[ 9595.982828] cx88[0]/2-mpeg: cx8802_timeout
[ 9595.999774] nxt200x: Timeout waiting for nxt2004 to init.
[ 9596.175107] cx88[0]/2-mpeg: cx8802_timeout
[ 9596.355106] nxt200x: Timeout waiting for nxt2004 to init.
[ 9596.598122] cx88[0]/2-mpeg: cx8802_timeout
[ 9596.790402] cx88[0]/2-mpeg: cx8802_timeout
[ 9596.982682] cx88[0]/2-mpeg: cx8802_timeout
[ 9597.174960] cx88[0]/2-mpeg: cx8802_timeout
[ 9597.367240] cx88[0]/2-mpeg: cx8802_timeout
[ 9597.559519] cx88[0]/2-mpeg: cx8802_timeout
[ 9597.751798] cx88[0]/2-mpeg: cx8802_timeout
[ 9597.944078] cx88[0]/2-mpeg: cx8802_timeout
[ 9598.136357] cx88[0]/2-mpeg: cx8802_timeout
[ 9598.328636] cx88[0]/2-mpeg: cx8802_timeout
[ 9598.508634] nxt200x: Timeout waiting for nxt2004 to init.
[ 9598.840893] nxt200x: Timeout waiting for nxt2004 to init.
[ 9599.173152] nxt200x: Timeout waiting for nxt2004 to init.
[ 9599.503872] nxt200x: Timeout waiting for nxt2004 to init.
[ 9599.857666] nxt200x: Timeout waiting for nxt2004 to init.
[ 9600.208383] nxt200x: Timeout waiting for nxt2004 to init.
[ 9600.540642] nxt200x: Timeout waiting for nxt2004 to init.
[ 9600.872900] nxt200x: Timeout waiting for nxt2004 to init.
[ 9601.209773] nxt200x: Timeout waiting for nxt2004 to init.
[ 9601.503552] cx88[0]/2-mpeg: cx8802_timeout
[ 9601.695832] cx88[0]/2-mpeg: cx8802_timeout
[ 9601.888111] cx88[0]/2-mpeg: cx8802_timeout
[ 9602.080390] cx88[0]/2-mpeg: cx8802_timeout
[ 9602.272669] cx88[0]/2-mpeg: cx8802_timeout
[ 9602.464948] cx88[0]/2-mpeg: cx8802_timeout
[ 9602.657228] cx88[0]/2-mpeg: cx8802_timeout
[ 9602.849508] cx88[0]/2-mpeg: cx8802_timeout
[ 9603.041787] cx88[0]/2-mpeg: cx8802_timeout
[ 9603.234066] cx88[0]/2-mpeg: cx8802_timeout
[ 9603.426345] cx88[0]/2-mpeg: cx8802_timeout
[ 9603.607882] nxt200x: Timeout waiting for nxt2004 to init.
[ 9603.938602] nxt200x: Timeout waiting for nxt2004 to init.
[ 9604.270860] nxt200x: Timeout waiting for nxt2004 to init.
[ 9604.603120] nxt200x: Timeout waiting for nxt2004 to init.
[ 9604.798476] nxt200x: Timeout waiting for nxt2004 to init.
[ 9605.130734] nxt200x: Timeout waiting for nxt2004 to init.
[ 9605.461454] nxt200x: Timeout waiting for nxt2004 to init.
[ 9605.793712] nxt200x: Timeout waiting for nxt2004 to init.
[ 9605.990606] nxt200x: Timeout waiting for nxt2004 to init.
[ 9606.321327] nxt200x: Timeout waiting for nxt2004 to init.
[ 9606.652048] nxt200x: Timeout waiting for nxt2004 to init.
[ 9606.984306] nxt200x: Timeout waiting for nxt2004 to init.
[ 9607.336561] nxt200x: Timeout waiting for nxt2004 to init.
[ 9607.668821] nxt200x: Timeout waiting for nxt2004 to init.
[ 9608.001080] nxt200x: Timeout waiting for nxt2004 to init.
[ 9608.333342] nxt200x: Timeout waiting for nxt2004 to init.
[ 9608.682517] nxt200x: Timeout waiting for nxt2004 to init.
[ 9609.014776] nxt200x: Timeout waiting for nxt2004 to init.
[ 9609.347035] nxt200x: Timeout waiting for nxt2004 to init.
[ 9609.679293] nxt200x: Timeout waiting for nxt2004 to init.
[ 9610.030010] nxt200x: Timeout waiting for nxt2004 to init.
[ 9610.362270] nxt200x: Timeout waiting for nxt2004 to init.
[ 9610.692990] nxt200x: Timeout waiting for nxt2004 to init.
[ 9611.023710] nxt200x: Timeout waiting for nxt2004 to init.
[ 9611.375966] nxt200x: Timeout waiting for nxt2004 to init.
[ 9611.745117] cx88[0]/2-mpeg: cx8802_timeout
[ 9611.937397] cx88[0]/2-mpeg: cx8802_timeout
[ 9612.129676] cx88[0]/2-mpeg: cx8802_timeout
[ 9612.321955] cx88[0]/2-mpeg: cx8802_timeout
[ 9612.514234] cx88[0]/2-mpeg: cx8802_timeout
[ 9612.706514] cx88[0]/2-mpeg: cx8802_timeout
[ 9612.898793] cx88[0]/2-mpeg: cx8802_timeout
[ 9613.091073] cx88[0]/2-mpeg: cx8802_timeout
[ 9613.246460] nxt200x: Timeout waiting for nxt2004 to init.
[ 9613.283352] cx88[0]/2-mpeg: cx8802_timeout
[ 9613.475631] cx88[0]/2-mpeg: cx8802_timeout
[ 9613.577179] nxt200x: Timeout waiting for nxt2004 to init.
[ 9613.667910] cx88[0]/2-mpeg: cx8802_timeout
[ 9613.847908] nxt200x: Timeout waiting for nxt2004 to init.
[ 9614.180167] nxt200x: Timeout waiting for nxt2004 to init.
[ 9614.510888] nxt200x: Timeout waiting for nxt2004 to init.
[ 9614.841608] nxt200x: Timeout waiting for nxt2004 to init.
[ 9615.173867] nxt200x: Timeout waiting for nxt2004 to init.
[ 9615.506125] nxt200x: Timeout waiting for nxt2004 to init.
[ 9615.838384] nxt200x: Timeout waiting for nxt2004 to init.
[ 9616.169104] nxt200x: Timeout waiting for nxt2004 to init.
[ 9616.499825] nxt200x: Timeout waiting for nxt2004 to init.
[ 9616.832083] nxt200x: Timeout waiting for nxt2004 to init.
[10200.616462] nxt200x: Timeout waiting for nxt2004 to init.
[10200.945644] nxt200x: Timeout waiting for nxt2004 to init.
[10201.274826] nxt200x: Timeout waiting for nxt2004 to init.
[10201.604009] nxt200x: Timeout waiting for nxt2004 to init.
[10201.962417] nxt200x: Timeout waiting for nxt2004 to init.
[10202.291599] nxt200x: Timeout waiting for nxt2004 to init.
[10202.620782] nxt200x: Timeout waiting for nxt2004 to init.
[10202.949964] nxt200x: Timeout waiting for nxt2004 to init.
[10203.142243] nxt200x: Timeout waiting for nxt2004 to init.
[10203.471425] nxt200x: Timeout waiting for nxt2004 to init.
[10203.800607] nxt200x: Timeout waiting for nxt2004 to init.
[10204.129790] nxt200x: Timeout waiting for nxt2004 to init.
[10204.478969] nxt200x: Timeout waiting for nxt2004 to init.
[10204.808151] nxt200x: Timeout waiting for nxt2004 to init.
[10205.138872] nxt200x: Timeout waiting for nxt2004 to init.
[10205.468054] nxt200x: Timeout waiting for nxt2004 to init.
[10205.821849] nxt200x: Timeout waiting for nxt2004 to init.
[10206.151030] nxt200x: Timeout waiting for nxt2004 to init.
[10206.480213] nxt200x: Timeout waiting for nxt2004 to init.
[10206.809394] nxt200x: Timeout waiting for nxt2004 to init.
[10207.155497] nxt200x: Timeout waiting for nxt2004 to init.
[10207.484680] nxt200x: Timeout waiting for nxt2004 to init.
[10207.813861] nxt200x: Timeout waiting for nxt2004 to init.
[10208.143043] nxt200x: Timeout waiting for nxt2004 to init.
[10208.492223] nxt200x: Timeout waiting for nxt2004 to init.
[10208.821405] nxt200x: Timeout waiting for nxt2004 to init.
[10209.150587] nxt200x: Timeout waiting for nxt2004 to init.
[10209.479770] nxt200x: Timeout waiting for nxt2004 to init.
[10209.825873] nxt200x: Timeout waiting for nxt2004 to init.
[10210.155055] nxt200x: Timeout waiting for nxt2004 to init.
[10210.484237] nxt200x: Timeout waiting for nxt2004 to init.
[10210.813419] nxt200x: Timeout waiting for nxt2004 to init.
[10211.173367] nxt200x: Timeout waiting for nxt2004 to init.
[10211.502549] nxt200x: Timeout waiting for nxt2004 to init.
[10211.831731] nxt200x: Timeout waiting for nxt2004 to init.
[10212.160913] nxt200x: Timeout waiting for nxt2004 to init.
[10212.510092] nxt200x: Timeout waiting for nxt2004 to init.
[10212.839274] nxt200x: Timeout waiting for nxt2004 to init.
[10213.168456] nxt200x: Timeout waiting for nxt2004 to init.
[10213.499177] nxt200x: Timeout waiting for nxt2004 to init.
[10213.691456] nxt200x: Timeout waiting for nxt2004 to init.
[10214.020643] nxt200x: Timeout waiting for nxt2004 to init.
[10214.349820] nxt200x: Timeout waiting for nxt2004 to init.
[10214.679002] nxt200x: Timeout waiting for nxt2004 to init.
[10215.028182] nxt200x: Timeout waiting for nxt2004 to init.
[10215.357364] nxt200x: Timeout waiting for nxt2004 to init.
[10215.686546] nxt200x: Timeout waiting for nxt2004 to init.
[10216.015729] nxt200x: Timeout waiting for nxt2004 to init.
[10216.206470] nxt200x: Timeout waiting for nxt2004 to init.
[10216.535652] nxt200x: Timeout waiting for nxt2004 to init.
[10216.864834] nxt200x: Timeout waiting for nxt2004 to init.
[10217.194017] nxt200x: Timeout waiting for nxt2004 to init.
[10217.383219] nxt200x: Timeout waiting for nxt2004 to init.
[10217.581651] cx88[0]/2-mpeg: cx8802_timeout
[10217.777007] cx88[0]/2-mpeg: cx8802_timeout
[10217.969286] cx88[0]/2-mpeg: cx8802_timeout
[10218.161566] cx88[0]/2-mpeg: cx8802_timeout
[10218.353845] cx88[0]/2-mpeg: cx8802_timeout
[10218.546124] cx88[0]/2-mpeg: cx8802_timeout
[10218.738403] cx88[0]/2-mpeg: cx8802_timeout
[10218.930683] cx88[0]/2-mpeg: cx8802_timeout
[10219.122962] cx88[0]/2-mpeg: cx8802_timeout
[10219.315241] cx88[0]/2-mpeg: cx8802_timeout
[10219.507521] cx88[0]/2-mpeg: cx8802_timeout
[10219.699800] cx88[0]/2-mpeg: cx8802_timeout
[10219.875159] nxt200x: Timeout waiting for nxt2004 to init.
[10220.204342] nxt200x: Timeout waiting for nxt2004 to init.
[10220.533523] nxt200x: Timeout waiting for nxt2004 to init.
[10220.862705] nxt200x: Timeout waiting for nxt2004 to init.
[10221.224191] nxt200x: Timeout waiting for nxt2004 to init.
[10221.553373] nxt200x: Timeout waiting for nxt2004 to init.
[10221.882555] nxt200x: Timeout waiting for nxt2004 to init.
[10222.211737] nxt200x: Timeout waiting for nxt2004 to init.
[10222.573222] nxt200x: Timeout waiting for nxt2004 to init.
[10222.903943] nxt200x: Timeout waiting for nxt2004 to init.
[10223.233125] nxt200x: Timeout waiting for nxt2004 to init.
[10223.562307] nxt200x: Timeout waiting for nxt2004 to init.
[10223.751510] nxt200x: Timeout waiting for nxt2004 to init.
[10224.080692] nxt200x: Timeout waiting for nxt2004 to init.
[10224.409874] nxt200x: Timeout waiting for nxt2004 to init.
[10224.739057] nxt200x: Timeout waiting for nxt2004 to init.
[10224.928259] nxt200x: Timeout waiting for nxt2004 to init.
[10225.257441] nxt200x: Timeout waiting for nxt2004 to init.
[10225.586623] nxt200x: Timeout waiting for nxt2004 to init.
[10225.915806] nxt200x: Timeout waiting for nxt2004 to init.
[10226.275753] nxt200x: Timeout waiting for nxt2004 to init.
[10226.604935] nxt200x: Timeout waiting for nxt2004 to init.
[10226.934117] nxt200x: Timeout waiting for nxt2004 to init.
[10227.263300] nxt200x: Timeout waiting for nxt2004 to init.
[10227.623246] nxt200x: Timeout waiting for nxt2004 to init.
[10227.952429] nxt200x: Timeout waiting for nxt2004 to init.
[10228.284698] nxt200x: Timeout waiting for nxt2004 to init.
[10228.646172] nxt200x: Timeout waiting for nxt2004 to init.
[10229.001505] nxt200x: Timeout waiting for nxt2004 to init.
[10229.384525] nxt200x: Timeout waiting for nxt2004 to init.
[10229.767545] nxt200x: Timeout waiting for nxt2004 to init.
[10230.150567] nxt200x: Timeout waiting for nxt2004 to init.
[10230.413604] nxt200x: Timeout waiting for nxt2004 to init.
[10230.796624] nxt200x: Timeout waiting for nxt2004 to init.
[10231.179645] nxt200x: Timeout waiting for nxt2004 to init.
[10231.562665] nxt200x: Timeout waiting for nxt2004 to init.
[10231.825703] nxt200x: Timeout waiting for nxt2004 to init.
[10232.208724] nxt200x: Timeout waiting for nxt2004 to init.
[10232.591744] nxt200x: Timeout waiting for nxt2004 to init.
[10232.974764] nxt200x: Timeout waiting for nxt2004 to init.
[10233.236264] nxt200x: Timeout waiting for nxt2004 to init.
[10233.619285] nxt200x: Timeout waiting for nxt2004 to init.
[10234.002305] nxt200x: Timeout waiting for nxt2004 to init.
[10234.385325] nxt200x: Timeout waiting for nxt2004 to init.
[10234.648363] nxt200x: Timeout waiting for nxt2004 to init.
[10234.934475] cx88[0]/2-mpeg: cx8802_timeout
[10235.126754] cx88[0]/2-mpeg: cx8802_timeout
[10235.319033] cx88[0]/2-mpeg: cx8802_timeout
[10235.328262] nxt200x: Timeout waiting for nxt2004 to init.
[10235.511313] cx88[0]/2-mpeg: cx8802_timeout
[10235.703591] cx88[0]/2-mpeg: cx8802_timeout
[10235.711283] nxt200x: Timeout waiting for nxt2004 to init.
[10235.895871] cx88[0]/2-mpeg: cx8802_timeout
[10236.072768] nxt200x: Timeout waiting for nxt2004 to init.
[10236.088150] cx88[0]/2-mpeg: cx8802_timeout
[10236.280430] cx88[0]/2-mpeg: cx8802_timeout
[10236.434253] nxt200x: Timeout waiting for nxt2004 to init.
[10236.474247] cx88[0]/2-mpeg: cx8802_timeout
[10236.666527] cx88[0]/2-mpeg: cx8802_timeout
[10236.794200] nxt200x: Timeout waiting for nxt2004 to init.
[10236.858805] cx88[0]/2-mpeg: cx8802_timeout
[10237.066474] nxt200x: Timeout waiting for nxt2004 to init.
[10237.449489] nxt200x: Timeout waiting for nxt2004 to init.
[10237.832509] nxt200x: Timeout waiting for nxt2004 to init.
[10238.215529] nxt200x: Timeout waiting for nxt2004 to init.
[10238.477029] nxt200x: Timeout waiting for nxt2004 to init.
[10238.860049] nxt200x: Timeout waiting for nxt2004 to init.
[10239.243070] nxt200x: Timeout waiting for nxt2004 to init.
[10239.609169] nxt200x: Timeout waiting for nxt2004 to init.
[10239.992190] nxt200x: Timeout waiting for nxt2004 to init.
[10240.375210] nxt200x: Timeout waiting for nxt2004 to init.
[10240.758230] nxt200x: Timeout waiting for nxt2004 to init.
[10240.965892] nxt200x: Timeout waiting for nxt2004 to init.
[10241.348912] nxt200x: Timeout waiting for nxt2004 to init.
[10241.731933] nxt200x: Timeout waiting for nxt2004 to init.
[10242.114953] nxt200x: Timeout waiting for nxt2004 to init.
[10242.376453] nxt200x: Timeout waiting for nxt2004 to init.
[10242.759473] nxt200x: Timeout waiting for nxt2004 to init.
[10243.142494] nxt200x: Timeout waiting for nxt2004 to init.
[10243.525514] nxt200x: Timeout waiting for nxt2004 to init.
[10243.787014] nxt200x: Timeout waiting for nxt2004 to init.
[10243.986984] cx88[0]/2-mpeg: cx8802_timeout
[10244.148499] nxt200x: Timeout waiting for nxt2004 to init.
[10244.182340] cx88[0]/2-mpeg: cx8802_timeout
[10244.374619] cx88[0]/2-mpeg: cx8802_timeout
[10244.566898] cx88[0]/2-mpeg: cx8802_timeout
[10244.759178] cx88[0]/2-mpeg: cx8802_timeout
[10244.951457] cx88[0]/2-mpeg: cx8802_timeout
[10245.143736] cx88[0]/2-mpeg: cx8802_timeout
[10245.336016] cx88[0]/2-mpeg: cx8802_timeout
[10245.528295] cx88[0]/2-mpeg: cx8802_timeout
[10245.720575] cx88[0]/2-mpeg: cx8802_timeout
[10245.912854] cx88[0]/2-mpeg: cx8802_timeout
[10246.105133] cx88[0]/2-mpeg: cx8802_timeout
[10246.312795] nxt200x: Timeout waiting for nxt2004 to init.
[10246.512765] cx88[0]/2-mpeg: cx8802_timeout
[10246.705045] cx88[0]/2-mpeg: cx8802_timeout
[10246.897324] cx88[0]/2-mpeg: cx8802_timeout
[10247.089603] cx88[0]/2-mpeg: cx8802_timeout
[10247.281882] cx88[0]/2-mpeg: cx8802_timeout
[10247.474162] cx88[0]/2-mpeg: cx8802_timeout
[10247.666441] cx88[0]/2-mpeg: cx8802_timeout
[10247.858720] cx88[0]/2-mpeg: cx8802_timeout
[10248.051002] cx88[0]/2-mpeg: cx8802_timeout
[10248.243279] cx88[0]/2-mpeg: cx8802_timeout
[10248.435558] cx88[0]/2-mpeg: cx8802_timeout
[10248.627838] cx88[0]/2-mpeg: cx8802_timeout
[10248.835499] nxt200x: Timeout waiting for nxt2004 to init.
[10249.204675] cx88[0]/2-mpeg: cx8802_timeout
[10249.396955] cx88[0]/2-mpeg: cx8802_timeout
[10249.589234] cx88[0]/2-mpeg: cx8802_timeout
[10249.781513] cx88[0]/2-mpeg: cx8802_timeout
[10249.973793] cx88[0]/2-mpeg: cx8802_timeout
[10250.166072] cx88[0]/2-mpeg: cx8802_timeout
[10250.358351] cx88[0]/2-mpeg: cx8802_timeout
[10250.550630] cx88[0]/2-mpeg: cx8802_timeout
[10250.742910] cx88[0]/2-mpeg: cx8802_timeout
[10250.935189] cx88[0]/2-mpeg: cx8802_timeout
[10251.127468] cx88[0]/2-mpeg: cx8802_timeout
[10251.307442] nxt200x: Timeout waiting for nxt2004 to init.
[10251.618166] cx88[0]/2-mpeg: cx8802_timeout
[10251.810445] cx88[0]/2-mpeg: cx8802_timeout
[10252.002724] cx88[0]/2-mpeg: cx8802_timeout
[10252.159624] nxt200x: Timeout waiting for nxt2004 to init.
[10252.195003] cx88[0]/2-mpeg: cx8802_timeout
[10252.387283] cx88[0]/2-mpeg: cx8802_timeout
[10252.579562] cx88[0]/2-mpeg: cx8802_timeout
[10252.771841] cx88[0]/2-mpeg: cx8802_timeout
[10252.964120] cx88[0]/2-mpeg: cx8802_timeout
[10253.156400] cx88[0]/2-mpeg: cx8802_timeout
[10253.348679] cx88[0]/2-mpeg: cx8802_timeout
[10253.527115] nxt200x: Timeout waiting for nxt2004 to init.
[10253.856296] nxt200x: Timeout waiting for nxt2004 to init.
[10254.187017] nxt200x: Timeout waiting for nxt2004 to init.
[10254.516199] nxt200x: Timeout waiting for nxt2004 to init.
[10254.845381] nxt200x: Timeout waiting for nxt2004 to init.
[10255.174563] nxt200x: Timeout waiting for nxt2004 to init.
[10255.503746] nxt200x: Timeout waiting for nxt2004 to init.
[10255.832928] nxt200x: Timeout waiting for nxt2004 to init.
[10256.163648] nxt200x: Timeout waiting for nxt2004 to init.

```

Doesn't seem like I have any such device. Of course: Preferences > Hardware Information says otherwise with a DVB device under CX23880 using linux.driver cx88-mpeg driver manager.

Any ideas what could be causing this?

UPDATE:[s] I had a brainstorm last night and thought possibly the V4L drivers could be interfering with the cx88 drivers? Two video devices under the CX238800 have v4l drivers running and not nxt2004/dvb/etc. -- I'm not quite sure what is supposed to be running there but would blacklisting V4L mess up anything else with my computer. From what I can see in the hardware information -- only those two video devices are running V4L, everything else related to the TV Tuner has a cx* driver. [/s]

UPDATE: apparently the device is running linux.driver cx8800 but the info.capabilities under the two video devices read video4linux. I have no idea what that means.

UPDATE: I removed the cx drivers and added them back and didn't fix anything. I also went and installed dvb-tools to scan for channels without MythTV and turned up nothing -- I got a few weird fail messages but I googled the result and didn't turn up anything unusual

```
root@tarrick-desktop:/usr/share/doc/dvb-utils/examples/scan/atsc# scan us-ATSC-center-frequencies-8VSB
scanning us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 63028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 69028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 79028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 85028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 177028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 183028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 189028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 195028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 201028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 201028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 207028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 207028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 213028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 213028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 473028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 473028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 479028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 485028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 485028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 491028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 491028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 497028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 497028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 503028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 503028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 509028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 509028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 515028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 515028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 521028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 521028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 527028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 527028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 533028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 533028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 539028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 539028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 545028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 545028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 551028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 557028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 557028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 563028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 563028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 569028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 569028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 575028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 575028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 581028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 581028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 587028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 593028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 599028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 605028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 611028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 611028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 617028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 617028615:8VSB (tuning failed)
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 623028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 629028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 629028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 635028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 635028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 641028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 641028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 647028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 647028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 653028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 653028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 659028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 659028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 665028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 671028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 671028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 677028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 683028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 683028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 689028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 689028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 695028615:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 701028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 701028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 707028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 707028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 713028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 713028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 719028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 719028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 725028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 725028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 731028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 731028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 737028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 737028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 743028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 743028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 749028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 749028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 755028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 755028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 761028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 761028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 767028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 767028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 773028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 773028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 779028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 779028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 785028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 785028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 791028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 791028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 797028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 797028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 803028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 803028615:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (0 services)
Done.
root@tarrick-desktop:/usr/share/doc/dvb-utils/examples/scan/atsc# ls
us-ATSC-center-frequencies-8VSB                 us-ID-Boise
us-Cable-EIA-542-HRC-center-frequencies-QAM256  us-MA-Boston
us-Cable-EIA-542-IRC-center_frequencies-QAM256  us-MI-Lansing
us-Cable-HRC-center-frequencies-QAM256          us-NTSC-center-frequencies-8VSB
us-Cable-IRC-center-frequencies-QAM256          us-NY-TWC-NYC
us-Cable-Standard-center-frequencies-QAM256     us-PA-Philadelphia
us-CA-SF-Bay-Area
root@tarrick-desktop:/usr/share/doc/dvb-utils/examples/scan/atsc# scan us-NTSC-center-frequencies-8VSB
scanning us-NTSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
>>> tune to: 57000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 63000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 63000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 69000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 69000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 79000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 79000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 85000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 85000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 177000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 177000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 183000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 183000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 189000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 189000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 195000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 195000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 201000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 201000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 207000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 207000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 213000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 213000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 473000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 473000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 479000000:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 485000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 485000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 491000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 491000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 497000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 497000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 503000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 503000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 509000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 509000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 515000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 515000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 521000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 521000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 527000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 527000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 533000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 533000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 539000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 539000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 545000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 545000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 551000000:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 557000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 557000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 563000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 563000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 569000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 569000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 575000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 575000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 581000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 581000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 587000000:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 593000000:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 599000000:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 605000000:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 611000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 611000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 617000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 617000000:8VSB (tuning failed)
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 623000000:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 629000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 629000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 635000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 635000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 641000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 641000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 647000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 647000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 653000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 653000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 659000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 659000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 665000000:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 671000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 671000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 677000000:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 683000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 683000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 689000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 689000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 695000000:8VSB
WARNING: filter timeout pid 0x0000
WARNING: filter timeout pid 0x1ffb
>>> tune to: 701000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 701000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 707000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 707000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 713000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 713000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 719000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 719000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 725000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 725000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 731000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 731000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 737000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 737000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 743000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 743000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 749000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 749000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 755000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 755000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 761000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 761000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 767000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 767000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 773000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 773000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 779000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 779000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 785000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 785000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 791000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 791000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 797000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 797000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
>>> tune to: 803000000:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 803000000:8VSB (tuning failed)
WARNING: >>> tuning failed!!!
dumping lists (0 services)
Done.

```

---

### Post by Egonis on 2008-02-18
I have the exact same dmesg, and issues all around.

I am using an AverMedia AverTVHD MCE A180

I am running Mythbuntu 7.10

---

### Post by d_morgan on 2008-03-09
I believe I have the same problem and I wanted to add my findings to this thread.  I have the ati hdtv wonder of course and have had the atsc input functional on ubuntu 7.04 using the install steps described here [http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder](http://www.mythtv.org/wiki/index.php/ATI_HDTV_Wonder) (load firmware, load driver, configure card).  I have used these same steps to get the atsc tunner on the card in ubunu 7.10 before i realized there were new v4l drivers.  When i have tried the v4l drivers I get a picture on the NTSC tuner for other-the-air stations but no sound. When i try the ATSC tuner for over the air stations i can't get the channel scanner to find channels.  I get the same "no tables" as the others in this thread.  I'm going to switch back to the previous install recommendation for atsc only.

I'm am glad to see that work is being done to add functionality.  Video over the NTSC input is nice to see.  If there are any developers from linuxtv.org out there reading we surely can be testers for you if you need it.

---

### Post by curryrice71 on 2008-03-17
I get the no tables error as well. I had given up on this card but messed around with it some more last night, and finally got it to pick up 2 channels, but the rest time out. I get the feeling that depending on where you live, you just need a really good antenna for this card.

I have 2 Pinnacle 800i cards that work great, and work with the crappiest antenna in the world (one I made)

---

### Post by wids on 2008-07-22
I was getting the "no tables" error until i selected the EIT option in Video Sources.

HDHomerun
Ubunutu 8.04
AMD64
OTA
us-broadcast

---

### Post by Noky on 2008-07-23
I tried EIT again and it's still not working. I'm officially giving up on the ATI card, it half works but it's not worth it. Thanks for your reply though.

---

